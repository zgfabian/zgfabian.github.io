---
title: R csomagok megőrzésre
lang: hu
categories: R
tags: packages
---


## A csomagok elhelyezése polcokon

Az adattudományi projekteknek öt fő szakaszát különböztette meg programozási szempontból Hadley Wickham[^1]:

[1]:[Introduction – R for Data Science (2e)](https://r4ds.hadley.nz/intro.html#what-you-will-learn) "you start with **(1) data import** and **(2) tidying**. Next, you understand your data with an iterative cycle of **(3) transforming**, **(4) visualizing**, and **(5) modeling**. You finish the process by **(6) communicating** your results to other humans."

1. Importálás (import)
2. Tisztítás (tidy)
3. Átalakítás, újrakódolás (transform)
4. Adatvizualizáció (visualize)
5. Statisztikai modellezés (modeling)
6. Kommunikáció, prezentáció (communicate)



![hadley-model]({{ '/assets/img/26-02-14-R-packages/hadley-model.png' |relative.url }})

![hadley-model]({{ site.baseurl }}/assets/img/26-02-14-R-packages/hadley-model.png)


## Importálás

rio, haven, foreign, readxl

## Tisztítás

tidyr, pivot,
summary
janitor
