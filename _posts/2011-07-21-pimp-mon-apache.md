---
id: 682
title: Pimp mon Apache
date: 2011-07-21T15:33:18+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=682
permalink: /pimp-mon-apache/
dsq_thread_id:
  - "419957805"
image: /wp-content/uploads/2011/07/h5ai-180x160.png
---
Si vous avez activé l’option Indexes sur votre apache, ce que je vous déconseille de faire dans la plupart des cas, vous aurez sans doute remarqué que l’interface de présentation des fichiers est un poil austère.

&nbsp;

<div id="attachment_683" style="width: 310px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/07/Capture-d_ecran-2011-07-21-a-17.14.51.jpg"><img class="size-medium wp-image-683" title="index apache " src="http://elliptips.info/wp-content/uploads/2011/07/Capture-d_ecran-2011-07-21-a-17.14.51-300x209.jpg" alt="Capture d ecran 2011 07 21 a 17.14.51 300x209 Pimp mon Apache" width="300" height="209" /></a>
  
  <p class="wp-caption-text">
    Il faut l’avouer, niveau user friendly, c’est pas génial
  </p>
</div>

&nbsp;

Heureusement, h5ai arrive à la rescousse à grand coup de HTML5, CSS3 et Jquery pour redonner à cette vilaine page un style, disons le, plus actuel.

&nbsp;

<div id="attachment_684" style="width: 310px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/07/Capture-d_ecran-2011-07-21-a-17.14.32.jpg"><img class="size-medium wp-image-684" title="index apache h5ai" src="http://elliptips.info/wp-content/uploads/2011/07/Capture-d_ecran-2011-07-21-a-17.14.32-300x136.jpg" alt="Capture d ecran 2011 07 21 a 17.14.32 300x136 Pimp mon Apache" width="300" height="136" /></a>
  
  <p class="wp-caption-text">
    La même avec h5ai
  </p>
</div>

## 

## Installation h5ai

Pour cela rien de plus simple, on commence par télécharger l’archive sur [le site du développeur](http://larsjung.de/h5ai/ "h5ai download page").

Une fois l’archive téléchargée, on récupère le dossier h5ai dans src que l’on place à la racine de son répertoire web.

On ajoute ensuite le contenu du fichier dot.htaccess dans le .htaccess à la racine du répertoire que l’on souhaite customiser.

Par exemple je souhaite appliquer le style au répertoire test contenu dans mon htdocs :

&nbsp;

<div id="attachment_700" style="width: 310px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/07/Capture-d_ecran-2011-07-21-a-18.43.49.jpg"><img class="size-medium wp-image-700" title="htaccess" src="http://elliptips.info/wp-content/uploads/2011/07/Capture-d_ecran-2011-07-21-a-18.43.49-300x33.jpg" alt="Capture d ecran 2011 07 21 a 18.43.49 300x33 Pimp mon Apache" width="300" height="33" /></a>
  
  <p class="wp-caption-text">
    On créé ou édite le .htaccess
  </p>
</div>

&nbsp;

Test en se rendant sur http://localhost/test

&nbsp;

<div id="attachment_686" style="width: 310px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/07/Capture-d_ecran-2011-07-21-a-17.24.05.jpg"><img class="size-medium wp-image-686" title="h5ai local" src="http://elliptips.info/wp-content/uploads/2011/07/Capture-d_ecran-2011-07-21-a-17.24.05-300x82.jpg" alt="Capture d ecran 2011 07 21 a 17.24.05 300x82 Pimp mon Apache" width="300" height="82" /></a>
  
  <p class="wp-caption-text">
    Ca marche !
  </p>
</div>

&nbsp;

<span style="text-decoration: underline;">Note</span> : pour que cela fonctionne, la directive AllowOveride doit être à all

<pre class="brush:shell">AllowOverride All</pre>

<p class="brush:shell">
  N’oubliez pas non plus l’option +Indexes, le mieux étant de la placer dans le .htaccess pour que seul le répertoire voulu puisse être indexé (il suffit d’ailleurs de la décommenter dans le dot.haccess).
</p>

<p class="brush:shell">
  Voilà, c’est quand même plus sympa pour créer un petit serveur de partage rapidement non ?
</p>

<p class="brush:shell" style="text-align: right;">
  [<a title="La ferme du web" href="http://www.lafermeduweb.net/billet/h5ai-votre-page-index-apache-modifiee-avec-style-1153.html">source : la ferme du web</a>]
</p>