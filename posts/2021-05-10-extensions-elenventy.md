---
layout: layouts/post.njk
title: Extensions elenventy
date: 2021-05-09T22:00:00.000Z
tags:
  - eleventy
---

### Netlify CMS

- [x] `css` pour preview
- [x] interface `fr`
- [x] admin css
  - [Change “admin.css” to tweak a bit the CMS ui defaults](https://answers.netlify.com/t/change-admin-css-to-tweak-a-bit-the-cms-ui-defaults/17835)

### Eleventy plugins

- [x] toc

### Extensions à Markdown-it

- [ ] markdown-it-attrs 
  
  `{.classe}` `{attr=value}` `{#id}`...

  - billet : [11ty Markdown Attributes](https://dev.to/iarehilton/11ty-markdown-attributes-2dl3) - Hilton Meyer (dev.to)
  - Module `npm` : [markdown-it-attrs](https://www.npmjs.com/package/markdown-it-attrs)

### Commentaires

- [ ] [Staticman](https://staticman.net) : 
  - billet : [Building A Static Blog With Eleventy And Staticman](https://kabardinovd.com/posts/eleventy-staticman/)
- [ ] [utterances](https://utteranc.es/)
  - billet : [Add comments to your 11ty blog with utterances](https://dev.to/antopiras89/add-comments-to-your-static-blog-with-utterances-3jao) - Antonio Piras (dev.to)
- [x] hypothesis
  - [Embedding Hypothesis in Websites and Platforms](https://web.hypothes.is/help/embedding-hypothesis-in-websites-and-platforms/)
  - code collé dans `post.njk` :
  
```
<script type="application/json" class="js-hypothesis-config">
{
"showHighlights": false
}
</script>
<script async src="https://hypothes.is/embed.js"></script>

```

### Suite