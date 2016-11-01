---
id: 1655
title: 'Twitter API : Sorry, that page does not exist (code 34)'
date: 2012-10-11T17:49:07+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=1655
permalink: /twitter-api-sorry-that-page-does-not-exist-code-34/
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
dsq_thread_id:
  - "881213592"
image: /wp-content/uploads/2012/10/twiiter-api-180x160.png
---
Jusqu’à hier, il était possible d’appeler l’API Twitter via l’adresse suivante :

<pre class="lang:default decode:true">https://twitter.com/statuses/user_timeline/home_timeline.xml</pre>

Or, cette requête retourne maintenant le code HTTP 404 avec le message d’erreur suivant (pour le format xml) :

<pre class="lang:default decode:true">&lt;errors&gt;
&lt;error code="34"&gt;Sorry, that page does not exist&lt;/error&gt;
&lt;/errors&gt;</pre>

Le problème en soi ne vient pas de l’API, mais de l’URL qui a été héritée de l’ancien système et il semblerait que Twitter ait décidé de se séparer définitivement de cette relique. Je sais que beaucoup de thèmes pour blog (notamment celui en place sur ce site) faisaient appel à cette URL pour afficher un bloc contenant les derniers tweets de l’utilisateur. Ainsi, si ce bloc est devenu mystérieusement vide depuis hier ou qu’une erreur s’affiche, il va vous falloir modifier l’URL utilisée pour faire appel à l’API par celle-ci :

<pre class="lang:default decode:true">http://api.twitter.com/1/statuses/home_timeline.format</pre>

  * home_timeline correspond au nom de l’utilisateur
  * format correspond à l’un des 4 formats de réponse disponibles (json, xml, rss, atom)

Pour modifier l’URL, faites tout simplement une recherche sur les fichiers de votre thème (l’appel peut se faire dans le JS ou directement depuis le PHP).

Si vous avez un problème avec l’un des paramètres, n’hésitez pas à consulter [la documentation](https://dev.twitter.com/docs/api/1/get/statuses/home_timeline "Documentation Twitter").