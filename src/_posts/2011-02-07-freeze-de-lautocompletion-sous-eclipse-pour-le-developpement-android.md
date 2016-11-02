---
id: 287
title: 'Freeze de l&#8217;autocomplétion sous Eclipse pour le développement Android'
date: 2011-02-07T16:15:12+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=287
permalink: /freeze-de-lautocompletion-sous-eclipse-pour-le-developpement-android/
dsq_thread_id:
  - "414302186"
image: /wp-content/uploads/2011/02/logo-eclipse-helios-180x160.jpg
---
<p style="text-align: center;">
  Si vous débutez le développement <strong>Android</strong> sous <strong>Eclipse</strong> en ce moment même, alors peut être êtes-vous en train de vous arracher les cheveux à cause de l<strong>&#8216;autocomplétion</strong> qui n&#8217;a de cesse de freezer.
</p>

<p style="text-align: justify;">
  Ainsi, pour accéder à certaines méthodes, il faut parfois attendre de nombreuses secondes (voir minutes ) avant que Eclipse ne se décide à afficher les résultats.
</p>

<p style="text-align: justify;">
  Rassurez-vous, ce bug est connu et devrait être corrigé dans les versions futures, en attendant, il existe une solution qui marche à merveille tout en vous évitant d&#8217;en arriver à désactiver l&#8217;autocomplétion.
</p>

<h3 style="text-align: justify;">
  Téléchargement des sources du SDK :
</h3>

<p style="text-align: justify;">
  Pour cela, on commence par télécharger les sources du SDK qui nous intéresse  (un peu plus de 100 MB):
</p>

<ul style="text-align: justify;">
  <li>
    <span style="color: #51d22c;"><strong>Android 2.3</strong></span> | API 9 ( gingerbread) :
  </li>
  <li>
    <span class="removed_link" title="http://android.git.kernel.org/?p=platform/frameworks/base.git;a=snapshot;h=gingerbread;sf=tgz">http://android.git.kernel.org/?p=platform/frameworks/base.git;a=snapshot;h=gingerbread;sf=tgz</span>
  </li>
</ul>

<ul style="text-align: justify;">
  <li>
    <span style="color: #51d22c;"><strong>Android 2.2</strong></span> | API 8 ( froyo) :
  </li>
  <li>
    <span class="removed_link" title="http://android.git.kernel.org/?p=platform/frameworks/base.git;a=snapshot;h=froyo;sf=tgz">http://android.git.kernel.org/?p=platform/frameworks/base.git;a=snapshot;h=froyo;sf=tgz</span>
  </li>
</ul>

<ul style="text-align: justify;">
  <li>
    <span style="color: #51d22c;"><strong>Android 2.1</strong></span> | API 7 ( eclair) :
  </li>
  <li>
    <span class="removed_link" title="http://android.git.kernel.org/?p=platform/frameworks/base.git;a=snapshot;h=eclair;sf=tgz">http://android.git.kernel.org/?p=platform/frameworks/base.git;a=snapshot;h=eclair;sf=tgz</span>
  </li>
</ul>

<ul style="text-align: justify;">
  <li>
    <span style="color: #51d22c;"><strong>Android 1.6</strong></span> | API 6 ( donut) :
  </li>
  <li>
    <span class="removed_link" title="http://android.git.kernel.org/?p=platform/frameworks/base.git;a=snapshot;h=donut;sf=tgz">http://android.git.kernel.org/?p=platform/frameworks/base.git;a=snapshot;h=donut;sf=tgz</span>
  </li>
</ul>

<h3 style="text-align: justify;">
  Marche à suivre :
</h3>

<p style="text-align: justify;">
  Une fois le tar.gz obtenu, il faut décompresser son contenu dans le répertoire dédié sur le disque dur, qui se situe ici :
</p>

> <p style="text-align: justify;">
>   <strong>[android-sdk]\plateform\android-[version]\sources</strong>
> </p>

<p style="text-align: justify;">
  Si le dossier <em>sources</em> n&#8217;existe pas, alors il faut le créer.
</p>

<p style="text-align: justify;">
  Par exemple, si vous avez téléchargé les sources pour froyo, alors vous devez placer le contenu de l&#8217;archive dans [android-sdk]\plateform\android-8\sources
</p>

<h3 style="text-align: justify;">
  On termine :
</h3>

<p style="text-align: justify;">
  Démarrez ou redémarrez Eclipse et admirez : il n&#8217;y à plus aucune latence pour l&#8217;autocomplétion, c&#8217;est quand même plus agréable non ?
</p>

<p style="text-align: justify;">
  Astuce trouvée sur<a href="http://envyandroid.com/archives/66/slow-android-autocomplete-eclipse-helios-36"> ce blog </a>(merci à lui)
</p>