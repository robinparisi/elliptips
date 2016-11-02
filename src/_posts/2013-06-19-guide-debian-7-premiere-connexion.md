---
id: 2230
title: 'Guide Debian 7 (partie 1/8) : Première connexion'
date: 2013-06-19T09:00:00+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=2230
permalink: /guide-debian-7-premiere-connexion/
dsq_thread_id:
  - "1411031897"
image: /wp-content/uploads/2013/06/wheezy-180x160.jpeg
---
Cet article fait partie d&#8217;une série de billets portant sur la mise en place d&#8217;un serveur sous Debian Wheezy ([voir le sommaire](http://elliptips.info/guide-sur-linstallation-dun-serveur-sous-debian-7-wheezy/ "guide debian wheezy sommaire")).

## Avant de se lancer

Le guide débute à la première connexion sur votre serveur :

  * homer sera l&#8217;utilisateur choisi pour illustrer les exemples
  * sauf indication contraire, toutes les commandes sont à lancer en root
  * aptitude est le gestionnaire de paquet utilisé (mais vous pouvez sans problème utiliser apt-get)

Pour rappel, [Wheezy](http://www.debian.org/releases/stable/armhf/release-notes/ch-whats-new.fr.html "nouveautés de Wheezy") est la dernière version stable du système d&#8217;exploitation Debian sortie le 4 mai 2013 et qui succède à Squeeze après ses deux ans de bons et loyaux services.

## **Mise à jour des paquets**

Avant toute chose, on commence par mettre à jour la liste des paquets puis les paquets eux-mêmes :

<pre class="lang:sh decode:true">aptitude update
aptitude safe-upgrade</pre>

## **Changer le nom d’hôte (hostname) de la machine**

Cette étape n’est pas obligatoire, mais elle vous permet de modifier le nom de votre machine, qui dans l’état actuel, doit être un identifiant choisi par votre hébergeur. Si vous possédez plusieurs serveurs, je vous conseille fortement de leur donner des noms afin d’éviter de vous tromper de machine lors de l’exécution d’une commande.

Pour changer le nom d’hôte de façon permanente, on édite le fichier /etc/hostname :

<pre class="lang:sh decode:true">vim /etc/hostname</pre>

Il suffit alors de remplacer le nom d’hôte par celui souhaité.

Note : Le changement sera visible lors de la prochaine connexion.

## **Zsh (optionnel)**

Par défaut, Debian est livré avec le Shell bash. J’ai pour ma part l’habitude d’utiliser [Zsh](http://fr.wikipedia.org/wiki/Z_Shell "Zsh sur Wikipedia"), qui est un Shell très puissant et hautement configurable.

<pre class="lang:sh decode:true">aptitude install zsh</pre>

On change de Shell (le changement sera pris en compte dès la prochaine connexion) :

<pre class="lang:sh decode:true">chsh -s /bin/zsh</pre>

Je vous propose de récupérer une petite configuration rapide disponible sur [mon Github](https://github.com/robinparisi/myzshrc/blob/master/.zshrc "myzshrc") :

<pre class="lang:sh decode:true">wget --no-check-certificate  https://raw.github.com/robinparisi/myzshrc/master/.zshrc 
mv .zshrc /etc/zsh</pre>

Le fait de placer la configuration dans le dossier /etc/zsh permettra à tous les utilisateurs d&#8217;en profiter.

Note : zsh sera utilisé pour les connexions suivantes. Pour l’activer sans se déconnecter, taper tout simplement zsh.

### **Pour aller plus loin**

Le fichier de configuration que nous avons récupéré permet une utilisation rapide et pratique de zsh. Toutefois, je ne saurais que trop vous conseiller de jeter un oeil du côté du célèbre projet oh-my-zsh (<https://github.com/robbyrussell/oh-my-zsh>) qui vous permettra une configuration aux petits oignons du célèbre Shell, notamment grâce à l&#8217;utilisation d&#8217;un système de plug-ins vraiment puissant.

## **Vim**

Si vim n’est pas installé sur votre système, je vous encourage à le faire grâce à la commande suivante :

<pre class="lang:sh decode:true">aptitude install vim</pre>

Dans le fichier de configuration de Vim (global à tous les utilisateurs)

<pre class="lang:sh decode:true">vim /etc/vim/vimrc</pre>

On décommente la ligne suivante ce qui nous permet d’obtenir la coloration syntaxique.

<pre class="lang:sh decode:true">syntax on</pre>

Note : la coloration syntaxique est selon moi le minimum à activer pour utiliser [Vim](http://vim-adventures.com/ "apprendre vim en s'amusant"). Comme il serait vain de tenter de vous expliquer ici la puissance de cet éditeur, je vous conseille de vous renseigner sur le sujet. Comme pour Zsh, on trouve sur la toile d’excellents vimrc, prêts à l’emploi, qui vous permettront d’étendre, avec un minimum de manipulations, les capacités offertes par l&#8217;éditeur de texte.

À demain pour le prochain article qui portera sur la sécurisation de l&#8217;accès SSH 🙂