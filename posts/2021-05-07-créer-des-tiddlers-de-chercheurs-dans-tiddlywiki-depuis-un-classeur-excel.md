---
layout: layouts/post.njk
title: Créer des tiddlers de chercheurs dans TiddlyWiki depuis un classeur Excel
date: 2021-05-06T22:00:00.000Z
tags:
  - TiddlyWiki
  - Excel
  - idHAL
  - idref
  - orcid
---
### Introduction

Je teste Obsidian depuis presque un an pour suivre la mode et parce que le ticket d'entrée est quasi nul quand on vient de 7 ans de WikiText (et le résultat excellent et bien plus 'portable'). 

En effet mon vrai amour de notebook est TiddlyWiki.

![logo TW]()

Ce n'est pas un 'vrai' wiki au sens où il n'est pas nativement collaboratif et ne gère pas les 'versions' de vos 'tiddlers' (entrées). C'est plutôt un notebook personnel avec des fonctions d'édition et de liens internes avancées (et très extensibles et personnalisables).

Il s'agit concrètement d'un seul fichier html 'gavé' de javascript. 

J'en créais un par conférence, atelier, formation... 

![dossier TW](/img/uploads/tiddly1.png)  

Aujourd'hui il m'en reste 3 "en production", dont un pour l'administration du portail HAL-e2s-UPPA (Université de Pau et des Pays de l'Adour). Ils sont sur le gitlab de l'université.  

[Je n'ai pas encore testé les versions `Node.js` mais ça à l'air merveilleux !]

### Empty TiddlyWiki

Je mets à disposition un TiddlyWiki vide avec les extensions qui me sont utiles (dont l'importateur Excel dont il va être question ici), décrites dans le tiddler 'Options'.

à télécharger ici : [empty_fr_5-1-22.html](https://git.univ-pau.fr/jrabaud001/tw/-/blob/master/empty_fr_5-1-22.html)  (7,27 Mo - Gitlab UPPA)

Ce fichier est directement utilisable, changez le nom et enregistrez vos modifications : vous avez un wiki.

### Les champs d'un Tiddler

![screenshot chercheur]()

Un 'tiddler' (tuile?) est une entrée du (tiddly)wiki. Il y a un champ 'text' où l'on écrit en wikitext (il y a un plugin markdown cependant), mais il y a aussi (et surtout pour nous) la possibilité d'ajouter (et d'éditer ensuite) autant de champs que l'on veut (par exemple : `labo`, `équipe`, `date d'entrée`, `idhal_s`, `idhal_i`, `idref`, `orcid`, `notes`...)

Ces champs sont mobilisables pour le tri, les listes, l'affichage dans des templates (par exemple un plugin BibTeX crée des tiddlers avec des champs 'bibtex').

![screenshot bibtex]()

Un autre plugin, [Dynamic tables](https://ooktech.com/jed/ExampleWikis/DynamicTables/) (installé dans mon `empty`), vous permet d'éditer (plus ou moins) simplement les champs dans un tableau de tiddlers (une ligne par tiddler, champs en colonnes), résultat d'une requête (sur tags ou sur champs 'customisés').

![screenshot Dynamic tables, idhal d'un labo]()

#### Le champs 'caption'

Sympathique pour les noms, s'affiche à la place du champ 'title' du tiddler dans les listes.

exemple :
- title : `Martin, Pierre`
- caption : `Pierre Martin`


### Le plugin [XLSX Utils](http://tiddlywiki.com/prerelease/editions/xlsx-utils/)

Le plugin [XLSX Utils](http://tiddlywiki.com/prerelease/editions/xlsx-utils/) permet de créer un tiddler par ligne avec des champs en colonne et les valeurs peuplées pour chaque tiddler créé.

![screenshot feuille excel]()

Un paramétrage adéquat du plugin va créer les bons tiddlers, avec les bons tags (un champs standard) et les bons champs 'customisés'.

![screenshot paramétrage]()

### Produire des listes en affichant/filtrant les champs

- des listes simples

```
code 1
```

![screenshot liste simple]()

- des listes html

```
code 2
```

![screenshot liste htm]()

- des tableaux html

```
code 3
```

![screenshot liste tableau html]()



