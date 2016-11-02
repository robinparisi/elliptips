---
id: 2300
title: 'Guide Debian 7 (partie 4/8) : gérer le trafic entrant et sortant avec Iptables'
date: 2013-07-04T18:49:48+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=2300
permalink: /guide-debian-7-gerer-le-trafic-entrant-et-sortant-avec-iptables/
dsq_thread_id:
  - "1467067541"
image: /wp-content/uploads/2013/07/firewall-180x160.jpg
---
Cet article fait partie d&#8217;une série de billets portant sur la mise en place d&#8217;un serveur sous Debian Wheezy ([sommaire du guide Debian Wheezy](http://elliptips.info/guide-sur-linstallation-dun-serveur-sous-debian-7-wheezy/ "Guide Debian Wheezy")).

## Introduction

Nous avons vu dans un article précédent comment sécuriser la porte d&#8217;entrée de notre serveur, c&#8217;est-à-dire l&#8217;accès SSH. C&#8217;est un début, mais n&#8217;oubliez pas que les fenêtres, elles, sont toujours ouvertes&#8230;

Dans l&#8217;état actuel, tout le trafic devrait être autorisé en **entrée et sortie sur votre serveur** (j&#8217;utilise le conditionnel, car parfois, les prestataires mettent à disposition un pare-feu intermédiaire).

Pour réguler ces entrées/sorties, nous allons utiliser [Iptables](http://fr.wikipedia.org/wiki/Iptables "Iptables"), **un logiciel qui permet de configurer les règles du pare-feu**, le tout en ligne de commandes. Il faut savoir que les règles Iptables sont réinitialisées à chaque reboot du serveur. La meilleure solution consiste donc à les placer dans un petit script qui s&#8217;occupera de mettre en place vos règles au démarrage de la machine.

## Le script

Bonne nouvelle, nul besoin de réinventer la roue, car il existe sur le net une multitude de scripts pour gérer le firewall. Nous allons utiliser le script de Nicolargo (qui au passage tient un excellent blog: <http://blog.nicolargo.com/> ).

J&#8217;ai forké le script pour mes propres besoins et pour être sûr que celui-ci reste accessible. On commence donc par le récupérer depuis Github :

<pre class="lang:sh decode:true">wget --no-check-certificate https://raw.github.com/robinparisi/debian-scripts/master/firewall.sh
mv firewall.sh /etc/init.d/firewall.sh</pre>

On rend le script exécutable :

<pre>chmod +x /etc/init.d/firewall.sh</pre>

## Configuration

<pre>vim /etc/init.d/firewall.sh</pre>

La configuration du script est rapide :

<pre># Services that the system will offer to the network
TCP_SERVICES="22" # SSH 
UDP_SERVICES=""
# Services the system will use from the network
REMOTE_TCP_SERVICES="80 443 25" # web browsing
REMOTE_UDP_SERVICES="53" # DNS
# FTP backups 
# Allow backups to an external FTP
FTP_BACKUPS=""</pre>

<span style="color: #ff0000;">Attention : le port SSH est ici le 22, mais n&#8217;oubliez pas que nous l&#8217;avons changé. Adaptez donc la conf au port choisi !</span>

Pour l&#8217;envoi de mail, il faut ajouter le port 25 dans REMOTE\_TCP\_SERVICES.

Il est possible de tester la configuration en appliquant les règles pendant 30 secondes pour s&#8217;assurer que tout va bien :

<pre class="lang:sh decode:true">/etc/init.d/firewall.sh test</pre>

Essayez de vous reconnecter au serveur avec SSH durant ce laps de temps. Si tout se passe bien, vous pouvez alors activer les règles en lançant la commande suivante :

<pre>/etc/init.d/firewall.sh start</pre>

Si un jour vous avez besoin d&#8217;effacer les règles (tout autoriser en entrée et sortie), lancez la commande suivante :

<pre>/etc/init.d/firewall.sh clear</pre>

<span style="color: #ff0000;">Warning !!! : ne lancez jamais la commande stop sur une connexion distante, car elle aurait pour effet de couper totalement l&#8217;accès au serveur (refuser tout le trafic entrant). </span>

## Ajouter le script au démarrage

<pre class="lang:default decode:true">update-rc.d firewall.sh defaults</pre>

pour l&#8217;enlever  :

<pre class="lang:sh decode:true">update-rc.d -f firewall.sh remove</pre>

## Pour aller plus loin

Il faut l&#8217;avouer, ce genre de script est bien pratique, mais il ne vous dispense pas de comprendre les règles Iptables qui s&#8217;appliquent sur votre serveur.

Pour rappel, vous pouvez obtenir à tout moment la liste des règles grâce à la commande suivante :

<pre class="lang:sh decode:true">iptables -L</pre>

Renseignez-vous sur le sujet, et surtout, évitez à tout prix de faire des copier/coller de règles en provenance d&#8217;internet que vous ne comprenez pas, car c&#8217;est en général le meilleur moyen pour se retrouver sur le pas de la porte à tambouriner comme un couillon après s&#8217;être enfermé dehors (j&#8217;en connais qui se remémorent des soirées sympathiques :P).

## J&#8217;ai bloqué ma connexion SSH&#8230;

Et voilà, on fait l&#8217;idiot dans le fond depuis le début des explications&#8230; mais maintenant, qui a l&#8217;air malin ?! 😛

Ne vous inquiétez pas, tout n&#8217;est pas perdu 🙂

Deux cas peuvent se présenter :

  * Vous avez joué avec des règles Iptables mais sans éditer le script. Dans ce cas un reboot du serveur depuis son interface suffira à rétablir les bonnes règles.
  * Vous avez édité ou mal configuré le script puis appliqué directement les règles. Ici, il faudra passer par la console de récupération de votre prestataire. En montant la partition de votre serveur, vous serez capable d&#8217;éditer le script puis de rebooter le serveur.