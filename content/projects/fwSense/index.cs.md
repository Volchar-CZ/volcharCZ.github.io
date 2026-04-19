+++
title = "OPNSense firewall"
description = "\"Paranoidní přežívají\" - Harold Finch (Lovci zločinců)"
type = "posts"
tags = [
    "Linux",
    "Interests",
    "Sysadmin",
    "Portfolio",
]
toc = true
date = "2026-04-16T22:00:00+02:00"
categories = [
    "Homelab",
    "OPNSense",
    "Portfolio",
]
series = []
[ author ]
  name = "Volchar"
+++

## Proč

Mnohdy začínám tím, že píši ***Proč***. I když to je jeden z projektů, který má reálný využití, tak si jej ale retrospektivně nemůžu odůvodnit jinak než "je to hustý". Zvláštní pocit.

Z technického pohledu:

 - Prohloubení mých znalostí v rámci OPNSense, síťování a OpenBSD
 - Vystoupení z komfortní zóny do neznáma
 - Lze říct, že nasazuji „enterprise“ řešení do mé domácí sítě/homelabu
 - Reálná ochrana mé sítě (Suricata IDS)

Přes tyto pádná argumenty stejně nevidím ten racionální a pragmatický důvod „proč“. 

Takhle. Celkový důvod, proč jsem se vůbec rozhodl nad firewallem, je ten, že chci směrovat VPNko z mé VPSky na můj domácí server. Jelikož otevírám cestu do mé interní sítě, tak se vystavuji také rizikům. Jak moc vážně beru svoje soukromí/bezpečnost už jaksi šlo vidět v mém příspěvku, kde ukazuji jak [zabezpečuji moji VPSku](../myVPS/index.cs.md). 

**Má domněnka** je taková, že firewall, který bude dirigovat tento orchestr skrze **surikatu** a **Pi hole s listy známých hrozeb**, bude další překážkou pro potencionálního útočníka.

 - Kdybych měl takovouto bezpečnost sítě (*z internetu k mému serveru*) přirovnat k míře destrukce:

	1. Pro začínající firmu, která nebere bezpečnost na lehkou váhu?  
    **1 či 3 střely z 152mm houfnice z tanku čtenářovo libosti.**
	2. Pro fanatika do Linuxu, který stejně vypíná porty na VPSce skrze UFW a má v plánu jen hostovat herní servery zda-li vůbec?  
    **Prohození váhy protonu s elektronem.** Jakou paseku by tohle nadělalo? Nevím.

To se snažím tady právě popsat. Je to jako použít motor proudové stíhačky jako gril. Pro osobní použití to je víc něž dost.  
Na druhou stranu **dalo mi to cenné zkušenosti**, **kontrolu nad moji sítí** a jak píšu, je to **další blokáda pro potencionální kyberšmejdy**.  

Aneb proč celý tento projekt vedu pod myšlenkou:

> *\"Paranoidní přežívají\" - Harold Finch (Lovci zločinců)*

Reálný důvod, proč jsem do tohoto projektu investoval byl ten, že mě prostě tyhle věci fascinují.  
Ano, nijak víc ušlechtilé to doopravdy není ;)


## Hardware
### PC
Jedná se o **HP Thin client T630**. Kupoval jsem ho na bazoši za 800,-kč [~33,-€]. 

![T630](img/T630.jpg)

A hnedle se dostáváme k prvnímu rádoby zádrhelu.

Prodávající měl inzerát na **T620**, což je starší, pomalejší a zejména **UŽŠÍ** model s **JINÝM** interním rozhraním. Ale dostal jsem **T630**, což je mladší (o 3 roky), rychlejší (4 jádra) a trošku **VYKRMENĚJŠÍ** model s **JINÝM** interním rozhraním.

Počítač jsem koupil před Velikonoci [**2.4.2026**] a s pánem jsme se domluvili, že mi to pošle přes Zásilkovnu. Chudáci pracují i přes svátky, jelikož už v sobotu jsem měl počítač tady, ale než se k tomu dostaneme..

