---
id: 230
title: Utiliser les tunnels SSH
date: 2011-01-27T14:12:13+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=230
permalink: /tunnel-ssh/
dsq_thread_id:
  - "416018323"
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
slider_style:
  - default
image: /wp-content/uploads/2011/01/190px-OpenSSH_logo-180x160.png
---
SSH c&#8217;est bien pratique et je pense que personne ne me contredira la dessus, mais connaissez-vous les tunnels SSH ?

Il existe plusieurs façons de créer un tunnel SSH. En ce qui nous concerne, nous allons voir aujourd&#8217;hui comment utiliser un de ces tunnels couplé à un navigateur web afin de surfer sur internet au travers d&#8217;un serveur distant.

### Ok, mais ça sert à quoi ?

Chacun y trouvera une utilité. Vous pouvez par exemple utiliser un tunnel SSH si :

  * Vous ne faites pas confiance au réseau sur lequel vous vous trouvez et ne souhaitez pas que votre trafic non-sécurisé y transite
  * Une politique de restriction est mise en place et vous ne pouvez pas accéder à certains sites
  * Vous ne voulez pas ouvrir d&#8217;autres ports que celui dédié à SSH sur votre routeur mais vous souhaitez tout de même accéder à des interfaces web de gestion sur votre serveur (par exemple pour un client torrent ou ftp).

### Comment ça marche ?

Je vous ai fait un petit schéma, ce sera sûrement mieux qu&#8217;un long discours :

Le principe est simple: initier une connexion chiffrée entre votre machine et un serveur distant et ensuite naviguer sur internet comme si vous vous trouviez sur le serveur distant. Le rôle du serveur est donc de relayer les requêtes HTTP ou autres qui transitent par le tunnel SSH.

<div id="attachment_839" style="width: 529px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/01/tunnel_ssh1.jpg"><img class="size-full wp-image-839  " title="tunnel_ssh" src="http://elliptips.info/wp-content/uploads/2011/01/tunnel_ssh1.jpg" alt="tunnel ssh1 Utiliser les tunnels SSH" width="519" height="358" srcset="http://elliptips.info/wp-content/uploads/2011/01/tunnel_ssh1.jpg 927w, http://elliptips.info/wp-content/uploads/2011/01/tunnel_ssh1-300x206.jpg 300w" sizes="(max-width: 519px) 100vw, 519px" /></a>
  
  <p class="wp-caption-text">
    Un tunnel SSH
  </p>
</div>

### Pré-requis

Vous aurez bien sûr besoin d&#8217;un serveur SSH  et d&#8217;un accès à ce serveur. Pour cet exemple, nous utiliserons Firefox mais le principe reste le même sur les autres navigateurs.

### Etablir la connexion SSH

Tout d&#8217;abord, choisissons un port au hasard, mais attention, celui-ci ne doit pas être utilisé sur la machine cliente, par exemple le 9999.

Ensuite dans un terminal (si vous êtes sous windows, vous pouvez utiliser Putty):

<pre class="brush:shell">ssh -D 9999 -p 2222 utilisateur@hostname</pre>

utilisateur : votre user sur le serveur distant

hostname : l&#8217;adresse ip du serveur distant

### Configurons Firefox

<p style="text-align: center;">
  Dans Firefox : Préférences -> Avancé -> Réseaux puis Paramêtres
</p>

<p style="text-align: center;">
  <a href="http://elliptips.info/wp-content/uploads/2011/01/firefox_parametres.png"><img class="aligncenter size-full wp-image-240" title="firefox_parametres" src="http://elliptips.info/wp-content/uploads/2011/01/firefox_parametres.png" alt="firefox parametres Utiliser les tunnels SSH" width="476" height="246" srcset="http://elliptips.info/wp-content/uploads/2011/01/firefox_parametres.png 680w, http://elliptips.info/wp-content/uploads/2011/01/firefox_parametres-300x154.png 300w" sizes="(max-width: 476px) 100vw, 476px" /></a>
</p>

<p style="text-align: center;">
  Configurez l&#8217;hôte SOCKS comme sur la capture ci-dessous
</p>

<div id="attachment_239" style="width: 510px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/01/firefox_config.png"><img class="size-full wp-image-239 " title="firefox_config" src="http://elliptips.info/wp-content/uploads/2011/01/firefox_config.png" alt="firefox config Utiliser les tunnels SSH" width="500" height="430" srcset="http://elliptips.info/wp-content/uploads/2011/01/firefox_config.png 625w, http://elliptips.info/wp-content/uploads/2011/01/firefox_config-300x258.png 300w" sizes="(max-width: 500px) 100vw, 500px" /></a>
  
  <p class="wp-caption-text">
    Configuration de Firefox pour le tunneling
  </p>
