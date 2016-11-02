---
id: 1541
title: 'Gitignore-boilerplate : un gitignore à portée de shell'
date: 2012-05-03T09:30:10+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=1541
permalink: /gitignore-boilerplate-un-gitignore-a-portee-de-shell/
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
dsq_thread_id:
  - "673881666"
image: /wp-content/uploads/2012/05/git-180x160.png
---
<p style="text-align: justify;">
  Le fichier <strong>gitignore</strong> est un petit fichier bien utile et connu de tous les utilisateurs du célèbre gestionnaire de version <strong>Git</strong>. Ce fichier, qu’il vous faut créer à la racine de vos projets, contient une liste de tous les fichiers qui ne <strong>doivent pas être pris en compte par Git</strong>. Vous vous en doutez, cette liste dépend fortement du langage/framework utilisé, et même de l’OS sur lequel vous vous trouvez (foutus DS_STORE). C’est là que le script shell <a title="gitgnore-boilerplate" href="https://github.com/simonwhitaker/gitignore-boilerplates">gitignore-boilerplate</a> intervient : il va se charger de remplir pour vous le fichier gitignore en se basant sur une série de templates (pour les curieux, disponibles sur GitHub à <a title="gitgnore templates" href="https://github.com/github/gitignore">cette adresse</a>).
</p>

<p style="text-align: justify;">
  On commence par récupérer le projet sur le <a title="Simon Whitacker on Github" href="https://github.com/simonwhitaker/gitignore-boilerplates">GitHub de Simon Whitacker</a>
</p>

<pre class="brush:shell">curl -OL https://github.com/simonwhitaker/gitignore-boilerplates/tarball/master</pre>

<p style="text-align: justify;">
  On décompresse le tout
</p>

<pre class="brush:shell">tar -xzvf master</pre>

<p style="text-align: justify;">
  Il faut ensuite copier l’exécutable dans un endroit accessible à votre $PATH (echo $PATH). En ce qui me concerne, je place mes exécutables dans /bin
</p>

<pre class="brush:shell">cd simonwhitaker-gitignore-boilerplates-c1987c5
sudo cp gibo /bin</pre>

<p style="text-align: justify;">
  Voilà pour ce qui est de l’installation. Passons maintenant à l’utilisation. Il suffit pour cela d’appeler le script en lui passant le ou les templates souhaités et de rediriger le résultat vers le fichier gitignore.  On commence donc par récupérer la liste des templates disponibles
</p>

<pre class="brush:shell">gibo -l</pre>

<p style="text-align: justify;">
  Puis on lance une commande
</p>

<pre class="brush:shell">gibo CakePHP OSX vim &gt;&gt; .gitignore</pre>

<p style="text-align: justify;">
  Ce qui nous donne
</p>

<pre class="brush:shell">### /Users/robin/.gitignore-boilerplates/CakePHP.gitignore

tmp/*
config/database.php
app/tmp/*
app/config/database.php
!empty

### /Users/robin/.gitignore-boilerplates/Global/OSX.gitignore

.DS_Store

# Thumbnails
._*

# Files that might appear on external disk
.Spotlight-V100
.Trashes

### /Users/robin/.gitignore-boilerplates/Global/vim.gitignore

.*.sw[a-z]
*.un~
Session.vim</pre>

<p style="text-align: justify;">
  Idéal pour gagner un peu de temps 🙂
</p>