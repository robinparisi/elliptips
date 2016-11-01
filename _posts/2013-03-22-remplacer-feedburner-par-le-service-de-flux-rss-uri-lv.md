---
id: 2061
title: Remplacer FeedBurner par le service de flux RSS URI.LV
date: 2013-03-22T15:53:42+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=2061
permalink: /remplacer-feedburner-par-le-service-de-flux-rss-uri-lv/
dsq_thread_id:
  - "1156980147"
image: /wp-content/uploads/2013/03/uri.lv_1-180x160.png
---
Officiellement, la **fin de FeedBurner**, le service de **flux RSS proposé par Google** n&#8217;a pas encore été annoncée mais dans les faits, nul doute que celle-ci ne saurait tarder.
  
Maintenant, si vous utilisiez le service sur votre blog ou votre site, il va vous falloir passer à une **solution alternative**. En ce qui me concerne, j&#8217;ai choisi de passer à [URI.LV](http://uri.lv/), un service proposé par Maxime Valette dont vous connaissez probablement le site VDM.

Vous y retrouverez les fonctionnalités qui ont su faire la notoriété de FeedBurner :

  * un système de statistiques
  *  le gestion du protocole PubSubHubbub qui permet la mise à jour des flux en temps réel
  *  l&#8217;abonnement par newsletter
  *  le cache des fichiers RSS

<img class="aligncenter size-large wp-image-2066" alt="Capture d ecran 2013 03 22 a 15.39.17 800x114 Remplacer FeedBurner par le service de flux RSS URI.LV" src="http://elliptips.info/wp-content/uploads/2013/03/Capture-d_ecran-2013-03-22-a-15.39.17-800x114.png" width="800" height="114" title="Remplacer FeedBurner par le service de flux RSS URI.LV photo" />

La mise en place est enfantine et contrairement à FeedBurner, ce sera **l&#8217;adresse de votre flux** qui apparaîtra dans le lecteur de vos abonnés (grâce à un système de redirection). Ce point est essentiel puisqu&#8217;il **supprimera toute dépendance** vis-a-vis du service et il vous suffira alors de supprimer la redirection pour utiliser à nouveau le système natif de votre blog.

[La procédure de migration](http://uri.lv/feeds/migrate) se déroule en 3 étapes :

  * inscription et création de votre flux sur URI.LV
  * redirection du flux natif (http://votresite.fr/feed) vers celui du service URI.LV
  * désactivation du flux sur feedburner et redirection vers le flux natif de votre blog (c&#8217;est cette étape qui vous permettra de ne pas perdre d&#8217;abonnés en cours de route)

Pour ceux qui utilisent **Nginx**, voici un exemple de redirection à mettre en place dans votre fichier de conf :

<pre class="lang:default decode:true">if ($http_user_agent !~ (FeedValidator|uri\.lv)){
    rewrite ^/feed$ http://feeds.uri.lv/elliptips redirect;
}</pre>

Je pense que la fermeture prochaine de Feedburner sera une bonne leçon pour tous ceux qui considèrent les services du géant Google comme éternels. Ne vous méprenez pas sur mes intentions : j&#8217;utilise leurs produits au quotidien (trop à mon goût) et je les trouve très pratiques.

Néanmoins, il est judicieux comme pour tout service externalisé d’être conscient de votre dépendance et des conséquences qu&#8217;un arrêt brutal de celui-ci pourrait entraîner.

C&#8217;est une problématique qui revient sans fin et la chute prochaine de Reader en est l&#8217;exemple parfait : beaucoup de services étaient basés sur Reader et tandis que certains doivent s&#8217;en mordre les doigts, d&#8217;autres sauront certainement tirer profit de cette ouverture (coucou Feedly).