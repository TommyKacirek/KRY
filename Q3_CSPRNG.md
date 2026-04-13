# Otázka 3 – Kryptograficky bezpečné generátory náhodných čísel (CSPRNG)

## 1. Jednovětá definice

CSPRNG je pseudonáhodný generátor určený pro kryptografii: z krátkého seedu s dostatečnou entropií vytváří dlouhý výstup, který má být pro útočníka prakticky nepředvídatelný.

## 2. Proč kryptografie potřebuje náhodnost

Náhodnost je nutná pro:

- **generování klíčů**,
- **IV, nonce a salt**,
- **challenge-response protokoly**,
- **dočasné hodnoty** v algoritmech typu DSA/ECDSA.

Pokud je generátor předvídatelný, padá bezpečnost celého systému.

## 3. Základní rozlišení

- **TRNG** – čerpá náhodnost z fyzikálního jevu, např. šumu.
- **PRNG** – deterministický algoritmus; pro kryptografii sám o sobě nestačí.
- **CSPRNG** – PRNG splňující kryptografické požadavky.

V praxi se používá **hybridní přístup**: entropie se vezme z fyzického zdroje a CSPRNG ji rychle rozvine do delší sekvence.

## 4. Požadavky na CSPRNG

### Nepředvídatelnost

- útočník nesmí z dosavadního výstupu odhadnout další bity,
- formálně se uvádí **next-bit test**.

### Kvalitní seed

- seed musí obsahovat dost skutečné entropie,
- inicializace nesmí být odvoditelná z času, PID apod.

### Odolnost při kompromitaci stavu

- **backward security** – ze současného stavu nesmí jít dopočítat minulé výstupy,
- **forward security** – po novém reseedování nesmí jít předpovídat budoucí výstupy.

### Praktické požadavky

- dostatečně velký vnitřní stav,
- pravidelné **reseedování**,
- odstranění biasu ze zdroje entropie.

## 5. Hodnocení bezpečnosti

Bezpečnost CSPRNG se hodnotí ve třech vrstvách:

1. **kvalita zdroje entropie** – kolik skutečné náhodnosti seed obsahuje,
2. **bezpečnost algoritmu** – zda je výstup bez znalosti stavu nepředvídatelný,
3. **správnost implementace** – chybné seedování nebo opakování stavu je kritická chyba.

### Statistické testy

- používají se např. **FIPS testy**, **NIST SP 800-22**, **Diehard/Dieharder**,
- ověřují, že výstup **vypadá náhodně**,
- jsou **nutné, ale ne postačující**: generátor může testy projít a přesto být kryptograficky slabý.

### Typická selhání

- **Debian OpenSSL bug (2008)** – malý počet možných seedů vedl ke slabým klíčům,
- **Android PRNG bug (2013)** – opakování hodnoty \(k\) v ECDSA umožnilo dopočítat privátní klíče.

## 6. Příklady realizace

- **HMAC-DRBG** – doporučený standardizovaný přístup, bezpečnost stojí na HMAC.
- **CTR-DRBG** – používá blokovou šifru, typicky AES v čítačovém režimu.
- **Hash-DRBG** – založen na kryptografické hašovací funkci.
- **/dev/urandom** – běžný systémový CSPRNG v Unixu po správné inicializaci.
- **Blum-Blum-Shub** – teoreticky zajímavý, ale pomalý.
- **Dual-EC-DRBG** – historicky známý kompromitovaný návrh; dnes se nepoužívá.

## 7. Krátký závěr pro ústní odpověď

CSPRNG je základní stavební kámen kryptografie, protože bez kvalitní náhodnosti nejsou bezpečné klíče ani protokoly. Musí být nepředvídatelný, správně seedovaný a odolný i při kompromitaci stavu. Statistické testy samy nestačí; rozhoduje i kvalita entropie a správnost implementace.
