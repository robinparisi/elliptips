---
id: 1444
title: Problèmes avec le cache de CakePHP
date: 2012-02-22T04:27:36+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=1444
permalink: /problemes-avec-le-cache-de-cakephp/
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
dsq_thread_id:
  - "584811839"
image: /wp-content/uploads/2012/02/cakephp-180x160.jpg
---
<p style="text-align: justify;">
  Voici un petit billet rapide qui je pense pourra servir à d’autres. Je travaille en ce moment sur un projet construit à l’aide du framework CakePHP. Après la modification de la structure d’une de mes tables, je me suis retrouvé avec des erreurs inexplicables concernant mon modèle. Après plusieurs minutes à vérifier encore et encore mon code, <del>le tout de manière très zen</del>, j’ai finalement cherché du côté du cache (qui pourtant est censé se mettre à jour lors des modifications) et bingo.
</p>

<p style="text-align: justify;">
  En clair, si vous vous retrouvez avec des erreurs incompréhensibles (champ inexistant alors qu’il existe bel et bien, update impossible, etc)  liées à vos modèles, supprimer tout simplement les fichiers de cache suivant :
</p>

<pre class="brush:shell crayon-selected">rm -f app/tmp/cache/models/*
rm -f app/tmp/cache/persistent/*</pre>