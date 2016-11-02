---
id: 2105
title: Optimiser le SSD de son MacBook
date: 2013-05-04T01:29:10+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=2105
permalink: /optimiser-le-ssd-de-son-macbook/
dsq_thread_id:
  - "1259515997"
image: /wp-content/uploads/2013/05/trim-enabler-180x160.png
---
Voici comme promis (désolé pour le retard) un article regroupant quelques astuces pour **optimiser le SSD de son MacBook** et par la même occasion, en **améliorer la durée de vie**.

Ce billet fait suite à l&#8217;article [installer un SSD dans son MacBook Pro](http://elliptips.info/installer-un-ssd-dans-un-macbook-pro/) que je vous conseille de lire si vous souhaitez passer à une configuration un peu plus véloce.

Encore une fois, n&#8217;hésitez pas à poster en commentaire vos propres astuces que je me ferais un plaisir d&#8217;ajouter ici même 🙂

## Sélectionner le SSD comme disque de démarrage

Comme Maxime l&#8217;a très justement fait remarquer dans les commentaires, la première manipulation consiste à sélectionner le SSD comme disque de démarrage dans Préférence système -> démarrage. Vous verrez que le changement est flagrant avec un ordinateur capable de booter et d&#8217;arriver sur le bureau en moins d&#8217;une dizaine de secondes.

## Installez Trim Enabler

