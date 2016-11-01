---
id: 2034
title: Internet Explorer ne peut pas afficher cette page web
date: 2013-03-15T23:00:30+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=2034
permalink: /internet-explorer-ne-peut-pas-afficher-cette-page-web/
dsq_thread_id:
  - "1137921216"
image: /wp-content/uploads/2013/03/crazy-cat1-180x160.jpg
---
J&#8217;ai eu à dépanner cet après midi un PC sous **Windows Vista** (arf) avec lequel il était impossible de se connecter à internet, ou plutôt d&#8217;afficher une page web (Internet explorer ne peut pas afficher cette page web**)**.

Il était cependant possible de pinger un hôte (ex: ping google.fr)

## Problème d&#8217;affichage des pages web

Internet Explorer affichait donc l&#8217;erreur suivante : **Internet explorer ne peut pas afficher cette page web**

Quant à Chrome et Firefox, ils me notifiaient d&#8217;un magnifique message : **Erreur 102 (net::ERR\_CONNECTION\_REFUSED) Le serveur a refusé la connexion**

Pour la petite histoire, le problème est arrivé du jour au lendemain, sans qu&#8217;aucun logiciel n&#8217;ait été installé ou mise à jour faite, aussi bien en WIFI que par câble ethernet. Le routeur, lui, fonctionnait correctement.

A ce moment, processus habituel pensant que l&#8217;une des manipulations allait régler l&#8217;affaire :

  * <span style="line-height: 13px;">vérification des paramètres du proxy (le plus probable dans ce cas)</span>
  * vérification des paramètres IP
  * tentative avec un navigateur standalone
  * vérification des paramètres de la carte réseau et réinitialisation de celle-ci
  * vérification du par-feu
  * vérification de l&#8217;antivirus
  * réinitialisation du protocole TCP/IP via la commande netsh
  * vérification que le port 80 n&#8217;est pas bloqué par un processus
  * et pour finir, tentative de désinfection à l&#8217;aide d&#8217;un antivirus standalone

A partir de là, je vous laisse imaginer le nombre incalculable de pages Google que je me suis farci pour avoir la chance de lire de nombreux &#8220;Bah formate et ça remarchera&#8221; (haaa les forums de Comment ça Marche, quel plaisir d&#8217;y chercher une solution :)).

Le problème semblait pourtant être récurent sur tout type de système (**XP, Vista ou Seven**). Au final, je suis tombé sur un post anglais ou la personne expliquait que Norton avait l&#8217;habitude de causer ce type de problème.

Il n&#8217;y avait pourtant aucune trace de celui-ci dans l&#8217;ordinateur mais dans le doute, j&#8217;ai finalement lancé **Norton Removal Tool **et le résultat ne s&#8217;est pas fait attendre : la navigation Internet a de nouveau été possible.

## Corriger le problème

Si toutes les solutions énoncées précédemment n&#8217;ont pas marché pour vous, il suffit donc de télécharger [Norton Removal Tool](https://support.norton.com/sp/en/us/home/current/solutions/kb20080710133834EN_EndUserProfile_en_us), un petit utilitaire fourni par la société qui édite Norton capable de désinstaller le logiciel antivirus proprement.

<p style="text-align: center;">
  <img class="aligncenter size-full wp-image-2036" alt="NortonRemovalTool Internet Explorer ne peut pas afficher cette page web" src="http://elliptips.info/wp-content/uploads/2013/03/NortonRemovalTool.png" width="555" height="464" srcset="http://elliptips.info/wp-content/uploads/2013/03/NortonRemovalTool.png 555w, http://elliptips.info/wp-content/uploads/2013/03/NortonRemovalTool-300x250.png 300w" sizes="(max-width: 555px) 100vw, 555px" title="Internet Explorer ne peut pas afficher cette page web photo" />
</p>

  1. Commencez par [télécharger le logiciel (lien direct)](ftp://ftp.symantec.com/public/english_us_canada/removal_tools/Norton_Removal_Tool.exe).
  2. Lancez-le
  3. Suivez les instructions 
      1. acceptez la licence
      2. cliquez sur suivant
      3. entrez le captcha
      4. faire suivant pour lancer la désinstallation
  4. Redémarrez votre ordinateur

Voilà pour la solution, en espérant que cela pourra en aider certains.