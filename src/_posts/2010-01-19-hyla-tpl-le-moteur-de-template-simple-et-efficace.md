---
id: 66
title: Hyla TPL, le moteur de template simple et efficace
date: 2010-01-19T19:00:23+00:00
author: Robin
layout: post
guid: http://localhost/wordpress/?p=66
permalink: /hyla-tpl-le-moteur-de-template-simple-et-efficace/
dsq_thread_id:
  - "447909622"
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
image: /wp-content/uploads/2010/01/hylatpl1-180x160.png
---
<p style="text-align: left;">
  Souvent, lorsque l&#8217;on se lance à la recherche d&#8217;un moteur de template pour php, ce qui frappe au premier abord est leur nombre sans cesse croissant.
</p>

Je vous présente aujourd&#8217;hui **<span style="color: #3366ff;"><a title="hyla tpl" href="http://tpl.hyla-project.org/fr/" target="_self">HylaTpl</a></span>**, un petit moteur simple mais qui fait ce qu&#8217;on lui demande. Loin de moi l&#8217;idée de le comparer à des systèmes tel que Smarty, après, tout dépend de l&#8217;utilisation que l&#8217;on a d&#8217;un tel outil.

Bref, HylaTpl se veut volontairement simple et minimaliste, non pas dans le sens péjoratif mais plutôt dans le sens où il offre les fonctionnalités amplement suffisantes la où d&#8217;autres sont de véritables usines à gaz&#8230;

Un petit Hello World :

hello.php

<pre class="brush:php">&lt;?php

require 'hyla_tpl.class.php';

// Créé l'objet Hyla_Tpl
$tpl = new Hyla_Tpl('.');

// Import le fichier hello.tpl
$tpl-&gt;importFile('hello.tpl');

// La variable de template var vaut Hello World !
$tpl-&gt;setVar('var', 'Hello World !');

// Affiche le résultat
echo $tpl-&gt;render();

?&gt;</pre>

hello .tpl

<pre class="brush:php">&lt;h1&gt;{$var}&lt;/h1&gt;</pre>

Retrouvez le <a title="le site du moteur HylaTpl" href="http://tpl.hyla-project.org/fr/" target="_blank">ici</a> ainsi qu&#8217;une documentation clair et illustrée avec les exemples qui vont bien