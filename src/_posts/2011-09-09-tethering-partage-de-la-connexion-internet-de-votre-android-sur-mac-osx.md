---
id: 738
title: 'Tethering : partage de la connexion internet de votre Android sur Mac OSX'
date: 2011-09-09T13:24:09+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=738
permalink: /tethering-partage-de-la-connexion-internet-de-votre-android-sur-mac-osx/
dsq_thread_id:
  - "413532985"
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
slider_style:
  - default
image: /wp-content/uploads/2011/09/images-180x160.jpg
---
De retour de vacances, je partage avec vous une manipulation qui m’a été bien utile au cours de mon périple. En effet, vous est-il déjà arrivé de vouloir partager la connexion internet 3G de votre smartphone Android afin de naviguer tranquillement sur votre Mac ? Dans le cas présent, ce tuto est fait pour vous 🙂

Cette procédure appelée Tethering est relativement simple à effectuer, mais attention, elle n’est pas forcément bien vue de la part des opérateurs mobiles, car bien que cette option soit présente de base sur les périphériques Android, elle empiète quelque peu sur les plates bandes des clés 3G ou des forfaits avec mode modem intégré.

J’avoue que je ne vois pas où est le mal, c’est sûr, il faut éviter d’en abuser et de vous télécharger l’intégrale de &#8220;Battlestar Galactica&#8221; via cette méthode, mais bon, il semblerait que cela s’inscrive dans une démarche actuelle de faire passer en supplément des services qui pourtant devraient être acquis&#8230;

Bref, les opérateurs semblent réagir de deux manières bien distinctes face au partage de connexion:

  * ils laissent faire car de toute façon, selon leur politique, une fois votre maximum atteint (500 Mo chez la plupart), votre connexion sera bridée ou bien facturée en tant que hors-forfait (et là attention !)
  * ils bloquent tout simplement cette technique (mais nous verrons comment passer outre dans la suite)

