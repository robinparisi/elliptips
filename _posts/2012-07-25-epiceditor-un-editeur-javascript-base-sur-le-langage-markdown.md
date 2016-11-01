---
id: 1611
title: 'EpicEditor : un éditeur JavaScript basé sur le langage markdown'
date: 2012-07-25T01:54:34+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=1611
permalink: /epiceditor-un-editeur-javascript-base-sur-le-langage-markdown/
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
dsq_thread_id:
  - "778732668"
image: /wp-content/uploads/2012/07/markdown-180x160.jpg
---
[EpicEditor](http://oscargodson.github.com/EpicEditor/# "EpicEditor site web") est un éditeur **JavaScript** simple à utiliser et facilement intégrable dans vos pages web, disposant de fonctionnalités appréciables telles que le fullscreen, le live preview ou encore la personnalisation avancée. Il est basé sur le langage markdown, un langage de **balisage léger**, très en vogue ces temps-ci, et utilisé par exemple sur **Github** ou **Stackoverflow**. Ce langage a l’avantage d’offrir une syntaxe facile à lire et à écrire, et est, par conséquent, une solide **alternative** à la plaie bien connue que sont les éditeurs **WYSIWYG**.

Un exemple d’intégration :

Intégration du script à la page (à récupérer au préalable sur Github)

<pre class="lang:xhtml decode:true">&lt;script src="epiceditor.min.js"&gt;&lt;/script&gt;</pre>

Création d’un élément conteneur

<pre class="lang:xhtml decode:true">&lt;div id="epiceditor"&gt;&lt;/div&gt;</pre>

On initialise l’éditeur

<pre class="lang:js decode:true">var editor = new EpicEditor().load();</pre>

Pour en savoir plus sur les possibilités offertes par cet éditeur (syntaxe, raccourcis clavier), n’hésitez pas à consulter la page de [documentation](https://github.com/OscarGodson/EpicEditor/wiki/User's-Manual "Documentation EpicEditor").

[<img class="size-full wp-image-1612 aligncenter" title="epiceditor" src="http://elliptips.info/wp-content/uploads/2012/07/epiceditor.png" alt="epiceditor EpicEditor : un éditeur JavaScript basé sur le langage markdown " width="610" height="293" srcset="http://elliptips.info/wp-content/uploads/2012/07/epiceditor.png 610w, http://elliptips.info/wp-content/uploads/2012/07/epiceditor-300x144.png 300w" sizes="(max-width: 610px) 100vw, 610px" />](http://elliptips.info/wp-content/uploads/2012/07/epiceditor.png)