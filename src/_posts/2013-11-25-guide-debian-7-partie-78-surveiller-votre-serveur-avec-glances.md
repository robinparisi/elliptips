---
id: 2349
title: 'Guide Debian 7 (partie 7/8) : surveiller votre serveur avec Glances'
date: 2013-11-25T04:45:58+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=2349
permalink: /guide-debian-7-partie-78-surveiller-votre-serveur-avec-glances/
dsq_thread_id:
  - "1996691054"
image: /wp-content/uploads/2013/11/glances-180x160.png
---
Cet article fait partie d&#8217;une série de billets portant sur la mise en place d&#8217;un serveur sous Debian Wheezy ([sommaire du guide Debian Wheezy](http://elliptips.info/guide-sur-linstallation-dun-serveur-sous-debian-7-wheezy/ "Sommaire du guide Debian 7")).

## Introduction

Nous venons de mettre en place notre serveur et il serait maintenant intéressant de pouvoir surveiller l&#8217;utilisation des différentes ressources (RAM, CPU, disque, etc&#8230;). Pour cela, nous allons utiliser Glances, un petit utilitaire développé en Python par [Nicolargo](http://blog.nicolargo.com/) qui permet de surveiller simplement un serveur en mode texte, c&#8217;est à directement depuis le terminal. Glances peut être comparé à un logiciel tel que htop en étant toutefois beaucoup plus agréable à utiliser selon moi (ne vous enflammez, ça reste de la ligne de commande :p )

## Installation de Glances

Glances étant développé en Python, nous allons passer par le gestionnaire de paquet officiel du langage, c&#8217;est à dire pip. On commence par installer les outils nécessaires :

<pre class="lang:sh decode:true">aptitude install python-dev python-pip</pre>

Puis on installe Glances via pip :

<pre class="lang:sh decode:true">pip install glances</pre>

Pour mettre à jour Glances par la suite :

<pre class="lang:sh decode:true">pip install --upgrade Glances</pre>

## Utilisation de Glances

Concernant l&#8217;utilisation, c&#8217;est très simple, il suffit de lancer la commande glances après vous être connecté via SSH :

<pre class="lang:sh decode:true">glances</pre>

<img class="aligncenter size-large wp-image-2351" alt="glances 800x505 Guide Debian 7 (partie 7/8) : surveiller votre serveur avec Glances" src="http://elliptips.info/wp-content/uploads/2013/11/glances-800x505.png" width="800" height="505" srcset="http://elliptips.info/wp-content/uploads/2013/11/glances-800x505.png 800w, http://elliptips.info/wp-content/uploads/2013/11/glances-300x189.png 300w, http://elliptips.info/wp-content/uploads/2013/11/glances.png 874w" sizes="(max-width: 800px) 100vw, 800px" title="Guide Debian 7 (partie 7/8) : surveiller votre serveur avec Glances photo" />

Je pense que l&#8217;interface parle d&#8217;elle même, sachez juste que le code couleur s&#8217;interprète de la façon suivante :

  * <span style="color: #00ff00;">VERT</span> : la statistique est &#8220;OK&#8221;
  * <span style="color: #3366ff;">BLEU</span> : la statistique est &#8220;CAREFUL&#8221; (à surveiller)
  * <span style="color: #ff00ff;">VIOLET</span> : la statistique est &#8220;WARNING&#8221; (en alerte)
  * <span style="color: #ff0000;">ROUGE</span> : la statistique est &#8220;CRITICAL&#8221; (critique)

L&#8217;aide de Glances, accessible en tapant h :

<pre class="lang:default decode:true">a  Classer automatiquement les procel  Show/hide logs
  c  Classer les processus par CPU%   b  Bytes or bits for network I/O
  m  Classer les processus par MEM%   w  Suppression des alertes warning
  p  Classer les processus par ordre ax  Supression de toutes les alertes
  i  Sort processes by I/O rate       1  Global CPU or per-CPU stats
  d  Montrer/cacher les IO disques    h  Show/hide this help screen
  f  Montrer/cacher les statistiques st  View network I/O as combination
  n  Montrer/cacher IO réseau         u  View cumulative network I/O
  s  Show/hide sensors stats          q  Quitter Glances (ESC ou Ctrl-C marc
  y  Show/hide hddtemp stats</pre>

Vous pouvez aussi accéder à une documentation plus complète sur [Github](https://github.com/nicolargo/glances/blob/master/docs/glances-doc.rst "La documentation complète de Glances").

Enfin, sachez que Glances dispose d&#8217;un client [Android](https://play.google.com/store/apps/details?id=org.jrenner.androidglances "Le client Android de Glances") et d&#8217;un client [web](https://github.com/spin0us/MetaGlances "Le client web de Glances") (et comme c&#8217;est Open Source, rien ne vous empêche de développer le vôtre 🙂 ).