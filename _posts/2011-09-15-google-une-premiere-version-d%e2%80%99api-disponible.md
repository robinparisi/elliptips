---
id: 832
title: 'Google+ : une première version d’API disponible'
date: 2011-09-15T22:35:07+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=832
permalink: '/google-une-premiere-version-d%e2%80%99api-disponible/'
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
dsq_thread_id:
  - "415877004"
image: /wp-content/uploads/2011/09/Google-Plus1-e13104450641223-180x160.jpg
---
Google vient tout juste de lancer une première version de son API pour le réseau social Google+, et en a d’ailleurs profité pour accompagner ce lancement avec un tout nouveau [site](https://developers.google.com/+/api/ "Nouveau site Google pour les développeurs") dédié aux développeurs.

Pour l’instant, celle-ci permet principalement un accès en lecture seule à des informations provenant du profil publique d’une personne (nom, prénom, anniversaire, etc) et reste donc très limitée, mais cela reste une aubaine pour tous les développeurs de part le monde qui rêvaient de se faire les dents dessus.

En ce qui concerne les détails techniques, l’API est de type [RESTful](http://fr.wikipedia.org/wiki/Representational_State_Transfer "Article Wikipedia") et renvoie les données sous forme JSON. Bien entendu, pour l’utiliser, vous aurez besoin de demander [votre clé d’API](https://developers.google.com/+/api/oauth#apikey "Obtenir une clé d’api google+").

Sachez aussi que Google dispose de nombreuses bibliothèques Open Sources histoire d’effectuer vos requêtes, notemment dans les langages suivants :

  *  [Java](http://code.google.com/p/google-api-java-client/)
  * [GWT](http://code.google.com/p/gwt-google-apis/)
  * [Python](http://code.google.com/p/google-api-python-client/)
  * [Ruby](http://code.google.com/p/google-api-ruby-client/)
  * [PHP](http://code.google.com/p/google-api-php-client/)
  * [Obj-C](http://code.google.com/p/google-api-objectivec-client/)
  * [.NET](http://code.google.com/p/google-api-dotnet-client/)

<span style="text-decoration: underline;">Un exemple d’appel :</span>

<pre class="brush:plain">GET https://www.googleapis.com/plus/v1/people/108189587050871927619?key=yourAPIKey</pre>

<span style="text-decoration: underline;">Un exemple de réponse :</span>

<pre class="brush:plain">{
 "kind": "plus#person",
 "id": "108189587050871927619",
 "displayName": "Chris Chabot",
 "image": {
  "url": "https://lh5.googleusercontent.com/-cQNLOQzkGpE/AAAAAAAAAAI/AAAAAAAAEjo/M9_pXL-ra4Q/photo.jpg"
 },
 "organizations": [
  {
   "name": "Google+ Developer Relations",
   "title": "Developer Advocate & Manager",
   "type": "work"
  }
 ]
}</pre>

<p class="brush:plain">
  A vos claviers 😉
</p>