# Otázka 1 – Formální definice kryptografického systému, symetrické a asymetrické šifry

## 1. Jednovětá definice

Kryptografický systém je formálně popsaný soubor zpráv, klíčů a algoritmů pro šifrování a dešifrování tak, aby oprávněný uživatel zprávu obnovil, ale útočník bez klíče ne.

## 2. Povinné body podle zadání

### Formální definice kryptosystému

Kryptosystém se obvykle zapisuje jako pětice:

\[
(\mathcal{M}, \mathcal{C}, \mathcal{K}, \mathcal{E}, \mathcal{D})
\]

- \(\mathcal{M}\) – množina otevřených textů,
- \(\mathcal{C}\) – množina šifrových textů,
- \(\mathcal{K}\) – množina klíčů,
- \(\mathcal{E}\) – množina šifrovacích funkcí,
- \(\mathcal{D}\) – množina dešifrovacích funkcí.

Pro příslušné klíče musí platit korektnost:

\[
D_{k_2}(E_{k_1}(m)) = m
\]

pro každou zprávu \(m \in \mathcal{M}\).

### Symetrická šifra

- pro šifrování a dešifrování se používá stejný klíč nebo snadno odvoditelný pár klíčů,
- obě strany musí sdílet tajemství předem,
- výhoda: vysoká rychlost a vhodnost pro velké objemy dat,
- nevýhoda: problém bezpečné distribuce klíče.

### Asymetrická šifra

- používá dvojici klíčů: veřejný a soukromý,
- veřejný klíč slouží k šifrování nebo ověření podpisu,
- soukromý klíč slouží k dešifrování nebo vytvoření podpisu,
- z veřejného klíče nesmí být prakticky možné odvodit klíč soukromý,
- výhoda: jednodušší distribuce klíčů a možnost digitálního podpisu,
- nevýhoda: vyšší výpočetní náročnost.

## 3. Princip / jak to funguje

- **Symetrie:** Alice i Bob znají stejný tajný klíč \(k\), takže \(c = E_k(m)\) a \(m = D_k(c)\).
- **Asymetrie:** příjemce zveřejní veřejný klíč \(e\), odesílatel šifruje \(c = E_e(m)\), dešifrovat umí jen vlastník soukromého klíče \(d\).
- V praxi se často používá **hybridní kryptografie**: asymetrie se použije pro výměnu session key a samotná data pak šifruje rychlá symetrická šifra.

## 4. Bezpečnost / výpočetně těžké problémy

Bezpečnost asymetrických šifer stojí na tom, že přímý výpočet je snadný, ale inverzní úloha bez tajného klíče je výpočetně těžká.

- **Faktorizace velkých čísel (IFP)** – základ RSA, Rabinova kryptosystému.
- **Problém diskrétního logaritmu (DLP)** – základ Diffie-Hellman, ElGamal, DSA.
- **Diskrétní logaritmus na eliptických křivkách (ECDLP)** – základ ECDH, ECDSA.
- Historicky se uvažoval i **knapsack problem**; u postkvantových systémů pak mřížky a dekódování lineárních kódů.

## 5. Příklady algoritmů a použití

- **Symetrické šifry:** AES, ChaCha20, 3DES.
- **Asymetrické algoritmy:** RSA, ElGamal, ECIES, Diffie-Hellman, ECDH.
- **Použití:** TLS, VPN, šifrování disků, elektronická pošta, digitální podpisy, PKI.

## 6. Krátký závěr pro ústní odpověď

Kryptosystém je formálně dán množinou zpráv, šifrových textů, klíčů a dvojicí funkcí pro šifrování a dešifrování se zaručenou korektností. U symetrických šifer je problém distribuce tajného klíče, u asymetrických je výhoda v práci s veřejným a soukromým klíčem. Klasická asymetrická kryptografie stojí hlavně na faktorizaci a diskrétním logaritmu, včetně varianty nad eliptickými křivkami.
