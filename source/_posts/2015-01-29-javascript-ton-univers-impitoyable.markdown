---
layout: post
title: "JavaScript, ton univers impitoyable"
date: 2015-01-29 16:08:16 +0000
comments: true
categories: [javascript, ecmascript, historique]
keywords: javascript, ecmascript, node.js, io.js, DOM, W3C
---
*JavaScript, ECMAScript, ES6/2015, W3C, V8, DOM, Node.js / io.js : qui fait quoi ?*

Quand j'ai débarqué dans le monde du JavaScript, j'étais assez confus par tous ces termes qui gravitent autour. Si vous pensez que l'ECMAScript c'est une maladie juvénile liée à l'acnée et que JavaScript est un plugin de Java, cet article est fait pour vous.

* TOC
{:toc}

### tl;dr, JR ! Ce billet en bref

- JavaScript n'a rien à voir avec Java. C'est qu'un choix de nommage "commercial/marketing". N'oubliez pas le "S" majuscule, s'il vous plait.
- ECMAScript, c'est une norme, une spécification, un standard. JavaScript est une implémentation de cette norme.
- ES6, ou ES2015, c'est la prochaine (la 6ème) version majeure (qui devrait sortir courant 2015) de ECMAScript.
- JavaScript 1.x est la terminologie utilisée historiquement par Netscape (puis Mozilla) pour nommer ses versions de JavaScript.
- JScript était le "JavaScript" de Microsoft pour concurrencer celui de Netscape.
- Mocha/LiveScript étaient les noms de code de JavaScript avant qu'il ne s'appelle JavaScript.
- W3C, WHATWG : on parle de "consortium". C'est une association de plusieurs membres influents d'entreprises, elles-mêmes influentes, qui s'unissent pour faire avancer le web.
- V8 : C'est le moteur JavaScript de Google (les navigateurs Chrome et Opera l'utilisent). C'est ce qui sert à lire et exécuter le JavaScript. D'autres moteurs : Spider Monkey / Rhino (Netscape/Mozilla), Chakra (Microsoft)
- DOM : c'est un standard (maintenu par le W3C) qui décrit comment représenter/modifier le code source d'une page web (le contenu, la structure et les styles). Il est attaché à JavaScript dans un navigateur (`window.document`). Le DOM n'est pas spécifié dans ECMAScript. C'est le WHATWG/W3C qui en a la charge.
- Node.js ça sert à exécuter JavaScript sur un serveur à l'aide du moteur JavaScript V8. C'est une marque déposée qui appartient à une entreprise qui s'appelle Joyent.
- io.js c'est un fork de Node.js. Ce sont les ptits gars qui font Node qui ont décidé de se défaire de l'emprise de Joyent.

J'ai cherché à en savoir plus sur chacun de ces termes. Voici mes trouvailles, n'hésitez pas à ajouter/corriger ces propos dans les commentaires.

<!--more-->

### JavaScript n'est pas Java !
JavaScript et Java n'ont de commun que le préfixe "Java". C'est comme dans Cartoon et Carnaval. Ils n'ont de commun que le "Car". Et bien là c'est pareil. (bon ok, y'a des trucs salaces que JavaScript a repris à Java, comme `Date` et `Math` par exemple, mais là n'est pas la question)

Ce choix de nommage est, à la base, purement commercial, marketing et historique.

Il faut remonter en 1995, alors que Sun sort le premier JDK Java. Ils veulent intégrer leur JVM dans Netscape Navigator 2.0 afin d'ouvrir leur technologie au web. Netscape, souhaitant donner une grosse plus-value afin d'enterrer totalement la rockstar des navigateurs de l'époque (Mosaic) flaire donc les avantages d'un tel partenariat.

Sun et Netscape sont alors en pleines discussions commerciale et marketing. Durant cette même année 1995, en avril, Brendan Eich (le papa de JavaScript) se fait embaucher pour créer un langage pour le navigateur. Mais attention, un langage qui ne doit pas marcher sur les plates bandes de Java.

L'enjeu de Brendan Eich est donc double. Il doit sortir de son chapeau, en très peu de temps, un tout nouveau langage et, surtout, convaincre Sun que ce nouveau langage ne fera pas de l'ombre à leur Java bien aimé.

En décembre 1995 sort le le Netscape Navigator 2.0. Dedans, le tout nouveau JavaScript (développé par Brendan Eich entre mai et novembre 1995 si on en croit la légende) ainsi qu'une machine virtuelle Java.

