# Otázka 2 – Služby bezpečnosti zajišťované kryptografickými prostředky a mechanismy

## 1. Jednovětá definice

Služba bezpečnosti říká, **co chceme chránit**, zatímco bezpečnostní mechanismus říká, **jak to kryptograficky zajistíme**.

## 2. Povinné body podle zadání

V pojetí ISO 7498-2 se v kryptografii typicky uvádí těchto **5 služeb bezpečnosti**:

1. **Autentizace**
2. **Řízení přístupu**
3. **Důvěrnost dat**
4. **Integrita dat**
5. **Nepopiratelnost**

## 3. Vazba služba -> mechanismus

| Služba | Co znamená | Typické kryptografické mechanismy |
|---|---|---|
| **Autentizace** | ověření identity entity nebo původu dat | challenge-response, MAC, digitální podpis, certifikáty, autentizační protokoly |
| **Řízení přístupu** | ke zdroji se dostane jen oprávněný subjekt | identifikace + autentizace, kryptografické tokeny, certifikáty, správa klíčů |
| **Důvěrnost dat** | obsah zprávy nesmí číst neoprávněná osoba | šifrování, výměna klíčů, obálka, traffic padding |
| **Integrita dat** | musí být poznat neautorizovaná změna | hash, MAC, AEAD, digitální podpis, pořadová čísla a nonce |
| **Nepopiratelnost** | odesílatel nebo příjemce nemůže věrohodně popřít svou účast | digitální podpis, PKI, časové razítko, notářská služba |

## 4. Hlavní bezpečnostní mechanismy

Podle ISO 7498-2 mezi hlavní mechanismy patří:

- **šifrování (encipherment)**,
- **digitální podpis**,
- **řízení přístupu**,
- **mechanismy integrity dat**,
- **výměna autentizační informace**,
- **traffic padding**,
- **řízení směrování**,
- **ověření třetím subjektem / notarization**.

## 5. Bezpečnost / hodnocení

- **Šifrování samo o sobě nezajišťuje integritu ani autenticitu.**
- **MAC zajišťuje integritu a autenticitu původu, ale ne nepopiratelnost**, protože obě strany sdílejí stejný klíč.
- **Digitální podpis** zajišťuje integritu, autentizaci původu i nepopiratelnost, pokud je správně navázán na identitu přes PKI.
- Bezpečnost celé služby závisí i na **správě klíčů**, čerstvosti zpráv (nonce, timestamp) a správné implementaci protokolu.
- **Dostupnost** je obecný bezpečnostní cíl, ale kryptografie ji zajišťuje jen nepřímo; typicky se řeší architekturou a provozem.

## 6. Příklady z praxe

- **TLS:** autentizace serveru certifikátem, výměna klíčů, pak důvěrnost a integrita pomocí AEAD.
- **Podepsaný dokument:** digitální podpis + certifikát + časové razítko.
- **API komunikace:** HMAC nebo podpis požadavků.
- **Šifrovaný disk:** důvěrnost dat, ale integrita závisí na použitém módu a doplňkových mechanismech.

## 7. Krátký závěr pro ústní odpověď

Služba bezpečnosti je cíl, mechanismus je prostředek. Kryptografie typicky zajišťuje autentizaci, řízení přístupu, důvěrnost, integritu a nepopiratelnost. Klíčové je nezaměňovat pojmy: šifrování dává důvěrnost, MAC dává integritu a autenticitu, digitální podpis navíc přidává nepopiratelnost.