Abych využil času co nejefektivněji, tak jsem si na Allegru ten samý den hnedle koupil PCIe-Mini->RJ45 port, jelikož inzerovaná varianta má jen jeden ETH port.

Jenže v sobotu jsem byl chytřejší.

 - T620: Má PCIe-Mini
 - T630: Má M.2, konkrétně 3x (v jednom byl Intel WiFi NIC, 2x na disky)

A já koupil PCIe-Mini->RJ45..

Po rychlé vratce jsem hnedle objednal M.2 na RJ45 a bohužel jim to dost trvalo..

Když jsem byl tak chytrý, že jsem využil volného času na nákup PCIe-Mini adaptéru, tak jsem se rozhodl použít T630 jako testovací platformu pro můj možný přechod. *potencionální další příspěvek?!*

#### PC specifikace

\+malá ochutnávka budoucího mého konání...
![T630Specs](img/T630Fastfetch.png)

Jelikož jsem zkoušel NixOS (Na separé disku), tak mě ani nenapadlo udělat benchmark či jiné fajnové prkotinky. 

Po aktualizaci a výslovné změny driveru ve prospěch 'amdgpu' počítač celkem zvládal běžné projíždění internetem.

FHD videa na fullscreenu ale už dávali zabrat. Osobně si myslím, že to bylo tím, že musel "rozjet" 2K monitor. Pak jsem rozlišení stáhl na FHD, ale už jsem nezkoušel žádné video. Domnívám se, že 'h264ify' by mohl asi pomoct.
___

#### Instalace druhého rozhraní

**T630** jsou dělané s vícero konfiguracemi a já měl konfiguraci "Wi-Fi NIC". Čili v zadním M.2 jsem měl další Intel Wi-Fi NIC, který mi zabírá místo. Nemluvě o tom, že tam už je předělaná pozice pro rozšiřující kartu. Co jsem viděl letmo na internetu, tak lze mít VGA, Eth atp.

***foceno špatně kvůli rozmazání údajů na NIC***
![T630 přiblížení na Intel Wi-Fi M.2 kartu](img/T630IntelNIC.jpg)

Ten 16ti pinový konektor hned pod M.2 pozicí,má text 'VGA'. Typuji, že to je ten port který by použili při konfiguraci s VGA portem.

Chtěl bych také pochválit HPčko. Nejsem žádný zastánce nemodulárních počítačů v roli PC. 

**!PC MUSÍ BÝT MODULÁRNÍ PRO OPRAVITELNOST!**

Jest můj názor...  
Ale tenhle ten kousek má nejen vyměnitelné RAMky, ale i  úložiště (viz zmínka o dalších 2 M.2 pozicích) v rámci ne-desktopového počítače, který ještě k tomu má toolless otevírání a výměnu SSD a RAMek. Suprový design. 

Ano, APU *(CPU+iGPU)*, zdroj, MoBo je vše v jednom, takže kdyby něco z toho odešlo, tak jde celý počítač. Můj argument je takový, že v tomto případě to dává smysl, jelikož Thin client počítače mají být úsporné, jak velikostí, tak i výkonem/elektřinou. Kdybych chtěl modularitu, tak bych musel do předražených ITX MoBo a skříní.  
Kdybych to měl brát až jako takové dogma, tak to bych si ani nemohl používat Raspberry Pi. 

Být to počítač o velikosti normálního desktopu s proprietárními kousky HW(např.: Dell počítače), tak to už bych piskoval.

**ZPĚT K OPNSENSE**

NIC jsem normálně vyšrouboval a vyměnil jsem ho za RTL Eth port. RTL - Realtek je celkem klíčový detail, jelikož OpenBSD s Realtekem se moc nekamarádí. 

Před objednáním tohoto adaptéru jsem se díval na internetu, zdali můj vybraný port funguje.