Mais alors, comment papa Eich a réussi à convaincre les gars de Sun que son langage n'avait rien à voir avec Java ?

Java était destiné aux développeurs expérimentés. Il imposait d'être intransigeant avec son typage, ses classes et ses méthodes static/main et il fallait compiler le code sous forme d'applet afin de l'embarquer dans une page web. Dès lors, le navigateur devait avoir la machine virtuelle pour l'exécuter.

Beaucoup trop d'étape. Beaucoup trop lourd. Beaucoup trop difficile à apprendre pour des débutants en programmation : voici comment les gars de Netscape voyaient Java.

Ils voulaient un langage plus simple. Un langage comme "Scheme" mais dans le navigateur. Un langage de script qui ne nécessite pas de compilation. Un langage qui ne génère pas d'erreur. Un langage permissif où il n'y a pas de notions de typage à la Java. Un langage qui s'exécute directement dans le HTML. Un langage facilement compréhensible par des débutants en programmation.

JavaScript se voulait donc tout le contraire de Java. Tout le complémentaire de Java, en fait.

Il a été pensé pour être facilement programmable par les débutants, il suit le concept du "vas-y que je te copie/colle ton snippet pour que ça marche".

Les deux langages se voulaient donc complémentaires :

- Java : permet de contrôler les éléments (hardware) de la machine. Le code est embarqué/compilé dans une applet. Destiné à un public de développeur expérimenté.
- JavaScript : permet de contrôler les éléments de la page web afin de la rendre dynamique facilement. Le code se fait directement dans le HTML. Destiné à un public de développeur débutant/amateur.

Sun s'est vite rendu compte que son langage n'était pas destiné aux novices en programmation, c'est pourquoi ils ont laissé les gars de Netscape développer JavaScript en parralèle afin d'avoir un langage pour le web plus simple d'utisation. "Mocha" était déjà une marque déposée. "LiveScript" n'était pas très aimé car d'autres projets au sein de Netscape avait déjà des technologies "Live-quelque-chose". Ils ne voulaient pas de "Live-ci", "Live-ça".

C'est ainsi que JavaScript est né, et avec lui la confusion.

Petit note marrante, Java a failli s'appeler Oak. Mais finalement, pour des raisons de trademarks (encore elles), ce fut Java. OakScript, c'est pas mal non plus, non ?

