---
id: 1086
title: 'Testify : un micro framework de tests unitaires simple et élégant pour PHP'
date: 2011-11-30T10:00:02+00:00
author: Robin
layout: post
guid: http://elliptips.info/?p=1086
permalink: /testify-un-micro-framework-de-tests-unitaires-simple-et-elegant-pour-php/
Hide SexyBookmarks:
  - "0"
Hide OgTags:
  - "0"
dsq_thread_id:
  - "488273045"
image: /wp-content/uploads/2011/11/testify-180x160.jpg
---
Récemment, je suis tombé sur <span class="removed_link" title="https://github.com/martinaglv/Testify.php">Testify</span>, un micro framework pour **PHP** permettant de réaliser rapidement et simplement des tests unitaires.

Pour ceux qui ne seraient pas familiers avec ce concept, sachez qu’un test unitaire est un procédé (un morceau de code) qui permet de s’assurer du bon fonctionnement d’une partie de l’un de vos programmes.

En clair, cela va vous permettre de tester certaines de vos fonctions, méthodes ou classes en leur passant plusieurs paramètres en entrée dans le but de comparer les valeurs de retour avec ce qui devrait théoriquement être retourné.

<span style="text-decoration: underline;">Un exemple avec Testify :</span>

<pre class="brush:php">include "testify/testify.class.php";
include "MyCalc.php";

// Create a new test suite
$tf = new Testify("MyCalc Test Suite");

// Add a new test case to this suite
$tf-&gt;test("Testing the Add method", function($tf){
	$calc = new MyCalc(10);

	$calc-&gt;add(4);
	$tf-&gt;assertEqual($calc-&gt;result(),14);

	$calc-&gt;add(-5);
	$tf-&gt;assertEqual($calc-&gt;result(),9);
});

// Run the test and generate a report
$tf-&gt;run();</pre>

Ici, nous testons la méthode additionner contenue dans une classe MyCalc.php

Et voici ce que testify va nous retourner :

[<img class="aligncenter size-full wp-image-1088" title="testify-resultat" alt="testify resultat1 Testify : un micro framework de tests unitaires simple et élégant pour PHP  " src="http://elliptips.info/wp-content/uploads/2011/11/testify-resultat1.jpg" width="600" height="306" srcset="http://elliptips.info/wp-content/uploads/2011/11/testify-resultat1.jpg 600w, http://elliptips.info/wp-content/uploads/2011/11/testify-resultat1-300x153.jpg 300w" sizes="(max-width: 600px) 100vw, 600px" />](http://elliptips.info/wp-content/uploads/2011/11/testify-resultat1.jpg)

L’affichage du résultat est extrêmement clair et je dois avouer que c’est plaisant. Bref, si vous voulez creuser un peu le truc, des exemples sont disponibles sur <span class="removed_link" title="https://github.com/martinaglv/Testify.php">Github</span> et une documentation vous est proposée à cette [adresse](http://tutorialzine.com/projects/testify/ "Documentation testify").