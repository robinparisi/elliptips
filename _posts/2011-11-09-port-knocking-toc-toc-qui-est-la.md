---
id: 1003
title: 'Port Knocking : toc toc, qui est là ?'
date: 2011-11-09T20:34:43+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=1003
permalink: /port-knocking-toc-toc-qui-est-la/
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
dsq_thread_id:
  - "466542653"
image: /wp-content/uploads/2011/11/knock-180x160.png
---
Si vous êtes du genre à mettre toutes les armes de votre côté en ce qui concerne la **sécurité** d’un serveur **Linux** mais que la technique du Port Knocking vous est étrangère, alors ceci devrait vous intéresser. Et puis si la sécurité vous importe peu, tout n’est pas perdu, vous devriez pouvoir trouver une place de consultant chez [Sony](http://www.makeuseof.com/tag/sony-playstation-network-breach-infographic/ "Sony infographie").

Troll mis à part, le **port knocking** est une technique permettant de modifier **dynamiquement les règles d’un pare-feu** grâce au lancement préalable d’une suite de connexions sur des ports distincts (tcp et udp) dans le bon ordre.

Ainsi, si même après avoir sécurisé un minimum votre accès SSH, vous continuez à essuyer trop de tentatives de type bruteforce, le port knocking peut-être une solution à votre problème.

Note: je prends ici l’exemple de SSH mais vous pouvez bien sûr utiliser le port knocking avec n’importe lequel de vos services.

# Installation du daemon knockd

Pour faire fonctionner cette technique, nous allons avoir besoin d’un daemon dont le rôle sera d’écouter les ports afin de détecter une éventuelle séquence connue et agir en conséquence sur les règles du pare-feu.

Sous debian (ou Ubuntu) :

<pre class="brush:shell">sudo aptitude install knockd</pre>

# Configuration de knockd

La configuration de knockd se trouve dans /etc/knockd.conf. Voici un exemple de configuration à utiliser pour SSH.

<pre class="brush:shell">[opions]
        UseSyslog

[options]
      logfile = /var/log/knockd.log

[openSSH]
        sequence    = 2000:tcp,3000:udp,4000:tcp
        seq_timeout = 5
        command     = /sbin/iptables -A INPUT -s %IP% -p tcp --dport 22 -j ACCEPT
        tcpflags    = syn 

[closeSSH]
        sequence    = 4000:tcp,3000:udp,2000:tcp
        seq_timeout = 5
        command     = /sbin/iptables -D INPUT -s %IP% -p tcp --dport 22 -j ACCEPT
        tcpflags    = syn</pre>

Je pense que le fichier parle de lui même :

  * la réception de la séquence &#8220;2000:tcp,3000:udp,4000:tcp&#8221; aura pour conséquence d’ouvrir le port SSH (ici le 22)
  * la séquence inverse fermera le port

<div>
  A noter : essayez d’utiliser un minimum de 3 ports avec les deux protocoles pour que votre séquence soit difficile à trouver.
</div>

On édite ensuite le fichier suivant :

<pre class="brush:shell">sudo vim /etc/default/knockd</pre>

Et on passe la valeur de START_KNOCKD à 1.

# Configuration du firewall

Pour que cela fonctionne, votre firewall doit **par défaut ne laisser passer aucune connexion sur le port SSH**.

# Démarrer le daemon

On démarre knockd :

<pre class="brush:shell">/etc/init.d/knockd start</pre>

# Et côté client ?

Il y a plusieurs solutions pour activer une séquence.

Utiliser telnet ou alors plus simplement, le client knockd disponible à l’[adresse suivante](http://www.zeroflux.org/projects/knock "Client knockd").

Assurez-vous de placer le binaire dans un endroit accessible par votre shell (echo $PATH dans le terminal pour connaître les emplacements).

On fait un toc sur la séquence prévue :

<pre class="brush:shell">knock [ip] 2000:tcp 3000:udp 4000:tcp</pre>

Pour se simplifier la vie, je vous conseil d’éditer un alias dans votre fichier de configuration dédié à votre shell. En ce qui me concerne, j’utilise ZSH donc :

<pre class="brush:shell">cd
vim .zshrc</pre>

<p class="brush:shell">
  Et voici ma configuration (modifiée):
</p>

<pre class="brush:shell crayon-selected"># Serveur
alias sms="toc && ssh [domaine] -p [port]"
# Port knocking
alias toc="knock [domaine] 2000:tcp 3000:udp 4000:tcp"
alias cot="knock [domaine] 4000:tcp 3000:udp 2000:tcp"</pre>

Ainsi, en tapant &#8220;sms&#8221;, je me connecte directement à mon serveur, le tout de manière transparente. Et pour envoyer la séquence inverse, j’utilise l’alias &#8220;cot&#8221;.

Pour conclure, knockd est un utilitaire utilisant peu de ressources et très facile à mettre en place qui vous permettra de sécuriser un peu plus les connexions à votre serveur. Bien entendu, ça n’est pas une solution magique qui vous mettra à l’abri de toute intrusion, mais cela vous permettra au moins de rendre la tâche plus difficile aux personnes mal intentionnées.

Et en bonus, le système équivalent dans le monde réel, le tout à base à base d’arduino :p

<p style="text-align: center;">
</p>

[[image]](http://worthyg.deviantart.com/art/Please-knock-103732985?offset=10 "image")