Le [TRIM](http://fr.wikipedia.org/wiki/TRIM "TRIM définition") est une fonctionnalité intéressante dont le but est d&#8217;optimiser les performances d&#8217;accès aux disques SSD. Malheureusement,  Apple  active le TRIM uniquement pour les périphériques livrés de base avec leurs machines. Si vous avez installé vous même un SSD, pas de panique, il vous suffit d&#8217;installer [TRIM Enabler](http://www.groths.org/trim-enabler/ "Trim Enabler") puis d&#8217;activer la fonctionnalité de TRIM.

&nbsp;

<p style="text-align: center;">
  <img class="aligncenter size-full wp-image-2144" alt="trim Optimiser le SSD de son MacBook" src="http://elliptips.info/wp-content/uploads/2013/05/trim.png" width="353" height="534" srcset="http://elliptips.info/wp-content/uploads/2013/05/trim.png 353w, http://elliptips.info/wp-content/uploads/2013/05/trim-198x300.png 198w" sizes="(max-width: 353px) 100vw, 353px" title="Optimiser le SSD de son MacBook photo" />
</p>

## Libérez de l&#8217;espace disque disque

Les SSD de faibles capacités sont devenus relativement abordables. Bien sûr, si vous choisissez d&#8217;installer un SSD de 128GB, il vous faudra probablement bousculer un peu vos habitudes et faire de la place sur le disque. Pour cela je vous conseille vivement d&#8217;utiliser [Disk Inventory X](http://www.derlien.com/ "Disk Inventory X") qui grâce à un rapport très visuel vous permet d&#8217;identifier immédiatement les fichiers prenant le plus d&#8217;espace.

## Empêcher les sauvegardes locales de Time Machine

Time Machine est bien pratique, le problème, c&#8217;est qu&#8217;il a tendance à sauvegarder régulièrement des informations sur le disque local lorsque le disque de backup n&#8217;est pas disponible.

Pour désactiver cette fonctionnalité, une seule option, la ligne de commande. Dans le terminal, taper la commande suivante pour désactiver les sauvegardes locales de Time Machine :

<pre class="lang:sh decode:true">sudo tmutil disablelocal</pre>

Pour la réactiver :

<pre class="lang:default decode:true">sudo tmutil enablelocal</pre>

## Désactiver le capteur de mouvement brusque

Vous l&#8217;avez probablement déjà entendu sur le disque dur de votre MacBook, le capteur de chute permet de parquer les têtes du disque pour limiter la casse en cas d&#8217;impact. Vous l&#8217;aurez compris, cette technologie est complètement inutile sur un SSD qui ne contient aucun élément mécanique. Pour vérifier l&#8217;état du capteur, entrer la commande suivante dans le terminal :

<pre class="lang:default decode:true">sudo pmset -g</pre>

Pour désactiver le capteur de chute (Sudden Motion Sensor ou SMS) :

<pre class="lang:default decode:true">sudo pmset -a sms 0</pre>

## Le mystérieux fichier sleepimage

Peut-être vous en êtes-vous rendu compte avec Disk Inventory X, il existe sur OS X un fichier dans lequel les données en RAM sont sauvegardées lorsque l&#8217;ordinateur se met en veille. L&#8217;on pourrait se dire que ce fichier n&#8217;est pas gênant, mais il provoque selon moi des accès au disque inutiles et pires, prend la place complète offerte par la RAM.

Pour être plus clair :

Vous possédez 8 GB de RAM, et, peu importe la quantité réelle de RAM utilisée, à partir du moment où votre ordinateur se mettra en veille, le fichier sleepimage utilisera 8GB sur le disque. Personnellement, je possède 16GB donc je vous avoue que j&#8217;ai très vite cherché une solution pour désactiver ce comportement.

<p style="text-align: center;">
  <p>
    Pour afficher la taille de ce fichier :
  </p>
  
  <pre class="lang:default decode:true">du -h /private/var/vm/sleepimage</pre>
  
  <p>
    J&#8217;ai trouvé la solution sur le topic suivant (https://discussions.apple.com/thread/4492672?start=0&tstart=0). Il faut donc feinter un peu. Je vous l&#8217;accorde, cette solution n&#8217;est pas très propre (voir pas du tout), mais c&#8217;est la seule qui a fonctionné dans mon cas :
  </p>
  
  <p>
    On commence par supprimer le fichier :
  </p>
  
  <pre class="lang:default decode:true">sudo rm /private/var/vm/sleepimage</pre>
  
  <p>
    Puis on en créé un nouveau vide :
  </p>
  
  <pre class="lang:default decode:true">sudo touch /private/var/vm/sleepimage</pre>
  
  <p>
    Si l&#8217;on s&#8217;arrête là, le système remplira automatiquement ce fichier avec les données de la RAM. On applique donc au fichier un flag qui spécifiera au système que ce fichier est &#8220;verrouillé&#8221; :
  </p>
  
  <pre class="lang:default decode:true">sudo chflags uchg /private/var/vm/sleepimage</pre>
  
  <p>
    À noter que vous verrez sur de nombreux autres blogs la commande suivante : <strong>sudo pmset -a hibernatemode 0</strong>. Elle ne fonctionne pas en ce qui me concerne et n&#8217;empêche en aucun cas la création du fichier sleepimage.
  </p>
  
  <h2>
    Utiliser un disque dur externe pour vos médias
  </h2>
  
  <p>
    Le dernier point est un conseil. Pour économiser la place et potentiellement la durée de vie de votre SSD, un bon compromis est de ne pas l&#8217;utiliser pour y stocker vos fichiers de &#8220;passages&#8221;. Ainsi, réservez vos films HD et autres fichiers médias à votre disque dur externe. L&#8217;intérêt d&#8217;un SSD est surtout de pouvoir en faire profiter les différentes applications qui elles utilisent énormément les accès disques. Bien entendu, si vous utilisez votre Mac pour de la MAO ou du montage vidéo, ce conseil n&#8217;a pas lieu d&#8217;être (mais il vous faudra probablement investir dans un SSD de capacité honorable). Enfin, si vous pensez que le cycle limité d&#8217;écriture d&#8217;un SSD en fait un objet &#8220;fragile&#8221;, je vous conseille de lire le dossier suivant chez PC Word : <a href="http://www.pcworld.fr/stockage/actualites,duree-vie-ssd-pratique,510669,1.htm">Test de la durée de vie d&#8217;un SSD</a>.
  </p>
  
  <h2>
    Conclusion
  </h2>
  
  <p>
    Vous trouverez ça et là d&#8217;autres optimisations qui sont à mon goût un peu tirées par les cheveux. Je ne dis pas qu&#8217;elles ne sont pas efficaces, mais selon moi, la simple activation du TRIM est déjà une bonne chose pour améliorer les performances d&#8217;accès au disque 🙂
  </p>