---
id: 874
title: 'Nmap : vos rapports au format html'
date: 2011-09-26T04:49:49+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=874
permalink: /nmap-vos-rapports-au-format-html/
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
dsq_thread_id:
  - "425809268"
image: /wp-content/uploads/2011/09/nmap_diff_logo-180x160.png
---
Voici une petite astuce afin d’exporter vos rapports **nmap** au format **html**.

Pour cela, on va ruser un peu en générant d’abord un rapport au format XML, puis le convertir au format html grâce à l’outil en ligne de commande **xsltproc**.

On commence par un scan basique avec export au format xml :

<pre class="brush:shell">nmap -oX rapport.xml 192.168.1.10</pre>

<p class="brush:shell">
  <span style="color: #339966;"><strong>-oX</strong></span> : Permet l’export au format XML
</p>

<p class="brush:shell">
  Une fois le scan terminé, on génère le html grâce à xsltproc :
</p>

<pre class="brush:shell">xsltproc rapport.xml -o rapport.html</pre>

Et voici le résultat :

[<img class="size-full wp-image-875 aligncenter" title="nmap-export-html" src="http://elliptips.info/wp-content/uploads/2011/09/nmap-export-html.jpg" alt="nmap export html Nmap : vos rapports au format html " width="520" height="215" srcset="http://elliptips.info/wp-content/uploads/2011/09/nmap-export-html.jpg 650w, http://elliptips.info/wp-content/uploads/2011/09/nmap-export-html-300x124.jpg 300w" sizes="(max-width: 520px) 100vw, 520px" />](http://elliptips.info/wp-content/uploads/2011/09/nmap-export-html.jpg)

Sympa non ?