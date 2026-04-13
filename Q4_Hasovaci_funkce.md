# Otázka 4 – Hašovací funkce

## 1. Jednovětá definice

Kryptografická hašovací funkce převádí vstup libovolné délky na krátký pevně dlouhý otisk tak, aby byl výpočet haše snadný, ale inverze a hledání kolizí výpočetně těžké.

## 2. Formální definice

Hašovací funkce je zobrazení

\[
H : \{0,1\}^* \rightarrow \{0,1\}^n
\]

kde:

- vstup může mít libovolnou délku,
- výstup má pevnou délku \(n\) bitů,
- pro stejný vstup vždy dostaneme stejný výstup.

## 3. Požadované vlastnosti

### Základní funkční vlastnosti

- výpočet \(H(m)\) musí být rychlý,
- výstup má pevnou délku,
- malá změna vstupu má způsobit velkou změnu výstupu (**avalanche effect**).

### Bezpečnostní vlastnosti

1. **Preimage resistance**  
   Pro daný haš \(h\) je prakticky nemožné najít zprávu \(m\), aby \(H(m)=h\).

2. **Second preimage resistance**  
   Pro danou zprávu \(m_1\) je prakticky nemožné najít jinou zprávu \(m_2\), aby \(H(m_1)=H(m_2)\).

3. **Collision resistance**  
   Je prakticky nemožné najít libovolné dvě různé zprávy \(m_1, m_2\), pro které platí \(H(m_1)=H(m_2)\).

## 4. Hodnocení bezpečnosti

- U haše délky \(n\) bitů se očekává odolnost proti preimage přibližně **\(2^n\)** operací.
- Pro kolize platí kvůli **birthday paradoxu** jen asi **\(2^{n/2}\)** operací.
- Proto je důležitá dostatečná délka výstupu; dnes se běžně používá **256 bitů a více**.
- Hodnocení bezpečnosti stojí na kryptanalýze: sleduje se, zda existují rychlejší útoky na kolize, druhý vzor nebo nalezení vstupu.
- **MD5 a SHA-1** se dnes nepovažují za bezpečné pro kolizní odolnost.
- **SHA-2, SHA-3, BLAKE2/BLAKE3** jsou dnes běžně považovány za bezpečné.

## 5. Příklady algoritmů

- **Historické / dnes nevhodné pro bezpečnost:** MD5, SHA-1.
- **Běžně používané:** SHA-256, SHA-512, SHA-3.
- **Praktické moderní varianty:** BLAKE2, BLAKE3.

## 6. Použití

- **Digitální podpisy** – podepisuje se haš zprávy, ne celá zpráva.
- **Kontrola integrity souborů** – ověření, že data nebyla změněna.
- **HMAC / MAC** – autenticita a integrita zpráv se sdíleným klíčem.
- **Ukládání hesel** – ne samotným hašem, ale pomocí specializovaných funkcí jako PBKDF2, bcrypt, scrypt, Argon2.
- **Merkleho stromy, blockchain, identifikátory dat**.

## 7. Krátký závěr pro ústní odpověď

Hašovací funkce převádí libovolně dlouhou zprávu na pevně dlouhý otisk. Bezpečná kryptografická hašovací funkce musí být jednocestná, odolná proti druhému vzoru a proti kolizím. V praxi se dnes používají hlavně SHA-2, SHA-3 a BLAKE2/BLAKE3, zatímco MD5 a SHA-1 už ne.
