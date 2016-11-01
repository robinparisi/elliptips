---
id: 2247
title: 'Guide Debian 7 (partie 2/8) : sécuriser l&#8217;accès SSH'
date: 2013-06-20T11:00:57+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=2247
permalink: /guide-debian-7-securiser-lacces-ssh/
dsq_thread_id:
  - "1414639670"
image: /wp-content/uploads/2013/06/open-ssh-logo-180x160.jpg
---
Cet article fait partie d&#8217;une série de billets portant sur la mise en place d&#8217;un serveur sous Debian Wheezy ([voir le sommaire](http://elliptips.info/guide-sur-linstallation-dun-serveur-sous-debian-7-wheezy/ "guide debian wheezy sommaire")).

## Introduction

De la même façon que vous ne laissez pas la porte ouverte en sortant de chez vous, la porte d’entrée de votre serveur, c’est-à-dire l’accès SSH, requiert un minimum de sécurisation.

## **Modifier le mot de passe root**

En général, après la commande d&#8217;un serveur dédié ou virtuel, votre prestataire vous transmettra les informations de connexion par mail, en y joignant le mot de passe du compte root. Il est important de **changer celui-ci immédiatement dès votre première connexion**.

Pour cela, lancez la commande suivante en root :

<pre class="lang:sh decode:true">passwd</pre>

Je ne vous ferai pas l&#8217;affront de vous expliquer pourquoi un mot de passe suffisamment complexe pour ne pas être trouvé pas une attaque de type bruteforce ou dictionnaire est très largement souhaitable 🙂

## **Ajout d’un nouvel utilisateur**

Pour la suite, et pour des raisons de sécurité évidentes, **nous n’utiliserons pas le compte root pour les connexions à distance**. C’est pourquoi nous allons créer un groupe contenant des utilisateurs qui seront autorisés à se connecter via SSH.

<pre class="lang:sh decode:true">groupadd sshusers</pre>

On créé ensuite un nouvel utilisateur puis on l&#8217;ajoute au groupe qui sera autorisé à se connecter via SSH.

<pre class="lang:sh decode:true">useradd -m homer
passwd homer
usermod -a -G sshusers homer</pre>

## **Configuration de ssh**

<pre class="lang:sh decode:true">vim /etc/ssh/sshd_config</pre>

On commence par changer le port par défaut :

<pre class="lang:default decode:true">Port 2222</pre>

Note : Vous pouvez utiliser n’importe quel port, pour peu que celui-ci ne soit pas réservé par un autre service. Avoir un port non standard vous permettra d&#8217;éviter une partie des attaques automatisées que l&#8217;on rencontre chez certains prestataires . Et comme j&#8217;entends déjà les experts hurler, je précise que oui, l&#8217;obscurantisme n&#8217;est en aucun cas un gage de sécurité. Toutefois, je peux vous assurer qu&#8217;un simple changement de port sur une _dedibox_ permet de souffler un peu au niveau des tentatives de bruteforce SSH (les IP des machines sont connues et les scripts kiddies s&#8217;en donnent à coeur joie). Pour conclure, n’oubliez jamais qu’un attaquant qui se focalisera sur votre serveur n’aura aucun mal à déterminer sur quel port tourne le daemon SSH.

Le compte root n&#8217;est pas autorisé à se connecter directement depuis SSH :

<pre>PermitRootLogin no</pre>

Seul les utilisateurs appartenant au groupe sshusers sont autorisés à se connecter (il faut ajouter cette ligne) :

<pre>AllowGroups sshusers</pre>

on vérifie que la version 2 du protocole est utilisée :

<pre class="lang:sh decode:true">Protocol 2</pre>

On redémarre le daemon SSH :

<pre class="lang:sh decode:true">/etc/init.d/ssh restart</pre>

<span style="color: #ff0000;">À ce stade, ne surtout pas fermer l’ancienne connexion, au risque de ne plus pouvoir se reconnecter par la suite. Ce que je vous conseille, c’est d’ouvrir un nouvel onglet dans votre terminal et de tester la connexion avec le port et l’utilisateur adéquat.</span>

## **Authentification par un système de clé publique/clé privée**

L&#8217;authentification par **clé publique/privée** se révèle pratique dans le cas où vous souhaitez ne pas avoir à taper le mot de passe à chaque connexion.

Cette technique permet de renforcer la sécurité, car elle demande à l’utilisateur d&#8217;être en possession de deux informations pour se connecter au serveur (**une clé privée et le mot de passe de cette clé**).

Je ne détaillerai pas ici le fonctionnement du protocole, sachez juste que nous allons avoir besoin de deux choses :

  * une clé privée, que l&#8217;on gardera précieusement sur notre ordinateur, dans le dossier .ssh de notre répertoire personnel
  * une clé publique, que l&#8217;on enverra dans le dossier .ssh de l&#8217;utilisateur sur le serveur

Pour générer tout ça, rien de plus simple, il suffit de lancer la commande suivante sur **votre ordinateur** .

<pre class="lang:sh decode:true">ssh-keygen -t rsa</pre>

Répondre aux questions :

<pre class="lang:default decode:true">Enter file in which to save the key (/Users/votre_user/.ssh/id_rsa): faire entrée

Enter passphrase (empty for no passphrase): choisir un mot de passe qui protègera la clé</pre>

La phrase de passe (ou passphrase) sert en fait à décrypter votre clé privée. Il est possible de ne pas en mettre, mais dans ce cas, une personne qui mettrait la main sur votre clé privée serait tout à fait apte à se connecter au serveur. Bref, il serait idiot de se priver d&#8217;une protection supplémentaire, donc choisissez un mot de passe avec soin.

Il faut maintenant copier la clé publique dans le répertoire .ssh de votre utilisateur (celui avec lequel vous vous connectez sur le serveur) :

Pour cela, lancer la commande suivante depuis votre ordinateur :

<pre class="lang:sh decode:true">ssh &lt;user&gt;@&lt;ip_du_serveur&gt; -p &lt;port&gt; "echo $(cat ~/.ssh/id_rsa.pub) &gt;&gt; .ssh/authorized_keys"</pre>

Note : il se peut que le répertoire .ssh n&#8217;existe pas dans le home de votre utilisateur sur le serveur. Il suffit de se connecter sur celui-ci et de le créer :

<pre class="lang:sh decode:true">cd
mkdir .ssh
touch .ssh/authorized_keys</pre>

Si tout s&#8217;est bien passé, vous devriez être en mesure de vous connecter au serveur en utilisant le système de clé. À la première connexion, le mot de passe servant à décrypter la clé privée vous sera demandé. Sur OSX, le système vous proposera de l&#8217;enregistrer dans le trousseau d&#8217;accès. Sous un système Linux, il est possible qu&#8217;il en fasse de même (sinon, utilisez ssh-agent pour ne pas avoir à retaper ce mot de passe).

Si vous le souhaitez, vous pouvez aussi utiliser uniquement le système de clés pour vous connecter au serveur en passant le paramètre PasswordAuthentication sur no dans le fichier /etc/ssh/sshd_config. De ce fait, seule une personne possédant la clé privée et son mot de passe sera apte à se connecter. Cependant, si jamais vous perdez cette clé, vous serez incapable de vous connecter par la suite. Faites donc attention si vous optez pour cette solution

Rendez-vous demain pour la troisième partie de ce guide qui portera sur l&#8217;envoi de mail depuis votre serveur 🙂