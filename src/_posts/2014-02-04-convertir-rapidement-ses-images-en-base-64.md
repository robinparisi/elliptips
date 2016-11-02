---
id: 2400
title: Convertir rapidement ses images en base 64
date: 2014-02-04T01:13:36+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=2400
permalink: /convertir-rapidement-ses-images-en-base-64/
dsq_thread_id:
  - "2216862512"
image: /wp-content/uploads/2014/02/base64.png
---
Encoder ses images en base64 est une technique d&#8217;optimisation web qui permet de convertir une image en une chaîne de caractères directement exploitable par le navigateur, le but principal étant d&#8217;économiser une requête HTTP vers la ressource (puisque celle-ci est directement embarquée dans le HTML ou le CSS).

Revers de la médaille, cette technique génère une chaîne plus lourde que le fichier original. Il faut donc l&#8217;utiliser avec parcimonie sur de **petites images** et jauger le gain en terme de performances.

Ainsi, même si la technique se révèle assez efficace pour une ou deux images, il faut lui préférer au-delà la technique des sprites CSS ou encore l&#8217;utilisation d&#8217;une police d&#8217;icônes (pour des icônes simples et monochromes).

Enfin, vous devez savoir que le navigateur IE7 ne gère pas ce format (mais ça on s&#8217;en fiche :p) et que IE8 impose une limite de 32 KB à celui-ci (mais à ce niveau, on perd l&#8217;intérêt de la chose).

## Utilisation concrète

<span style="line-height: 1.5em;">Un exemple dans le HTML :</span>

<pre class="lang:xhtml decode:true">&lt;img src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7"&gt;</pre>

Un exemple dans le CSS :

<pre class="lang:css decode:true">background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAYAAAAECAIAAAAiZtkUAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAE1JREFUeNpi6dFgYmdj//nrpwAXx6+f3xkYGFj+MrN++/uPgZn1968fbOycICFhdmYGMPj+h+nrtx/MTExMEMVA8uP3n0AdvxiZAQIMABFCHYYroQd+AAAAAElFTkSuQmCC);</pre>

## L&#8217;astuce avec openssl

Il existe de nombreux convertisseurs en ligne capable d&#8217;effectuer cette tâche. Toutefois, sachez que vous disposez déjà des outils nécessaires et il serait donc dommage de s&#8217;en priver 🙂

L&#8217;astuce se situe au niveau de l&#8217;utilitaire openssl (à utiliser en ligne de commande) :

<pre class="lang:sh decode:true">openssl base64 -in mon_image.png | tr -d '\n'</pre>

Ici, on convertit l&#8217;image en base64 pour ensuite rediriger le résultat vers la commande **tr** qui permet de supprimer les retours chariot.

Pour encore plus de rapidité, il est possible de copier directement la chaîne dans votre presse-papier.

Sur OSX :

<pre class="lang:default decode:true">openssl base64 -in vertical_cloth.png  | tr -d '\n' | pbcopy</pre>

Sur Linux (nécessite l&#8217;installation du paquet xclip) :<span style="background-color: #f4f4f4;"><br /> </span>

<pre class="lang:sh decode:true">openssl base64 -in vertical_cloth.png  | tr -d '\n' | xclip</pre>

bref, une technique à utiliser avec modération mais qui peut parfois s&#8217;avérer utile.