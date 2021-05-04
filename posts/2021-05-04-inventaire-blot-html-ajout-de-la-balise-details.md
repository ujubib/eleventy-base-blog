---
layout: layouts/post.njk
title: "Inventaire Blot html : ajout de la balise `<details>`"
date: 2021-05-03T22:00:00.000Z
tags:
  - html
  - blot
  - regex
---
***
La balise `<details>` est merveilleuse.  
Elle permet de replier son contenu. Idéal pour les notices de monuments (j'aurais du la connaître plus tôt). --> `<details>` sur [MDN Web Docs](https://developer.mozilla.org/fr/docs/Web/HTML/Element/details).
***
(Schéma) de regex pour remplacer les `<h3>` en `<details>` (en conservant les attributs) dans l'[*inventaire blot html*](https://inventaire-blot.netlify.app/final2.html) [`final2.html`].

### Regex 1
<div style="margin-left:2em">

|Rechercher|Remplacer|
|---|---|
|`<h3($1)>($2)</h3>`|`<details($1)><summary>($2)</summary>`|

</div>


### Regex 2
<div style="margin-left:2em">

|Rechercher|Remplacer|
|---|---|
|`</section>`|`</details></section>`|

</div>


#Yapluka