---
id: 1684
title: Installer Apache, MySQL et PHP sous OSX sans passer par MAMP
date: 2012-11-16T08:30:55+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=1684
permalink: /installer-apache-mysql-et-php-sous-osx-sans-passer-par-mamp/
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
dsq_thread_id:
  - "928538161"
image: /wp-content/uploads/2012/11/apache_php_mysql-180x160.jpg
---
Venant tout juste de changer de Mac, je découvre **Mountain Lion** et je me suis dit qu&#8217;il était temps de mettre un peu d&#8217;ordre dans mon environnement de développement. J&#8217;avais l&#8217;habitude d&#8217;utiliser **MAMP** pour le développement web, car celui-ci a l&#8217;avantage indéniable de fournir un package prêt à l&#8217;emploi, le tout en un clic. Revers de la médaille, il nous rend tributaire des versions de logiciels qu&#8217;il propose et s&#8217;intègre parfois mal avec d&#8217;autres environnements. Ainsi, nous verrons dans ce tutoriel comment mettre en place un stack AMP (**Apache, MySQL et PHP**) sous Mac OSX simplement et rapidement, le tout en utilisant au maximum les outils déjà intégrés au système.

Note : ce tutoriel a été réalisé sous Mountain Lion, mais il devrait fonctionner pour les autres versions. En effet, les versions précédentes (Snow Leopard et Lion) possèdent, elles aussi un serveur Apache intégré. Si vous rencontrez des difficultés, n&#8217;hésitez pas à laisser un commentaire à la suite de l&#8217;article.

# Installer Apache

Première bonne nouvelle, Apache est déjà intégré à votre système. Pour en avoir la preuve, lancez donc la commande suivante :

<pre class="lang:sh decode:true">httpd -v</pre>

Le retour devrait ressembler à ceci :

<pre class="lang:default decode:true">Server version: Apache/2.2.22 (Unix)
Server built:   Aug 24 2012 17:16:58</pre>

L&#8217;administration d&#8217;apache se fait grâce aux commandes suivantes :

<pre class="lang:sh decode:true">sudo apachectl start 
sudo apachectl restart
sudo apachectl stop
sudo apachectl graceful # relance apache en attendant la fermeture des connexions établies</pre>

# Le document root

En vous rendant sur <span style="color: #000000;"><strong>http://localhost</strong></span>, vous devriez voir le célèbre &#8220;It Works&#8221;.

Pour le moment, le document root se trouve dans :

<pre class="lang:default decode:true">/Library/WebServer/Documents/</pre>

Sur les anciennes versions de l&#8217;OS, les utilisateurs disposaient d&#8217;un dossier **Sites dans leur répertoire personnel** et l&#8217;on pouvait accéder à celui-ci via l&#8217;adresse http://localhost/~user (notez l&#8217;utilisation du tilde dans l&#8217;adresse).

Nous allons utiliser ce système. On commence donc par créer le répertoire Sites s&#8217;il n&#8217;existe pas déjà (c&#8217;est votre cas si vous êtes sous Mountain Lion).

<pre class="lang:sh decode:true">mkdir ~/Sites</pre>

Création d&#8217;un fichier de configuration pour votre utilisateur :

<pre class="lang:sh decode:true">sudo vim /etc/apache2/users/votreuser.conf</pre>

Note : si vous ne connaissez pas votre utilisateur, lancer la commande suivante :

<pre class="lang:sh decode:true">whoami</pre>

On y insère la configuration suivante :

<pre class="lang:default mark:8 decode:true">&lt;Directory "/Users/votreuser/Sites/"&gt;
Options Indexes MultiViews
AllowOverride All
Order allow,deny
Allow from all
&lt;/Directory&gt;

Include /Users/votreuser/Sites/httpd-vhosts.conf</pre>

Le include à la ligne 8 permet d&#8217;apporter un peu de commodités dans la gestion des vhosts car le fichier de conf sera disponible à la racine de ~/Sites, donc accessible rapidement. Notez que vous pourriez très bien mettre vos vhosts à la suite du fichier votreuser.conf.

Il faut donc créer le fichier alloué à la configuration des vhosts :

<pre>touch ~/Sites/httpd-vhosts.conf</pre>

On vérifie les permissions du fichier &#8220;votreuser.conf&#8221;  qui doivent être à 644 :

<pre class="lang:sh decode:true">sudo chmod 644 /etc/apache2/users/robin.conf</pre>

