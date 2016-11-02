---
id: 2328
title: 'Guide Debian 7 (partie 5/8) : Fail2ban, gardien de votre serveur'
date: 2013-11-05T01:38:45+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=2328
permalink: /guide-debian-7-partie-58-fail2ban-gardien-de-votre-serveur/
dsq_thread_id:
  - "1936894527"
image: /wp-content/uploads/2013/11/fail2ban-logo-180x160.jpg
---
Cet article fait partie d&#8217;une série de billets portant sur la mise en place d&#8217;un serveur sous Debian Wheezy ([sommaire du guide Debian Wheezy](http://elliptips.info/guide-sur-linstallation-dun-serveur-sous-debian-7-wheezy/ "Sommaire du guide Debian 7")).

## Introduction

Fail2ban est un petit programme chargé de surveiller les logs de votre serveur à la recherche de comportements suspects. Pour reprendre la métaphore utilisée dans un article précédent, si votre serveur était votre maison et SSH la porte d’entrée, fail2ban serait un imposant molosse attendant tranquillement sur le pas de la porte d’éventuels voleurs (en théorie, il ne fera rien au facteur).

Fail2ban se configure simplement via un système de prison et permet de bannir les IP dangereuses en ajoutant dynamiquement des règles à IPTables.

## Installation

On commence par l&#8217;installer :

<pre class="lang:sh decode:true">aptitude install fail2ban</pre>

Rapide configuration pour bannir les tentatives infructueuses de connexion via SSH :

<pre class="lang:sh decode:true">vim /etc/fail2ban/jail.conf</pre>

On bannit après 3 tentatives de connexion pour 15 minutes (rien ne vous empêche d’être beaucoup plus sévère) :

<pre class="lang:sh range:7 decode:true">[ssh]                                                                        

enabled = true
port    =  2222
filter  = sshd
logpath  = /var/log/auth.log
maxretry = 3</pre>

Conseil : évitez d&#8217;utiliser une valeur trop haute pour la durée de bannissement. En effet, si vous vous bannissez par erreur (ce qui n&#8217;arrivera pas si vous utilisez un certificat SSH), vous devrez attendre, ce qui peut poser problème en cas d&#8217;urgence. Dans tous les cas, trouvez le juste milieu, et, si une IP est trop insistante, vous pourrez prendre les mesures nécessaires pour la bannir plus longtemps.

Prise en compte des changements :

<pre class="lang:default decode:true">/etc/init.d/fail2ban restart</pre>

Il est possible de vérifier les bans en surveillant les logs :

<pre class="lang:default decode:true">tail –f /var/log/fail2ban.log</pre>

## **Revevoir des mails de fail2ban**

Par défaut, fail2ban utilise sendmail pour l’envoi de rapport, et ça tombe plutôt bien, puisque nous aussi.

On édite de nouveau le fichier jail.conf :

<pre class="lang:default decode:true">vim /etc/fail2ban/jail.con</pre>

Modification de l’adresse mail destinée à recevoir les rapport :

<pre class="lang:default decode:true">destemail = votremail@domain.com</pre>

Et l’étape à **ne pas oublier**, on active l’action permettant l’envoi de rapport :

<pre class="lang:default decode:true">action = %(action_mwl)s</pre>

Les actions disponibles :

  * **action_** => simple ban
  * **action_mw** => ban et envoi de mail
  * **action_mwl** => ban, envoi de mail accompagné des logs