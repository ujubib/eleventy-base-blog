---
title: "Inventaire Blot html : découverte (et ajout) de la balise `<details>`"
description: This is a post on My Blog about agile frameworks.
layout: layouts/post.njk
date: 2021-04-04T22:00:00.000Z
tags:
  - html
  - blot
  - regex
---
La balise `<details>` est merveilleuse :  
Elle permet de replier le contenu. Idéal pour les notices de monuments. 
 
Regex pour remplacer les `<h3>` en `<details>` (en conservant les attributs) dans l'[inventaire Blot html](https://inventaire-blot.netlify.app/final2.html) [`final2.html`].

<details><summary><span style="font-size:1.3em;font-style:italic;color:deeppink">Ce qu'on a :</span></summary>

```html
<h3 id="ahaxe---bilgotza-mendebalde-1---tumulus-cromlech"><span class="spatial">Ahaxe</span> - <span class="coverage">Bilgotza Mendebalde</span> 1 - <span class="type">Tumulus-cromlech</span></h3>

<details>
    <summary>Details</summary>
    Something small enough to escape casual notice.
</details>
```
</details>


#### Regex 1

|Rechercher|Remplacer|
|---|---|
|`<h3($1)>($2)</h3>`|`<details($1)><summary>($2)</summary>`|


#### Regex 2
|Rechercher|Remplacer|
|---|---|
|`</section>`|`</details></section>`|






#Yapluka
