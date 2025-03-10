---
theme: seriph
addons:
  - slidev-addon-ultracharger
addonsConfig:
  ultracharger:
    inlineSvg:
      markersWorkaround: false
    disable:
      - metaFooter
      - tocFooter
NObackground: >-
  https://images.unsplash.com/photo-1511149755252-35875b273fd6?ixlib=rb-4.0.3&dl=leon-contreras-qpdfU6vehgs-unsplash.jpg&w=1920&q=80&fm=jpg&crop=entropy&cs=tinysrgb
background: /mountain.jpg
highlighter: shiki
routerMode: hash
lineNumbers: false
info: >
  ## Slidev ultracharger demo

  A doc / demo presentation for the ultracharger set of
  [Sli.dev](https://sli.dev) addons.

  It also acts as an experimental area for some features I can imagine.


  NB: [Source code
  available](https://github.com/twitwi/slidev-addon-ultracharger)
css: unocss
title: Deep Learning
subtitle: Convolutional Neural Networks
date: 03/02/2025
venue: HSE
author: Alexey Boldyrev
---

# <span style="font-size:28.0pt" v-html="$slidev.configs.title?.replaceAll(' ', '<br/>')"></span>
# <span style="font-size:32.0pt" v-html="$slidev.configs.subtitle?.replaceAll(' ', '<br/>')"></span>
# <span style="font-size:18.0pt" v-html="$slidev.configs.author?.replaceAll(' ', '<br/>')"></span>

<span style="font-size:18.0pt" v-html="$slidev.configs.date?.replaceAll(' ', '<br/>')"></span>

<div>
<br>
<span style="color:#b3b3b3ff; font-size: 11px; float: right;">Image credit: ‘Glacier du Rhone au haut du Valais’<br> by Claude Niquet after Jean Séraphin Désiré Besson<br>
<a href="https://wellcomecollection.org/works/e3y95vtv">https://wellcomecollection.org/works/e3y95vtv</a>
</span>
</div>

<style>
  :deep(footer) { padding-bottom: 3em !important; }
</style>

<!--
NB: This demo uses a custom syntax (using preparser extensions), with all the @@@@.
-->

---
src: ./slides/0_introduction.md
---

---
src: ./slides/1_convolutional_layer.md
---

---
src: ./slides/2_pooling_layer.md
---

---
src: ./slides/3_convolution_mathematically.md
---

---
src: ./slides/4_CNNs.md
---

---
src: ./slides/5_semantic_segmentation.md
---

---
src: ./slides/0_end.md
---
