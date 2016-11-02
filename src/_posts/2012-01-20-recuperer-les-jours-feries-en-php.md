---
id: 1337
title: Récupérer les jours fériés en PHP
date: 2012-01-20T17:33:09+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=1337
permalink: /recuperer-les-jours-feries-en-php/
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
dsq_thread_id:
  - "546692219"
image: /wp-content/uploads/2012/01/calendrier-180x160.png
---
<p style="text-align: justify;">
  Récemment, il m’a fallu récupérer une liste des <strong>jours fériés grâce à PHP</strong>. Comme vous le savez probablement, nous disposons en France de 11 jours fériés : la date de 8 d’entre eux est très facile à déterminer puisque celle-ci ne change pas au cours des ans. Mais en ce qui concerne les 3 derniers, ceux-ci sont basés sur le jour de Pâque qui je cite Wikipedia «est célébré le dimanche après le 14e jour du premier mois lunaire du printemps, donc le dimanche après la première pleine lune advenant pendant ou après l&#8217;équinoxe de printemps». Bref, après quelques recherches, je suis tombé sur une fonction PHP bien sympathique qui permet de retourner un timestamp UNIX pour Pâque, à minuit pour une année donnée : <span style="color: #339966;"><strong>easter_date()</strong></span>.
</p>

<p style="text-align: justify;">
  Et comme bien souvent sur <strong>php.net</strong>, la réponse à ma question était déjà présente dans l’un des commentaires. Voici donc la fonction qui vous retournera un tableau des jours fériés en France, au format timestamp UNIX, et ce pour une année donnée (en remerciant l’auteur de cette fonction).
</p>

<pre class="brush:php ">&lt;?php
/**
 * Cette fonction retourne un tableau de timestamp correspondant
 * aux jours fériés en France pour une année donnée.
*/
function getHolidays($year = null)
{
  if ($year === null)
  {
    $year = intval(date('Y'));
  }

  $easterDate  = easter_date($year);
  $easterDay   = date('j', $easterDate);
  $easterMonth = date('n', $easterDate);
  $easterYear   = date('Y', $easterDate);

  $holidays = array(
    // Dates fixes
    mktime(0, 0, 0, 1,  1,  $year),  // 1er janvier
    mktime(0, 0, 0, 5,  1,  $year),  // Fête du travail
    mktime(0, 0, 0, 5,  8,  $year),  // Victoire des alliés
    mktime(0, 0, 0, 7,  14, $year),  // Fête nationale
    mktime(0, 0, 0, 8,  15, $year),  // Assomption
    mktime(0, 0, 0, 11, 1,  $year),  // Toussaint
    mktime(0, 0, 0, 11, 11, $year),  // Armistice
    mktime(0, 0, 0, 12, 25, $year),  // Noel

    // Dates variables
    mktime(0, 0, 0, $easterMonth, $easterDay + 1,  $easterYear),
    mktime(0, 0, 0, $easterMonth, $easterDay + 39, $easterYear),
    mktime(0, 0, 0, $easterMonth, $easterDay + 50, $easterYear),
  );

  sort($holidays);

  return $holidays;
}
?&gt;</pre>

<p class="brush:php">
  Source : <a title="Fonction easter_date() sur php.net" href="http://php.net/manual/fr/function.easter-date.php">http://php.net/manual/fr/function.easter-date.php</a>
</p>