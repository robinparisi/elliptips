---
id: 757
title: 'Lifestream : votre vie virtuelle sous forme de timeline en JQuery'
date: 2011-09-12T09:00:43+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=757
permalink: /lifestream-votre-vie-virtuelle-sous-forme-de-timeline-en-jquery/
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
dsq_thread_id:
  - "413481095"
image: /wp-content/uploads/2011/09/lifestream.png
---
[Lifestream](http://christianv.github.com/jquery-lifestream/ "Télécharger lifestream.") est un petit plugin JQuery pour le moins intéressant. Il vous permet de générer un flux de votre présence sur le web en se servant d&#8217;informations en provenance de divers sites et réseaux sociaux tel que Twitter, Github, Foursquare, WordPress, etc&#8230;

Un exemple est visible [ici](http://christianv.github.com/jquery-lifestream/example.html "Exemple lifestream") où vous pouvez directement créer votre propre flux sur cette [page](http://christianv.github.com/jquery-lifestream/me/ "Créer votre lifestream.").

Un exemple d&#8217;intégration :

<pre class="brush:js">$("#lifestream").lifestream({
  classname: "lifestream",
  feedloaded: feedcallback,
  limit: 30,
  list:[
    {
      service: "github",
      user: "homer"
    },
    {
      service: "twitter",
      user: "homer"
    },
    {
      service: 'flickr',
      user: '60378309@N02'
    }
  ]
});</pre>

&nbsp;