```BASH
:~$ pciconf -lv
    class      = network
    subclass   = ethernet
re1@pci0:2:0:0:	class=XX rev=XX hdr=XX vendor=0x10ec device=XX subvendor=0x10ec subdevice=XX
    vendor     = 'Realtek Semiconductor Co., Ltd.'
    device     = 'RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet Controller'
```
Jelikož to je nějaký noname, tak zde máte výpis, kdybyste chtěli replikovat můj postup. Nedělejte to ;)

Následně jsem našrouboval samotný RJ45 port do šasi. Musel jsem trošku ohnout takovýma kovovýma packama, ale vešlo se to tam jak kdyby to tam bylo pro to dělaný.

![T630 ukázka našroubovaného portu](img/T630ExPort.jpg)

## Software
### OPNSense
OPNSense je otevřenější varianta **pfSense**.  
Tak jsem jsem psal v [proč](#proč), neměl jsem moc důvodů proč pro FW, natož už výběr konkrétního OS.

Líbila se mi myšlenka více otevřeného ekosystému, který je vyvíjen v Evropě. V rámci funkcionalit, které se teprve musím naučit, si myslím, že pro moje použití by vystačili obě varianty.

#### Instalace
Celkem proběhla v pořádku, ale měl jsem jeden "zajímavý" moment.

Když jsem poprvé nainstaloval OPNSense, tak jsem omylem nechal flashku v počítači a po restartu jsem se načetl z ní. To jsem nevěděl, ale přišlo mi divné, že mi nefungovalo nastavené heslo pro **roota**. Po zjištění, že tam mám furt flashku, jsem ji odpojil a radši mi nefungovalo žádné heslo. Jelikož jsem nechtěl hledat příčinu, tak jsem to prostě reinstaloval.

![T630 OPNSense instalace](img/T630OPNSenseInstall.jpg)

Následně mi zbývalo jen počkat na adaptér. Díky magii blogů se tedy přesuneme do budoucna.

![T630 OPNSense ukázka funkčnosti externího portu](img/T630OPNSenseRE1Check.jpg)

Po nádherném zjištění, že Realtek si umí kamarádit s OpenBSD, jsem se konečně mohl vrhnout na nastavování.

#### Nastavení
![OPNSense dashboard](img/OPNSenseLandingPage.png)
Nejdříve jsem musel zařídit, abych měl internet, což znamenalo:

 1. Vyrobit/nastavit DHCP server
    1. Nastavit rozhraní - re0 a re1  
    Rozdělení co je WAN co je LAN.
    2. Nastavit IP rozsah mé sítě (něco jiného než 1.x)  
    Ať nekoliduji s IP rozsahem "wifiny".

 2. Nastavit DNS
    1. Nastavit IP adresy povolených DNS překladačů  
    Ať můžu překládat google.com na 142.251.209.14 .
    2. Zajistit, ať můj počítač a server umí brát DNSko z FW  
    Abych neměl "it was DNS" problém.

##### LAN
Zde to bylo v GUIčku jednoduché. Reálně mi stačilo jen nastavit jiný rozsah, než má moje "wifina".

![OPNSense IPv4](img/OPNSenseLanIPv4.png)

A následně samotné DHCP. Pro moji **ne**znalost OPNSense a služeb, tak jsem se rozhodl pro "defaultní" řešení, a to "Dnsmasq DNS & DHCP". Jsou tu i jiné služby, vykonávající stejné činnosti.

##### WAN
WAN by dal trošku zabrat, a opět, kvůli banalitě.

Za boha se mi nechtěl "zapnout" port. Tím myslím, že jsem měl '```status: no carrier```'. Ať jsem dělal co jsem dělal v GUI či v konzoly skrze SSH, **NIC NEPOMOHLO**.

Budu upřímný, zde jsem využil AI, protože jsem byl bezradný. AI mi řeklo, že po všech mých testech to je na 99% DOA (dead on arrival) adaptér. Pravda je, že jsem to neměl kde vyzkoušet, jelikož nikde jinde nemám takhle lehce dostupný M.2. Já tomu nechtěl věřit. Tak jsem to **vypl**, rozebral a důkladně jsem multimetrem projel ***PIN CO PIN*** na kabelu propojující M.2 motherboard s RJ45 daughterboard. Vše vypadalo že ok. Tak jsem to pozapojoval a zkusil **zapnout** a voilà.. **```status: active```**.

Co to vidím zvýrazněně? **vypl** a **zapnout**? Neboli... ***!? restartovat ?!***

Náš učitel L. M. na hodinách EaA, Elektrotechnika a Automatizace, říkal, že nejdříve musíme říct **A**, a pak můžeme vyprávět od **B**.

Mělo mě to napadnou dřív, zejména když Realtek je nevyzpytatelný na OpenBSD.  
IT crowd scénka... prosím!

Jelikož mi FW sedí za "wifinou" (proč už někdo nevymyslel lepší název pro router/AP/modem kombo od ISPčka?), tak jsem jenom odškrtl ```Block private networks```.

Poté jsem jen nastavil statické IP adresy pro můj server.

Realisticky jsem měl základ hotový. Teď DNS!

##### DNS
Používám v tomto pořadí:

 1. moji instanci Pi hole
 2. 1.1.1.1 # Cloudflare
 3. 8.8.8.8 # Google

Samotný Pi hole má pak stejnou konfiguraci (samozřejmě bez odkazu na sebe sama).

Mám tam konkrétně listy od **osid.nl** a od **Stevena Blacka**.

V GUI OPNSense se DNS dělá velice intuitivně.. čili vůbec :D

Myslel jsem si, že když DNS se z drtivé většiny dává do DHCP serveru, tak že bude někde nastavení pro vložení seznamu DNS překladačů. Bohužel, v OPNSense se do dává do '*Systém->Nastavení->Obecné*'. Jak intuitivní!

Jako první jsem si tam dal Pi hole. Následně v případě výpadku, např.:něco budu dělat na [Generálovi](../../about/index.cs.md#server-generál), jsem tam dal cloudflare a google DNSko v rámci redundance.

A funguje to hezky
![OPNSense v Pi hole](img/OPNSensePiHole.png)

V rámci mého počítače jsem jen musel zaškrtnout u sekce **DNS** ```automaticky```. Generál si to přebral sám a to bez pomoci.

### Suricata
*budu ale psát surikata*

Surikata je **FOSS IDS** systém, který má OPNSense již zabudovaný. Je to vlastně celý důvod, proč jse vůbec chtěl FW. Do teď jsem jen pospal nastavení funkcí, které dávno již mám.

#### Nastavení
Nejdříve jsem si stáhl pár pravidel od 'ET open', konkrétně:  
emerging-  
 attack_response  
 malware  
 misc  
![Suricata pravidla](img/SuricataDownload.png)

Neměl jsem specifický nároky. Chtěl jsem jen "malware", jelikož.. no.. dává to prostě rozum že ten nechci.. a pak ještě "attack_response", jelikož obsahuje testovací pravidlo, kterým zjistím, že surikata funguje dobře.

Následně jsem zapl jen "detekující mód".
![Suricata dashboard](img/SuricataAdmin.png)
a zaškrtl ```Enabled```.

Na počítači jsem spustil tenhle příkaz:
```BASH
curl http://testmynids.org/uid/index.html
```

A opět...

![Suricata hrozby](img/SuricataDetectedThreats.png)

Teď co to píšu [**19.4.2026**], jsem nezaznamenal falešné ani doopravdické detekce hrozeb, takže jsem dneškem zapl normálně blokaci.

*toto pravidlo jen varuje, ale nastavil jsem ho tak, ať blokuje*
![Suricata blokace](img/SuricataBlockedThreats.png)