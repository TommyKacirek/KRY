# Otázka 8 – Postkvantová kryptografie (McEliece, mřížky, Lamport)

## 1. Jednovětá definice

Postkvantová kryptografie je soubor kryptografických algoritmů navržených tak, aby zůstaly bezpečné i proti útočníkovi vybavenému velkým kvantovým počítačem.

## 2. Důvody použití

Klasická asymetrická kryptografie stojí hlavně na:

- **faktorizaci velkých čísel** – RSA,
- **diskrétním logaritmu** – Diffie-Hellman, DSA,
- **diskrétním logaritmu na eliptických křivkách** – ECC.

Tyto problémy by velký kvantový počítač řešil pomocí **Shorova algoritmu** v polynomiálním čase, takže dnešní veřejnoklíčové systémy by přestaly být bezpečné.

Naopak u symetrických šifer a hašovacích funkcí kvantový útok obvykle znamená jen **kvadratické zrychlení** (Groverův algoritmus), takže se spíš zvětšují parametry.

## 3. Jaké těžké problémy se v postkvantové kryptografii používají

### Kódová kryptografie

- **dekódování obecného lineárního kódu**,
- používá ji hlavně **McEliece**.

### Mřížková kryptografie

- **SVP** – shortest vector problem,
- **CVP** – closest vector problem,
- v moderních schématech hlavně **LWE / MLWE / NTRU** problémy.

### Hash-based podpisy

- bezpečnost stojí na **jednosměrnosti hašovacích funkcí**,
- příkladem je **Lamportův jednorázový podpis**.

## 4. McElieceův kryptosystém

McEliece je postaven na tom, že:

- veřejně je zveřejněn kód, který vypadá jako obecný lineární kód,
- vlastník soukromého klíče ale zná jeho skrytou strukturu a umí efektivně dekódovat.

### Princip

- soukromý klíč: strukturovaný kód a dekódovací algoritmus,
- veřejný klíč: zamaskovaná generující matice,
- šifrování: ke kódovanému slovu se přidá chybový vektor,
- dešifrování: vlastník tajného klíče chyby opraví.

### Bezpečnost a vlastnosti

- bezpečnost stojí na obtížnosti dekódování obecného lineárního kódu,
- je považován za velmi odolný,
- hlavní nevýhoda jsou **velké veřejné klíče**.

## 5. Kryptografie založená na mřížkách

Mřížka je množina celočíselných lineárních kombinací bázových vektorů. Bezpečnost schémat stojí na tom, že některé úlohy na mřížkách jsou těžké i pro kvantové počítače.

### Hlavní problémy

- **SVP** – najít nejkratší nenulový vektor mřížky,
- **CVP** – najít bod mřížky nejbližší danému bodu,
- **LWE / MLWE** – z lineárních rovnic s malým šumem dopočítat tajemství.

### Příklady

- **NTRU** – klasický mřížkový kryptosystém,
- **Kyber / ML-KEM** – dnešní standardizovaný postkvantový KEM.

### Vlastnosti

- výhoda: vysoká rychlost a menší klíče než u McEliece,
- nevýhoda: složitější matematika a opatrnost při volbě parametrů.

## 6. Lamportův jednorázový podpis

Lamport OTS je hash-based podpisové schéma.

### Princip

- pro každý bit haše zprávy má podepisující připravené dvě tajné hodnoty,
- veřejný klíč tvoří jejich haše,
- při podpisu zveřejní vždy jednu hodnotu podle toho, zda je bit haše 0 nebo 1,
- ověřovatel zkontroluje odpovídající haše.

### Bezpečnost a omezení

- stojí na jednosměrnosti hašovací funkce,
- je odolný i proti kvantovým útokům při dostatečně dlouhém haši,
- **jeden klíč lze použít jen jednou**,
- nevýhodou jsou velké klíče a podpisy.

## 7. Příklady standardizace

- **ML-KEM (Kyber)** – postkvantový KEM, FIPS 203,
- **ML-DSA (Dilithium)** – postkvantový podpis, FIPS 204,
- **SLH-DSA (SPHINCS+)** – hash-based podpis, FIPS 205.

## 8. Krátký závěr pro ústní odpověď

Postkvantová kryptografie nahrazuje dnešní veřejnoklíčové systémy, které by zlomil Shorův algoritmus. Hlavní směry jsou kódová kryptografie, mřížková kryptografie a hash-based podpisy. Typické příklady jsou McEliece, mřížkové systémy jako NTRU nebo Kyber a jednorázový podpis Lamport.
