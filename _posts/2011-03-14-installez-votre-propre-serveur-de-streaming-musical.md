---
id: 455
title: Installez votre propre serveur de streaming musical
date: 2011-03-14T02:00:37+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=455
permalink: /installez-votre-propre-serveur-de-streaming-musical/
dsq_thread_id:
  - "413641460"
image: /wp-content/uploads/2011/03/subsonic-180x160.png
---
<span style="font-size: 20px; font-weight: bold;">Introduction</span>

Je vous propose aujourd&#8217;hui un tutoriel sur l&#8217;installation, la configuration et l&#8217;utilisation d&#8217;un serveur de streaming musical open source: j&#8217;ai nommé [Subsonic](http://www.subsonic.org/pages/index.jsp "Subsonic website").

Pour résumer, Subsonic vous permet donc de monter votre propre clone d&#8217;un service de Musique On Demand tel que Deezer ou Spotify. Grâce à lui, vous pourrez :

  * écouter votre musique de n&#8217;importe où  et depuis un simple navigateur internet (cela inclus les périphériques Android, Windows 7, Iphone/Ipod&#8230;)
  * exporter et importer vos playlists aux formats M3U, PLS and XSPF
  * gérer de manière avancée des utilisateurs qui pourront commenter, noter, dialoguer, etc&#8230;
  * télécharger et uploader des musiques sur le serveur
  * vous abonner à des podcasts
  * gérer votre collection musicale et éditer directement les tags de vos musiques
  * et j&#8217;en passe &#8230;

Subsonic gère la plupart des formats pouvant être diffusé via HTTP.

## Installation

Je ne décrirai que l&#8217;installation sous Linux (Ubuntu). Pour les autres systèmes, il vous suffit de télécharger l&#8217;installateur sur [cette page](http://www.subsonic.org/pages/download.jsp "Subsonic download").

On commence donc par se procurer l&#8217;environnement d&#8217;exécution java (si ça n&#8217;est pas déjà fait) :

<pre class="brush:shell">sudo apt-get install openjdk-6-jre</pre>

