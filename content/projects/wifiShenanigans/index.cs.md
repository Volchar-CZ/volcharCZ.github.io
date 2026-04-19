+++
title = "Raspberry Pi Zero 2W wifi radioteleskop 1#"
description = "aneb když mi někdo dá do ruky směrovou anténu..."
type = "posts"
tags = [
    "Interests",
    "Linux",
    "Shenanigans",
]
toc = true
date = "2026-03-12T10:00:00+02:00"
categories = [ "Technial" ]
series = []
[ author ]
  name = "Volchar"
+++
Fascinovalo mě [video](https://www.youtube.com/watch?v=aeah3fFYlnA) od "The Thought Emporium", kde postavili funkční 2.4GHz radioteleskop, který použili k skenování jejich prostředí a tvorbě mapy (grafu) síly signálu/pozice. Tak jsem si řekl, proč to nezkusit? 

### Proč?
**Proč ne?**

Koupil jsem si MIMO čtvercovou venkovní anténu o rozměrech 25 cm², lehce pofidérní WiFi USB adaptér o dvou odnímatelných anténách, 2x rp SMA kabel a posledně 2x rp SMA->TNC adaptér. Celé mě to vyšlo na necelých **`1 700,- Kč [~70€]`**. Na konkrétních dílech nezáleží, aneb proč tu nemám linky, tak jako u blogu o [nabíječce](../lifepo4Charger/index.cs.md). Jádro celého projektu je **směrová anténa**.

### Směrová anténa
Existuje mnohé antény, které by se na tenhle malý projektík hodili. Měl jsem realisticky na výběr dva druhy:

  - `Sektorová anténa` = _Rádoby "pouliční lampa"_
  
    - Tenhle druh se hodí pro pokrytí širší oblasti.

  - `Směrová anténa` = _Rádoby "reflektor na fotbalovém stadionu"_

    - Tenhle druh se hodí pro konkrétní spojení mezi dvěma body. Typické pro propojení dvou budov.

A následně designy a všemožné proměnné.

Na tenhle projekt se hodila _směrová anténa_, protože de facto potřebuji úzký rozptyl, ale ne až tak úzký, abych to nemusel vyměřovat na azimuty jak minomet. Dá se říct, že jsem hledal _směrovou sektorovou anténu_ a kupodivu jsem i ji našel.

#### Vybraná anténa

Tenhle konkrétní model, od nějakého polského bezejmenného výrobce, má dva TNC konektory, jelikož dokáže obsáhnout *obě polarizace 2.4GHz*.
Dle informací, které jsem našel na internetu, drtivá většina normálních "wifinových" zařízení používá **horizontální** polarizaci. To má i moje anténa vyznačené. Naštěstí to já řešit nemusím, jelikož má druhý TNC konektor na **vertikální** polarizaci. Realisticky můžu mít zapojenou jen jeden konektor a jen se ujistit, že to držím správně, ale nerad se v neznámých vodách svévolně vzdám možnosti. Taky jiné plackotény byly za stejné peníze, né-li dražší.

### WiFi adaptér
Nečekal bych, že hledání USB WiFiny, která má 2 odnímatelné antény bude taková práce.

Kritéria byly jasné. 2 odnímatelné antény. Toť vše.

Hlavním důvodem, proč jsem nezbastlil náhodné dvojanténní WiFi usbčko je ten, že moje pájecí schopnosti nejsou perfektní a u rádio věcí je lepší, když to je dělané eňoňůňo, jinak šumu a malému zisku zdar.