</div>

Et voilà, vous pouvez maintenant surfez en toute tranquillité.

### Test

Pour tester, si je me rends sur un site affichant l&#8217;adresse IP, je me retrouve avec :

<div id="attachment_242" style="width: 394px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/01/ip_distante.png"><img class="size-full wp-image-242" title="ip_distante" src="http://elliptips.info/wp-content/uploads/2011/01/ip_distante.png" alt="ip distante Utiliser les tunnels SSH" width="384" height="56" srcset="http://elliptips.info/wp-content/uploads/2011/01/ip_distante.png 384w, http://elliptips.info/wp-content/uploads/2011/01/ip_distante-300x43.png 300w" sizes="(max-width: 384px) 100vw, 384px" /></a>
  
  <p class="wp-caption-text">
    IP avec laquelle je navigue
  </p>
</div>

On retrouve bien l&#8217;adresse du serveur alors que ma propre adresse est :

<div id="attachment_243" style="width: 383px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/01/mon_ip.png"><img class="size-full wp-image-243" title="mon_ip" src="http://elliptips.info/wp-content/uploads/2011/01/mon_ip.png" alt="mon ip Utiliser les tunnels SSH" width="373" height="49" srcset="http://elliptips.info/wp-content/uploads/2011/01/mon_ip.png 373w, http://elliptips.info/wp-content/uploads/2011/01/mon_ip-300x39.png 300w" sizes="(max-width: 373px) 100vw, 373px" /></a>
  
  <p class="wp-caption-text">
    Ma véritable IP
  </p>
</div>

On peut donc en conclure que le tunnel fonctionne.

Et je peux par exemple accéder à l&#8217;interface Webmin du serveur sur le port 10000:

<div id="attachment_245" style="width: 507px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/01/webmin.png"><img class="size-full wp-image-245 " title="webmin" src="http://elliptips.info/wp-content/uploads/2011/01/webmin.png" alt="webmin Utiliser les tunnels SSH" width="497" height="214" srcset="http://elliptips.info/wp-content/uploads/2011/01/webmin.png 829w, http://elliptips.info/wp-content/uploads/2011/01/webmin-300x128.png 300w" sizes="(max-width: 497px) 100vw, 497px" /></a>
  
  <p class="wp-caption-text">
    Interface Webmin
  </p>
</div>

### <span style="font-size: medium;">Pour finir</span>

### <span style="font-weight: normal; font-size: small;">Les requêtes DNS, elles, ne passent pas par le tunnel. Pour résoudre le problème, il faut taper dans la barre d&#8217;adresse de Firefox &#8220;about:config&#8221; puis répondre à l&#8217;avertissement par &#8220;Je ferai attention&#8221;.</span>

<span style="font-size: small;">A l&#8217;aide du filtre, rechercher la valeur <strong>network.proxy.socks_remote_dns </strong>puis inverser son état (clique droit -> inverser)</span>

&nbsp;

<div id="attachment_247" style="width: 606px" class="wp-caption aligncenter">
  <a href="http://elliptips.info/wp-content/uploads/2011/01/config_dns_firefox.png"><img class="size-full wp-image-247 " title="config_dns_firefox" src="http://elliptips.info/wp-content/uploads/2011/01/config_dns_firefox.png" alt="config dns firefox Utiliser les tunnels SSH" width="596" height="75" srcset="http://elliptips.info/wp-content/uploads/2011/01/config_dns_firefox.png 852w, http://elliptips.info/wp-content/uploads/2011/01/config_dns_firefox-300x37.png 300w" sizes="(max-width: 596px) 100vw, 596px" /></a>
  
  <p class="wp-caption-text">
    Inverser l&#8217;état de network.proxy.socks_remote_dns
  </p>
</div>

Et voilà, les requêtes DNS passent elles aussi par le tunnel.

Ne pas oublier de repasser la valeur à false lorsque vous aurez terminé.

Une fois que vous n&#8217;avez plus l&#8217;utilité du tunnel, fermez-le en tuant le processus (Ctrl + c)

Encore une fois, si vous désirez pousser plus loin les possibilités que vous offre SSH, utilisez le man 😉

<span style="font-size: small;"><br /> </span>