---
id: 2266
title: 'Guide Debian 7 (partie 3/8) : envoyer des mails depuis la ligne de commande'
date: 2013-06-23T20:45:00+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=2266
permalink: /guide-debian-7-envoi-de-mails-ligne-de-commande/
dsq_thread_id:
  - "1437566397"
dsq_needs_sync:
  - "1"
image: /wp-content/uploads/2013/06/logo-mail-180x160.jpg
---
Cet article fait partie d&#8217;une série de billets portant sur la mise en place d&#8217;un serveur sous Debian Wheezy ([voir le sommaire](http://elliptips.info/guide-sur-linstallation-dun-serveur-sous-debian-7-wheezy/ "guide debian wheezy sommaire")).

## Introduction

<span style="font-size: 13px;">Le but de cette partie est de permettre l’envoi de mails depuis la ligne de commande.</span>

Ainsi, je ne vous parlerai pas ici de l’installation d’un serveur de mails complet, car cette étape serait bien trop longue et fastidieuse étant donné le résultat attendu.

## Comment ça marche ?

Nous allons utiliser pour cela un client SMTP léger, dont le rôle sera d’envoyer les e-mails en passant par un relai SMTP. Dans la majorité des cas, ce relai sera mis à votre disposition par votre prestataire.

Ce type d&#8217;envoi sera particulièrement utile pour les utilitaires capables de générer des rapports (fail2ban, cron-apt, &#8230;) de leur activité et de les envoyer par mail à l&#8217;administrateur du serveur, c&#8217;est à dire vous.

## Mon prestataire ne propose pas de relai SMTP

Selon le prestataire que vous aurez retenu, vous vous retrouverez généralement face à deux cas de figure :

  * le prestataire dispose d&#8217;un STMP en interne pour l&#8217;envoi de mail depuis ses serveurs (parfois, la distribution est préconfigurée pour utiliser ce SMTP (ex: Ikoula)
  * le prestataire ne dispose pas d&#8217;un SMTP en interne (ex: Dedibox). Dans ce cas, nous allons utiliser un autre relai SMTP

## **Testons l’envoi de mail**

