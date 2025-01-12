# Jak klasifikovat proměnné

## 1. Číselné (Numerické)
- **Charakteristika**: Hodnoty jsou čísla, která mají smysl pro matematické operace (např. sčítání, odčítání, průměr).
- **Dělení**:
  - **Spojité (Continuous)**: 
    - Hodnoty mohou být libovolné na škále (reálná čísla).
    - **Příklady**: váha, výška, teplota, čas (přesně měřený), vzdálenost.
  - **Diskrétní (Discrete)**:
    - Hodnoty jsou obvykle celá čísla a mají pevný počet možností.
    - **Příklady**: počet dětí, počet kliknutí na webové stránce, počet aut na parkovišti.

## 2. Kategorické (Kvalitativní)
- **Charakteristika**: Hodnoty vyjadřují kategorie nebo skupiny. Nelze s nimi přímo provádět matematické operace.
- **Dělení**:
  - **Nominální (Nominal)**:
    - Kategorie jsou neuspořádané (nelze je smysluplně seřadit).
    - **Příklady**: pohlaví (muž/žena), barva očí, typ auta.
  - **Ordinální (Ordinal)**:
    - Kategorie jsou uspořádané, ale rozdíly mezi nimi nejsou měřitelné.
    - **Příklady**: vzdělání (základní, střední, vysoké), hodnocení spokojenosti (nespokojený, neutrální, spokojený).

---

## Další pomůcky
1. **Je možné hodnoty seřadit?**
   - Ano: Ordinální.
   - Ne: Nominální.
2. **Jsou hodnoty číselné?**
   - Ano: Číselné.
   - Ne: Kategorické.
3. **Může hodnota nabývat nekonečně mnoho různých hodnot v určitém intervalu?**
   - Ano: Spojité.
   - Ne: Diskrétní.

# Přehled pravděpodobnostních rozdělení

## Diskrétní rozdělení

### Binomické rozdělení
- **Popis**: Počet úspěchů v \( n \) nezávislých pokusech, kde každý pokus má pravděpodobnost úspěchu \( p \).
- **Funkce**:
  - `dbinom(k, n, p)`: Pravděpodobnost, že nastane přesně \( k \) úspěchů.
  - `pbinom(k, n, p)`: Pravděpodobnost, že nastane nejvýše \( k \) úspěchů.
- **Střední hodnota**: \( \mu = n \cdot p \)
- **Rozptyl**: \( \sigma^2 = n \cdot p \cdot (1 - p) \)
- **Použití**: Například při hádání odpovědí v testu s \( n \) otázkami, kde šance na správnou odpověď je \( p \).

---

### Hypergeometrické rozdělení
- **Popis**: Počet úspěchů při náhodném výběru \( n \) objektů z populace obsahující \( w \) úspěšných objektů a \( b \) neúspěšných, bez vracení.
- **Funkce**:
  - `dhyper(k, w, b, n)`: Pravděpodobnost, že mezi \( n \) vybranými objekty je přesně \( k \) úspěšných.
  - `phyper(k, w, b, n)`: Pravděpodobnost, že mezi \( n \) vybranými objekty je nejvýše \( k \) úspěšných.
- **Střední hodnota**: \( \mu = n \cdot \frac{w}{w + b} \)
- **Rozptyl**: \( \sigma^2 = \mu \cdot \left(1 - \frac{w}{w + b}\right) \cdot \frac{w + b - n}{w + b - 1} \)
- **Použití**: Například při losování výherních losů z pevně dané sady.

---

### Geometrické rozdělení
- **Popis**: Počet neúspěšných pokusů před prvním úspěchem, kde pravděpodobnost úspěchu v jednom pokusu je \( p \).
- **Funkce**:
  - `dgeom(k, p)`: Pravděpodobnost, že první úspěch nastane po \( k \) neúspěších.
  - `pgeom(k, p)`: Pravděpodobnost, že první úspěch nastane nejpozději po \( k \) neúspěších.
- **Střední hodnota**: \( \mu = \frac{1 - p}{p} \)
- **Rozptyl**: \( \sigma^2 = \frac{1 - p}{p^2} \)
- **Použití**: Například počet hodů kostkou do prvního hodu šestky.

---

### Poissonovo rozdělení
- **Popis**: Počet událostí nastávajících za pevný časový interval nebo v daném prostoru, pokud události nastávají nezávisle.
- **Funkce**:
  - `dpois(k, lambda)`: Pravděpodobnost, že nastane \( k \) událostí.
  - `ppois(k, lambda)`: Pravděpodobnost, že nastane nejvýše \( k \) událostí.
- **Střední hodnota**: \( \mu = \lambda \)
- **Rozptyl**: \( \sigma^2 = \lambda \)
- **Použití**: Například počet zákazníků přicházejících do obchodu za hodinu.

---

## Spojitá rozdělení

### Normální (Gaussovo) rozdělení
- **Popis**: Modeluje mnoho přírodních jevů (např. výšku lidí). Charakterizováno střední hodnotou \( \mu \) a směrodatnou odchylkou \( \sigma \).
- **Funkce**:
  - `dnorm(x, mu, sigma)`: Hustota pravděpodobnosti.
  - `pnorm(x, mu, sigma)`: Distribuční funkce.
  - `qnorm(p, mu, sigma)`: Kvantilová funkce.
- **Použití**: Například rozložení výšek dospělých lidí.
- **Příklad**:
  - Pravděpodobnost, že náhodně vybraný člověk je vyšší než 170 cm, pokud \( \mu = 180 \), \( \sigma = 7 \).

---

### Lognormální rozdělení
- **Popis**: Náhodná veličina \( X \) má lognormální rozdělení, pokud \( \ln(X) \) má normální rozdělení.
- **Funkce**:
  - `plnorm(x, mu, sigma)`: Distribuční funkce.
  - `qlnorm(p, mu, sigma)`: Kvantilová funkce.
- **Střední hodnota**: \( \text{E}[X] = e^{\mu + \sigma^2 / 2} \)
- **Rozptyl**: \( \text{Var}[X] = \left(e^{\sigma^2} - 1\right) e^{2\mu + \sigma^2} \)
- **Použití**: Například modelování příjmů nebo hodnot akcií.

---

### Exponenciální rozdělení
- **Popis**: Modeluje dobu mezi událostmi v Poissonově procesu.
- **Funkce**:
  - `pexp(x, rate)`: Distribuční funkce.
  - `qexp(p, rate)`: Kvantilová funkce.
- **Střední hodnota**: \( \mu = \frac{1}{\text{rate}} \)
- **Rozptyl**: \( \sigma^2 = \frac{1}{\text{rate}^2} \)
- **Použití**: Například doba do rozpadu radioaktivního atomu.

---

## Central Limit Theorem (CLT)
- **Popis**: Rozdělení součtu nezávislých, stejně rozdělených náhodných veličin konverguje k normálnímu rozdělení, pokud počet veličin roste nade všechny meze.
- **Použití**: Například pro aproximaci rozdělení průměru velkého vzorku.

---

## Testování hypotéz
- **Postup**:
  1. Formulace nulové hypotézy (\( H_0 \)) a alternativní hypotézy (\( H_1 \)).
  2. Stanovení hladiny významnosti (obvykle \( \alpha = 0.05 \)).
  3. Výpočet p-hodnoty:
     - \( p \leq \alpha \): Zamítáme \( H_0 \), platí \( H_1 \).
     - \( p > \alpha \): Nezamítáme \( H_0 \).
- **Příklad**:
  - Testování, zda je průměrná výška policistů rovna 180 cm:  
    ```R
    t.test(vyska, mu = 180)
    ```
