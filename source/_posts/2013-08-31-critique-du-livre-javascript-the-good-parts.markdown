---
layout: post
title: "Critique du livre JavaScript: The Good Parts"
date: 2013-08-31 00:14
comments: true
categories: [javascript, critique]
keywords: javascript, critique, livre, the good parts, douglas crockford
--- 
### de Douglas Crockford
*ISBN-10: 0596517742 / ISBN-13: 978-0596517748*

Ce livre, écrit par Douglas Crockford, est destiné à un public intermédiaire en Javascript, ayant déjà connaissance des bases du langage. Il est court, une centaine de pages sans les annexes. Les "bonnes pratiques", selon l'auteur, sont décrites de façons claires, concises et facilement compréhensibles pour peu que vous ayez déjà des notions en Javascript.

Afin de bien comprendre le but du livre, il est nécessaire de savoir qui est ce Douglas "Papa" Crockford et pourquoi Javascript a des mauvais côtés. Sir D. Crockford est considéré comme l'un des pères de Javascript par la communauté éponyme. Il est le créateur du fameux format [JSON](http://json.org) et de l'outil [JSLint](http://jslint.com).
<!--more-->
Le premier est un format d'échange de données facile pour nous, développeurs, à lire et à écrire et, indépendant de tout langage. Il est très utile pour la communication entre un client et un serveur de par sa légèreté et ses outils (parse <> stringify). Par exemple, ceci est un JSON :

    {
      "message": "Compréhension OK !", 
      "erreur":  false, 
      params:    ["n'importe", "quoi", 1] 
    }

Le deuxième est un outil qui juge la qualité d'un code Javascript. Il remonte toutes les "mauvaises pratiques" qu'il faut éviter en Javascript. Par exemple, pour une comparaison il faut privilégier l'opérateur `===` plutôt que `==`. Si vous utilisez `==`, l'outil remontra une erreur.

Javascript, quant à lui, a connu un passé tumultueux. En résumé, il est sorti des laboratoires de Netscape (anciennement Mozilla) dans le but de réaliser des interactions simples avec le document web. En pleine guerre contre Internet Explorer, c'était à celui qui sortirait la meilleure fonctionnalité avant l'autre. Heureusement, une norme a vu le jour, ECMAScript, ce qui a permis de standardiser le langage. Mais le mal était fait ! De cet affront ont résulté des fonctionnalités bénéfiques pour le langage, mais aussi des maléfiques. Pour ne pas casser les pages web réalisées avec le Javascript d'Internet Explorer, et celles construites avec celui de Netscape, une nouvelle version de Javascript ne doit pas tuer la précédente sous peine de tuer de nombreux sites ! C'est pourquoi les mauvaises conceptions cohabitent tranquillement avec les bonnes.

Douglas Crockford est donc un homme qui aime la rigueur, la qualité du code et qui le veut simple de lecture aussi bien par l'homme que par la machine. Il nous apprend donc dans ce livre à apprécier les bonnes fonctionnalités et à oublier les maléfiques ! Il le fait par des exemples concrets et explique clairement sa démarche par l'apprentissage. Bien sûr, certains points sont à la bonne appréciation du lecteur, mais l'auteur nous explique pourquoi telle ou telle fonctionnalité est à écarter. Libre à nous, ensuite, de la garder ou non.

Ce livre m'a donc littéralement ouvert les yeux sur certaines pratiques que je pensais bonnes, mais qui sont, quand on creuse, mauvaises ou susceptibles de faire tomber notre code à la moindre secousse.

A la fin de ce livre, vous serez donc avertis de ce qu'il faut faire en Javascript pour éviter les pièges classiques qui font malheureusement partie du langage de par son historique. Si vous avez l'ambition de parfaire vos connaissances en Javascript, vous devez lire ce livre !

Il existe une version Version Française, *JavaScript : Gardez le meilleur*, traduit par Patrick Fabre. Cependant, je pense qu'il est préférable de le lire en Version Originale si vous êtes à l'aise avec l'anglais. Car dans la traduction, ce qui ne devrait pas être traduit, selon moi, l'est. Par exemple, la *closure* devient la *fermeture*. Pourquoi apprendre de nouveaux termes techniques que nous ne reverrons nulle part ailleurs ?