Ensuite, il faut récupérer le package .deb à [cette adresse](http://www.subsonic.org/pages/download.jsp "Subsonic download") puis le lancer :

<pre class="brush:shell">sudo dpkg -i subsonic-x.x.deb</pre>

Pour gérer Subsonic:

<pre class="brush:shell">sudo subsonic {start|stop|status|restart|force-reload}</pre>

On termine en vérifiant que ça fonctionne en allant sur :

http://localhost:4040

En cas de problème vérifier bien que l&#8217;environnement java à été installé.
  
Vous obtiendrez plus d&#8217;informations sur l&#8217;erreur en regardant les logs :

<pre class="brush:shell">cat /var/subsonic/subsonic_sh.log</pre>

## Configuration

Lors de votre première connexion, il vous faudra utiliser le couple d&#8217;identifiant admin | admin :

<div id="attachment_463" style="width: 310px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/03/subsonic-first.png"><img class="size-medium wp-image-463" title="subsonic-first" src="http://elliptips.info/wp-content/uploads/2011/03/subsonic-first-300x147.png" alt="subsonic first 300x147 Installez votre propre serveur de streaming musical" width="300" height="147" srcset="http://elliptips.info/wp-content/uploads/2011/03/subsonic-first-300x147.png 300w, http://elliptips.info/wp-content/uploads/2011/03/subsonic-first.png 510w" sizes="(max-width: 300px) 100vw, 300px" /></a>
  
  <p class="wp-caption-text">
    Bienvenue sur Subsonic.
  </p>
</div>

Laissez vous ensuite guider par les étapes en page d&#8217;accueil:

<p style="text-align: center;">
  <span style="text-decoration: underline;">1 &#8211; Changez votre mot de passe administrateur :</span>
</p>

<div id="attachment_466" style="width: 310px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/03/subsonic-change-password1.png"><img class="size-medium wp-image-466" title="subsonic-change-password" src="http://elliptips.info/wp-content/uploads/2011/03/subsonic-change-password1-300x167.png" alt="subsonic change password1 300x167 Installez votre propre serveur de streaming musical" width="300" height="167" srcset="http://elliptips.info/wp-content/uploads/2011/03/subsonic-change-password1-300x167.png 300w, http://elliptips.info/wp-content/uploads/2011/03/subsonic-change-password1.png 492w" sizes="(max-width: 300px) 100vw, 300px" /></a>
  
  <p class="wp-caption-text">
    Utilisez un password sécurisé, n'oubliez pas que le compte admin aura accès à toutes vos musiques stockées sur le serveur
  </p>
</div>

<p style="text-align: center;">
  <span style="text-decoration: underline;">2 &#8211; Choisir le répertoire contenant vos musiques:</span>
</p>

<div id="attachment_467" style="width: 310px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/03/subsonic-folder.png"><img class="size-medium wp-image-467" title="subsonic-folder" src="http://elliptips.info/wp-content/uploads/2011/03/subsonic-folder-300x100.png" alt="subsonic folder 300x100 Installez votre propre serveur de streaming musical" width="300" height="100" srcset="http://elliptips.info/wp-content/uploads/2011/03/subsonic-folder-300x100.png 300w, http://elliptips.info/wp-content/uploads/2011/03/subsonic-folder.png 900w" sizes="(max-width: 300px) 100vw, 300px" /></a>
  
  <p class="wp-caption-text">
    Vous pourrez choisir plusieurs répertoires
  </p>
</div>

<p style="text-align: center;">
  <span style="text-decoration: underline;">3 &#8211; Configurez les paramètres réseaux</span>
</p>

<p style="text-align: center;">
  Il est possible de configurer automatiquement votre routeur pour le port fowarding ou de créer une adresse accessible depuis l&#8217;extérieur de votre réseau du type monadresse.subsonic.org. Je vous conseil de régler ces paramètres à la main dans l&#8217;interface administration de votre box/routeur.
</p>

Voilà en ce qui concerne les principaux réglages, vous pourrez à tout moment dans l&#8217;onglets &#8220;Settings&#8221; accéder à des paramêtres de configurations avancées tel que:

  * le type d&#8217;encodeur à utiliser
  * personnaliser le message d&#8217;accueil, le texte, la langue
  * les informations à afficher pour les musiques (année, type, &#8230;)
  * le player à utiliser (web, externe, jukebox)
  * les flux pour les podcasts
  * etc&#8230;

<div id="attachment_468" style="width: 310px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/03/subsonic-settings.png"><img class="size-medium wp-image-468" title="subsonic-settings" src="http://elliptips.info/wp-content/uploads/2011/03/subsonic-settings-300x57.png" alt="subsonic settings 300x57 Installez votre propre serveur de streaming musical" width="300" height="57" srcset="http://elliptips.info/wp-content/uploads/2011/03/subsonic-settings-300x57.png 300w, http://elliptips.info/wp-content/uploads/2011/03/subsonic-settings.png 541w" sizes="(max-width: 300px) 100vw, 300px" /></a>
  
  <p class="wp-caption-text">
    Baladez vous dans les nombreux réglages disponibles
  </p>
</div>

## Utilisation

Nous allons voir quelques unes des nombreuses fonctionnalités offertes par Subsonic 🙂

<h5 style="text-align: center;">
  Créer de nouveaux utilisateurs
</h5>

L&#8217;un des principaux intérêt de Subsonic est de pouvoir le partager avec vos amis. Pour créer de nouveaux comptes utilisateurs, rendez-vous dans Settings-> Users

<div id="attachment_469" style="width: 310px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/03/subsonic-new-user.png"><img class="size-medium wp-image-469" title="subsonic-new-user" src="http://elliptips.info/wp-content/uploads/2011/03/subsonic-new-user-300x173.png" alt="subsonic new user 300x173 Installez votre propre serveur de streaming musical" width="300" height="173" srcset="http://elliptips.info/wp-content/uploads/2011/03/subsonic-new-user-300x173.png 300w, http://elliptips.info/wp-content/uploads/2011/03/subsonic-new-user.png 389w" sizes="(max-width: 300px) 100vw, 300px" /></a>
  
  <p class="wp-caption-text">
    Attention aux permissions que vous accordez à vos utilisateurs.
  </p>
</div>

<p style="text-align: center;">
  Complétez les permissions (par default, seul le droit de lecture est alloué aux utilisateurs) et donné par exemple les droits à vos amis de télécharger vos musiques, d&#8217;en uploader, créer et éditer des playlists, noter les musiques&#8230; bref de nombreuses possibilités sont offertes.
</p>

<p style="text-align: center;">
  <span style="font-size: 11px; font-weight: bold;">Le chat</span>
</p>

 <span style="font-size: 11px; font-weight: bold;"></span>

<div id="attachment_470" style="width: 220px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/03/subsonic-chat.png"><img class="size-full wp-image-470" title="subsonic-chat" src="http://elliptips.info/wp-content/uploads/2011/03/subsonic-chat.png" alt="subsonic chat Installez votre propre serveur de streaming musical" width="210" height="220" /></a>
  
  <p class="wp-caption-text">
    Le chat, une fonctionnalité sympathique
  </p>
</div>

<p style="text-align: center;">
  Un petit chat sur le côté droit de l&#8217;écran vous offre la possibilité de dialoguer entre utilisateurs et de voir les morceaux joués par chacun. Une fonctionnalité plutôt sympathique lorsque vous ne savez pas quoi écouter, il vous suffit de vous laisser guider par les autres.
</p>

<p style="text-align: center;">
  Il est possible dans l&#8217;onglet &#8220;Statut&#8221; d&#8217;accéder à des statistiques détaillées sur vos utilisateurs (bande passante,lecture en cours,&#8230;).
</p>

<p style="text-align: center;">
  <span style="font-size: 11px;"> </span>
</p>

<h5 style="text-align: center;">
  <span style="font-size: 11px;">Les podcasts</span>
</h5>

 <span style="font-size: 11px;"></span>

<div id="attachment_471" style="width: 310px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/03/subsonic-podcast.png"><img class="size-medium wp-image-471" title="subsonic-podcast" src="http://elliptips.info/wp-content/uploads/2011/03/subsonic-podcast-300x53.png" alt="subsonic podcast 300x53 Installez votre propre serveur de streaming musical" width="300" height="53" srcset="http://elliptips.info/wp-content/uploads/2011/03/subsonic-podcast-300x53.png 300w, http://elliptips.info/wp-content/uploads/2011/03/subsonic-podcast.png 759w" sizes="(max-width: 300px) 100vw, 300px" /></a>
  
  <p class="wp-caption-text">
    Une bonne façon de mettre à disposition de nombreux podcasts
  </p>
</div>

<p style="text-align: center;">
  Pour souscrire à un podcast, rien de plus simple : rentrez l&#8217;adresse puis valider.
</p>

<h5 style="text-align: center;">
  Un mode bien pratique : le jukebox.
</h5>

<div id="attachment_472" style="width: 310px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/03/subsonic-jukebox.png"><img class="size-medium wp-image-472" title="subsonic-jukebox" src="http://elliptips.info/wp-content/uploads/2011/03/subsonic-jukebox-300x73.png" alt="subsonic jukebox 300x73 Installez votre propre serveur de streaming musical" width="300" height="73" srcset="http://elliptips.info/wp-content/uploads/2011/03/subsonic-jukebox-300x73.png 300w, http://elliptips.info/wp-content/uploads/2011/03/subsonic-jukebox.png 734w" sizes="(max-width: 300px) 100vw, 300px" /></a>
  
  <p class="wp-caption-text">
    Contrôlez votre musique à distance.
  </p>
</div>

<p style="text-align: center;">
  Si vous avez installé Subsonic sur un ordinateur à votre domicile, il peux être intéressant de le relier à votre système audio. Ainsi, en passant le player en mode jukebox dans Settings -> Players, la musique sera lue directement sur le serveur, vous permettant de lancer votre musique à distance depuis n&#8217;importe quel endroit et n&#8217;importe quel périphérique.
</p>

<h5 style="text-align: center;">
  Upload
</h5>

<div id="attachment_473" style="width: 310px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/03/subsonic-upload.png"><img class="size-medium wp-image-473" title="subsonic-upload" src="http://elliptips.info/wp-content/uploads/2011/03/subsonic-upload-300x66.png" alt="subsonic upload 300x66 Installez votre propre serveur de streaming musical" width="300" height="66" srcset="http://elliptips.info/wp-content/uploads/2011/03/subsonic-upload-300x66.png 300w, http://elliptips.info/wp-content/uploads/2011/03/subsonic-upload.png 521w" sizes="(max-width: 300px) 100vw, 300px" /></a>
  
  <p class="wp-caption-text">
    Complétez votre bibliothèque musicale à tout moment
  </p>
</div>

<p style="text-align: center;">
  Dans l&#8217;onglet &#8220;More&#8221;, vous aurez la possibilité d&#8217;uploader des fichiers zip sur le serveur qui se chargera de les décompresser pour les ajouter à votre collection musicale. Indispensable si vous être une bande d&#8217;amis à utiliser Subsonic.
</p>

<h5 style="text-align: center;">
  Subsonic Apps
</h5>

<p style="text-align: center;">
  Vous pourrez utiliser subsonic aussi bien sur Android, que sur Windows 7 phone ou Iphone. Rendez vous sur <span style="text-decoration: underline;"><a href="http://subsonic.org/pages/apps.jsp">cette page</a></span> pour plus d&#8217;informations.
</p>

<div id="attachment_481" style="width: 190px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/03/SC20110314-041134.png"><img class="size-medium wp-image-481" title="subsonic-android" src="http://elliptips.info/wp-content/uploads/2011/03/SC20110314-041134-180x300.png" alt="SC20110314 041134 180x300 Installez votre propre serveur de streaming musical" width="180" height="300" srcset="http://elliptips.info/wp-content/uploads/2011/03/SC20110314-041134-180x300.png 180w, http://elliptips.info/wp-content/uploads/2011/03/SC20110314-041134.png 480w" sizes="(max-width: 180px) 100vw, 180px" /></a>
  
  <p class="wp-caption-text">
    Le client pour Android est très complet
  </p>
</div>

<p style="text-align: center;">
  Voici le lien vers le market pour l&#8217;application android (gratuite):
</p>

<div id="attachment_474" style="width: 145px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/03/chart1.png"><img class="size-full wp-image-474" title="subsonic" src="http://elliptips.info/wp-content/uploads/2011/03/chart1.png" alt="chart1 Installez votre propre serveur de streaming musical" width="135" height="135" /></a>
  
  <p class="wp-caption-text">
    QRcode Subsonic
  </p>
</div>

## Pour conclure

Ainsi se clôt cet assez long tutoriel sur le serveur de streaming Subsonic. Vous l&#8217;aurez compris, l&#8217;outil est incroyablement riche et je n&#8217;ai même pas pu citer 1/3 des fonctionnalités donc n&#8217;hésitez pas à l&#8217;installer et à l&#8217;utiliser par vous même. Vous verrez, l&#8217;essayer, c&#8217;est l&#8217;adopter 😉

&nbsp;