Dans un premier temps, nous allons devoir tester l’envoi de mail car il est possible que votre prestataire l’ait déjà configuré pour vous (chez certains prestataires, les fichiers de confs sont préremplis à l&#8217;installation de la distribution) :

Lancer la ligne suivante en y insérant votre adresse mail (il est possible que le mail arrive dans vos spams) :

<pre class="lang:sh decode:true">echo "Mail envoyé le $(date)" | mail -s "Test envoi de mail depuis $HOST" votre_adresse@exemple.com</pre>

À partir d’ici, si l’envoi fonctionne, nul besoin d&#8217;aller plus loin. Dans le cas contraire, il va nous falloir installer ssmtp. Ne paniquez pas, la configuration est enfantine.

## Méthode ssmtp (passer par le SMTP de votre prestataire)

[Source : [http://doc.ubuntu-fr.org/ssmtp](http://doc.ubuntu-fr.org/ssmtp "ssmtp")]

Nous allons commencer par installer le client ssmtp :

<pre class="lang:sh decode:true">aptitude install ssmtp</pre>

Pour tout envoi de mail, un système UNIX tentera de faire appel à la commande sendmail (ceci pour une raison historique). La commande sendmail peut être founie par l’utilitaire sendmail, postfix, ou dans notre cas, par ssmtp.

<pre class="lang:sh decode:true">whereis sendmail</pre>

Si vous obtenez un retour semblable à l&#8217;exemple ci-dessous, c&#8217;est que la commande sendmail se trouve sur votre sytème.

<pre class="lang:default decode:true">sendmail: /usr/sbin/sendmail /usr/lib/sendmail /usr/lib64/sendmail /usr/share/man/man8/sendmail.8.gz</pre>

Il faut maintenant vérifier que ssmtp est l&#8217;utilitaire qui se cache derrière cette commande :

<pre class="lang:sh decode:true">ls -la /usr/sbin/sendmail</pre>

La réponse attendue :

<pre class="lang:default decode:true">lrwxrwxrwx 1 root root 5 20 déc.   2010 /usr/sbin/sendmail -&gt; ssmtp*</pre>

Ici, l&#8217;on voit que lors d&#8217;un appel à sendmail, le sytème appellera en fait le client ssmtp au travers d&#8217;un lien symbolique.

### **Configuration de ssmtp**

<pre class="lang:sh decode:true">vim /etc/ssmtp/ssmtp.conf</pre>

Afin d’être le plus clair possible, je vous place ici la configuration de mon serveur ( hébergé chez Ikoula). À vous de l’adapter avec les informations de votre prestataire.

<pre class="lang:default mark:4,11 decode:true"># The place where the mail goes. The actual machine name is required no 
# MX records are consulted. Commonly mailhosts are named mail.domain.com

mailhub=mail.ikoula.fr

# Where will the mail seem to come from?
#rewriteDomain=

# The full hostname

hostname=ik34.ikoula.com

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
#FromLineOverride=YES</pre>

Le point à noter est que l’utilisation du SMTP de votre prestataire ne semble pas requérir d’authentification. Ne vous y trompez pas, l’envoi vous est autorisé, car effectué depuis une de leur machine, c’est pourquoi il vous serait impossible d’utiliser leur serveur SMTP depuis une machine située à l’extérieur du réseau sans vous identifier au préalable.

À ce stade, testez de nouveau l’envoi de mail grâce à la commande donnée en début de ce chapitre. Si vous obtenez une erreur, passez à la section suivante.

### Un cas particulier, l’envoi de mail depuis root

Vous l’aurez compris, l’envoi de mail jusque ici se fait en tant que root. Chez certains prestataires, il est possible que l’envoi depuis root soit refusé.

Un exemple de refus :

<pre class="lang:default decode:true">send-mail: RCPT TO:&lt;parisi.robin@gmail.com&gt; (554 5.7.1 &lt;root@ik34.ikoula.com&gt;: Sender address rejected: Access denied)</pre>

Nous allons pour cela ruser en modifiant l’adresse d’expédition du compte root.

<pre class="lang:sh decode:true">vim /etc/ssmtp/revaliases</pre>

Je rajoute alors la ligne suivante :

<pre class="lang:default decode:true">root:homer@mail.ikoula.com</pre>

Notez que l’utilisateur n’a aucunement besoin d’exister sur votre serveur. En clair, vous pouvez mettre  à peu près n’importe quoi (cette donnée sera utilisée pour le champ from), cela pour la simple et bonne raison que nous n’attendons aucune réponse aux mails qui seront envoyés. De l’envoi et simplement de l’envoi, souvenez-vous !

À partir de ce point, les futurs paquets que vous installerez devraient être capables d’envoyer des mails s’ils sont lancés avec les privilèges du compte root. N’hésitez pas non plus à utiliser la commande mail au sein de vos scripts, pour être averti par exemple de la bonne exécution d&#8217;une tâche.

## **Méthode exim4 (pas de SMTP chez votre prestataire)**

Dans ce cas, nous allons utiliser un compte mail qui nous permettra de gérer l&#8217;envoi. Deux solutions s&#8217;offrent à vous :

  * <span style="line-height: 13px;">utiliser un compte type gmail, outlook, etc&#8230;</span>
  * créer un compte mail chez votre prestataire de nom de domaine

En ce qui me concerne, j&#8217;ai pris l&#8217;habitude de créer une adresse dédiée à l&#8217;envoi de mail depuis le serveur du type ne-pas-repondre@mondomaine.fr.

Je vous laisse vous renseigner sur la façon de créer une boîte mail avec votre domaine.

Nous allons maintenant configurer exim4 pour envoyer les mails en passant par votre compte :

<pre class="lang:sh decode:true">vim /etc/exim4/update-exim4.conf.conf</pre>

À adapter selon vos informations de connexion :

<pre>dc_eximconfig_configtype='satellite'
dc_other_hostnames=''
dc_local_interfaces='127.0.0.1'
dc_readhost='mon-domaine.com'
dc_relay_domains=''
dc_minimaldns='false'
dc_relay_nets=''
dc_smarthost='mail.gandi.net:587'
CFILEMODE='644'
dc_use_split_config='false'
dc_hide_mailname='true'
dc_mailname_in_oh='true'
dc_localdelivery='mail_spool'</pre>

Dans mon cas, je passe par le SMTP de Gandi (mail.gandi.net sur le port 587). Il vous faudra donc trouver ces informations pour votre prestataire.

Dans /etc/exim4/passwd.client

<pre>*:NOM-UTILISATEUR@DOMAINE.FR:MOT-DE-PASSE-DU-COMPTE</pre>

Cette ligne nous permet de nous identifier avec notre compte auprès du serveur SMTP.

Puis l&#8217;on termine en rechargeant la configuration d&#8217;exim4 :

<pre>update-exim4.conf</pre>

Arrivé à ce point, vous devriez être capable d&#8217;envoyer des mails grâce à la commande utilisée plus haut.

## Limites d&#8217;envoi

Il est important de comprendre que ces techniques permettent un envoi de mail &#8220;modéré&#8221; depuis la ligne de commande (ou depuis un script PHP, Python, Ruby, etc&#8230;). Au-delà d&#8217;un certain quota, le SMTP refusera de transmettre vos emails. Pour de l&#8217;envoi de masse (newsletter) et pour éviter de finir dans les spams, préférez une solution spécialisée (Mailchimp propose par exemple l&#8217;envoi de newsletter gratuitement jusqu&#8217;à 2000 inscrits).

&nbsp;