Sources : [1)](http://devchat.tv/js-jabber/124-jsj-the-origin-of-javascript-with-brendan-eich)

### ECMAScript, ou ES de son petit nom
Non, AcnéeScript, pardon, ECMAScript, n'est pas une maladie.

ECMAScript, c'est un standard, une norme, une spécification.

JavaScript est une implémentation de cette norme. Au même titre qu'ActionScript 3 l'est, par exemple.

Un commité technique (TC39) a été mis en place au sein d'Ecma (association de membres influents de l'industrie informatique) pour définir des spécifications au langage afin d'éviter les divergences constatées à l'époque entre JavaScript (le langage de script de Netscape) et JScript (celui de Microsoft).
Ces spécifications se nomment donc ECMAScript (nom de code de la norme : ECMA-262 pour être précis). <sup>[2)](http://ecma-international.org/memento/TC39-M.htm)</sup>

#### Pourquoi la standardisation a t elle était confiée à Ecma et non au W3C ?
Certains disent que c'est parce que le W3C ne standardise pas de langage de programmation <sup>[3)](http://www.quora.com/Why-was-JavaScript-standardized-by-ECMA-and-not-W3C/answer/Dan-Connolly-1?srid=CoM&share=1)</sup>, d'autres disent que c'est Microsoft qui a forcé Netscape à choisir ce protagoniste <sup>[4)](http://quod.lib.umich.edu/j/jep/3336451.0014.103/--why-standardization-efforts-fail?rgn=main;view=fulltext#5.2)</sup>.
Je n'ai pas vraiment réussi à trouver la véritable raison. Mais il y a fort à parier que c'est un peu ces deux affirmations qui ont poussé Netscape à confier le bébé à Ecma.

#### Pourquoi ECMAScript ne s'appelle pas JavaScript ?

{:.imgPostCenter}
![Qui veut JavaScript ?]({{ root_url }}/images/post/jr_dallas.jpg "Qui veut JavaScript ?")

Uniquement pour des raisons de "trademarks", de marques, de gros sous (voir l'histoire ci-après). Le nom "JavaScript" appartenait à Sun, maintenant Oracle <sup>[5)](http://tsdr.uspto.gov/#caseNumber=75026640&caseType=SERIAL_NO&searchType=statusSearch)</sup>. Ils n'ont pas trouvé de terrain d'entente pour leur céder les droits. D'où le nom ECMAScript. Microsoft n'a pas pu utiliser non plus le nom JavaScript à l'époque, pour les mêmes raisons. C'est pourquoi ils avaient opté pour "JScript".

Fait marrant, prouvant la détermination de Sun à ne pas laisser les autres se faire du pognon sur leur marque si eux ne peuvent pas en faire eux mêmes (alors que le nom est bien ancré dans la tête des gens). Il existait ce site, Javanko.com, qui appartenait à un homme s'appelant "Javanko" de père en fils depuis de nombreuses générations. Les avocats de Sun l'ont poursuivi afin qu'ils ferment son site car il utilisait un nom commençant par JAVA <sup>[1)](http://devchat.tv/js-jabber/124-jsj-the-origin-of-javascript-with-brendan-eich)</sup>. Alors imaginons un organisme voulant standardiser le JavaScript ... avoir les droits d'utiliser ce nom était donc perdu d'avance. 

Remercions Sun pour la confusion.

Et d'ailleurs, heureusement que Sun n'a jamais attaqué Gainsbourg pour sa "JAVAnaise". Nav'allavez pavas lave davirave avà avOravaclave.

#### Les versions d'ECMAScript
Il y a eu, pour le moment en janvier 2015, [4 versions majeures d'ES](http://www.ecma-international.org/publications/standards/Ecma-262-arch.htm) depuis la toute première de juin 1997.

- ES1 / ES2 : c'est en fait un portage du JavaScript de Netscape vers ECMAScript.
- ES3 : c'est la version majeure qui a régné entre 1999 et 2009 de laquelle on commence à se défaire.
- ES4 : ce fut un fiasco total. Cette version n'est jamais sortie à cause des discordances entre les principaux acteurs du TC39 d'Ecma.
- ES5 / ES5.1 : sortie fin 2009, puis révisé en 2011. Il s'agit de la 5ème édition de la norme ECMAScript, faisant suite à ES3.
- ES6 : a été fraichement renommée ES2015. C'est la prochaine version majeure de la norme. Les moteurs JavaScript sont en pleines courses, à celui qui réussira le premier à couvrir l'ensemble des fonctionnalités
- ES XXXX : Les prochaines versions porteront l'année de leur publication à la suite de leur nom. A noter que le numéro de version restera ancré dans la tête des gens.

Une autre version d'ECMAScript ([norme ECMA-357](http://www.ecma-international.org/publications/standards/Ecma-357.htm)), indépendante de celle que l'on connait, a tenté de percer : [E4X](https://developer.mozilla.org/en-US/docs/Archive/Web/E4X). Il faut lire "ECMASCript for XML". Rien à voir avec ES4 donc qui fait partie de la norme ECMA-262 (le ECMAScript que l'on connait tous).

Cette spécification désuète ajoutait le support natif d'XML dans ECMAScript. Le but était de se passer du DOM pour lire les informations d'un document XML. Cela a été implémenté à partir de Firefox 1.5 et vite retiré. Désactivée dès Firefox 17, retirée définitivement depuis Firefox 21.

Son échec est dû essentiellement à l'essor du JSON (qui a eu lieu en même temps vers 2004/2005 grâce à Douglas Crockford, fervent défenseur de ce format) et sa simplicité par rapport au XML.

#### ES6 vs ES.next vs ES Harmony

ES Harmony est l'ensemble des versions d'ECMAScript à partir d'ES5. En effet, suite à la discordance du commité (TC39) autour d'ES4, ils ont  donné un nom de code à toutes les nouvelles fonctionnalités faisant suite au fiasco ES4 : ES Harmony <sup>[6)](https://esdiscuss.org/topic/javascript-2015#content-13)</sup>.
ES Harmony est donc l'ensemble des fonctionnalités suivants cette mésentente ES4 <sup>[6)](https://mail.mozilla.org/pipermail/es-discuss/2008-August/003400.html)</sup>.

ES.next est le nom de code pour la prochaine version d'ECMAScript. A l'heure actuelle, ES.next est donc la version qui suivra ES5.1, soit ES2015/ES6. Quand ES2015/ES6 sera la dernière version publiée, ES.next sera ES2016/ES7 (si une version 7 est publiée en 2016) et ainsi de suite.

ES6 a été pendant longtemps le nom de la version majeure suivant ES5.1. L'année de publication viendra compléter ce nom, comme on peut le voir sur cette [couverture](https://twitter.com/awbjs/status/558316031039381504) du brouillon en cours. En effet, "6<sup>th</sup> edition" est toujours présent sur la couverture. Cela laisse sous-entendre que les deux noms cohabiteront.

### JavaScript 1.x, JScript, Mocha/LiveScript

Mocha/LiveScript étaient les premiers noms de code de JavaScript (voir le point "JavaScript n'est pas Java !" ci-dessus pour savoir pourquoi ils n'ont pas été sélectionnés).

JavaScript 1.x, c'est la règle de nommage spécifique à Mozilla. Historiquement, un nouveau navigateur venait avec son lot de nouveautés JavaScript qui voyait alors son numéro de version s'incrémenter. Chaque version ayant un équivalent ECMAScript <sup>[7)](https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide/JavaScript_Overview)</sup> (ou presque).

- JavaScript 1.0 : Netscape Navigator 2.0, tout premier navigateur ayant JavaScript
- JavaScript 1.1 : Netscape Navigator 3.0 / ECMAScript 1
- JavaScript 1.2 : Netscape Navigator 4.0 à 4.05 / ECMAScript 1 + des nouveautés non standardisées encore
- JavaScript 1.3 : Netscape Navigator 4.06 à 4.5 / ECMAScript 1 remis à niveau pour être consistent avec la spéc.
- JavaScript 1.4 : seulement utilisé en interne chez Netscape, sur de la techno côté serveur.
- JavaScript 1.5 : Netscape Navigator 6+ / Firefox 1 / ECMAScript 3 édition 1999
- JavaScript 1.6 : Firefox 1.5 / ECMAScript 3 + des fonctionnalités du mort-né [E4X](https://developer.mozilla.org/en-US/docs/Archive/Web/E4X)
- JavaScript 1.7 : Firefox 2 / ECMAScript 3 + des fonctionnalités des [futures normes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/New_in_JavaScript/1.7#New_features_in_JavaScript_1.7)
- JavaScript 1.8 : Firefox 3 / ECMAScript 3 + des fonctionnalités des [futures normes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/New_in_JavaScript/1.8#Changed_functionality_in_JavaScript_1.8)
- JavaScript 1.8.1 : Firefox 3.5 / Idem que JavaScript 1.8 + le nouveau compilateur JIT : [Tracemonkey](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/SpiderMonkey/Internals/Tracing_JIT)
- JavaScript 1.8.5 : Firefox 4 / ECMAScript 5

Le processus de livraison de Firefox s'étant calqué sur celui de Chrome (1 version par mois), il n'y a plus eu d'évolution du numéro de version de JavaScript. Chaque nouvelle version du navigateur Firefox embarque de plus en plus de nouvelles fonctionnalités du prochain ECMAScript.

Quant à Internet Explorer, flairant le succès de ce langage de script, décide de sortir sa version de JavaScript (appelée JScript) <sup>[8)](https://msdn.microsoft.com/en-us/library/2z6exc9e(v=vs.90).aspx)</sup>.

- Internet Explorer 1 : Basé sur le code source Spyglass Mosaic. Un fork du tout premier navigateur : NCSA Mosaic.
- Internet Explorer 2 : Il est inclut dans Windows 95. JScript n'est pas encore présent dans ces deux premiers navigateurs.
- Internet Explorer 3 : Première apparition de JScript sous l'appellation JScript 1.0, plus ou moins JavaScript 1 de Netscape
- Internet Explorer 4 : JScript 3.0, plus ou moins JavaScript 1.1 de Netscape
- Internet Explorer 5.5 : JScript 5.5 / ECMAScript 3 plus ou moins
- Internet Explorer 6 : JScript 5.6 / ECMAScript 3 plus ou moins
- Internet Explorer 7 : JScript 5.7 / ECMAScript 3 plus ou moins
- Internet Explorer 8 : JScript 5.8 / ECMAScript 3 plus ou moins. Cette version est la dernière sous le nom JScript.
- Internet Explorer 9 : ECMAScript 5 plus ou moins. A partir de IE 9, l'appelation JScript disparait au profit de "JavaScript", correspondant à la version 5 d'ECMAScript
- Internet Explorer 10 : ECMAScript 5.1 + des nouveautés du prochain ECMAScript
- Internet Explorer 11 : ECMAScript 5.1 + des nouveautés du prochain ECMAScript

### W3C, WHATWG
Le W3C et le WHATWG, en gros, c'est un peu comme le groupe Ecma. Ce sont des hommes/femmes vachement calés dans les technologies du web et qui font avancer les standards. Ils viennent de tout horizon mais bien plus souvent des grosses entreprises liées au web telles Google, Apple, et consors. Les standards ont pour vocation à être implémentés dans les navigateurs, utilisés par les développeurs, et évoluent en fonction de feedbacks, de critiques, etc.

On parle de "consortium". C'est une association de plusieurs membres influents d'entreprises, elles-mêmes influentes, qui s'unissent pour faire avancer les standards du web.

Mes définitions grossière (elles sont réductrices de tout le travail fournit pas ces organisations) :

- Le W3C <sup>[9)](http://www.w3.org/standards/faq.html)</sup> : ils "figent" et publient diverses spécifications de standard liés au web et lui attribuent un petit nom. DOM level XXX, xHTML, HTML5, etc...
- Le WHATWG <sup>[10)](https://wiki.whatwg.org/wiki/FAQ)</sup> : c'est un groupe du W3C créé par une entente Apple/Mozilla/Opera. Ils font dans le "live". Comprendre qu'ils font évoluer sans cesse la spécification. Une fois suffisament évoluée, ils décident de la figer et un autre groupe du W3C reprend le bébé pour le figer/publier.

### Les moteurs JavaScript
Ils permettent de lire et d'exécuter du code JavaScript. Il y en a énormément <sup>[11)](http://en.wikipedia.org/wiki/List_of_ECMAScript_engines)</sup>. Certains vivent dans un navigateur, d'autres non.

- V8 est le moteur JavaScript de Google (les navigateurs Chrome et Opera l'utilisent).
- Spider Monkey fut le premier moteur JavaScript de Netscape Navigator, puis ensuite de Firefox
- Chakra est celui de Microsoft

### Le DOM, Document Object Model
Le DOM est un standard <sup>[12)](https://dom.spec.whatwg.org/)</sup> (maintenu par le WHATWG/W3C) qui décrit comment représenter/modifier le code source d'une page web (le contenu, la structure et les styles).

Voyez-le comme une sorte de modèle (imaginez ça comme un "plugin") attaché à l'objet racine de JavaScript (`window`) quand il s'exécute dans un navigateur (accessible via `window.document`). Mais il peut très bien être présent dans d'autres langages. Il est "neutre". C'est le WHATWG/W3C qui a la charge de le faire évoluer. En ce moment (janvier 2015), c'est le WHATWG qui le fait évoluer quasi quotidiennement. On parle alors de "Living Standard".

DOM veut dire Document Object Model, c'est tout simplement le code HTML qui est transformé en arbre afin d'être manipulé, transformé.

Le DOM est né assez simplement. Brendan Eich s'est vite rendu compte que pour écrire du code dans le HTML (principe de base de JavaScript), il fallait que ce code puisse manipuler le code source HTML <sup>[1)](http://devchat.tv/js-jabber/124-jsj-the-origin-of-javascript-with-brendan-eich)</sup>. Il a alors pensé à un système qui permet : 

- de faire appel à tous les liens : `document.links`
- d'appeler le 2ème formulaire : `document.forms[1]`
- carrément d'appeler le formulaire s'appelant toto : `document.forms.toto`

Ainsi naquit le DOM primitif qui devint plus tard le fameux DOM level 0 <sup>[13)](http://www.w3.org/DOM/DOMTR)</sup>, une fois standardisé.

### Node.js

Node est né en 2009 des mains de [Ryan Dahl](https://github.com/ry). Il est basé sur le moteur JavaScript V8 et permet donc d'exécuter du JavaScript sur un serveur.

C'est une marque déposée <sup>[14)](http://tsdr.uspto.gov/#caseNumber=85262623&caseType=SERIAL_NO&searchType=statusSearch)</sup> qui appartient à une entreprise qui s'appelle Joyent.

### io.js

C'est un fork de Node.js. Ce sont les ptits gars <sup>[15)](https://github.com/iojs/io.js/blob/v1.x/README.md#current-project-team-members)</sup> qui faisaient Node qui ont décidé de se défaire de l'emprise de Joyent en faisant évoluer io.js plutôt que Node.js directement. Ils ont un modèle de gouvernance <sup>[16)](https://github.com/iojs/io.js/blob/v1.x/GOVERNANCE.md#iojs-project-governance)</sup> très souple où tout le monde peut s'exprimer. Ils opèrent de la même façon que le W3C ou qu'Ecma (comprendre il y a un Comité Technique). Ces membres sont les contributeurs principaux du projet (comprendre les serials commiters) mais d'autres personnes externes, comme [Domenic Denicola](https://twitter.com/domenic) membre du TC39 d'Ecma / Google Chrome Team, sont entrées au sein de ce comité. Cela ne peut apporter que du bon à io.js. En l'occurrence des ententes entre ECMAScript et le moteur V8.

### Et après ?
La guerre des navigateurs, ça a du bon.

C'est ainsi qu'est standardisée une technologie.

C'est ainsi que les fonctionnalités nous arrivent à nous, développeurs.

C'est ainsi les rythmes de release sont de plus en plus rapide.

C'est ainsi que nous pouvons nous exprimer afin d'arriver à un consensus final.

La diversité fait du bien, grâce à cette guerre, je dirais plutôt paix mouvementée, la norme tout juste sortie est déjà presque totalement implémentée dans nos navigateurs préférés.

Pour notre plus grand plaisir et le plus grand plaisir de nos clients. C'est-à-dire nous, en fait, consommateurs de l'Internet !

### Sources
  * 1) [Interview de Brendan Eich, inventeur de JavaScript](http://www.infoworld.com/article/2653798/application-development/javascript-creator-ponders-past--future.html), [Podcast](http://devchat.tv/js-jabber/124-jsj-the-origin-of-javascript-with-brendan-eich)
  * 2) [TC39](http://ecma-international.org/memento/TC39-M.htm), [Membres d'Ecma](http://www.ecma-international.org/memento/Ecma%20Awards%20of%20Appreciation.htm)
  * 3) [Why was JavaScript standardized by ECMA and not W3C?](http://www.quora.com/Why-was-JavaScript-standardized-by-ECMA-and-not-W3C/answer/Dan-Connolly-1?srid=CoM&share=1) Réponse de Dan Connolly, au W3C au moment des faits
  * 4) ["Microsoft had just forced Netscape to standardize JavaScript in Ecma"](http://quod.lib.umich.edu/j/jep/3336451.0014.103/--why-standardization-efforts-fail?rgn=main;view=fulltext#5.2), [Carl Cargill](http://www.adobe.com/devnet/author_bios/carl-cargill.html), chez Sun au moment des faits
  * 5) [JavaScript trademark](http://tsdr.uspto.gov/#caseNumber=75026640&caseType=SERIAL_NO&searchType=statusSearch)
  * 6) [ES Harmony](https://esdiscuss.org/topic/javascript-2015#content-13), [Les discordances ES4](https://mail.mozilla.org/pipermail/es-discuss/2008-August/003400.html)
  * 7) [Relation versions ES/JavaScript](https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide/JavaScript_Overview)
  * 8) [Relation versions ES/JScript](https://msdn.microsoft.com/en-us/library/2z6exc9e(v=vs.90).aspx)
  * 9) [W3C - FAQ](http://www.w3.org/standards/faq.html)
  * 10) [WHATWG - FAQ](https://wiki.whatwg.org/wiki/FAQ)
  * 11) [Liste des moteurs JavaScript](http://en.wikipedia.org/wiki/List_of_ECMAScript_engines)
  * 12) [DOM Standard](https://dom.spec.whatwg.org/)
  * 13) [La liste des différents "level" du DOM](http://www.w3.org/DOM/DOMTR)
  * 14) [Node.js Trademark](http://tsdr.uspto.gov/#caseNumber=85262623&caseType=SERIAL_NO&searchType=statusSearch)
  * 15) [Membres de io.js](https://github.com/iojs/io.js/blob/v1.x/README.md#current-project-team-members)
  * 16) [Modèle de gouvernance d'io.js](https://github.com/iojs/io.js/blob/v1.x/GOVERNANCE.md#iojs-project-governance)
