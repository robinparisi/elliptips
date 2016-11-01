---
id: 1619
title: Analyse du piratage des 12 millions d’identifiants de terminaux Apple subtilisés au FBI
date: 2012-09-05T08:30:52+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=1619
permalink: /analyse-du-piratage-des-12-millions-didentifiants-de-terminaux-apple-subtilises-au-fbi/
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
dsq_thread_id:
  - "831501068"
image: /wp-content/uploads/2012/09/antisec-logo-180x160.jpg
---
<p style="text-align: justify;">
  <span style="text-align: justify;">L’information ne vous aura sans doute pas échappée puisqu’elle a fait le tour des médias, mais sachez qu’un groupe de hackers appartenant à la mouvance <a title="Le mouvement AntiSec sur wikipedia" href="http://fr.wikipedia.org/wiki/Antisec_Movement">AntiSec</a> a <a title="antisec pastebin" href="http://pastebin.com/nfVT7b0Z">accusé le FBI</a> d’avoir constitué une liste d’environ <strong>12 millions d’identifiants uniques</strong> liés à des <strong>terminaux Apple</strong>. Selon le groupe de hacker, ces données seraient utilisées par le FBI à des fins de surveillance. Le FBI, lui, se défend de cette accusation, notamment par l’intermédiaire de son compte Twitter :</span>
</p>

<p style="text-align: justify;">
  <blockquote class="twitter-tweet" width="550">
    <p>
      Statement soon on reports that one of our laptops with personal info was hacked. We never had info in question. Bottom Line: TOTALLY FALSE
    </p>
    
    <p>
      &mdash; FBI PressOffice (@FBIPressOffice) <a href="https://twitter.com/FBIPressOffice/statuses/243089221529763840">September 4, 2012</a>
    </p>
  </blockquote>
  
  <p>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p style="text-align: justify;">
    Cette attaque ferait suite au discours d’un général de la NSA lors de la précédente Defcon qui se tenait à Las Vegas. Le général en question se serait ainsi présenté à cet évènement dans le but d’y recruter des hackers, ce qui n’a visiblement pas plu à certains des membres de cette communauté.
  </p>
  
  <p style="text-align: justify;">
    Un fichier contenant un échantillon d’identifiants de terminaux Apple a ainsi été publié (le fichier source représenterait 12 millions d’ID). En accord avec l’idéologie du courant de pensée AntiSec, les informations personnelles n’ont pas été communiquées et le fichier a par conséquent été dépouillé de toute donnée sensible, cette publication ayant pour vocation de créer un petit buzz médiatique et en toute logique, d’attirer l’attention.
  </p>
  
  <p style="text-align: justify;">
    Publié sous forme d’une archive protégée, le fichier texte est disponible à l’une des adresses suivantes.
  </p>
  
  <pre class="lang:default decode:true">http://freakshare.com/files/6gw0653b/Rxdzz.txt.html
http://u32.extabit.com/go/28du69vxbo4ix/?upld=1
http://d01.megashares.com/dl/22GofmH/Rxdzz.txt
http://minus.com/l3Q9eDctVSXW3
https://minus.com/mFEx56uOa
http://uploadany.com/?d=50452CCA1
http://www.ziddu.com/download/20266246/Rxdzz.txt.html
http://www.sendmyway.com/2bmtivv6vhub/Rxdzz.txt.html</pre>
  
  <p>
    Le fichier est encrypté à l’aide d’openssl
  </p>
  
  <pre class="lang:sh decode:true">openssl aes-256-cbc -d -a -in Rxdzz.txt -out decryptedfile.tar.gz</pre>
  
  <p>
    Mot de passe :
  </p>
  
  <pre>antis3cs5clockTea#579d8c28d34af73fea4354f5386a06a6</pre>
  
  <p>
    On décompresse l’archive
  </p>
  
  <pre class="lang:sh decode:true">tar -xzvf decryptedfile.tar.gz</pre>
  
  <p>
    Puis l’on se retrouve avec un fichier texte pesant 136 Mo
  </p>
  
  <p>
    Le fichier contient 1,000,001 identifiants (une portion du véritable fichier)
  </p>
  
  <pre class="lang:sh mark:2 decode:true">→ wc -l iphonelist.txt 
 1000001 iphonelist.txt</pre>
  
  <p style="text-align: justify;">
    La première colonne correspond à l’UDID, un identifiant unique de 40 caractères permettant de rendre chaque iDevice unique. En théorie (oui tout est possible), vous ne risquez rien à ce que cette donnée se balade dans la nature.<br /> Dans l’ordre, les autres colonnes correspondent au :
  </p>
  
  <ul>
    <li>
      Jeton Apple Push Notification
    </li>
    <li>
      Nom du terminal
    </li>
    <li>
      Type du terminal (iPad, iPhone)
    </li>
  </ul>
  
  <p style="text-align: justify;">
    Il semblerait que le jeton puisse permettre l’envoi de notifications push vers le device concerné. J’ai franchement un gros doute concernant ce point, et si un développeur iOS passe dans le coin, qu’il n’hésite pas à éclairer ma lanterne.
  </p>
  
  <p style="text-align: justify;">
    En cherchant les chaînes de caractères «iPad de» «iPhone de» ou «iPod de», l’on peut avoir un ordre d’idée concernant le nombre de périphériques français contenu dans ce fichier. Je vous l’accorde, c’est un raccourci très grossier puisqu’il existe bien évidemment plusieurs pays francophones, mais l’on cherche juste à obtenir une approximation (il faut aussi partir du postulat que la plupart des gens ne changent pas le nom par défaut de leur terminal).
  </p>
  
  <pre class="lang:sh mark:2 decode:true">→ egrep -c "iPad de|iPod de|iPhone de" iphonelist.txt
41717</pre>
  
  <p style="text-align: justify;">
    Soit environ 4% sur le total d&#8217;identifiants contenu dans ce fichier.
  </p>
  
  <p style="text-align: justify;">
    Si vous souhaitez savoir si vous vous trouvez dans cette liste, il vous suffit de <strong>récupérer votre UDID</strong> (possible depuis iTunes ou en téléchargeant une application gratuite sur le store, je vous laisse chercher avec «UDID») et pour finir, de lancer un simple grep sur le fichier.
  </p>
  
  <pre class="lang:sh decode:true">grep UDID iphonelist.txt</pre>
  
  <p style="text-align: justify;">
    N’oubliez pas que la liste est incomplète. J’attire toutefois votre attention sur le fait que dans l’absolu, vous ne risquez rien. L’opération vise surtout à informer le grand public des risques d’un identifiant unique, mais aussi à s’interroger sur certaines pratiques qu’ont les autorités américaines. Bref une histoire de plus dans la longue liste des gouvernements un peu trop curieux vis-a-vis des données personnelles de leurs citoyens.
  </p>