---
title: Magyarország korfája, 1980-2022
lang: hu
categories:
tags:
---

# Notes

## Adattudományi projektek fő szakaszai (Steps in data sciences projects)

According to Hadley Wickham [Introduction – R for Data Science (2e)](https://r4ds.hadley.nz/intro.html#what-you-will-learn) "you start with **(1) data import** and **(2) tidying**. Next, you understand your data with an iterative cycle of **(3) transforming**, **(4) visualizing**, and **(5) modeling**. You finish the process by **(6) communicating** your results to other humans."

1. Importálás (import)
2. Tisztítás (tidying)
3. Átalakítás, újrakódolás (transforming)
4. Adatvizualizáció (visualizing)
5. Statisztikai modellezés (modeling)
6. Kommunikáció, prezentáció (communicating)

![pic](https://r4ds.hadley.nz/diagrams/data-science/base.png)


## Importálás

## Adatok forrása
Korévenkénti bontás:
[22.1.1.3. Népesség korév és nem szerint, január 1.](https://www.ksh.gov.hu/stadat_files/nep/hu/nep0003.html)
[Népszámlálás 2022 – A népesség főbb jellemzői (országos és területi adatok)](https://nepszamlalas2022.ksh.hu/eredmenyek/vegleges-adatok/kiadvany/)


Korcsoportok szerinti bontás:

- [nsz2022-1.1.2.xlsx](https://nepszamlalas2022.ksh.hu/eredmenyek/vegleges-adatok/tablazatok/nsz2022-1.1.2.xlsx)
- [Népszámlálás 2022](https://nepszamlalas2022.ksh.hu/eredmenyek/vegleges-adatok) - 5. slide 2011–2022

## Adattisztítás

Az adatok tisztítása a Libre Office Calc programmal történt tekintve, hogy xlsx formátumban töltöttük le. A tisztított ("tidy") csv formátumú adatok letölthetők [innen](https://github.com/zgfabian/data-and-scripts/blob/cc7a25ddc09513cc7531a1277bce7ddb87643b5d/korfa.csv ).

Az adattisztítás során a kvirtmínusz (emdash) `–` karaktert félvirtmínusz (endash) `-` karakterrel helyettesítettük. Megjegyzés: Linux alatt az emdash `alt + z` billenyűkombinációval hívható elő. A tisztítás tehát nyelvtanilag helytelen volt! Ugyanis a "kiskötőjel és a nagykötőjel különbsége bizonyos esetekben értelmi különbséget is hordoz:
Az „1985-1990” arra utal, hogy hozzávetőleg akkortájt valamikor (bár lehet, hogy 1984-ben vagy 1991-ben), az „1985–1990” pedig pontosan az adott időtartományra utal." [Gondolatjel és nagykötőjel – Wikipédia](https://hu.wikipedia.org/wiki/Gondolatjel_%C3%A9s_nagyk%C3%B6t%C5%91jel)
