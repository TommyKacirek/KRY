# Otázka 6 – Digitální podpis, standardy a distribuce veřejných klíčů (PKI)

## 1. Jednovětá definice

Digitální podpis je asymetrický kryptografický mechanismus, který zajišťuje autenticitu původu dat, integritu zprávy a při správném navázání na identitu i nepopiratelnost.

## 2. Princip digitálního podpisu

Podpisové schéma má tři základní algoritmy:

- **KeyGen** – vygeneruje veřejný a soukromý klíč,
- **Sign** – soukromým klíčem vytvoří podpis,
- **Verify** – veřejným klíčem podpis ověří.

V praxi se nepodepisuje celá zpráva, ale její **haš**:

1. spočítá se \(h = H(m)\),
2. podepisující vytvoří podpis \(s = Sign(k_{prv}, h)\),
3. ověřovatel zkontroluje \(Verify(k_{pub}, h, s)\).

To je rychlejší a zároveň to zajišťuje:

- **autenticitu** – kdo zprávu podepsal,
- **integritu** – že nebyla změněna,
- **nepopiratelnost** – podepisující nemůže podpis věrohodně popřít.

## 3. Bezpečnost / důležité poznámky

- Digitální podpis **nezajišťuje důvěrnost**; k tomu slouží šifrování.
- Bezpečnost závisí na soukromém klíči, bezpečné hašovací funkci a správné implementaci.
- U DSA/ECDSA je kritická náhodná hodnota \(k\); její opakování může prozradit soukromý klíč.
- MAC a digitální podpis nejsou totéž: **MAC nedává nepopiratelnost**, protože klíč znají obě strany.

## 4. Standardy a příklady algoritmů

- **RSA podpis** – bezpečnost stojí na faktorizaci.
- **DSA** – podpisové schéma založené na diskrétním logaritmu.
- **ECDSA** – varianta DSA nad eliptickými křivkami.
- **EdDSA** – moderní podpisové schéma, typicky Ed25519.

### Důležité standardy

- **DSS / FIPS 186** – Digital Signature Standard.
- **PKCS#1** – RSA šifrování a podpis.
- **X.509** – formát certifikátů.
- **CMS / PKCS#7** – formáty podepsaných kryptografických zpráv.

## 5. Metody distribuce veřejných klíčů

Veřejný klíč nestačí jen zveřejnit; je nutné vědět, **komu opravdu patří**.

Základní přístupy jsou:

1. **Veřejné oznámení** – nejjednodušší, ale snadno podvržitelné.
2. **Veřejný adresář** – klíče spravuje důvěryhodná instituce.
3. **Autorita pro veřejné klíče** – on-line autorita potvrzuje pravost klíče.
4. **Certifikáty a PKI** – nejběžnější praktické řešení.

## 6. PKI – Public Key Infrastructure

PKI je soubor technických a organizačních prostředků pro:

- vydávání certifikátů,
- vazbu veřejného klíče na identitu,
- správu platnosti a odvolání certifikátů.

### Hlavní prvky PKI

- **CA (Certification Authority)** – vydává a podepisuje certifikáty,
- **RA (Registration Authority)** – ověřuje identitu žadatele,
- **certifikát X.509** – váže identitu subjektu s veřejným klíčem,
- **CRL** – seznam odvolaných certifikátů,
- **OCSP** – on-line ověření, zda certifikát stále platí,
- **TSA** – autorita časových razítek.

### Certifikát

Certifikát obsahuje zejména:

- identitu subjektu,
- veřejný klíč,
- identitu vydavatele,
- dobu platnosti,
- podpis certifikační autority.

## 7. Krátký závěr pro ústní odpověď

Digitální podpis funguje tak, že se haš zprávy podepíše soukromým klíčem a ověří veřejným klíčem. Zajišťuje autenticitu, integritu a nepopiratelnost, ale ne důvěrnost. Aby šlo veřejným klíčům věřit, používá se PKI s certifikáty X.509, certifikační autoritou a mechanismy jako CRL nebo OCSP.
