---
id: 168
title: Votre serveur de streaming sur demande avec Flumotion
date: 2011-01-22T22:43:14+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=168
permalink: /votre-serveur-de-streaming-sur-demande-avec-flumotion/
dsq_thread_id:
  - "418320335"
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
image: /wp-content/uploads/2011/01/flumotion-streaming-multimedia-pack-180x160.jpg
---
**Flumotion** est un serveur de streaming **open source** distribué sous licence GPL. Sa grande force est qu&#8217;il supporte le **webM**, le format video ouvert par Google l&#8217;an dernier basé sur le codec video vp8, successeur  du défunt H.264.

Pour faire simple, Flumotion permet la diffusion de contenu video et audio (webcam, fichier, tunner TV) à travers le réseau, contenu visionnable directement dans un navigateur compatible webM (Chromium).

## Installation sous Ubuntu

à partir des dépôts :

<pre class="brush:shell">sudo apt-get install flumotion</pre>

## Configuration

<p style="text-align: center;">
  &#8211; On commence par lancer Flumotion dans le menu son et videos.
</p>

<p style="text-align: center;">
  &#8211; Choisir &#8220;Connect to a running manager&#8221;
</p>

<p style="text-align: center;">
  <a href="http://elliptips.info/wp-content/uploads/2011/01/flumotion_11.png"><img class="aligncenter size-full wp-image-207" title="flumotion_1" src="http://elliptips.info/wp-content/uploads/2011/01/flumotion_11.png" alt="flumotion 11 Votre serveur de streaming sur demande avec Flumotion" width="346" height="276" srcset="http://elliptips.info/wp-content/uploads/2011/01/flumotion_11.png 346w, http://elliptips.info/wp-content/uploads/2011/01/flumotion_11-300x239.png 300w" sizes="(max-width: 346px) 100vw, 346px" /></a>
</p>

<p style="text-align: center;">
  &#8211; Les informations de connexion
</p>

<p style="text-align: center;">
  <a href="http://elliptips.info/wp-content/uploads/2011/01/flumotion_21.png"><img class="aligncenter size-full wp-image-196" title="flumotion_2" src="http://elliptips.info/wp-content/uploads/2011/01/flumotion_21.png" alt="flumotion 21 Votre serveur de streaming sur demande avec Flumotion" width="345" height="252" srcset="http://elliptips.info/wp-content/uploads/2011/01/flumotion_21.png 345w, http://elliptips.info/wp-content/uploads/2011/01/flumotion_21-300x219.png 300w" sizes="(max-width: 345px) 100vw, 345px" /></a>
</p>

<p style="text-align: center;">
  &#8211; Authentification (par default username: <strong><span style="color: #ff0000;">user</span></strong> et password: <strong><span style="color: #ff0000;">test</span></strong>) à changer dans les fichiers de configuration de Flumotion
</p>

<p style="text-align: center;">
  <a href="http://elliptips.info/wp-content/uploads/2011/01/flumotion_31.png"><img class="aligncenter size-full wp-image-197" title="flumotion_3" src="http://elliptips.info/wp-content/uploads/2011/01/flumotion_31.png" alt="flumotion 31 Votre serveur de streaming sur demande avec Flumotion" width="344" height="223" srcset="http://elliptips.info/wp-content/uploads/2011/01/flumotion_31.png 344w, http://elliptips.info/wp-content/uploads/2011/01/flumotion_31-300x194.png 300w" sizes="(max-width: 344px) 100vw, 344px" /></a>
</p>

<p style="text-align: center;">
  &#8211; S&#8217;ouvre alors l&#8217;assistant de configuration
</p>

<p style="text-align: center;">
  <a href="http://elliptips.info/wp-content/uploads/2011/01/flumotion_41.png"><img class="aligncenter size-full wp-image-195" title="flumotion_4" src="http://elliptips.info/wp-content/uploads/2011/01/flumotion_41.png" alt="flumotion 41 Votre serveur de streaming sur demande avec Flumotion" width="610" height="375" srcset="http://elliptips.info/wp-content/uploads/2011/01/flumotion_41.png 762w, http://elliptips.info/wp-content/uploads/2011/01/flumotion_41-300x184.png 300w" sizes="(max-width: 610px) 100vw, 610px" /></a>
</p>

