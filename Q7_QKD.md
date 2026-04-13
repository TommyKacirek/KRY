# Otázka 7 – Kvantová distribuce klíčů (QKD)

## 1. Jednovětá definice

QKD je metoda, která pomocí kvantových stavů přenášených po kvantovém kanálu umožňuje dvěma stranám dohodnout sdílený symetrický klíč tak, že odposlech zanechá zjistitelnou stopu.

## 2. Princip

QKD nešifruje samotná data; řeší pouze **bezpečnou distribuci klíče**.

Používá se:

- **kvantový kanál** – typicky jednotlivé fotony v optickém vlákně nebo volným prostorem,
- **klasický veřejný kanál** – ten ale musí být **autentizovaný**.

Bezpečnost stojí na vlastnostech kvantové informace:

- **měření kvantového stavu jej narušuje**,
- **neznámý kvantový stav nelze dokonale kopírovat** (no-cloning theorem),
- odposlech tedy způsobí chyby, které mohou Alice a Bob odhalit.

## 3. Jak probíhá dohoda na klíči

Typický postup:

1. Alice zakóduje náhodné bity do kvantových stavů fotonů.
2. Bob měří přijaté fotony v náhodně volených bázích.
3. Po veřejném kanálu si porovnají použité báze a ponechají jen případy, kde se shodli.
4. Část bitů obětují na kontrolu chybovosti a detekci odposlechu.
5. Ze zbytku po opravě chyb a **privacy amplification** získají sdílený tajný klíč.

## 4. Důvody použití

- umožňuje **bezpečnou distribuci klíče i proti aktivnímu útočníkovi**,
- u vhodných protokolů nabízí **informačně teoretickou bezpečnost**,
- odposlech není jen obtížný, ale i **detekovatelný**,
- je odolná vůči tomu, že velký kvantový počítač prolomí klasickou asymetrickou výměnu klíčů.

V praxi se QKD používá jako náhrada asymetrické výměny klíčů; samotná data se pak šifrují symetricky, například pomocí AES nebo v teorii i Vernamovou šifrou.

## 5. Bezpečnost a omezení

- QKD **neřeší autentizaci sama o sobě**; bez autentizovaného klasického kanálu je možný útok man-in-the-middle.
- Reálné systémy trpí ztrátami, šumem a nedokonalostí zařízení.
- Praktické útoky často míří na implementaci: detektory, zdroje fotonů nebo side-channel úniky.
- Problém je i **omezený dosah**, nemožnost klasického zesilování a útoky typu **photon number splitting**; proto se používají např. **decoy states**.

## 6. Příklady protokolů

### BB84

- nejznámější QKD protokol, navržen Bennett a Brassardem v roce 1984,
- používá dvě navzájem nekompatibilní báze,
- odposlech se projeví zvýšenou chybovostí.

### B92

- zjednodušená dvoustavová varianta Bennettova protokolu,
- používá méně stavů než BB84, ale stejnou základní myšlenku.

### E91

- protokol založený na **kvantovém provázání**,
- bezpečnost je spojena s vlastnostmi entanglementu a porušením Bellových nerovností.

Další varianty jsou např. **šestistavový protokol**, **COW**, **MDI-QKD** nebo **TF-QKD**.

## 7. Krátký závěr pro ústní odpověď

QKD je metoda distribuce symetrického klíče založená na tom, že kvantový stav nelze bez narušení měřit ani kopírovat. Hlavní výhodou je možnost detekovat odposlech a u některých protokolů dosáhnout informačně teoretické bezpečnosti. Nejznámější protokoly jsou BB84, B92 a E91, ale v praxi je nutné řešit autentizaci, ztráty a nedokonalosti zařízení.
