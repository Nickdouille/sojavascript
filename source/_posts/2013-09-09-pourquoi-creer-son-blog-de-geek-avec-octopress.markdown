---
layout: post
title: "Pourquoi créer son blog (de geek) avec Octopress"
date: 2013-09-09 23:44
comments: true
categories: [blog, octopress, tutoriel]
keywords: blog, octopress, pourquoi, comment, créer
---
## ... et laisser tomber le gros Wordpress

Soyons clairs, je ne connais pas Wordpress intimement. Ce sous-titre a simplement une vocation trollesque :)
Je n'ai jamais travaillé avec, si ce n'est l'avoir installé *"pour tester"*. Cet article ne sera donc ni une comparaison [Octopress](http://octopress.org/)/[Wordpress](http://wordpress.com/) ni une critique de Wordpress qui n'a d'ailleurs rien à prouver. A l'heure où j'écris ces lignes, environ [70 millions](http://en.wordpress.com/stats/) de personnes pourront vous dire que Wordpress, c'est le pied. Par contre, [un nombre plus limité](https://github.com/imathis/octopress/wiki/Octopress-Sites) vous parlera d'Octopress.
<!--more-->
# Pourquoi j'ai choisi Octopress ?
Parce que c'est cool et comme ça, je passe pour un bon geek crédible ! Non ? Tant pis j'aurais essayé :)

Avant de me lancer dans un blog, j'avais quelques besoins et contraintes :

- ne pas payer un hébergement supplémentaire pour me lancer de le blogging. Après tout, ce n'est peut-être qu'une lubie qui s'estompera dans quelques temps ! *dixit le type qui a quand même acheté un nom de domaine*
- mettre à jour et déployer le blog le plus simplement possible (comprendre un clic ou une ligne de commande)
- pas d'interface admin lourde avec gestion de droits / utilisateurs / plugins etc
- pourvoir installer / supprimer un thème facilement
- être *responsive* et s'adapter à tous les écrans
- configurer simplement l'aspect social

Après avoir écumé les forums, les *benchmarks*, les différences entre plusieurs plateformes de blog et *CMS*, mon choix s'est donc arrêté sur Octopress qui répondait, et répond toujours, à mes besoins et contraintes.

# Un blog fait par des geeks, pour les geeks
Octopress en a fait sa devise : `A blogging framework for hackers.`

![A blogging framework for hackers]({{ root_url }}/images/octopress.jpg "A blogging framework for hackers")

Il ne faut pas avoir peur de : 

- git, 
- oublier ftp pour deployer son blog (c'est possible avec ftp, mais plus contraignant), 
- s'y connaitre un peu dans l'univers Ruby (Gems, Rake),
- [Jekyll](https://github.com/mojombo/jekyll) qui permet de générer les pages statiques à partir de templates,
- taper des lignes de commande

Vous êtes encore là ? Ne partez pas ! Il y a tellement d'avantages.

# Les avantages
Le principal avantage c'est la création et la mise en ligne du blog qui tient en une ligne : `rake gen_deploy`

Votre blog est à jour et disponible sur le net. Bien sûr, cela demande un peu de configuration de fichiers avant, mais rien d'insurmontable ! Surtout que la [documentation](http://octopress.org/docs/) est excellente.

### Performances & Scalabilité
La commande ci-dessus, `rake gen_deploy`, va générer du html, du javascript, du css et déployer le blog sur le serveur. C'est tout. Ce qui est un point fort indéniable : un hébergement gratuit est suffisant au départ pour tester la bête qui ne demandera pas, ou très peu, de ressources. Délivrer une page statique ou une page dynamique ? Niveau performance et scalabilité, je crois que [le test et vite fait](http://jason.pureconcepts.net/2013/01/benchmark-octopress-wordpress/).

### Sécurité
Il n'y a donc pas de langage serveur, pas de base de données, donc pas de risque de se faire attaquer de ce coté. Il faut néanmoins faire attention à la conf' serveur qui est le seul vecteur potentiel d'attaque.

### Maintenance
Oubliez donc les mises à jours PHP, MySQL, etc ... quelques simples lignes de commande permettront à la rigueur de mettre à jour Octopress si vous le souhaitez

### Gestion des commentaires & réseaux sociaux
Octopress peut-être lié à un système de gestion des commentaires (j'ai choisi [Disqus](http://www.disqus.com/)). Mais il est possible d'en utiliser un autre, il suffit de l'indiquer dans le fichier de configuration. De la même façon, on gère tous les réseaux sociaux dans ce fichier (`_config.yml`).

# Les inconvénients
Voici des choses qui pourraient vous manquer si vous venez de Wordpress, par exemple :

### Adieu interface admin
Aucune interface administrateur avec Octopress. Pour poster, il faudra donc être sur votre poste ayant ruby installé pour pouvoir générer/déployer le blog. Ce qui est l'inconvénient majeur, j'en conviens.

### Gestion des images
Tout se fait à la main sous Octopress. De la découpe, au redimensionnement, à l'upload, au code dans votre article pour insérer l'image.

### Internationalisation
Ce qui est dommage, c'est qu'il faille toucher à certains fichiers du coeur pour modifier l'anglais. On aurait apprécié une apporche plus simple pour "franciser" tous les termes plutôt que de devoir plonger dans les fichiers sources.

### Tout régénérer à chaque changement
Que vous changiez une lettre dans un fichier ou ajoutez un nouvel article, il faudra régénérer tout le blog. Du coup, un blog avec un nombre conséquent d'articles peut engendrer une attente non négligeable. (j'ai vu quelque part 1min10 environ pour 1'000 articles).

# Conclusion
J'ai donc créé mon blog avec Octopress pour la simplicité, la solution rbuste de blogging et les performances qu'il offre tout en nécessitant de faible coût (voire nul) de fonctionnement. A titre d'exemple, voici comment je publie un article :

- ouvrir un [gist](https://gist.github.com/) au format `markdown` (`.md`) pour pouvoir travailler dessus de n'importe où, le faire corriger, etc.
- Une fois corrigé et révisé je me connecte sur ma machine, me place dans le répertoire où tout le code du blog est versionné (`git`) et lance `rake new_post["Mon titre d'article"]`
- J'ouvre le fichier fraîchement généré, je change les quelques options de configuration (tags, commentaires actifs ou non ?, description, etc.) et copie/colle l'article
- `rake gen_deploy`

# Pour aller plus loin
Dans un prochain article, je listerai les commandes que j'utilise le plus et expliquerai, entre autres, comment :

- j'ai installé Octopress sur mon environnement (Ubuntu 12.04)
- bien choisir sa solution d'hébergement (gratuite !) et pourquoi j'ai choisi `alwaysdata.net` 
- bien paramétrer le nom de domaine avec la solution d'hébergement
- poster un article, modifier les méta données
- ajouter une nouvelle page
- franciser tous les termes, malheureusement, *"en dur"* dans le code
- corriger les *bizarreries* qui ne sont pas encore corrigées dans la branche principale (`meta description` et `keywords`)
- utiliser `git` pour les tâches courantes