On test les changements :

<pre class="lang:default decode:true">sudo apachectl restart
cd ~/Sites/
touch index.html
echo "It works from my personal folder" &gt; index.html</pre>

Rendez vous sur <span style="color: #000000;"><strong>http://localhost/~votreuser/index.html</strong></span>. La page devrait afficher votre texte &#8220;It works from my personal folder&#8221;.

# Édition d&#8217;un vhost

Les vhosts vous permettront de tester **plusieurs sites en utilisant des noms de domaine en local**.

On édite  le fichier httpd-vhosts.conf :

<pre class="lang:default decode:true">vim ~/Sites/httpd-vhosts.conf</pre>

On y ajoute la configuration suivante :

<pre class="lang:apache decode:true">NameVirtualHost *:80
&lt;Directory "/Users/votreuser/Sites"&gt;
  Options Indexes FollowSymLinks MultiViews
  AllowOverride All
  Order allow,deny
  Allow from all
&lt;/Directory&gt;

&lt;VirtualHost _default_:80&gt;
  ServerName localhost
  DocumentRoot /Library/WebServer/Documents
&lt;/VirtualHost&gt;

&lt;VirtualHost *:80&gt;
  ServerName site1.local
  DocumentRoot "/Users/votreuser/Sites/site1"
&lt;/VirtualHost&gt;</pre>

La dernière section est celle que vous devrez copier/coller pour créer autant de vhost que nécessaire.

Bien sûr, nous ne disposons pas d&#8217;un nom de domaine réel pour tester le vhost et nous n&#8217;en avons d&#8217;ailleurs pas besoin. Nous allons tout simplement ajouter un host dans le fichier /etc/hosts :

<pre class="lang:sh decode:true">sudo vim /etc/hosts</pre>

On ajoute la ligne suivante (à la fin du fichier) :

<pre class="lang:default decode:true">127.0.0.1 site1.local</pre>

Cette ligne aura pour effet de faire pointer le nom de domaine site1.local sur localhost.

Pour tester, l&#8217;on créé un dossier site1 dans ~/Sites :

<pre class="lang:default decode:true">mkdir ~/Sites/site1
touch ~/Sites/site1/index.html 
echo "It Works from site1" &gt; ~/Sites/site1/index.html</pre>

On relance Apache :

<pre>sudo apachectl restart</pre>

On se rend sur <span style="color: #000000;"><strong>http://site1.local</strong></span> pour tester le résultat.

# Installer PHP

Comme pour Apache, la procédure se révèle simplissime. Il suffit de décommenter la ligne du module php5 dans le httpd.conf :

<pre class="lang:default decode:true crayon-selected">sudo vim /etc/apache2/httpd.conf</pre>

On décommente la ligne suivante :

<pre class="lang:apache decode:true">LoadModule php5_module libexec/apache2/libphp5.so</pre>

On redémarre Apache :

<pre class="lang:sh decode:true">sudo apachectl restart</pre>

On teste le fonctionnement de php avec notre fichier créé précédemment :

<pre class="lang:default decode:true">mv ~/Sites/site1/index.html ~/Sites/site1/index.php
echo  '&lt;?php phpinfo(); ?&gt;' &gt; ~/Sites/site1/index.php</pre>

Puis on pointe sur l&#8217;adresse <span style="color: #000000;"><strong>http://site1.local</strong></span>. Si tout s&#8217;est bien passé, le phpinfo() devrait s&#8217;afficher.

Note : la configuration de php se situe dans /etc/php.ini.default (à renommer en php.ini).

<pre class="lang:default decode:true">cd /etc
sudo cp php.ini.default php.ini
sudo chmod ug+w php.ini
sudo chgrp staff php.ini</pre>

# Installer MySQL

Avant d&#8217;installer MySQL, rendez vous dans **Préférences systèmes->Système et confidentialité**. Après avoir dévérrouillé le cadenas, cochez &#8220;n&#8217;importe où&#8221; pour la section &#8220;Autoriser les applications téléchargées de&#8221;.

