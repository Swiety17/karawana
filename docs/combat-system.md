# System Walki — Wagoner

> **Wersja:** 0.2.0  
> **Mechanika:** Taktyczne Wybory Narracyjne (5 decyzji, statystyki 70/30)

---

## 1. Fundament

- **Nie zręcznościowa** — zero skill-shota, zero refleksu
- Oparta na **statystykach gracza, sprzęcie, towarzyszach**
- **5 punktów decyzyjnych** (tur), każdy z 2-5 opcjami
- **5-10 minut** na całą walkę
- **Zawsze można uniknąć walki** — każda walka oferuje wybór: walcz / przekup / uciekaj / dyplomacja

---

## 2. Anatomia punktu decyzyjnego

### Szablon

```
== PUNKT X/5 ==
[Opis sytuacji — 1-2 zdania, narracyjnie, klimatycznie]

Dostępne opcje:
[N] [Nazwa opcji] (wymaganie: X) — [krótki opis efektu]
[N] ...
[N] [Ucieczka] — zawsze dostępna, szansa zależna od szybkości/statystyk
```

### Przykład

```
== PUNKT 1/5 ==
Bandyci blokują trakt. Ich herszt szczerzy spróchniałe zęby i domaga się "opłaty za przejazd".

[1] Strzał z kuszy (wymaga: kusza) — celujesz w herszta
[2] Tarcza i kontratak (wymaga: tarcza) — bronisz pozycji przy wozie  
[3] Przekupić (koszt: ~50 zł) — rzucić sakiewkę
[4] Zastraszyć — powołujesz się na ochronę Żelaznej Unii
[5] Bomba dymna (wymaga: bomba dymna) — ucieczka w chaosie
```

---

## 3. Źródła opcji

| Źródło | Co daje |
|--------|---------|
| **Postać gracza** | Opcje podstawowe (zawsze 2-3 bazowe: walcz wręcz, przekup, uciekaj) |
| **Sprzęt** | Odblokowuje konkretne opcje (kusza → strzał, tarcza → blok, bomba → ucieczka) |
| **Towarzysze** | Każdy dodaje 1 opcję (narracyjną lub taktyczną) |
| **Statystyki** | Modyfikują szanse powodzenia (ukryte) |
| **Reputacja** | Odblokowuje opcje dyplomatyczne/zastraszenia |

**Zasada:** Brak sprzętu = brak opcji. Bez kuszy nie strzelisz. Bez tarczy nie zablokujesz.

---

## 4. Szanse — formuła 70/30

```
Szansa powodzenia = 0.7 × STATYSTYKA + 0.3 × LOS
```

- **Gracz NIE widzi liczbowych szans**
- Efekty opisane narracyjnie, pośrednio sugerujące prawdopodobieństwo:
  - "Pewnym ruchem napinasz kuszę..." → wysokie szanse
  - "Drżącą ręką sięgasz po miecz..." → niskie szanse
  - "Wahasz się przez moment..." → ~50/50

---

## 5. Stawka — co można stracić

| Straty | Mechanika |
|--------|-----------|
| **Życie** | Śmierć woźnicy = koniec gry / restart |
| **Towar** | Kradzież, zniszczenie części ładunku |
| **Towarzysze** | Śmierć lub ucieczka najemnika/towarzysza |
| **Koń** | Zabity → towar trzeba ukryć przy trakcie, wrócić po niego później |
| **Stan wozu** | Uszkodzenia wymagające naprawy |
| **Reputacja** | Wzrost (gdy zabijesz bandytę) lub spadek (gdy uciekniesz) |

---

## 6. Towar po stracie konia (stała mechanika)

1. Koń pada → gracz ukrywa towar przy trakcie
2. Gracz wraca do ostatniego miasta piechotą (lub okazją)
3. Towar czeka **X dni** (zależne od biomu)
4. Gracz musi wrócić przed upływem czasu
5. Inny handlarz może znaleźć towar (szansa losowa)

---

## 7. Eskalacja — konsekwencje zabicia znaczącego przeciwnika

### Rozpoznanie

Gracz dowiaduje się, że zabił "kogoś" przez:
| Kanał | Czas |
|-------|------|
| **Loot** | Od razu — herb, pierścień, list |
| **Perki (heraldyka)** | Od razu — rozpoznajesz insygnia |
| **Plotki** | 1-3 dni — wieść się rozchodzi |
| **Atak zemsty** | 3-14 dni — ktoś przychodzi po twoją głowę |
| **Informacje od NPC** | Zmiennie — agenci donoszą |

### Konsekwencje

- **Reputacja rośnie** u wrogów zabitego
- **Reputacja spada** u sojuszników zabitego
- **Chęć zemsty** — frakcja/rodzina może wysłać pościg
- **Nowe opcje handlowe** — ktoś chce wynagrodzić "bohatera"

---

## 8. Typy spotkań

| Typ | Przykład | Częstotliwość |
|-----|----------|---------------|
| Bandyci | Zwykli rabusie, dezerterzy | Częste |
| Potwory | Plugawa kreatura, nieumarli | Rzadkie (ciemne biomy) |
| Frakcyjne patrole | Żołnierze Unii, mnisi Zakonu | Zależne od biomu i geopolityki |
| Inni handlarze | Konkurencja, zagubieni kupcy | Rzadkie |
| Zasadzka | Zaplanowany atak (ktoś chce twojej głowy) | Bardzo rzadkie |
| Blokada | Frakcja blokuje trakt | Tylko w czasie wojny/napięcia |

---

## 9. Opcje unikania walki (zawsze dostępne)

| Opcja | Szansa | Koszt |
|-------|--------|-------|
| **Przekupstwo** | Wysoka | Złoto (skaluje się z siłą przeciwnika) |
| **Ucieczka** | Zależna od szybkości (koń, biom) | Utrata czasu, może uszkodzić wóz |
| **Dyplomacja** | Zależna od Reputacji + charakteru przeciwnika | Nic |
| **Skradanie** | Zależne od perków, biomu | Nic (wymaga perka) |
| **Zastraszenie** | Zależne od Reputacji | Nic, ale może eskalować |

---

## 10. Loot

- **Nie jest głównym źródłem nagród**
- Po walce można znaleźć: złoto, informacje (list, mapa), artefakt, ekwipunek
- Loot zależy od typu przeciwnika:
  - Bandyci → złoto, czasem informacja o kryjówce
  - Patrol frakcyjny → insygnia, rozkazy (informacja!)
  - Potwór → artefakt, część plugawej istoty (handel z Zakonem)

---

## 11. Walka z bossem / znaczącym NPC

- Rzadkie wydarzenie (quest, zemsta, geopolityka)
- Do 5 punktów decyzyjnych, ale wyższa stawka
- Może wymagać konkretnego sprzętu / towarzyszy
- Konsekwencje rozchodzą się po całym świecie

---

## 12. Do rozpisania (przyszłe iteracje)

- [ ] Pełna lista opcji walki (bazowych, sprzętowych, towarzyskich)
- [ ] Tabela statystyk wpływających na szanse
- [ ] Algorytm szans (co konkretnie wpływa na `STATYSTYKA` w formule)
- [ ] Szablon spotkań per biom
- [ ] Balans: ile złota za przekup, szanse ucieczki
