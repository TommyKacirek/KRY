# Otázka 10 – Autentizační protokoly, principy, použití, hodnocení bezpečnosti (BAN logika)

## 1. Jednovětá definice

Autentizační protokol je výměna zpráv, pomocí které jedna nebo obě strany ověřují identitu partnera a často si zároveň dohodnou čerstvý session key.

## 2. Principy autentizačních protokolů

### Základní cíl

- ověřit, **s kým** komunikuji,
- případně ověřit i **původ zprávy**,
- často také bezpečně navázat **sdílený klíč relace**.

### Typické principy

- **jednosměrná autentizace** – ověřuje se jen jedna strana,
- **vzájemná autentizace** – ověřují se obě strany,
- **challenge-response** – jedna strana pošle výzvu, druhá odpověď odvozenou z tajemství,
- **čerstvost zpráv** – používají se **nonce**, časová razítka nebo sekvenční čísla.

Čerstvost je důležitá hlavně proto, aby nešel použít starý záznam komunikace znovu.

## 3. Použití

Autentizační protokoly se používají například pro:

- přihlašování do systémů,
- Wi-Fi a podnikové sítě,
- VPN,
- webové a API služby,
- doménové prostředí typu **Kerberos**,
- TLS s certifikáty nebo vzájemnou autentizací.

## 4. Bezpečnost a typické útoky

Dobře navržený autentizační protokol musí odolat hlavně těmto útokům:

- **replay attack** – znovupřehrání staré zprávy,
- **man-in-the-middle** – útočník se vloží mezi obě strany,
- **reflection attack** – strana je donucena odpovědět sama sobě,
- **interleaving attack** – kombinace zpráv z více běhů protokolu,
- **guessing attack** – hádání hesla nebo slabého tajemství,
- **desynchronizace** – problém u sekvenčních čísel.

Proto musí protokol:

- vázat odpověď na **čerstvou hodnotu**,
- svázat zprávy s konkrétní identitou účastníků,
- chránit session key a potvrdit, že ho obě strany opravdu sdílejí,
- používat bezpečná primitiva a správnou správu klíčů.

## 5. Příklady protokolů

- **PAP** – heslo se posílá v podstatě přímo; dnes je považován za nebezpečný.
- **CHAP** – challenge-response se sdíleným tajemstvím.
- **Kerberos** – autentizace přes důvěryhodnou třetí stranu a časová razítka.
- **EAP / EAP-TLS** – běžné v síťové autentizaci; EAP-TLS používá certifikáty.

## 6. BAN logika

### Co je BAN logika

**BAN logika** (Burrows–Abadi–Needham) je formální metoda pro hodnocení bezpečnosti autentizačních protokolů. Nezkoumá implementaci, ale to, **co si mohou účastníci po přijetí zpráv oprávněně myslet**.

### Typické výroky

| Zápis | Význam |
|---|---|
| **P believes X** | P věří, že X platí |
| **P sees X** | P obdržel zprávu obsahující X |
| **fresh(X)** | X je čerstvé, nepochází ze starého běhu |
| **P ↔K Q** | K je sdílený klíč jen mezi P a Q |

### Hlavní myšlenka pravidel

1. **Message meaning rule** – když P věří, že klíč \(K\) sdílí jen s Q, a vidí zprávu šifrovanou tímto klíčem, může věřit, že ji vyslovil Q.
2. **Nonce verification rule** – když je zpráva čerstvá, může P věřit, že Q tomu výroku věří i nyní, ne jen někdy v minulosti.
3. **Jurisdiction rule** – pokud je Q autoritou nad určitým tvrzením, může P toto tvrzení převzít.

### K čemu slouží

BAN logika se používá například při analýze protokolů typu **Needham-Schroeder** nebo **Kerberos**, kde pomáhá ukázat, zda si strany opravdu mohou věřit, že sdílejí čerstvý klíč a komunikují se správným partnerem.

### Omezení

- neřeší detailní vlastnosti kryptografických algoritmů,
- abstrahuje od implementačních chyb,
- nepostihuje dobře side-channel útoky ani reálné HW slabiny.

## 7. Krátký závěr pro ústní odpověď

Autentizační protokoly slouží k ověření identity a často i k dohodě na čerstvém session key. Jejich bezpečnost stojí hlavně na challenge-response principu, čerstvosti zpráv a ochraně proti replay a MitM útokům. BAN logika je klasický formální nástroj, kterým se ověřuje, zda z průběhu protokolu opravdu plyne vzájemná důvěra účastníků.
