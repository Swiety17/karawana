# Model Ekonomiczny — Karawana

> **Wersja:** 0.1.0 (draft)  
> **Data:** 2026-06-16  
> **Uwaga:** Wszystkie liczby są wstępne, do balansowania po spike'u walidacyjnym.

---

## 1. Towary

### 1.1. Katalog towarów

| ID | Nazwa | Kategoria | Cena bazowa (zł) | Waga | Psuje się? | Czas psucia (dni) |
|----|-------|-----------|-------------------|------|------------|---------------------|
| `iron_ore` | Ruda żelaza | Surowce | 10 | 5 | Nie | — |
| `coal` | Węgiel | Surowce | 8 | 4 | Nie | — |
| `wood` | Drewno | Surowce | 6 | 3 | Nie | — |
| `herbs` | Zioła lecznicze | Surowce | 15 | 1 | Tak | 20 |
| `steel` | Stal | Towary wojenne | 35 | 4 | Nie | — |
| `weapons` | Broń | Towary wojenne | 60 | 3 | Nie | — |
| `armor` | Pancerze | Towary wojenne | 50 | 5 | Nie | — |
| `gunpowder` | Czarny proch | Towary wojenne | 80 | 2 | Nie | — |
| `relic` | Starożytna relikwia | Artefakty | 150 | 1 | Nie | — |
| `rune` | Magiczna runa | Artefakty | 120 | 1 | Nie | — |
| `scroll` | Zaklęty zwój | Artefakty | 200 | 1 | Nie | — |
| `grain` | Zboże | Żywność | 5 | 3 | Tak | 30 |
| `meat` | Suszone mięso | Żywność | 12 | 2 | Tak | 15 |
| `wine` | Wino | Żywność | 25 | 2 | Nie | — |
| `spices` | Przyprawy | Luksusy | 40 | 1 | Nie | — |
| `silk` | Jedwab | Luksusy | 70 | 1 | Nie | — |
| `gems` | Klejnoty | Luksusy | 100 | 1 | Nie | — |
| `incense` | Kadzidła | Luksusy | 55 | 1 | Nie | — |
| `info_map` | Mapa (informacja) | Informacje | 30 | 0 | Nie | — |
| `info_rumor` | Plotka frakcyjna | Informacje | 15 | 0 | Tak* | — |
| `info_writ` | List żelazny | Informacje | 50 | 0 | Nie | — |

> *Plotka frakcyjna "traci ważność" — po X dniach staje się bezwartościowa (zdezaktualizowana).

### 1.2. Wartość vs waga (efektywność transportu)

Kluczowa metryka dla gracza: **złoto na jednostkę wagi**.

| Towar | zł/jedn. wagi | Opłacalność |
|-------|---------------|-------------|
| Ruda żelaza | 2.0 | ⭐ |
| Stal | 8.75 | ⭐⭐⭐ |
| Relikwia | 150.0 | ⭐⭐⭐⭐⭐ |
| Zboże | 1.67 | ⭐ |
| Jedwab | 70.0 | ⭐⭐⭐⭐ |
| Plotka | ∞ (waga 0!) | ⭐⭐⭐⭐⭐ (ale ryzyko dezaktualizacji) |

**Zasada balansu:** Im cięższy towar, tym niższa marża jednostkowa. Artefakty i informacje = wysokie ryzyko (zmienne ceny), wysokie zyski. Surowce = stabilne, niskie zyski, bezpieczne.

---

## 2. Formuła cenowa

### 2.1. Cena finalna

```
CENA = CENA_BAZOWA × M_LOKALNY × M_GEOPOL × M_SEZON × M_REPUTACJA
```

Gdzie:
- **M_LOKALNY** — mnożnik podaży/popytu miasta (0.5 do 2.0)
- **M_GEOPOL** — mnożnik sytuacji geopolitycznej (0.7 do 3.0)
- **M_SEZON** — mnożnik sezonowy (0.8 do 1.5)
- **M_REPUTACJA** — bonus od reputacji u frakcji (0.9 do 1.2)

### 2.2. Mnożnik lokalny — per miasto

Każde miasto ma przypisane:

| Pole | Opis |
|------|------|
| **Produkuje** | Lista towarów, które miasto wytwarza (podaż) |
| **Potrzebuje** | Lista towarów, na które jest popyt |
| **Mnożnik kupna** | Cena, po której miasto SPRZEDAJE (gracz kupuje) — im wyższa podaż, tym niższy mnożnik |
| **Mnożnik sprzedaży** | Cena, po której miasto KUPUJE (gracz sprzedaje) — im wyższy popyt, tym wyższy mnożnik |

