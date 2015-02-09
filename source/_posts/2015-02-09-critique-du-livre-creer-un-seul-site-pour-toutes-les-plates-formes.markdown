---
layout: post
title: "Critique du livre Créer un seul site pour toutes les plates-formes"
date: 2015-02-09 13:53:30 +0000
comments: true
categories: [javascript, critique]
keywords: javascript, critique, livre, javascript, one web, responsive, adaptive, design, sylvain pollet-villard
---
### aux sources des approches responsive et adaptative, de Sylvain Pollet-Villard

### À propos de l'auteur
*[Sylvain Pollet-Villard](http://www.syllab.fr/) est ingénieur (ISEN de Lille) d'études et développement expert en web front-end. Il est auteur de [nombreux jeux](http://syllab.fr/#play) ou [expérimentations](http://syllab.fr/#lab) aussi funs que loufoques. Il est également bénévole pour répondre aux questions des développeurs débutants sur les forums de [developpez.net](http://www.developpez.net/forums/), en particulier sur le forum JavaScript. Il se peut que vous le croisiez aux détours d'une [ChtiJS](https://twitter.com/chtijs) (meetups sur JavaScript) ou d'un apéro [WelshDesign](https://twitter.com/welsh_design) (meetups sur les métiers du front, orientés UI/UX).*

### Critique du livre

{% blockquote Sylvain Pollet-Villard %}
Pourquoi développer plusieurs versions d'un site web [...] ? Il est possible de concilier les usages autour d'un seul site et d'une seule URL : c'est ce que propose l'approche One Web
{% endblockquote %}

<!--more-->

{:.imgPostCenter}
[![Couverture du livre](http://ecx.images-amazon.com/images/I/41D91wuH-gL._SX385_.jpg "Couverture du livre")](https://www.amazon.fr/dp/2212139861?tag=sojava-21&camp=1414&creative=6410&linkCode=as1&creativeASIN=2212139861&adid=1AJC86CAH0RJ56X1T9PN&)<br>
[Créer un seul site pour toutes les plates-formes](https://www.amazon.fr/dp/2212139861?tag=sojava-21&camp=1414&creative=6410&linkCode=as1&creativeASIN=2212139861&adid=1AJC86CAH0RJ56X1T9PN&)

Ce livre est destiné aux webdesigners, intégrateurs, développeurs web, chargés de marketing et responsables de communication. Il faut avoir au moins participé à l'élaboration d'un site afin de bien comprendre le livre. Il n'est donc pas adressé à un public débutant.

Il tente de répondre à une problématique : face à la recrudescence des objets connectés, comment faire en sorte que son site soit compatible avec tous les appareils sans avoir besoin de maintenir plusieurs versions ? (Il ne traite néanmoins pas des objets connectés, tels les montres, lunettes ou smart TV, jugés trop instables pour le moment). La réponse à cette problématique est accompagnée d'un [site compagnon](http://onecake.syllab.fr/) qui permet de mettre en pratique la théorie parfaitement maitrisée par l'auteur.

Il y a quatre grosses parties dans ce livre :

- Normalisation / Contextualisation : pour poser les bases et comprendre le reste du livre, uniformisation des styles, les préfixes vendeurs, événements souris/tactiles, les polyfills/shims/fallbacks, le contexte dans lequel le site est lancé (récupération des éléments essentiels tels que la hauteur de la fenêtre, l'orientation, la connexion, etc)
- Approche Responsive : pourquoi on en a eu besoin, les unités CSS à utiliser, le viewport, les media queries
- Approche Adaptive : histoire et différences avec le responsive, la relation avec les URL/REST/HTTP, AJAX à la rescousse pour servir des ressources adaptées
- Outils du dév front d'aujourd'hui : préprocesseurs CSS, outils de build Grunt/Gulp, debugging (console), tests, etc

Chacune des ces parties est très complète, la précédente amène toujours la suivante et c'est donc très fluide à lire. Il y a même une partie qui explique comment concilier l'approche responsive avec l'approche adaptive afin d'offrir une expérience optimale à l'utilisateur.

Ce que j'ai aimé dans ce livre :

- Chaque partie commence par une phrase d'introduction décrivant parfaitement ce que l'on va lire
- Les encarts "Pour aller plus loin", "Remarques" qui proposent au lecteur d'appronfondir le sujet
- Le site web compagnon
- Le côté technique omniprésent mais accompagné d'exemples concrets
- Le dernier chapitre qui liste les outils d'ajourd'hui qui nous permettent de gagner du temps (préprocesseurs CSS, outils de build Grunt/Gulp, debugging, tests, etc)
- ... et plus particulièrement la partie sur les tests

Sylvain nous offre là un livre très clair et concis (120 pages) dans l'air du temps, bourré de bonnes pratiques pour réaliser un site adapté à plusieurs appareils et donc plusieurs écrans. A la fin de ce bouquin, vous serez en mesure d'avoir les meilleures bases pour créer un site "responsive/adaptive".

*ISBN-10: 2212139861 / ISBN-13: 978-2212139860*