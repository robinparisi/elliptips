---
id: 2429
title: Fixer le problème de locales sur Digital Ocean
date: 2014-06-01T02:50:24+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=2429
permalink: /fixer-probleme-locales-digital-ocean/
dsq_thread_id:
  - "2727271319"
image: /wp-content/uploads/2014/06/digital-ocean.jpg
---
Suite à l&#8217;installation d&#8217;un système Debian ou Ubuntu, il se peut que les locales ne soient pas correctement configurées. C&#8217;est notamment le cas chez Digital Ocean et vous vous retrouverez alors avec le message d&#8217;avertissement suivant en tentant de mettre à jour le système :

<pre class="lang:sh decode:true">Can't set locale; make sure $LC_* and $LANG are correct!
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_US:en",
	LC_ALL = (unset),
	LC_CTYPE = "fr_FR.UTF-8",
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory</pre>

Pour corriger le problème, il suffit de re-configurer les locales à l&#8217;aide de la commande suivante (à lancer en root) :

<pre class="lang:default decode:true">dpkg-reconfigure locales</pre>

Pour le français, choisissez dans la liste fr_FR.UTF-8 UTF-8 puis valider pour re-générer correctement les paramètres régionaux :

<img class="aligncenter size-large wp-image-2431" src="http://elliptips.info/wp-content/uploads/2014/06/debian-locales-800x273.png" alt="debian locales 800x273 Fixer le problème de locales sur Digital Ocean" srcset="http://elliptips.info/wp-content/uploads/2014/06/debian-locales-800x273.png 800w, http://elliptips.info/wp-content/uploads/2014/06/debian-locales.png 926w" sizes="(max-width: 800px) 100vw, 800px" title="Fixer le problème de locales sur Digital Ocean photo" />