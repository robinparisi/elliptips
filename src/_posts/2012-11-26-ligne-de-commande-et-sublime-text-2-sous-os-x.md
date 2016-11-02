---
id: 1766
title: Ligne de commande et Sublime Text 2 sous OS X
date: 2012-11-26T19:50:35+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=1766
permalink: /ligne-de-commande-et-sublime-text-2-sous-os-x/
dsq_thread_id:
  - "945085482"
image: /wp-content/uploads/2012/11/sublime-text-logo-180x160.png
---
Voici une petite astuce pour éditer un ou plusieurs fichiers directement depuis la ligne de commande avec Sublime Text. Cette manipulation se révèle extrêmement pratique si vous avez l’habitude d’utiliser le terminal au lieu du Finder pour naviguer dans votre arborescence de fichiers (plus rapide pour l&#8217;édition de fichiers cachés ou non accessibles par défault depuis le Finder).

# Configuration

Commencez par créer un répertoire bin dans votre home (si ça n’est pas déjà fait) :

<pre class="lang:default decode:true">mkdir ~/bin</pre>

N’oubliez pas d’éditer la variable d’environnement PATH pour y ajouter le dossier bin  (exemple avec ma configuration) :

<pre class="lang:sh decode:true">export PATH=/bin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:/usr/X11/bin:/opt/bin:/usr/local/git/bin:~/bin</pre>

On créé un lien symbolique pointant vers le binaire de Sublime Text dans le dossier bin :

<pre class="lang:sh decode:true">ln -s "/Applications/Sublime Text 2.app/Contents/SharedSupport/bin/subl" ~/bin/subl</pre>

On recharge la configuration pour prendre en compte les changements (dans mon cas, la variable PATH se trouve dans mon .zshrc) :

<pre class="lang:sh decode:true">source .zshrc</pre>

# Utilisation

Exemple d&#8217;édition d&#8217;un fichier :

<pre class="lang:sh decode:true">subl /etc/php.ini</pre>

La liste des commandes (subl &#8211;help) :

<pre class="lang:default decode:true crayon-selected">Sublime Text 2 Build 2217

Usage: subl [arguments] [files]         edit the given files
   or: subl [arguments] [directories]   open the given directories
   or: subl [arguments] -               edit stdin

Arguments:
  --project &lt;project&gt;: Load the given project
  --command &lt;command&gt;: Run the given command
  -n or --new-window:  Open a new window
  -a or --add:         Add folders to the current window
  -w or --wait:        Wait for the files to be closed before returning
  -b or --background:  Don't activate the application
  -s or --stay:        Keep the application activated after closing the file
  -h or --help:        Show help (this message) and exit
  -v or --version:     Show version and exit

--wait is implied if reading from stdin. Use --stay to not switch back
to the terminal when a file is closed (only relevant if waiting for a file).

Filenames may be given a :line or :line:column suffix to open at a specific
location.</pre>