**Algorytm:**
```
Jeśli miasto PRODUKUJE towar:
  M_KUPNA = 0.7   (tanio, bo lokalne)
  M_SPRZEDAŻY = 0.5 (słaba cena skupu, bo mają własne)

Jeśli miasto POTRZEBUJE towar:
  M_KUPNA = 1.5   (drogo, bo import)
  M_SPRZEDAŻY = 1.3 (dobra cena skupu, bo potrzebują)

Jeśli neutralne:
  M_KUPNA = 1.0
  M_SPRZEDAŻY = 0.8
```

### 2.3. Mnożnik geopolityczny

| Sytuacja | Towary wojenne | Artefakty | Żywność | Surowce |
|----------|----------------|-----------|---------|---------|
| Pokój | ×1.0 | ×1.0 | ×1.0 | ×1.0 |
| Napięcie | ×1.5 | ×1.2 | ×1.1 | ×1.1 |
| Wojna | ×2.5 | ×1.5 | ×1.5 | ×1.3 |
| Oblężenie | ×3.0 | ×2.0 | ×3.0 | ×2.0 |

### 2.4. Mnożnik sezonowy

| Pora roku | Żywność | Surowce | Inne |
|-----------|---------|---------|------|
| Wiosna | ×1.0 | ×1.0 | ×1.0 |
| Lato | ×0.8 | ×1.0 | ×1.0 |
| Jesień | ×0.9 | ×1.0 | ×1.0 |
| Zima | ×1.5 | ×1.3 | ×1.0 |
| Susza (event) | ×2.0 | ×1.0 | ×1.0 |
| Głód (event) | ×3.0 | ×1.0 | ×1.0 |

### 2.5. Mnożnik reputacji

| Reputacja | Mnożnik |
|-----------|---------|
| 0-20 (wróg) | ×1.5 (gorzej kupujesz), ×0.5 (gorzej sprzedajesz) |
| 21-40 (obcy) | ×1.2 / ×0.7 |
| 41-60 (neutralny) | ×1.0 / ×0.8 |
| 61-80 (przyjaciel) | ×0.9 / ×1.0 |
| 81-100 (sojusznik) | ×0.8 / ×1.2 |

---

## 3. Miasta — profile ekonomiczne (wstępny zestaw)

### 3.1. Twierdza Korin (Żelazna Unia)

| Atrybut | Wartość |
|---------|---------|
| **Frakcja** | Żelazna Unia |
| **Biom** | Równiny |
| **Produkuje** | `steel`, `weapons`, `armor`, `gunpowder` |
| **Potrzebuje** | `iron_ore`, `coal`, `grain`, `meat` |
| **Opis** | Wojskowa stolica Unii. Kuźnie pracują dzień i noc. Stal tania, żywność droga. |

### 3.2. Świątynia Ashvel (Zakon Płomienia)

| Atrybut | Wartość |
|---------|---------|
| **Frakcja** | Zakon Płomienia |
| **Biom** | Las Grozy |
| **Produkuje** | `relic`, `rune`, `scroll`, `incense` |
| **Potrzebuje** | `herbs`, `wine`, `silk`, `gems` |
| **Opis** | Klasztor-twierdza w sercu mrocznego lasu. Mnisi handlują artefaktami i wiedzą. |

### 3.3. Wolne Miasto Portowe (Wolne Grody)

| Atrybut | Wartość |
|---------|---------|
| **Frakcja** | Wolne Grody |
| **Biom** | Równiny (wybrzeże) |
| **Produkuje** | `grain`, `meat`, `wine`, `spices`, `silk` |
| **Potrzebuje** | `steel`, `weapons`, `gunpowder`, `coal` |
| **Opis** | Największy port kontynentu. Żywność i luksusy za bezcen. Brakuje obrony. |

### 3.4. Kopalnia Gorath (Wyklęci)

| Atrybut | Wartość |
|---------|---------|
| **Frakcja** | Wyklęci |
| **Biom** | Przełęcz Cieni |
| **Produkuje** | `iron_ore`, `coal`, `gems` |
| **Potrzebuje** | `grain`, `meat`, `herbs`, `weapons` |
| **Opis** | Nielegalna osada górnicza. Surowce za półdarmo. Nikt nie pyta o pochodzenie towaru. |

### 3.5. Wieża Obserwatorium (Zakon Płomienia)

