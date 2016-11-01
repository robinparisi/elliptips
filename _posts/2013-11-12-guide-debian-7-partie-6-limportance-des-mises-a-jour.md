---
id: 2340
title: 'Guide Debian 7 (partie 6/8) : l&#8217;importance des mises à jour'
date: 2013-11-12T10:30:03+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=2340
permalink: /guide-debian-7-partie-6-limportance-des-mises-a-jour/
dsq_thread_id:
  - "1957961299"
image: /wp-content/uploads/2013/11/update-180x160.png
---
Cet article fait partie d&#8217;une série de billets portant sur la mise en place d&#8217;un serveur sous Debian Wheezy ([sommaire du guide Debian Wheezy](http://elliptips.info/guide-sur-linstallation-dun-serveur-sous-debian-7-wheezy/ "Sommaire du guide Debian 7")).

## Introduction

Il est essentiel de maintenir votre serveur à jour, dans une optique de sécurité bien sûr, mais aussi en vue d&#8217;obtenir les versions optimisées de chacun de vos logiciels.

La procédure manuelle n&#8217;est pas très complexe. On commence par synchroniser la liste des paquets :

<pre class="lang:sh decode:true">aptitude update</pre>

Puis on lance la mise à jour :

<pre class="lang:default decode:true">aptitude dist-upgrade</pre>

## L&#8217;utilitaire cron-apt

Cron-apt est un petit utilitaire qui va nous aider dans la gestion des mises à jour sur notre serveur.

On installe le paquet cron-apt :

<pre class="lang:sh decode:true">aptitude install cron-apt</pre>

On édite le fichier de configuration :

<pre class="lang:sh decode:true">vim /etc/cron-apt/config</pre>

Il faut alors spécifier le gestionnaire de paquet à utiliser (dans mon cas **aptitude**) et une adresse mail de réception pour les rapports :

<pre class="lang:sh decode:true">APTCOMMAND=/usr/bin/aptitude
MAILTO="votre_mail@example.com"</pre>

Dès lors, la vérification des mises à jour se fera tous les jours à 4h et vous recevrez un rapport sur votre boîte mail.

## **Mises à jour automatiques**

Avec la configuration précédente, les mises à jour sont uniquement téléchargées sans être appliquées. Sachez qu&#8217;il est possible de lancer automatiquement l&#8217;installation de celles-ci.

<span style="color: #ff0000;"><strong>Attention : j&#8217;insiste sur le fait que cette configuration n&#8217;est pas souhaitable sur un serveur dont les services sont critiques. Il peut arriver qu&#8217;une mise à jour se passe mal et empêche le service de redémarrer (souvent à cause d&#8217;un fichier de configuration écrasé).</strong></span>

Toutefois, si vous souhaitez ne pas trop vous prendre la tête sur votre serveur perso, vous pouvez activer cette fonctionnalité en créant un fichier contenant la commande adéquate dans le répertoire **action.d** :

<pre class="lang:default decode:true">touch /etc/cron-apt/action.d/5-install</pre>

Puis on y insère la ligne suivante :

<pre class="lang:sh decode:true">dist-upgrade -y -o APT::Get::Show-Upgraded=true</pre>

Et voilà, les mises à jour se feront maintenant de manière automatique 🙂