Passons maintenant à la pratique. Voici ma configuration pour ce tuto :

  * Mac OSX 10.6.8
  * Samsung Galaxy S sous Android 2.3 (je ne sais pas quelle est la version minimale requise, à vous de tester)
  * Un cable USB (il existe sur Android une option pour transformer votre téléphone en modem wifi, perso je n&#8217;ai jamais testé car je n&#8217;en vois pas l&#8217;intérêt et que cela consomme beaucoup trop de batterie).

# Prérequis

<div>
  Vérifier que la configuration de votre APN (Access Point Network, en quelques sorte la passerelle entre le réseau mobile et les réseaux ip externe) est bonne dans :</p> 
  
  <blockquote>
    <p>
      <em>Paramètres->Connexions sans fils->Réseaux mobiles->Noms des points d&#8217;accès</em>
    </p>
  </blockquote>
  
  <p>
    Vous trouverez une liste pour les opérateurs francophones sur le wiki de <a title="Le wiki de Frandroid" href="http://wiki.frandroid.com/wiki/Configurations_Op%C3%A9rateurs">Frandroid </a>
  </p>
  
  <h1>
    Sur votre Android
  </h1>
</div>

<div>
  Comme pour le transfert de fichiers, passer votre téléphone en débogage USB :
</div>

<div>
  <blockquote>
    <p>
      <em>Paramètres->Applications->Développement->Cocher Débogage USB</em>
    </p>
  </blockquote>
  
  <h1>
    Connexion à votre Mac
  </h1>
  
  <p>
    Connectez le téléphone à votre Mac. Une nouvelle interface réseau devrait vous être signalée. Dans préférences système, allez dans réseaux.
  </p>
  
  <p>
    Si l&#8217;interface n&#8217;a pas été ajoutée dans la liste, faites-le en cliquant sur le +
  </p>
  
  <div id="attachment_742" style="width: 310px" class="wp-caption aligncenter">
    <a href="http://elliptips.info/wp-content/uploads/2011/09/Capture-d_ecran-2011-09-09-a-15.59.02.jpg"><img class="size-medium wp-image-742" title="nouvelle interface réseau mac osx" src="http://elliptips.info/wp-content/uploads/2011/09/Capture-d_ecran-2011-09-09-a-15.59.02-300x112.jpg" alt="Capture d ecran 2011 09 09 a 15.59.02 300x112 Tethering : partage de la connexion internet de votre Android sur Mac OSX" width="300" height="112" /></a>
    
    <p class="wp-caption-text">
      Ajout d'une interface réseau sur MAC OSX
    </p>
  </div>
  
  <p>
    Choisissez la bonne interface, pour moi SAMSUNG_Android, dans la liste déroulante.
  </p>
  
  <div id="attachment_743" style="width: 310px" class="wp-caption aligncenter">
    <a href="http://elliptips.info/wp-content/uploads/2011/09/Capture-d_ecran-2011-09-09-a-16.10.43.jpg"><img class="size-medium wp-image-743" title="choix de l'interface réseau" src="http://elliptips.info/wp-content/uploads/2011/09/Capture-d_ecran-2011-09-09-a-16.10.43-300x116.jpg" alt="Capture d ecran 2011 09 09 a 16.10.43 300x116 Tethering : partage de la connexion internet de votre Android sur Mac OSX" width="300" height="116" /></a>
    
    <p class="wp-caption-text">
      Choix de l'interface réseau
    </p>
  </div>
  
  <p>
    Sur l&#8217;interface créée, cliquez sur avancé, dans l&#8217;onglet modem, choisir le fabriquant et modèle GPRS (GSM/3G).
  </p>
  
  <div id="attachment_746" style="width: 310px" class="wp-caption aligncenter">
    <a href="http://elliptips.info/wp-content/uploads/2011/09/Capture-d_ecran-2011-09-09-a-16.12.14.jpg"><img class="size-medium wp-image-746 " title="édition avancée" src="http://elliptips.info/wp-content/uploads/2011/09/Capture-d_ecran-2011-09-09-a-16.12.14-300x192.jpg" alt="Capture d ecran 2011 09 09 a 16.12.14 300x192 Tethering : partage de la connexion internet de votre Android sur Mac OSX" width="300" height="192" /></a>
    
    <p class="wp-caption-text">
      Aller dans avancé de l'interface
    </p>
  </div>
  
  <div id="attachment_747" style="width: 310px" class="wp-caption aligncenter">
    <a href="http://elliptips.info/wp-content/uploads/2011/09/Capture-d_ecran-2011-09-09-a-16.12.39.jpg"><img class="size-medium wp-image-747 " title="onglet modem" src="http://elliptips.info/wp-content/uploads/2011/09/Capture-d_ecran-2011-09-09-a-16.12.39-300x113.jpg" alt="Capture d ecran 2011 09 09 a 16.12.39 300x113 Tethering : partage de la connexion internet de votre Android sur Mac OSX" width="300" height="113" /></a>
    
    <p class="wp-caption-text">
      Onglet Modem
    </p>
  </div>
  
  <p>
    Cliquez sur OK et c&#8217;est tout. Cliquez maintenant sur &#8220;Se connecter&#8221;, appliquez les changements et la connexion devrait s&#8217;établir assez rapidement.
  </p>
  
  <div id="attachment_748" style="width: 310px" class="wp-caption aligncenter">
    <a href="http://elliptips.info/wp-content/uploads/2011/09/Capture-d_ecran-2011-09-09-a-16.37.27.jpg"><img class="size-medium wp-image-748" title="connexion réussie" src="http://elliptips.info/wp-content/uploads/2011/09/Capture-d_ecran-2011-09-09-a-16.37.27-300x56.jpg" alt="Capture d ecran 2011 09 09 a 16.37.27 300x56 Tethering : partage de la connexion internet de votre Android sur Mac OSX" width="300" height="56" /></a>
    
    <p class="wp-caption-text">
      Bravo, vous êtes maintenant connecté
    </p>
  </div>
  
  <p>
    Note : j&#8217;ai vu sur plusieurs sites que des personnes remplissaient les champs numéro du téléphone, nom du compte, mot de passe et nom du point d&#8217;accès, en ce qui me concerne c&#8217;est inutile, j&#8217;imagine que cela utilise deja les réglages APN du téléphone.
  </p>
  
  <p>
    Comme dit précédemment, certains opérateurs bloquent cette technique en se basant sur le USER-AGENT, une information envoyée par votre navigateur web dans les en-têtes http, et permettant d&#8217;identifier celui-ci.
  </p>
  
  <h1>
    Contourner le blocage du user-agent
  </h1>
  
  <p>
    Il faut savoir que les headers HTTP sont aisément modifiables coté client (c&#8217;est pourquoi il faut éviter de trop s&#8217;y fier). Histoire de faire simple, nous allons utiliser un petit addon firefox nommé &#8220;<a title="User Agent Switcher" href="https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/">User Agent Switcher</a>&#8220;.
  </p>
  
  <p>
    Une fois ajouté à Firefox, éditer une configuration comme ci-dessous :
  </p>
  
  <div id="attachment_749" style="width: 310px" class="wp-caption aligncenter">
    <a href="http://elliptips.info/wp-content/uploads/2011/09/Capture-d_ecran-2011-09-09-a-16.24.21.jpg"><img class="size-medium wp-image-749" title="édition user agent" src="http://elliptips.info/wp-content/uploads/2011/09/Capture-d_ecran-2011-09-09-a-16.24.21-300x201.jpg" alt="Capture d ecran 2011 09 09 a 16.24.21 300x201 Tethering : partage de la connexion internet de votre Android sur Mac OSX" width="300" height="201" /></a>
    
    <p class="wp-caption-text">
      Edition d'un user-agent
    </p>
  </div>
  
  <div id="attachment_750" style="width: 310px" class="wp-caption aligncenter">
    <a href="http://elliptips.info/wp-content/uploads/2011/09/Capture-d_ecran-2011-09-09-a-16.47.26.jpg"><img class="size-medium wp-image-750" title="new user agent" src="http://elliptips.info/wp-content/uploads/2011/09/Capture-d_ecran-2011-09-09-a-16.47.26-300x42.jpg" alt="Capture d ecran 2011 09 09 a 16.47.26 300x42 Tethering : partage de la connexion internet de votre Android sur Mac OSX" width="300" height="42" /></a>
    
    <p class="wp-caption-text">
      Faire new
    </p>
  </div>
  
  <div id="attachment_751" style="width: 310px" class="wp-caption aligncenter">
    <a href="http://elliptips.info/wp-content/uploads/2011/09/Capture-d_ecran-2011-09-09-a-16.25.41.jpg"><img class="size-medium wp-image-751" title="edition user agent" src="http://elliptips.info/wp-content/uploads/2011/09/Capture-d_ecran-2011-09-09-a-16.25.41-300x37.jpg" alt="Capture d ecran 2011 09 09 a 16.25.41 300x37 Tethering : partage de la connexion internet de votre Android sur Mac OSX" width="300" height="37" /></a>
    
    <p class="wp-caption-text">
      Edition d'un user-agent
    </p>
  </div>
  
  <p>
    Voici mon user-agent par exemple :
  </p>
  
  <pre class="brush:plain">Mozilla/5.0 (Linux; U; Android 2.3.4; fr-fr; GT-I9000 Build/GINGERBREAD) AppleWebKit/533.1 (KHTML, like Gecko) Version/4.0 Mobile Safari/533.1</pre>
  
  <p>
    Pour bien faire, vous pouvez vérifier votre user-agent grâce à <a title="Tester son user-agent" href="http://www.useragentstring.com/">ce site</a> depuis votre mobile et remettre exactement le même.
  </p>
  
  <p>
    Une fois le user-agent édité, il vous suffit de le choisir dans la liste de &#8220;User Agent Switcher&#8221; pour l&#8217;utiliser. Vous pouvez vérifier le bon fonctionnement grâce au site précédent.
  </p>
  
  <p>
    Une dernière chose, les sites devraient maintenant vous prendre pour un navigateur mobile, et donc afficher les informations comme tel. Sachez cependant que la plupart des sites possèdent un bouton afin de switcher vers le site version desktop.
  </p>
  
  <p>
    Voilà, bon surf à tous 😉
  </p>
</div>