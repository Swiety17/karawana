# Model Ekonomiczny — Karawana (SZKIELET)

> **Wersja:** 0.1.1 (szkielet — do wypełnienia po decyzjach)  
> **Powiązane decyzje:** checklist §4, §7, §8  
> **Uwaga:** Ten dokument wypełnimy PO podjęciu decyzji o systemie handlu.

---

## 1. Towary (szkielet)

> 🟡 Decyzje: 4.1, 4.2, 4.3

| Kategoria | Przykładowe towary | Psuje się? | Uwagi |
|-----------|--------------------|------------|-------|
| **TODO** | — | — | do ustalenia po decyzji 4.1 |

Struktura rekordu towaru (do wypełnienia):

| Pole | Opis |
|------|------|
| ID | `snake_case` |
| Nazwa | Wyświetlana |
| Kategoria | Surowce / Żywność / Broń / Artefakty / Luksusy / Informacje |
| Cena bazowa | W złocie |
| Waga | Jednostki ładowności |
| Psuje się? | Tak/Nie |
| Czas psucia | W dniach (jeśli tak) |

---

## 2. Formuła cenowa (szkielet)

> 🟡 Decyzje: 4.4, 4.5, 4.6, 4.7

Wzór (do doprecyzowania):

```
CENA = CENA_BAZOWA × [mnożniki]
```

Mnożniki do rozważenia:
- **Lokalny** — zależny od miasta (podaż/popyt)
- **Geopolityczny** — zależny od sytuacji frakcji
- **Sezonowy** — zależny od pory roku
- **Reputacyjny** — zależny od relacji gracza z frakcją
- **Targowania** — jeśli gracz może negocjować (4.5)

---

## 3. Miasta (szkielet)

> 🟡 Decyzje: 2.2, 2.4

Struktura profilu miasta (do wypełnienia):

| Pole | Opis |
|------|------|
| Nazwa | |
| Frakcja | |
| Biom | |
| Produkuje | Lista ID towarów (podaż — ceny niższe) |
| Potrzebuje | Lista ID towarów (popyt — ceny wyższe) |
| Opis | Flavor text |

Liczba miast: do ustalenia (2.2)

---

## 4. Start gracza

> 🟡 Decyzje: 3.1, 8.3

- Złoto startowe: `TODO`
- Ładowność startowa: `TODO`
- Inne zasoby: `TODO`

---

## 5. Koszty stałe

> 🟡 Decyzje: 5.4, 8.1

Potencjalne koszty dzienne / na podróż:
- Żywność (dla woźnicy)
- Pasza (dla zwierzęcia)
- Naprawy wozu
- Cła / łapówki
- Najemnicy

---

## 6. Balans i testy

> 🟡 Decyzje: 11.5

- Marże celowe: `TODO` (np. 20-40% na surowcach, 50-200% na artefaktach)
- Złoto na godzinę gry: `TODO`
- Czas do pierwszego upgrade'u: `TODO`
- Narzędzie testowe: `tools/price-sim.py` (do napisania)