[<img class="aligncenter size-full wp-image-1714" title="autorisation-app-osx" alt="autorisation app osx Installer Apache, MySQL et PHP sous OSX sans passer par MAMP" src="http://elliptips.info/wp-content/uploads/2012/11/autorisation-app-osx.png" width="660" height="519" srcset="http://elliptips.info/wp-content/uploads/2012/11/autorisation-app-osx.png 660w, http://elliptips.info/wp-content/uploads/2012/11/autorisation-app-osx-300x235.png 300w" sizes="(max-width: 660px) 100vw, 660px" />](http://elliptips.info/wp-content/uploads/2012/11/autorisation-app-osx.png)

Sur le site de MySQL, on télécharge la version 64 bits sous format **d&#8217;archive DMG**  (<span style="color: #339966;"><strong>Mac OS X ver. 10.6 (x86, 64-bit), DMG Archive</strong>)</span>

Le site : [http://dev.mysql.com/downloads/mysql/](http://dev.mysql.com/downloads/mysql/ "Téléchargement de MySQL")

Note : vous n&#8217;êtes pas obligé de vous inscrire pour télécharger MySQL

[<img class="aligncenter size-full wp-image-1705" title="telechargement-mysql" alt="telechargement mysql1 Installer Apache, MySQL et PHP sous OSX sans passer par MAMP" src="http://elliptips.info/wp-content/uploads/2012/11/telechargement-mysql1.png" width="660" height="368" srcset="http://elliptips.info/wp-content/uploads/2012/11/telechargement-mysql1.png 660w, http://elliptips.info/wp-content/uploads/2012/11/telechargement-mysql1-300x167.png 300w" sizes="(max-width: 660px) 100vw, 660px" />](http://elliptips.info/wp-content/uploads/2012/11/telechargement-mysql1.png)

Une fois l&#8217;archive décompressée et lancée, il vous suffit d&#8217;installer les 3 composants :

[<img class="aligncenter size-full wp-image-1707" title="mysql-installation" alt="mysql installation1 Installer Apache, MySQL et PHP sous OSX sans passer par MAMP" src="http://elliptips.info/wp-content/uploads/2012/11/mysql-installation1.png" width="660" height="346" srcset="http://elliptips.info/wp-content/uploads/2012/11/mysql-installation1.png 660w, http://elliptips.info/wp-content/uploads/2012/11/mysql-installation1-300x157.png 300w" sizes="(max-width: 660px) 100vw, 660px" />](http://elliptips.info/wp-content/uploads/2012/11/mysql-installation1.png)

Pour démarrer/arrêter MySQL, rendez vous dans vos préférences systèmes :

[<img class="aligncenter size-full wp-image-1760" title="administrer-mysql" alt="administrer mysql Installer Apache, MySQL et PHP sous OSX sans passer par MAMP" src="http://elliptips.info/wp-content/uploads/2012/11/administrer-mysql.png" width="660" height="105" srcset="http://elliptips.info/wp-content/uploads/2012/11/administrer-mysql.png 660w, http://elliptips.info/wp-content/uploads/2012/11/administrer-mysql-300x47.png 300w" sizes="(max-width: 660px) 100vw, 660px" />](http://elliptips.info/wp-content/uploads/2012/11/administrer-mysql.png)

Pour tester MySQL :

<pre class="lang:sh decode:true">/usr/local/mysql/bin/mysql -v</pre>

Cela devrait vous ouvrir un shell MySQL en affichant le numéro de version. Pour le quitter, faites **Ctrl + C**.

Pour utiliser le binaire directement, on ajoute celui-ci à notre path (à adapter selon votre configuration). SI vous débuter et utilisez bash, créer tout simplement un fichier .bash_profile dans votre home.

<pre class="lang:sh decode:true">vim ~/.bash_profile</pre>

Ajoutez-y la ligne suivante :

<pre class="lang:default decode:true">export PATH="/usr/local/mysql/bin:$PATH"</pre>

On teste sans le chemin absolu :

<pre class="lang:sh decode:true">mysql -v</pre>

## Un mot de passe root pour MySQL

Il est important de définir un mot de passe root pour MySQL à l&#8217;aide de la commande suivante :

<pre class="lang:default decode:true">mysqladmin -u root password 'motdepasse'</pre>

Faites attention à bien utiliser les simples quotes.

# Installer phpMyAdmin

Se rendre sur la page de download de phpMyAdmin :

[http://www.phpmyadmin.net/home_page/downloads.php](http://www.phpmyadmin.net/home_page/downloads.php "Télécharger phpMyAdmin")

On récupère le fichier <span style="color: #339966;"><strong>phpMyAdmin-3.5.3-all-languages.zip</strong></span>.

Une fois décompressé, on renomme le dossier en phpmyadmin puis on le place à la racine dans ~/Sites.

On fixe un problème d&#8217;erreur 2002 :

[<img class="aligncenter size-full wp-image-1703" title="erreur-2002-phpmyadmin" alt="erreur 200 phpmyadmin Installer Apache, MySQL et PHP sous OSX sans passer par MAMP" src="http://elliptips.info/wp-content/uploads/2012/11/erreur-200-phpmyadmin.png" width="660" height="170" srcset="http://elliptips.info/wp-content/uploads/2012/11/erreur-200-phpmyadmin.png 660w, http://elliptips.info/wp-content/uploads/2012/11/erreur-200-phpmyadmin-300x77.png 300w" sizes="(max-width: 660px) 100vw, 660px" />](http://elliptips.info/wp-content/uploads/2012/11/erreur-200-phpmyadmin.png)

<pre class="lang:default decode:true">sudo mkdir /var/mysql
sudo ln -s /tmp/mysql.sock /var/mysql/mysql.sock</pre>

On pointe sur l’adresse <span style="color: #000000;"><strong>http://localhost/~votreuser/phpmyadmin/</strong></span>

Il suffit alors de se connecter avec l&#8217;utilisateur root et le mot de passe que vous avez configuré dans l&#8217;étape précédente.

[<img class="aligncenter size-full wp-image-1704" title="connexion-phpmyadmin" alt="connexion phpmyadmin Installer Apache, MySQL et PHP sous OSX sans passer par MAMP" src="http://elliptips.info/wp-content/uploads/2012/11/connexion-phpmyadmin.png" width="660" height="265" srcset="http://elliptips.info/wp-content/uploads/2012/11/connexion-phpmyadmin.png 660w, http://elliptips.info/wp-content/uploads/2012/11/connexion-phpmyadmin-300x120.png 300w" sizes="(max-width: 660px) 100vw, 660px" />](http://elliptips.info/wp-content/uploads/2012/11/connexion-phpmyadmin.png)

# En bonus : un script pour générer vos vhosts

Dans le but de simplifier un peu plus la procédure d&#8217;ajout de vhosts, j&#8217;ai créé un petit **script bash** dédié à cette tâche qui :

  * éditera le fichier /etc/hosts
  * créera un repertoire dédié au site dans ~/Sites (s&#8217;il n&#8217;existe pas déjà)
  * éditera un vhost dans votre httpd-vhosts.conf
  * redémarrera Apache pour prendre en compte les changements

[<img class="aligncenter size-full wp-image-1717" title="vhosts-generator" alt="vhosts generator Installer Apache, MySQL et PHP sous OSX sans passer par MAMP" src="http://elliptips.info/wp-content/uploads/2012/11/vhosts-generator.png" width="652" height="408" srcset="http://elliptips.info/wp-content/uploads/2012/11/vhosts-generator.png 652w, http://elliptips.info/wp-content/uploads/2012/11/vhosts-generator-300x187.png 300w" sizes="(max-width: 652px) 100vw, 652px" />](http://elliptips.info/wp-content/uploads/2012/11/vhosts-generator.png)

## 

## Pour l&#8217;utiliser

Récupérez  le script sur [Github](https://github.com/robinparisi/scripts-osx/blob/master/vhosts-generator.sh "vhosts generator sur Github") :

<pre class="lang:sh decode:true">curl -OL https://raw.github.com/robinparisi/scripts-osx/master/vhosts-generator.sh</pre>

Rendez-le exécutable :

<pre class="lang:default decode:true">chmod +x vhosts-generator.sh</pre>

Editez la partie concernant le user :

<pre class="lang:default decode:true">USER="votre_user_ici"</pre>

Lancez-le (sans oublier sudo nécessaire car demande l&#8217;édition du fichier hosts et le contrôle d&#8217;Apache) :

<pre class="lang:default decode:true">sudo ./vhosts-generator.sh</pre>

Choisir un nom de domaine (celui que vous entrerez dans votre navigateur pour accéder au site en local) et un nom pour le répertoire du site.

Et voilà, vous avez maintenant un environnement de développement fonctionnel et pleinement intégré à votre système. Si vous testez ce tutoriel depuis une autre version de Mac OS X, n&#8217;hésitez pas à valider la procédure dans les commentaires.

Bon dev à tous 🙂