---
id: 1889
title: Corriger l’erreur libmysqlclient.18.dylib (LoadError) de Rails
date: 2013-01-28T15:53:27+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=1889
permalink: /corriger-lerreur-libmysqlclient-18-dylib-loaderror-de-rails/
dsq_thread_id:
  - "1051321911"
image: /wp-content/uploads/2013/01/ror_logo-180x160.jpg
---
À force de ne lire que du bien de Ruby et en particulier du framework Ruby on Rails, j&#8217;ai finalement décidé de m&#8217;y mettre. Je dois avouer que l&#8217;installation est enfantine et j&#8217;apprécie tout particulièrement le système de gems (surtout avec bundler qui permet de maintenir l&#8217;environnement d&#8217;une application en une seule commande).

J&#8217;ai cependant eu un petit problème au lancement du serveur (rails server) sous OSX à cause de la gem mysql2. Voici comment la résoudre simplement :

Si vous obtenez l&#8217;erreur suivante en lançant le serveur de votre application :

<pre class="lang:sh mark:1 decode:true">/Library/Ruby/Gems/1.8/gems/mysql2-0.2.7/lib/mysql2/mysql2.bundle: dlopen(/Library/Ruby/Gems/1.8/gems/mysql2-0.2.7/lib/mysql2/mysql2.bundle, 9): Library not loaded: libmysqlclient.18.dylib (LoadError)
  Referenced from: /Library/Ruby/Gems/1.8/gems/mysql2-0.2.7/lib/mysql2/mysql2.bundle
  Reason: image not found - /Library/Ruby/Gems/1.8/gems/mysql2-0.2.7/lib/mysql2/mysql2.bundle
	from /Library/Ruby/Gems/1.8/gems/mysql2-0.2.7/lib/mysql2.rb:8
	from /Library/Ruby/Gems/1.8/gems/bundler-1.2.3/lib/bundler/runtime.rb:68:in `require'
	from /Library/Ruby/Gems/1.8/gems/bundler-1.2.3/lib/bundler/runtime.rb:68:in `require'
	from /Library/Ruby/Gems/1.8/gems/bundler-1.2.3/lib/bundler/runtime.rb:66:in `each'
	from /Library/Ruby/Gems/1.8/gems/bundler-1.2.3/lib/bundler/runtime.rb:66:in `require'
	from /Library/Ruby/Gems/1.8/gems/bundler-1.2.3/lib/bundler/runtime.rb:55:in `each'
	from /Library/Ruby/Gems/1.8/gems/bundler-1.2.3/lib/bundler/runtime.rb:55:in `require'
	from /Library/Ruby/Gems/1.8/gems/bundler-1.2.3/lib/bundler.rb:128:in `require'
	from /Users/robin/RubymineProjects/comebacksoon/config/application.rb:7
	from /Users/robin/.gem/ruby/1.8/gems/railties-3.2.11/lib/rails/commands.rb:53:in `require'
	from /Users/robin/.gem/ruby/1.8/gems/railties-3.2.11/lib/rails/commands.rb:53
	from /Users/robin/.gem/ruby/1.8/gems/railties-3.2.11/lib/rails/commands.rb:50:in `tap'
	from /Users/robin/.gem/ruby/1.8/gems/railties-3.2.11/lib/rails/commands.rb:50
	from script/rails:6:in `require'
	from script/rails:6</pre>

Il suffit de créer un lien symbolique de la lib mysql vers /usr/lib/ :

<pre class="lang:default decode:true">sudo ln -s /usr/local/mysql/lib/libmysqlclient.18.dylib /usr/lib/libmysqlclient.18.dylib</pre>

Et le tour est joué.

Si vous souhaitez vous lancer dans le développement d&#8217;applications rails, je ne saurais que trop vous conseiller l&#8217;excellent [IDE RubyMine](http://www.jetbrains.com/ruby/ "RubyMine IDE") qui vous assistera et vous guidera énormément en tant que débutant (il est possible d&#8217;obtenir une license si vous être dans une école d&#8217;informatique).