<p style="text-align: center;">
  <p style="text-align: center;">
    &#8211; Directory : le répertoire qui contiendra les videos
  </p>
  
  <p style="text-align: center;">
    &#8211; Port : le port sur lequel le serveur est accessible
  </p>
  
  <p style="text-align: center;">
    Mount Point : le point de montage qui donnera http://adresse:port/pointdemontage/video.webm
  </p>
  
  <p style="text-align: center;">
    <a href="http://elliptips.info/wp-content/uploads/2011/01/flumotion_5.png"><img class="aligncenter size-full wp-image-194" title="flumotion_5" src="http://elliptips.info/wp-content/uploads/2011/01/flumotion_5.png" alt="flumotion 5 Votre serveur de streaming sur demande avec Flumotion" width="610" height="375" srcset="http://elliptips.info/wp-content/uploads/2011/01/flumotion_5.png 762w, http://elliptips.info/wp-content/uploads/2011/01/flumotion_5-300x184.png 300w" sizes="(max-width: 610px) 100vw, 610px" /></a>
  </p>
  
  <p style="text-align: center;">
    <p style="text-align: center;">
      &#8211; On valide et on en a terminé avec la configuration de Flumotion. Le serveur est maintenant lancé.
    </p>
    
    <p style="text-align: center;">
      <a href="http://elliptips.info/wp-content/uploads/2011/01/flumotion_6.png"><img class="aligncenter size-full wp-image-198" title="flumotion_6" src="http://elliptips.info/wp-content/uploads/2011/01/flumotion_6.png" alt="flumotion 6 Votre serveur de streaming sur demande avec Flumotion" width="578" height="395" srcset="http://elliptips.info/wp-content/uploads/2011/01/flumotion_6.png 722w, http://elliptips.info/wp-content/uploads/2011/01/flumotion_6-300x205.png 300w" sizes="(max-width: 578px) 100vw, 578px" /></a>
    </p>
    
    <p style="text-align: center;">
      <p style="text-align: center;">
        <h2>
          Encodage des videos
        </h2>
        
        <p style="text-align: left;">
          Il va nous falloir encoder les videos. Pour cela, un petit soft bien sympa va faire tout le travail.
        </p>
        
        <p style="text-align: left;">
          <pre class="brush:shell">sudo apt-get install arista</pre>
          
          <p>
            Une fois installé, on lance arista dans sons et vidéos.
          </p>
          
          <p>
            Il suffit de choisir l&#8217;emplacement d&#8217;une video et le format voulu, donc webM, ainsi que le nom de la video encodée. J&#8217;ai choisit test.webm
          </p>
          
          <p>
            L&#8217;encodage va prendre plus ou moins de temps selon votre config.
          </p>
          
          <p style="text-align: center;">
            <a href="http://elliptips.info/wp-content/uploads/2011/01/arista.png"><img class="aligncenter size-full wp-image-199" title="arista" src="http://elliptips.info/wp-content/uploads/2011/01/arista.png" alt="arista Votre serveur de streaming sur demande avec Flumotion" width="627" height="302" srcset="http://elliptips.info/wp-content/uploads/2011/01/arista.png 784w, http://elliptips.info/wp-content/uploads/2011/01/arista-300x144.png 300w" sizes="(max-width: 627px) 100vw, 627px" /></a>
          </p>
          
          <p style="text-align: center;">
            <p style="text-align: center;">
              Maintenant que notre video est prête il suffit de la placer dans le répertoire choisit dans Flumotion.
            </p>
            
            <h2>
              Test
            </h2>
            
            <p style="text-align: center;">
              Aller à l&#8217;adresse http://localhost:8800/test.webm avec un navigateur compatible webM.
            </p>
            
            <p style="text-align: center;">
              Si votre navigateur n&#8217;est pas compatible, la video se téléchargera et vous pourrez l&#8217;ouvrir avec Totem ou VLC par exemple.
            </p>
            
            <p style="text-align: center;">
              <span style="text-decoration: underline;">Lecture de la video avec VLC</span>
            </p>
            
            <p style="text-align: center;">
              <span style="text-decoration: underline;"><a href="http://elliptips.info/wp-content/uploads/2011/01/vlc.png"><img class="aligncenter size-full wp-image-200" title="vlc" src="http://elliptips.info/wp-content/uploads/2011/01/vlc.png" alt="vlc Votre serveur de streaming sur demande avec Flumotion" width="560" height="360" srcset="http://elliptips.info/wp-content/uploads/2011/01/vlc.png 622w, http://elliptips.info/wp-content/uploads/2011/01/vlc-300x192.png 300w" sizes="(max-width: 560px) 100vw, 560px" /></a><br /> </span>
            </p>
            
            <p style="text-align: center;">
              <h2>
                Conclusion
              </h2>
              
              <p>
                Bien sûr, certains d&#8217;entre vous se demanderont peut être la différence entre l&#8217;approche avec Flumotion et le fait de placer directement la video dans la balise html5 dediée. Et bien Flumotion est un serveur de streaming, ce qui veut dire qu&#8217;il diffuse la video de manière intelligente (selon la bande passante, le format du fichier, etc&#8230;).
              </p>
              
              <p>
                Les tests en local sont très concluants. Cela va de soi, si vous comptez vous lancer dans la diffusion à travers internet depuis votre propre serveur, le débit sera limité mais j&#8217;ai pu tester avec un ami et ça fonctionne très bien.
              </p>
              
              <p>
                Pour pousser un peu plus loin, je vous conseille <a title="Le site de Flumotion" href="http://www.flumotion.net/documentation/">le site de Flumotion</a>.
              </p>
              
              <p>
                [Merci à Thomas pour la découverte]
              </p>
              
              <p style="text-align: center;">