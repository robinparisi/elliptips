---
id: 796
title: Rediriger un domaine www sur un domaine non-www (et inversement)
date: 2011-09-17T09:00:51+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=796
permalink: /rediriger-un-domaine-www-sur-un-domaine-non-www-et-inversement/
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
dsq_thread_id:
  - "414953402"
image: /wp-content/uploads/2011/09/redirection-180x160.jpg
---
Vous ne le saviez peut-être pas, mais les moteurs de recherche considèrent comme différent les sites http://elliptips.info et http://**www**.elliptips.info. Ainsi, il est préférable au niveau référencement de redirigé votre domaine non préféré vers le domaine que vous souhaitez utiliser.

En ce qui concerne le choix de la forme, **www** vs **non-www**, il n’y à pas de différences notoires à ma connaissance, cela dépend juste de vous. Pour ma part, vous l’aurez remarqué, je préfère la forme courte, mais nous allons voir comment avec Apache, créer une redirection 301 (redirection permanente) pour les deux cas de figure.

# Début de la procédure

assurez-vous que le module mod rewrite d’Apache est activé : pour cela décommentez ou ajoutez la ligne suivante à votre httpd.conf

<pre class="brush:plain">LoadModule rewrite_module modules/mod_rewrite.so</pre>

<div id="attachment_801" style="width: 310px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/09/rewrite-module1.jpg"><img class="size-medium wp-image-801 " title="rewrite module" src="http://elliptips.info/wp-content/uploads/2011/09/rewrite-module1-300x121.jpg" alt="rewrite module1 300x121 Rediriger un domaine www sur un domaine non www (et inversement)" width="300" height="121" srcset="http://elliptips.info/wp-content/uploads/2011/09/rewrite-module1-300x121.jpg 300w, http://elliptips.info/wp-content/uploads/2011/09/rewrite-module1.jpg 481w" sizes="(max-width: 300px) 100vw, 300px" /></a>
  
  <p class="wp-caption-text">
    mod rewrite apache
  </p>
</div>

<p class="brush:plain">
  Insérez l’une des configurations suivantes dans votre <strong>.htaccess</strong> (s’il n’existe pas, créez en un à la racine de votre répertoire web).
</p>

## www vers non-www {.brush:plain}

<pre class="brush:plain">RewriteEngine On
RewriteBase /
RewriteCond %{HTTP_HOST} ^www.votredomaine.com [NC]
RewriteRule ^(.*)$ http://votredomaine.com/$1 [L,R=301]</pre>

## non-www vers www {.brush:plain}

<pre class="brush:plain">RewriteEngine On
RewriteBase /
RewriteCond %{HTTP_HOST} ^votredomaine.com [NC]
RewriteRule ^(.*)$ http://www.votredomaine.com/$1 [L,R=301]</pre>

La redirection devrait maintenant s’opérer pour l’un de vos domaines.