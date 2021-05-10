---
layout: layouts/post.njk
title: Créer des tiddlers de chercheurs dans un TiddlyWiki depuis un classeur Excel
date: 2021-05-06T22:00:00.000Z
tags:
  - TiddlyWiki
  - Excel
  - idHAL
  - idref
  - orcid
---

### TiddlyWiki et moi

Je teste *Obsidian* depuis presque un an, un peu pour suivre la mode, un peu parce que le ticket d'entrée est quasi nul quand on vient de 7 ans de *WikiText* mais surtout parce que le concept de 'carnet de fichiers markdown' est extrêmement simple et bien plus *portable*. C'est très satisfaisant au final. 

Mais mon vrai systeme de notebook coup de cœur, c'est [TiddlyWiki](https://tiddlywiki.com).

Ce n'est pas un **vrai** wiki au sens où il n'est pas nativement collaboratif et ne gère pas les **versions** de vos *tiddlers* (entrées). C'est plutôt un notebook personnel avec des fonctions d'**édition** et de **liens internes** avancées (et très extensibles et personnalisables).

Il s'agit concrètement d'un seul fichier html *gavé* de javascript. 

Pour mes notes, j'en créais un par conférence, atelier, formation... 

![dossier TW](/img/TW-Excel/tiddly1.png)  

Aujourd'hui il m'en reste 3 "en production", dont un pour l'administration du portail HAL-e2s-UPPA (Université de Pau et des Pays de l'Adour). Ils sont sur le gitlab de l'université.

[Je n'ai pas encore testé les versions `Node.js` mais ça à l'air merveilleux !]

#### Empty TiddlyWiki

Je mets à disposition un TiddlyWiki vide avec les extensions qui me sont utiles (dont l'importateur Excel dont il va être question ici).

- à télécharger ici : [empty_fr_5-1-22.html](https://git.univ-pau.fr/jrabaud001/tw/-/blob/master/empty_fr_5-1-22.html)  (7,27 Mo - Gitlab UPPA)
  - Mes modifications sont décrites dans le *Tiddler* `Options`

Ce fichier est directement utilisable, changez le nom, enregistrez régulièrement vos modifications (*voir dans le panneau de configuration du wiki, roue denté*) : vous avez un nouveau Wiki (un *TiddlyWiki* autonome).

### Les champs d'un *Tiddler*

![Screenshot chercheur](/img/TW-Excel/TW-champsChercheurs.png)

Un *tiddler* (tuile?) est une entrée du (tiddly)wiki. Il y a un champ `text` où l'on écrit en wikitext (*il y a un plugin markdown cependant*), mais il y a aussi (et surtout pour nous) la possibilité d'ajouter (et d'éditer ensuite) autant de champs que l'on veut (par exemple : `labo`, `équipe`, `date d'entrée`, `idhal_s`, `idhal_i`, `idref`, `orcid`, `notes`...)

Ces champs sont mobilisables pour le tri, les listes, l'affichage dans des templates (par exemple le plugin BibTeX permet à la lecture de fichiers `.bib` la création de tiddlers avec des champs de type `bibtex-propriété`).

![Gabarit de citation d'un article bibtex](/img/TW-Excel/tw-bibtex-gabcitart.png)  
Tiddler 'GabCitArt' : template pour afficher un tiddler bibtex (titre du tiddler = clé bibtex) dans un autre tiddler avec une syntaxe de type transclusion/tempate.

![Screenshot Biblio Robin de Mourat]()

Un autre plugin, [Dynamic tables](https://ooktech.com/jed/ExampleWikis/DynamicTables/) (installé dans mon `empty`), vous permet d'éditer (plus ou moins simplement) les champs dans un tableau de tiddlers (une ligne par tiddler, champs en colonnes), résultat d'une requête (sur tags ou sur champs 'customisés').

![screenshot Dynamic tables, idhal d'un labo](/img/TW-Excel/tw-dynamictables.png)

le code : 
- `<<RawTable` : appel d'une macro installée par le plugin *Dynamic Tables*
- `[tag[LATEP]tag[publiant]]` : filtre les **tiddlers** à afficher (en lignes, *RawTable*)
- `[[idHAL_i]][[idHAL_s]][[ind]][[orcid]][[idref]][[note]]` : liste les **champs** à afficher/éditer (en colonnes), même si ces champs n'existent pas encore dans les tiddlers !!!

#### Le champs 'caption'

Sympathique pour les noms, s'affiche à la place du champ 'title' du tiddler dans les listes (tri sur le titre).

exemple :
- title : `Martin, Pierre`
- caption : `Pierre Martin`


### Le plugin [XLSX Utils](http://tiddlywiki.com/prerelease/editions/xlsx-utils/)

Le plugin [XLSX Utils](http://tiddlywiki.com/prerelease/editions/xlsx-utils/) permet de créer un tiddler par ligne avec des champs en colonne et les valeurs peuplées pour chaque tiddler créé.

![screenshot ou lien feuille excel]()

Un paramétrage adéquat du plugin va créer les bons tiddlers, avec les bons tags (un champs standard) et les bons champs *customisés*.

![screenshot paramétrage](/img/TW-Excel/tw-xlsxutils.png)

### Produire des listes en affichant/filtrant les champs

#### Des listes simples :

- ici un seul champs affiché (`idhal_s`), avec retour à la ligne (`<br/>`)
- filtre sur les tiddler qui ont et le tag `CRAJ` et le tag `publiant` et dont le champs `idhal_s` contient une valeur.

```html
<$list filter='[tag[CRAJ]tag[publiant]has[idhal_s]]'>
{{!!idhal_s}}<br/>
</$list>
```

![screenshot liste simple](/img/uploads/tw-listesimple.png)

#### Des listes html

- ici utilisation des champs `idhal_s` et `title`
- balisage `code` pour que le html ne soit pas interprété par TW
-  pour produire une liste de liens vers des fichiers de type `idhal.html` dans un sous-répertoire `/html`, à coller dans un fichier html de type `indexLabo.html`
- ces fichiers de type `idhal.html` peuvent avoir été produits en réponse à l'API de HAL ;) 

```
<$list filter='[tag[CRAJ]tag[publiant]has[idhal_s]]'>
`<li><a href="html/`{{!!idhal_s}}`.html">`{{!!title}}`</a></li>`<br/>
</$list>
```

![screenshot liste htm](/img/uploads/tw-listehtml.png)

- des tableaux html

```
code 3
```

![screenshot liste tableau html]()



