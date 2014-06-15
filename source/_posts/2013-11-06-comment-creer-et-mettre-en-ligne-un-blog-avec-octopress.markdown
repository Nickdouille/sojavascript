---
layout: post
title: "Comment créer et déployer un blog avec Octopress ?"
date: 2013-11-06 00:19
comments: true
categories: [blog, octopress, tutoriel]
keywords: blog, octopress, comment, créer, déployer, mettre en ligne, héberger
---
*sur Ubuntu et hébergement alwaysdata*

* TOC
{:toc}

Comme je l'ai dit dans le premier post [Pourquoi créer son blog (de geek) avec Octopress ?]({{site.url}}/blog/2013/09/09/pourquoi-creer-son-blog-de-geek-avec-octopress/), il ne faut pas avoir peur de taper quelques lignes de commande pour gérer le blog. Aucune interface graphique n'est à disposition.
Octopress a besoin de quelques prérequis pour fonctionner :

- [git](http://git-scm.com/) pour récupérer Octopress, le mettre à jour et versionner ses fichiers
- Ruby 1.9.3 utilisant une machine virtuelle (par exemple [RVM](http://octopress.org/docs/setup/rvm))

Pour le reste, comme chaque environnement est spécifique, le mieux est de lire la [documentation](http://octopress.org/docs/setup/) très rapide et claire.
Cependant, si vous êtes, comme moi, sous Ubuntu (12.04), voici comment j'ai procédé (fin août 2013) :
<!--more-->

# Installation des dépendances (Git, RVM, Ruby)

    # Installation de git
    sudo apt-get install git-core
    
    # Installation de RVM (bien suivre les étapes)
    curl -L https://get.rvm.io | bash -s stable --ruby
    
    # Installation de Ruby 1.9.3
    rvm install 1.9.3

    # Indiquer à rvm d'utiliser Ruby 1.9.3
    [[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm"
    rvm use 1.9.3
    
    # Récupérer le gestionnaire de paquets Ruby (équivalent de npm pour Node par exemple)
    rvm rubygems latest
    
    # Vérifier que la version de Ruby est bien la 1.9.3
    ruby --version
    
# Installation d'Octopress

    # Nommer le répertoire cible par le nom du blog (dans mon cas : sojavascript)
    git clone git://github.com/imathis/octopress.git sojavascript
    
    # On se met dans le répertoire fraîchement créé qui est d'ailleurs versionné avec git
    cd sojavascript
    # Un message demandera si vous voulez faire confiance au fichier .rvmrc (il indique quelle version de Ruby utiliser. En l'occurrence, la version 1.9.3)
    yes

    # Octopress dépend de packages (gem) tiers. Il faut installer la gem "bundler" (équivalent de Bower pour Node) qui va inclure ces dépendances au projet (listées dans le fichier Gemfile)
    gem install bundler
    
    # Installation des dépendances
    bundle install

Pour le moment, je n'ai rien fait de plus (si ce n'est expliquer en français) que ce qui est indiqué sur [la page d'installation](http://octopress.org/docs/setup/) d'Octopress.

# Configuration du blog et de l'hébergement

### Personnalisation du blog

A ce stade, Octopress est installé mais le blog n'est pas encore généré. En effet, il va falloir paramétrer les variables "d'environnement" afin qu'il soit à notre image ! Examinons les dossiers et les deux fichiers de configuration importants :

    |_ .themes
    |_ plugins
    __ _config.yml
    __ Rakefile
    
    # Des tas d'autres fichiers de configuration (git, gem, config ruby, etc) non nécessaires pour une personnalisation basique
    
- .themes : Par défaut, il n'y a que le thème "classic" mais d'autres [peuvent être installés](https://github.com/imathis/octopress/wiki/3rd-Party-Octopress-Themes).
- plugins : Par défaut, les utilitaires de base inclus dans Octopress qui apportent des fonctionnalités intéressantes telles que générer les catégories du blog, intégrer des fiddle / gist / codeblock dans les articles, embarquer des vidéos, etc
- _config.yml : ce fichier recense les variables d'environnement nécessaires à la personnalisation du blog
- Rakefile : ce fichier définit toutes les tâches de gestion du blog (pour installer un thème, pour générer le blog, le déployer, etc) et les informations de l'hébergement

Ouvrir le fichier `_config.yml`. Il est très compréhensible et les variables parlent d'elles-mêmes. On y configure, entre autres, le format de date, nos identifiants de réseaux sociaux, le système de commentaires des posts.

### Configuration de l'hébergement

Encore une fois, si vous n'avez pas choisi la même solution que moi, la [documentation Octopress](http://octopress.org/docs/deploying/) est très complète. J'ai choisi [alwaysdata](https://www.alwaysdata.com/) car c'est gratuit pour stocker ce type de blog, on peut se connecter via ssh (très important pour Octopress) et il propose moults technologies intéressantes (Mongo, Couch, Rails, Django par exemple).

Une fois inscrit, dans le [panneau d'administration SSH](https://admin.alwaysdata.com/ssh/), il faut cocher la case pour activer SSH.

    # Ensuite, se connecter via ssh :
    ssh user@ssh.alwaysdata.com
    
    # Créer le répertoire qui contiendra le blog. Dans mon cas :
    cd ~/www/
    mkdir sojavascript

Revenir dans le [panneau d'administration SSH](https://admin.alwaysdata.com/ssh/) afin de définir le répertoire `home`. Ainsi, à chaque connexion, on démarrera directement de ce dossier. (Dans mon cas : `/www/sojavascript`)

Dans le [panneau d'administration des sites](https://admin.alwaysdata.com/site/), il faut paramétrer le blog :

- le répertoire qui contiendra le code du blog. Dans mon cas : `/www/sojavascript/`
- les DNS attachés à l'hébergement (peu importe d'où ils viennent, je les ai pris chez OVH). Dans mon cas : `sojavascript.com`, `sojavascript.fr` 

Ouvrir le fichier `Rakefile` afin de configurer l'hébergement et renseigner les informations. [Dans mon cas](https://github.com/Nickdouille/sojavascript/blob/master/Rakefile#L7) :

    ssh_user       = "cmoreau@ssh.alwaysdata.com"
    ssh_port       = "22"
    document_root  = "~" # Car j'ai paramétré par défaut le répertoire HOME lors de la connexion SSH
    rsync_delete   = true
    rsync_args     = ""  # Any extra arguments to pass to rsync
    deploy_default = "rsync"

# Génération et déploiement du blog

Avant de générer le blog, il faut lui choisir un thème. Par défaut, Octopress inclut un thème classique mais d'autres peuvent être utilisés selon les goûts et les couleurs de chacun.

    rake install # équivaut à rake install['classic']. Remplacer classic par le nom d'un autre thème le cas échéant

Cela va tout simplement créer deux nouveaux dossiers qui vont être copiés à partir de `.themes/classic`

- sass : contient toutes les feuilles de style
- source : contient les fichiers de templates du blog

A ce stade, le blog a un squelette, on peut donc le générer (css à partir de sass, html et JavaScript à partir des templates).

    # Génération du blog
    rake generate

Un nouveau dossier est créé : `public`. Il contient donc le blog statique qui sera déployé sur le serveur d'hébergement.

    # Déploiement du blog
    rake deploy
    
A noter que `rake gen_deploy` est un alias pour réaliser les deux opérations ci-dessus.

# Conclusion

Si tout s'est bien passé, votre blog statique propulsé par Octopress est disponible sur le net ! 

D'autres articles sur [Octopress]({{site.url}}/blog/categories/octopress/) suivront, notamment :

- profiter de la puissance de Git
- poster un article, modifier les méta données, ajouter une nouvelle page
- franciser tous les termes, malheureusement, *"en dur"* dans le code
- corriger les *bizarreries* qui ne sont pas encore corrigées dans la branche principale (`meta description` et `keywords`)