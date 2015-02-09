---
layout: post
title: "Critique du livre JavaScript Enlightenment"
date: 2013-12-18 21:26:53 +0100
comments: true
categories: [javascript, critique]
keywords: javascript, critique, livre, javascript, enlightenment, cody lindley
---
### de Cody Lindley

*TL;DR
Ce livre est réservé, selon l'auteur, à des débutants ayant déjà manipulé JavaScript ou une librairie JavaScript (jQuery par exemple). Il enseigne en profondeur le fonctionnement des objets JavaScript : les objets natifs (`Object`, `Array`, `String`, etc), les primitives (`"string"`, `12`, `false`, `undefined`, `null`) et les objets définis par le développeur. Comme tout est objet, ou peut être utilisé comme tel en JavaScript, l'auteur part du principe que si ce point est compris, alors le lecteur aura toutes les bases pour comprendre le langage et ainsi passer d'un développeur utilisant une librairie à un développeur JavaScript*

{% blockquote Cody Lindley, JavaScript Enlightenment %}
A book to turn a JavaScript library user into a JavaScript developer
{% endblockquote %}

<!--more-->

{:.imgPostCenter}
[![Couverture du livre JavaScript Enlightenment]({{ root_url }}/images/post/javascript_enlightenment.gif "Couverture du livre JavaScript Enlightenment")](http://www.amazon.fr/gp/product/1449342884/ref=as_li_tf_il?ie=UTF8&camp=1642&creative=6746&creativeASIN=1449342884&linkCode=as2&tag=sojava-21)<br>
[JavaScript Enlightenment](http://www.amazon.fr/gp/product/1449342884/ref=as_li_tf_il?ie=UTF8&camp=1642&creative=6746&creativeASIN=1449342884&linkCode=as2&tag=sojava-21)

Ce livre, écrit par Cody Lindley, transformera, selon lui, les développeurs utilisant des librairies (par exemple, jQuery) en développeur JavaScript. Je n'ai pas compris pourquoi. Selon moi, ce livre aurait dû s'appeler "JavaScript : **Object** Enlightenment".

### Contexte : 
Ce livre est sorti en 2011 et se base sur la spécification [ECMA-262, Edition 3 (JavaScript 1.5)](http://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-262,%203rd%20edition,%20December%201999.pdf), de son petit nom ES3. Depuis, ES5, qui a enrichi énormément JavaScript, est sorti en juin 2011 et nous sommes à l'aube de la sortie d'ES6. De fait, ses explications sont, au jour d'aujourd'hui, incomplètes et pourraient donner au lecteur une vision de JavaScript ne reflétant pas la réalité. Il aborde, très rapidement, la librairie [underscore](http://underscorejs.org/) qui permet d'apporter à JavaScript (ES3) des fonctions avancées pas encore disponible dans les navigateurs implémentant la norme ES3 (IE8-).
De fait, lu avant 2011, ce livre est parfait pour comprendre la vraie nature de JavaScript et des fonctionnalités qu'il offre. Lu aujourd'hui, fin 2013, bien qu'il soit efficace pour assimiler le fonctionnement des objets en JavaScript, il m'a semblé être insuffisant pour apprécier le périmètre complet de JavaScript.

### Les plus :

- "JavaScript Object Enlightenment" : les objets n'ont plus de secret pour moi
- `Function`, `Function.prototype`, le `scope` et `this` très bien expliqués
- Bonnes distinctions entre les primitives et objets complexes
- Le résumé à la fin du livre de ce qu'on doit avoir retenu
- Ecriture concise, claire bien qu'un peu trop d'expressions familières
- Des liens vers des [jsFiddle](http://jsfiddle.net) pour pouvoir tester les bouts de code

### Les moins :
- Trois objets natifs manquants : `Date`, `Error` et `RegEx`. Car, selon l'auteur, son livre n'est pas un guide exhaustif et ces objets n'apporteraient rien de plus à la compréhension du fonctionnement objet de JavaScript. Alors pourquoi liste - t - il des propriétés de `Number`, `Array`, etc ? 
- Beaucoup de répétitions ennuyeuses de l'auteur (*leverage*, *the take away*, *grok*, etc) qui rendent la lecture parfois chronophage
- Les exemples de code manquent de vie : que du `foo` et du `bar`. J'aurais aimé plus de cas concrets

### Conclusion

JavaScript Enlightenment aurait pu être une référence intemporelle sans ses listes de propriétés d'objets ES3 et l'exemple sur [underscore](http://underscorejs.org/). Outre ce point négatif et une fois habitué au style littéraire de l'auteur, ce livre conviendra parfaitement aux débutants expérimentés qui comprendront parfaitement la logique objet de JavaScript

*ISBN-10: 1449342884 / ISBN-13: 978-1449342883*