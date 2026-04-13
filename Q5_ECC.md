# Otázka 5 – Kryptografie nad eliptickými křivkami (ECC)

## 1. Jednovětá definice

ECC je asymetrická kryptografie postavená na grupě bodů eliptické křivky nad konečným polem; bezpečnost stojí na obtížnosti diskrétního logaritmu na eliptických křivkách.

## 2. Principy

Eliptická křivka nad polem \(F_p\) je typicky dána rovnicí

\[
y^2 = x^3 + ax + b \pmod p
\]

kde musí platit, že křivka není singulární:

\[
4a^3 + 27b^2 \not\equiv 0 \pmod p
\]

Body na křivce spolu s bodem v nekonečnu tvoří **grupu**.

### Základní operace

- **sčítání bodů** \(P + Q\),
- **zdvojení bodu** \(2P\),
- **skalární násobení** \(Q = kP\).

Právě skalární násobení je snadné spočítat, ale inverzní úloha je těžká.

## 3. Bezpečnostní základ

Základním problémem je:

### ECDLP – Elliptic Curve Discrete Logarithm Problem

Je dána křivka, bod \(P\) a bod \(Q = kP\). Úkolem je najít \(k\).

- výpočet \(Q = kP\) je efektivní,
- dopočítat \(k\) z dvojice \(P, Q\) je prakticky těžké,
- právě na tom stojí bezpečnost ECDH, ECDSA a dalších EC algoritmů.

## 4. Důvody použití

Hlavní výhoda ECC je **stejná bezpečnost při mnohem kratších klíčích** než u RSA nebo klasického DH.

To přináší:

- menší certifikáty a podpisy,
- rychlejší výměnu klíčů,
- nižší nároky na paměť, přenos i energii,
- vhodnost pro **mobilní a embedded zařízení**.

Typicky:

- RSA / DH pro cca 128bitovou bezpečnost potřebují asi **3072 bitů**,
- ECC stačí asi **256 bitů**.

## 5. Příklady algoritmů

- **ECDH** – výměna klíčů.
- **ECDSA** – digitální podpis.
- **ECIES** – šifrovací schéma kombinující ECC a symetrickou kryptografii.
- **EdDSA / Ed25519** – moderní podpisové schéma nad Edwardsovými křivkami.

## 6. Bezpečnost / praktické poznámky

- bezpečnost silně závisí na **správné volbě křivky a parametrů**,
- je nutná ochrana proti **side-channel útokům** a chybám implementace,
- u podpisů typu ECDSA je kritická kvalitní náhodná hodnota \(k\); její opakování prozradí soukromý klíč,
- ECC stejně jako RSA a DH **není odolná vůči velkému kvantovému počítači** (Shorův algoritmus).

## 7. Krátký závěr pro ústní odpověď

ECC používá body eliptické křivky jako grupu, ve které je snadné spočítat skalární násobení, ale těžké řešit diskrétní logaritmus. Hlavním důvodem použití jsou krátké klíče při stejné bezpečnosti. V praxi se používá hlavně ECDH pro výměnu klíčů a ECDSA nebo EdDSA pro digitální podpis.
