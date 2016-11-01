---
id: 1933
title: 'SSH-Manager : un script pour gérer vos connexions SSH'
date: 2013-02-25T22:54:53+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=1933
permalink: /ssh-manager-script-gerer-connexions-ssh/
dsq_thread_id:
  - "1104947836"
image: /wp-content/uploads/2011/01/190px-OpenSSH_logo-180x160.png
---
Si vous avez comme moi l&#8217;habitude de **switcher entre plusieurs serveurs SSH**, vous devez probablement avoir mis en place une petite routine pour gérer toutes ces connexions. Personnellement, j&#8217;avais pris l&#8217;habitude d&#8217;utiliser de simples alias placés dans le fichier de configuration de mon Shell, mais au fur et à mesure que le nombre de serveurs à gérer augmentait, il devenait difficile pour moi de m&#8217;y retrouver.

Je me suis alors mis en quête d&#8217;un petit soft qui serait capable de gérer l&#8217;ensemble de mes connexions simplement et je suis tombé sur un **script bash** écrit par Errol Byrd (j&#8217;ai malheureusement perdu le lien initial) que j&#8217;ai modifié à ma sauce.

**SSH-Manager** permet :

  * <span style="line-height: 13px;">d&#8217;ajouter/supprimer des serveurs</span>
  * de se connecter rapidement à un serveur en utilisant un système d&#8217;alias
  * de garder un oeil sur la liste des serveurs disponibles
  * de vérifier l&#8217;état des serveurs (simple ping)
  * d&#8217;exporter sa configuration pour la retrouver sur un autre ordinateur (le script utilise un fichier nommé ssh_servers placé à la racine de votre répertoire personnel)

[<img class="aligncenter size-full wp-image-1936" alt="ssh manager SSH Manager : un script pour gérer vos connexions SSH" src="http://elliptips.info/wp-content/uploads/2013/02/ssh-manager.png" width="764" height="576" srcset="http://elliptips.info/wp-content/uploads/2013/02/ssh-manager.png 764w, http://elliptips.info/wp-content/uploads/2013/02/ssh-manager-300x226.png 300w" sizes="(max-width: 764px) 100vw, 764px" title="SSH Manager : un script pour gérer vos connexions SSH photo" />](http://elliptips.info/wp-content/uploads/2013/02/ssh-manager.png)

Comme c&#8217;est un script bash, il fonctionne bien entendu sur Linux et OSX.

## Installation du script ssh-manager

On commence par récupérer le script sur [Github](https://github.com/robinparisi/ssh-manager "SSH-Manager sur Github") puis on le rend exécutable.

<pre class="lang:sh decode:true">cd ~
wget --no-check-certificate https://raw.github.com/robinparisi/ssh-manager/master/ssh-manager.sh
chmod +x ssh-manager.sh
./ssh-manager.sh</pre>

Pour plus de commodité, vous pouvez créer un alias vers le script :

<pre class="lang:sh decode:true">alias sshs="~/ssh-manager.sh</pre>

## Utilisation du script ssh-manager

Ajouter un serveur :

<pre class="lang:sh decode:true">sshs add &lt;alias&gt;:&lt;user&gt;:&lt;host&gt;:[port]</pre>

Supprimer un serveur :

<pre class="lang:sh decode:true">sshs del &lt;alias&gt;</pre>

Se connecter à un serveur :

<pre class="lang:sh decode:true">sshs cc &lt;alias&gt;</pre>

Voir la liste des serveurs :

<pre class="lang:sh decode:true">sshs</pre>