---
id: 300
title: 'Entrez dans la peau d&#8217;un hacker avec Gruyere'
date: 2011-02-14T21:15:10+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=300
permalink: /entrez-dans-la-peau-dun-hacker-avec-gruyere/
dsq_thread_id:
  - "417531697"
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
image: /wp-content/uploads/2011/02/GoogleGruyere-180x160.png
---
<p style="text-align: left;">
  <strong>Gruyere</strong> est une petite application python au nom plus qu&#8217;évocateur qui a pour but de vous familiariser avec les techniques utilisées par les Hackers pour <strong>exploiter</strong> les <strong>failles de sécurité</strong> au sein d&#8217;une application web.
</p>

La méthodologie employée par Gruyere est de vous faire comprendre par la pratique la façon dont les hackers trouvent et exploitent ces mêmes failles de sécurité, ce qui vous permettra par la suite de les stopper.

Vous l&#8217;aurez compris, Gruyere est donc un véritable&#8230; gruyère informatique non sécurisé qui ne demande qu&#8217;à être attaqué .

<div id="attachment_302" style="width: 584px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/02/home-page-gruyere.png"><img class="size-large wp-image-302  " title="home page gruyere" src="http://elliptips.info/wp-content/uploads/2011/02/home-page-gruyere-1024x504.png" alt="home page gruyere 1024x504 Entrez dans la peau dun hacker avec Gruyere" width="574" height="282" srcset="http://elliptips.info/wp-content/uploads/2011/02/home-page-gruyere-1024x504.png 1024w, http://elliptips.info/wp-content/uploads/2011/02/home-page-gruyere-300x147.png 300w, http://elliptips.info/wp-content/uploads/2011/02/home-page-gruyere.png 1216w" sizes="(max-width: 574px) 100vw, 574px" /></a>
  
  <p class="wp-caption-text">
    Et hop, par ici les droits admin !
  </p>
</div>

Le fonctionnement est simple : en vous rendant sur cette [page](http://google-gruyere.appspot.com/start) , vous aurez accès à votre propre instance de l&#8217;application avec un identifiant unique. Vous pourrez à tout moment réinitialiser votre instance via le lien :

<pre>http://google-gruyere.appspot.com/resetbutton/&lt;id&gt;</pre>

Ensuite, votre rôle est de mettre la main sur les failles de sécurité et de mener à bien des exploits. Pour cela, vous pourrez suivre un [petit guide](http://google-gruyere.appspot.com/part1) qui vous expliquera la marche à suivre (des connaissances en HTML, templates, cookies, AJAX, etc&#8230; sont quand même requises).

Dans ce guide vous rencontrerez des tags dont l&#8217;objectif est de vous donner quelques pistes sur le challenge à accomplir :

<div id="attachment_301" style="width: 629px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/02/challenges.png"><img class="size-full wp-image-301" title="challenges_légende" src="http://elliptips.info/wp-content/uploads/2011/02/challenges.png" alt="challenges Entrez dans la peau dun hacker avec Gruyere" width="619" height="123" srcset="http://elliptips.info/wp-content/uploads/2011/02/challenges.png 619w, http://elliptips.info/wp-content/uploads/2011/02/challenges-300x59.png 300w" sizes="(max-width: 619px) 100vw, 619px" /></a>
  
  <p class="wp-caption-text">
    Renseignement sur la façon de résoudre le challenge
  </p>
</div>

Gruyere traite de types de failles tel que :

  * Cross-Site Scripting (XSS)
  * Cross-Site Request Forgery (XSRF)
  * Cross Site Script Inclusion (XSSI)
  * Manipulation coté client
  * Path Traversal
  * Deni de service
  * Code Execution
  * Configuration Vulnerabilities
  * AJAX vulnerabilities
  * et d&#8217;autres (tel que le buffer overflow ou l&#8217;injection sql&#8230;)

Tout un programme en perspective qui se révèle être très formateur 🙂

**Attention**, je vous rappelle toutefois que Gruyere est volontairement bourré de failles donc évitez d&#8217;y rentrer de véritables identifiants ou autres.