# Otázka 9 – eIDAS: elektronický podpis, zaručený a kvalifikovaný podpis, elektronická pečeť, elektronické časové razítko

## 1. Jednovětá definice

**eIDAS** je nařízení EU o elektronické identifikaci a službách vytvářejících důvěru, které právně definuje pojmy jako elektronický podpis, pečeť a časové razítko.

## 2. Pojmy podle eIDAS

### Elektronický podpis

- data v elektronické podobě, která jsou připojena k jiným datům nebo jsou s nimi logicky spojena,
- podepisující osoba je používá k podepsání,
- je to **nejširší pojem**.

Může jím být i velmi jednoduchá forma, například kliknutí na „souhlasím“ nebo napsání jména pod e-mail.

### Zaručený elektronický podpis

Je to elektronický podpis, který navíc splňuje tyto požadavky:

1. je **jednoznačně spojen** s podepisující osobou,
2. umožňuje **identifikaci** podepisující osoby,
3. je vytvořen pomocí prostředků, které má podepisující **pod svou výhradní kontrolou**,
4. je spojen s podepsanými daty tak, že je možné zjistit **jakoukoliv následnou změnu**.

### Kvalifikovaný elektronický podpis

Je to zaručený elektronický podpis, který navíc:

- je vytvořen **kvalifikovaným prostředkem** pro vytváření podpisu,
- je založen na **kvalifikovaném certifikátu**.

Je to tedy nejsilnější forma elektronického podpisu; právně má v EU postavení ekvivalentní vlastnoručnímu podpisu.

## 3. Elektronická pečeť

Elektronická pečeť je obdobou podpisu, ale:

- neváže se k fyzické osobě, nýbrž k **právnické osobě**,
- slouží hlavně k prokázání **původu** a **integrity** dokumentu,
- typicky se používá tam, kde dokument vydává organizace, ne konkrétní člověk.

Stručně:

- **podpis** = fyzická osoba,
- **pečeť** = právnická osoba.

I u pečetí eIDAS rozlišuje zaručenou a kvalifikovanou variantu.

## 4. Elektronické časové razítko

Elektronické časové razítko jsou data, která spojují jiná data s konkrétním okamžikem a dokazují, že tato data v daném čase existovala.

Používá se hlavně k tomu, aby šlo prokázat:

- že dokument existoval v určitém okamžiku,
- že od té doby nebyl nepozorovaně změněn,
- že podpis vznikl ještě v době platnosti certifikátu.

### Kvalifikované časové razítko

Kvalifikované elektronické časové razítko musí navíc:

- používat **přesný zdroj času** navázaný na UTC,
- být vydáno kvalifikovaným poskytovatelem služby vytvářející důvěru,
- být chráněno podpisem, pečetí nebo rovnocennou metodou.

## 5. Přehled rozdílů

| Pojem | Kdo / co | Hlavní význam |
|---|---|---|
| **Elektronický podpis** | fyzická osoba | nejširší pojem, libovolná elektronická forma podpisu |
| **Zaručený elektronický podpis** | fyzická osoba | identifikace osoby, výhradní kontrola, detekce změny dat |
| **Kvalifikovaný elektronický podpis** | fyzická osoba | zaručený podpis + kvalifikovaný certifikát + kvalifikovaný prostředek |
| **Elektronická pečeť** | právnická osoba | prokázání původu a integrity dokumentu organizace |
| **Elektronické časové razítko** | data + čas | důkaz existence dat v určitém okamžiku |

## 6. Krátký závěr pro ústní odpověď

eIDAS rozlišuje tři úrovně podpisu: elektronický, zaručený a kvalifikovaný. Zaručený podpis přidává vazbu na osobu, výhradní kontrolu a detekci změn dat, kvalifikovaný podpis k tomu přidává kvalifikovaný certifikát a prostředek. Elektronická pečeť je podobný institut pro právnické osoby a elektronické časové razítko prokazuje existenci dat v konkrétním čase.