| Atrybut | Wartość |
|---------|---------|
| **Frakcja** | Zakon Płomienia |
| **Biom** | Popioły |
| **Produkuje** | `info_map`, `info_rumor`, `info_writ`, `scroll` |
| **Potrzebuje** | `wood`, `coal`, `herbs`, `incense` |
| **Opis** | Odcięta od świata wieża magów. Informacje to ich waluta. |

---

## 4. Przykładowe transakcje (balans)

### 4.1. Trasa A: Twierdza Korin → Wolne Miasto Portowe

**W Twierdzy Korin (stal tania, bo produkują):**
- Kup 10 stali po `35 × 0.7 = 24.5 zł/szt` = **245 zł**, waga 40

**W Wolnym Mieście Portowym (potrzebują stali):**
- Sprzedaj 10 stali po `35 × 1.3 = 45.5 zł/szt` = **455 zł**

**Zysk:** 455 - 245 = **210 zł** (marża 86%)

### 4.2. Trasa B: Świątynia Ashvel → Kopalnia Gorath

**W Świątyni Ashvel (relikwie tanie, bo produkują):**
- Kup 3 relikwie po `150 × 0.7 = 105 zł/szt` = **315 zł**, waga 3

**W Kopalni Gorath (neutralne na artefakty):**
- Sprzedaj 3 relikwie po `150 × 0.8 = 120 zł/szt` = **360 zł**

**Zysk:** 360 - 315 = **45 zł** (marża 14% — słaba trasa! Lepsza w czasie wojny.)

### 4.3. Trasa C: spekulacja wojenna (Żelazna Unia w stanie wojny)

**W Twierdzy Korin (WOJNA — stal ×2.5):**
- Sprzedajesz stal (przywiezioną z Wolnych Grodów):
  - Cena sprzedaży: `35 × 2.5(wojna) × 1.3(potrzebują w czasie wojny) = 113.75 zł/szt`
  
**Zysk na 10 stali:** 1137 zł (zamiast 455 w czasie pokoju!)

---

## 5. Start gracza i progresja ekonomiczna

### 5.1. Stan początkowy

- Złoto: 50
- Wóz: 100 ładowności
- Osiołek: stary, 100% szybkości
- Towary: brak
- Miasto startowe: losowe (graniczne)

### 5.2. Kamienie milowe bogactwa

| Etap | Złoto | Co można kupić |
|------|-------|----------------|
| Biedak | 0-200 | Podstawowe towary, żywność |
| Handlarz | 200-1000 | Lepszy wóz (+50 ładowności = 500 zł) |
| Kupiec | 1000-5000 | Koń bojowy, artefakty, pancerz |
| Magnat | 5000+ | Najemnicy, forteca na kołach, wpływy polityczne |

### 5.3. Koszty stałe

| Pozycja | Koszt | Okres |
|---------|-------|-------|
| Żywność (dla woźnicy) | 3 zł/dzień | Dziennie |
| Pasza dla osiołka | 2 zł/dzień | Dziennie |
| Naprawa wozu | 10-50 zł | Po walce/uszkodzeniu |
| Cło graniczne | 5% wartości towaru | Przy wjeździe do miasta wrogiej frakcji |
| Łapówka | 20-100 zł | Opcjonalnie (omijasz cło) |
| Najemnik | 15 zł/dzień | Dziennie (jeśli zatrudniony) |

---

## 6. Balans — zasady

1. **Marża na surowcach:** 20-40% (niska, ale stabilna)
2. **Marża na artefaktach:** 50-200% (wysoka, ale zmienna i ryzykowna)
3. **Marża na informacjach:** 0-500% (zero wagi, ale dezaktualizacja)
4. **Marża w czasie wojny:** 100-400% na towarach wojennych (limitowana ładownością)
5. **Dzienne koszty stałe:** ~5-20 zł (presja na handel, nie można stać w miejscu)
6. **Czas podróży:** 1-5 dni między miastami (zależnie od biomu i osiołka)
7. **Złoto na godzinę gry:** cel ~200-500 zł/h na wczesnym etapie, ~1000-2000 zł/h na późnym

---

## 7. Do zrobienia (przed implementacją)

- [ ] Rozpisać pełną tabelę mnożników dla każdego miasta × każdego towaru (5 miast × 22 towary = 110 komórek — narzędzie `tools/price-sim.py`)
- [ ] Przetestować 10 tras na papierze i sprawdzić, czy żadna nie jest "zepsuta" (zysk >500% lub strata na każdej)
- [ ] Określić tempo zarabiania — ile dni gry do pierwszego upgrade'u?
- [ ] Zbalansować wagi towarów — czy 100 ładowności to dużo czy mało?
