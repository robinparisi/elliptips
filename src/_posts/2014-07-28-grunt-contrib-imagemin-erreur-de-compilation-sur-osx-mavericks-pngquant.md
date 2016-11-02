---
id: 2441
title: 'Grunt-contrib-imagemin : erreur de compilation sur OSX Mavericks (pngquant)'
date: 2014-07-28T14:58:54+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=2441
permalink: /grunt-contrib-imagemin-erreur-de-compilation-sur-osx-mavericks-pngquant/
dsq_thread_id:
  - "2879848244"
image: /wp-content/uploads/2014/07/pngquant-logo.png
---
Si vous utilisez [Grunt](http://gruntjs.com/) et plus précisément le module [grunt-contrib-imagemin](https://github.com/gruntjs/grunt-contrib-imagemin) afin de compresser vos images à la volée, vous vous êtes peut être rendu compte que l&#8217;installation pose problème sur Mavericks (la dernière version d&#8217;OSX).

En effet, le module utilise plusieurs libs de compression dont l&#8217;excellent [**pngquant**](http://pngquant.org/) qui n&#8217;est malheureusement plus distribué avec le système.

Aussi, l&#8217;installation via npm vous gratifiera du magnifique message d&#8217;erreur suivant :

<pre class="lang:sh decode:true">&gt; pngquant-bin@0.3.1 postinstall /****/node_modules/grunt-contrib-imagemin/node_modules/imagemin/node_modules/imagemin-pngquant/node_modules/pngquant-bin
&gt; node index.js

✗ pre-build test failed, compiling from source...
libpng-dev is installed

{ [Error: Command failed: In file included from pngquant.c:59:
./rwpng.h:35:10: fatal error: 'png.h' file not found
#include "png.h"    /* libpng header; includes zlib.h */
         ^
1 error generated.
make: *** [pngquant.o] Error 1
] killed: false, code: 2, signal: null }</pre>

Pour corriger cela, rien de plus simple, commencez par supprimez le dossier node_modules de votre projet :

<pre class="lang:sh decode:true">rm -rf node_modules</pre>

Installez ensuite pngquant sur votre système (si vous n&#8217;avez pas brew, commencer par l&#8217;installer) :

<pre class="lang:default decode:true">brew install libpng</pre>

Puis on relance l&#8217;installation des modules :

<pre class="lang:sh decode:true">npm install</pre>

Résultat :

<pre class="lang:sh decode:true">✓ pre-build test passed successfully
 
&gt; pngquant-bin@0.3.1 postinstall /****/node_modules/grunt-contrib-imagemin/node_modules/imagemin/node_modules/imagemin-pngquant/node_modules/pngquant-bin
&gt; node index.js</pre>