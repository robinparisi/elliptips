---
id: 2417
title: 'InstantClick: accélérer la navigation sur son site web'
date: 2014-02-16T23:49:54+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=2417
permalink: /instantclick-accelerer-la-navigation-de-son-site-web/
dsq_thread_id:
  - "2277031145"
image: /wp-content/uploads/2014/02/instant-click.png
---
[InstantClick](http://instantclick.io/ "InstantClick site") est une petite **bibliothèque JavaScript** bien sympathique puisque celle-ci permet d&#8217;accélérer la navigation sur un site internet.

Pour cela, InstantClick va précharger les pages lors de la navigation en se basant sur trois types d&#8217;évènements au choix :

  * au hover sur un lien
  * au hover sur un lien et après un délai
  * au mousedown (un lien n&#8217;est ouvert que lorsque le bouton de la souris est relâché, on gagne donc quelques millisecondes qui participent tout de même à donner cette impression de vitesse)

Si vous êtes un peu dubitatif sur le fonctionnement, je vous encourage à faire le test du clic sur la [page suivante](http://instantclick.io/click-test.html "IInstantClick test"). Ainsi, on remarque que le délai écoulé entre le hover sur un lien et le clic est en général situé entre 200 et 500 ms.

<p style="text-align: center;">
  <img class="aligncenter size-full wp-image-2419" alt="instant click InstantClick: accélérer la navigation sur son site web" src="http://elliptips.info/wp-content/uploads/2014/02/instant-click.png" title="InstantClick: accélérer la navigation sur son site web photo" />
</p>

InstantClick va alors tirer profit de ce délai pour faire une requête en utilisant [le combo pushState + Ajax](https://github.com/defunkt/jquery-pjax "Découvrir pjax") (plus connu sous le nom de pjax) et propose de ce fait plusieurs avantages :

  * les fichiers JS et CSS ne sont pas recompilés à chaque changement de page
  * le chargement est casi imperceptible (pas de flash)
  * la navigation n&#8217;est pas cassée (un point crucial dans l&#8217;expérience utilisateur)

Maintenant, si vous choisissiez d&#8217;implémenter la lib sur votre site, je vous encourage à bien réfléchir avant **au type d&#8217;évènement que vous souhaitez utiliser** :

  * L&#8217;évènement hover sur un site contenant énormément de liens pourrait entrainer trop de requêtes superflues vers le serveur (et donc surcharger celui-ci inutilement)
  * L&#8217;évènement mousedown sera **inefficace avec l&#8217;utilisation d&#8217;un trackpad**. J&#8217;ai fait le test sur mon mac, le mousedown levé par un clic au trackpad génère un délai d&#8217;environ 7 ms (contre 100 ms avec le bouton physique).
  * L&#8217;évènement hover + délai semble lui être un bon compromis, à condition que le délai soit en dessous de la barre des 100 ms (sinon le mousedown lui sera préférable)

Pour finir, sachez qu&#8217;il ne vous suffira pas de charger InstantClick pour que tout se fasse comme par magie et vous aurez probablement besoin de faire quelques ajustements pour éviter le conflit avec vos autres scripts (**notamment parce que l&#8217;évènement DOMContentLoaded ne sera pas déclenché par la lib**).De plus, il faut être conscient que le script permettra d&#8217;accélérer la navigation et non d&#8217;améliorer les performances globales de votre site.