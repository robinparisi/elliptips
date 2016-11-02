---
id: 518
title: 'IOIO : Interagissez depuis Android avec le monde réel'
date: 2011-04-11T21:36:26+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=518
permalink: /ioio-interagissez-depuis-android-avec-le-monde-reel/
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
dsq_thread_id:
  - "414084691"
image: /wp-content/uploads/2011/04/ioio-android-B-180x160.jpg
---
Je viens de tomber sur un truc plutôt cool qui je pense plaira à tous les bidouilleurs adeptes du développement Android.

IOIO (à prononcer yo-yo) est une petite carte électronique qui se connecte à un périphérique Android par l’intermédiaire de l’usb, et qui vous permet de faire le lien entre le software et le monde réel. Vous pourrez alors, grâce aux entrées/sorties de IOIO, imaginer tout un tas d’interactions possibles et les mettre en pratique le plus simplement du monde (pour peu de savoir développer sous Android).

&nbsp;

<div id="attachment_519" style="width: 310px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/04/IOIO-carte-electronique-entres-sorties-android-usb-2.jpg"><img class="size-medium wp-image-519" title="IOIO la carte éléctronique" src="http://elliptips.info/wp-content/uploads/2011/04/IOIO-carte-electronique-entres-sorties-android-usb-2-300x137.jpg" alt="IOIO carte electronique entres sorties android usb 2 300x137 IOIO : Interagissez depuis Android avec le monde réel" width="300" height="137" srcset="http://elliptips.info/wp-content/uploads/2011/04/IOIO-carte-electronique-entres-sorties-android-usb-2-300x137.jpg 300w, http://elliptips.info/wp-content/uploads/2011/04/IOIO-carte-electronique-entres-sorties-android-usb-2.jpg 600w" sizes="(max-width: 300px) 100vw, 300px" /></a>
  
  <p class="wp-caption-text">
    IOIO est minuscule mais dispose tout de même de 48 pins d’entrées/sorties
  </p>
</div>

<p style="text-align: left;">
  <p style="text-align: left;">
    Pour les spécifications techniques :
  </p>
  
  <ul>
    <li style="text-align: left;">
      48 pins d’entrées/sorties
    </li>
    <li style="text-align: left;">
      16 entrées analogiques (10-bits)
    </li>
    <li style="text-align: left;">
      9 sorties PWM
    </li>
    <li style="text-align: left;">
      jusqu’à 4 liaisons séries UART
    </li>
    <li style="text-align: left;">
      jusqu’à 3 liaisons SPI
    </li>
    <li style="text-align: left;">
      jusqu’à 3 liaisons TWI (I2C-compatible)
    </li>
  </ul>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    J’ai pu lire dans les spécifications que la carte disposait d’un régulateur de tension 5v &#8211; 1,5 A permettant de recharger le téléphone ou d’alimenter de petits moteurs ( je vois d’ici nombre de petits robots voir le jour)
  </p>
  
  <p>
    Pour contrôler les entrées/sorties, vous pourrez utiliser une application toute faite ou bien créer la vôtre, ce qui en passant, je pense, est bien plus fun 🙂
  </p>
  
  <p>
    Voilà un petit exemple pour contrôler un petit servo moteur sur le pin 12 et récupérer la valeur d’un potentiomètre sur le pin 14 :
  </p>
  
  <pre class="brush:java">ioio.waitForConnect();
AnalogInput input = ioio.openAnalogInput(40);
PwmOutput pwmOutput = ioio.openPwmOutput(12, 100);  // 100Hz
while (true) {
  float reading = input.read();
  pwmOutput.setPulseWidth(1000 + Math.round(1000 * reading));
  sleep(10);
}</pre>
  
  <p>
    IOIO est donc un excellent compagnon pour de petits projets, comme par exemple pour des étudiants ne voulant pas acheter des capteurs trop couteux, et préférant utiliser les capteurs du device sous Android ( et j’imagine qu’il y a de quoi faire)&#8230;
  </p>
  
  <p>
    Le fabriquant à mis une liste des périphériques reconnu comme compatibles sur <a href="http://www.sparkfun.com/products/10585">son site</a> (nul doutes qu’il y en a d’autre) :
  </p>
  
  <ul>
    <li>
      Nexus One
    </li>
    <li>
      Nexus S
    </li>
    <li>
      Motorola
    </li>
    <li>
      Droid X
    </li>
    <li>
      G1
    </li>
  </ul>
  
  <p>
    Pour se procurer IOIO, aux alentours de 50 dollars (environ 35 euros), c’est par <a title="Le site de sparkfun" href="http://www.sparkfun.com/products/10585">ici</a> (pour le moment en rupture de stock).
  </p>
  
  <p>
    J’imagine déjà les futurs projets à base de cette petite carte fleurir 😀
  </p>
  
  <p>
    &nbsp;
  </p>