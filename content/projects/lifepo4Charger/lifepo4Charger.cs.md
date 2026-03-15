---
title: "LiFePO4 DIY nabíječka"
date: 2025-08-25T11:00:00+02:00
draft: true
toc: false
images:
tags:
  - 3D printing
  - Soldering
---
Jeden z mých prvních projektů, který zahrnuje pájení a skutečný návrh výrobku! Alespoň pro mě.

Proč LiFePO4? Proč ne obyčejné LiPo? Protože kdybych to zvoral, tak by došlo k nečekanému ohňostroji.

## Řešení budoucího problému
Rád bych si vyrobil bateriovou banku LiFePO4, pomocí které bych mohl napájet nejen svůj telefon a notebooky s USB-C PD, ale také vlastní nástroje, notebooky bez USB-C PD a elektrické nářadí. Je pochopitelné, že se jedná o velký projekt, takže nyní vyrábím „podpůrné“ prvky, které mi pomohou. Jak jsem již zmínil výše, nebudu používat LiPo, protože se jedná o DIY projekt, a proto je pro mě klíčové, zda to bude zábavný projekt pro mě, nebo pro hasiče.

Abych trochu osvětlil tuto budoucí powerbanku:
 - Normální porty USB-A a USB-C s PD [100 W]
 - Variabilní výstup (pro notebooky, nářadí, vlastní nástroje)

Protože chci, aby byl tento projekt připravený na budoucnost, bude tato powerbanka univerzální. Důvodem pro 100 W u USB-C je přenosná páječka, kterou bych rád měl s sebou jako EDC. Variabilní výstup, opět se opakuji, je určený pro notebooky, které lze nabíjet pouze přes konektory typu barrel, a pro nabíjení elektrického nářadí nebo dokonce pro jeho napájení z něj.

# Komponenty
Všechno jsem koupil na laskakit.cz, českém webu pro kutily. Žádný sponzor!
 - [Držák baterie](https://www.laskakit.cz/bateriovy-box-1x18650-do-dps/)
    - Mohl jsem si ho vytisknout na 3D tiskárně, ale stojí 20 Kč a ušetřil sjem na elektřině 
 - [Modul desky USB-C PD](https://www.laskakit.cz/laskakit-usb-c-pd-ch224k-prepinac-napajeciho-napeti/)
    - Opravdu skvěle vypadající deska a navíc levná. Lze na ní nastavit vstupní napětí!
 - [Nabíječka baterií LiFePO4/LiPo (TP5000)](https://www.laskakit.cz/nabijecka-li-ion-clanku-tp5000--2a-lifepo4-lithium/)
    - Jediná nabíječka LiFePO4 baterií, kterou měli. Upřímně řečeno, žádný jiný důvod.
## Pájení
Na desku USB-C PD jsem připájel šroubovací svorku. Myšlenka je, že kdybych ji někdy chtěl rozebrat, tak aby to bylo jednodušší.

Také jsem na nabíječku připájel dodanou LED diodu, která signalizuje, co se právě děje. Podle mého názoru mohli být vodiče trochu více popisné, protože jsem si musel přečíst PDF dokumentaci k TP5000 a vyhledat vodiče, abych mohl LED diodu připájet správně. Nemyslím tím připájet vstup na GND, ale připájet správnou barvu pro správný stav.

Kromě toho jsem na držák baterie připájel nějaké silnější vodiče. Přebytečné vodiče z doby, kdy jsem instaloval LED pásku pod linku v kuchyni. 
## Návrh
Stejně jako u modulárního pouzdra pro Raspberry Pi Zero 2W, jsem návrh vytvořil tak, že jsem na ně s trochou fantazie umístil komponenty.

Obecná myšlenka byla umístit desku USB-C PD s nabíječkou na sebe. Nabíječka byla prakticky na stejné úrovni jako horní část šroubového terminálu.

Teď přišel čas na kreslení. Prostě jsem umístil komponenty na papír, obkreslil je a začal navrhovat kryt.