# Game Design Document — Wagoner

> **Wersja:** 0.2.0 (szkielet z decyzjami)  
> **Data:** 2026-06-16  
> **Status:** Sekcje 1-8 rozstrzygnięte. Sekcje 9-14 czekają na decyzje.

---

## 1. Elevator Pitch

**Wagoner** to single-player ekonomiczne RPG w dark fantasy. Zaczynasz jako woźnica-handlarz — kupujesz tanio, sprzedajesz drożej, rozbudowujesz tabor. Gdy uzbierasz dość bogactwa i reputacji, wchodzisz w geopolitykę: wpływasz na frakcje przez handel, informacje i dezinformację, kreujesz bohaterów z szeregowych NPC, budujesz swoją wersję endgame'u.

**Dominanta:** Ekonomia → Geopolityka. Zaczyna się od handlu, kończy na wpływie.

---

## 2. Core Loop

```
KUPUJ → PODRÓŻUJ → BROŃ SIĘ / UNIKAJ → SPRZEDAJ → UPGRADUJ →
  │                                                          │
  └────────── (gdy Finanse + Reputacja > próg) ──────────────┘
                               ↓
              WPŁYWAJ NA FRAKCJE / KREUJ BOHATERÓW / BUDUJ ENDGAME
```

---

## 3. System WPŁYWU (Influence)

### 3.1. Dwie statystyki

```
WPŁYW = FINANSE + REPUTACJA
```

- **Finanse** — złoto, majątek, faktorie, kompania handlowa. Mierzalne, widoczne.
- **Reputacja** — jak świat postrzega gracza. Mierzalna? → TAK, liczbowo (0-100), ale widoczna tylko przez reakcje NPC, dialogi i perki.

### 3.2. Progi wpływu

- Każdy NPC, miasto, frakcja, władca, heros ma swój poziom wpływu
- **Wpływ NPC jest UKRYTY** — gracz musi go oszacować
- Gracz może wpłynąć na NPC tylko gdy: `WPŁYW_GRACZA > WPŁYW_NPC`
- **Wyjątki:** szantaż (gdy gracz ma kompromitującą informację), dług wdzięczności (NPC "winien" graczowi), charakter NPC (szemrany łatwiej ulega pieniądzom mimo różnicy wpływu)
- **Siła wpływu** rośnie z różnicą wpływów (większa przewaga = silniejszy efekt). Dokładna formuła → do testów w praktyce (A5).

### 3.3. Jak gracz ocenia wpływ NPC?

| Poziom gracza | Co widzi |
|---------------|----------|
| Bez perków, bez znajomości | Tylko przez rozmowy, ton dialogów, wygląd NPC, strój |
| Perk "Znajomości" (poziom 1) | Dodatkowe wskazówki w dialogach, znajomi podpowiadają |
| Perk "Sieć informacyjna" (poziom 2) | Raporty o ważnych postaciach, przybliżony poziom wpływów |
| Perk "Siatka szpiegowska" (poziom 3) | Dokładne informacje, przewidywanie decyzji NPC |

Dodatkowo: nastawienie NPC (wrogo / przyjaźnie / ze strachem) widać od razu — to też wskazówka o charakterze.

---

## 4. Endgame

### 4.1. Cztery szablony (kształtowane przez decyzje gracza)

| Szablon | Opis | Jak osiągnąć |
|---------|------|-------------|
| **Król Kupców** | Monopol handlowy, kontrolujesz rynek, frakcje tańczą jak zagrasz | Przez handel, wykup towarów, faktorie |
| **Władca** | Własne księstwo/terytorium, poddani, armia | Przez sojusze, małżeństwa polityczne, przewroty |
| **Mistrz Intryg** | Nikt nie wie kim jesteś, ale pociągasz za wszystkie sznurki | Przez informacje, szantaż, dezinformację |
| **Niezależny Magnat** | Bogaty outsider — nie grasz w politykę, ale masz na wszystko wpływ przez pieniądze | Przez czysty handel, ignorowanie frakcji |

### 4.2. Charakter endgame'u

- **Sandboksowy** — nie ma ekranu "wygrana". Osiągasz stan i grasz dalej.
- **Większa skala** dotychczasowych mechanik (nie nowe systemy, ale większe liczby, więcej opcji, wyższe stawki).

---

## 5. NPC i Bohaterowie

### 5.1. Typy NPC

**Ustaleni bohaterowie** — generałowie frakcji, legendarni kupcy, mistrzowie cechów, słynni bandyci. Mają imiona, portrety, historię. Działają niezależnie. Są znani z "książek fantasy" tego świata.

**Szeregowi NPC** — żołnierze, kupcy, chłopi, złodzieje. Mogą zostać wyniesieni przez gracza.

### 5.2. Charaktery NPC (więcej niż 3, pełna lista do rozpisania)

NPC mają wielowymiarowy charakter. Przykładowe osie:
- Szlachetny ↔ Szemrany
- Odważny ↔ Tchórzliwy
- Lojalny ↔ Przekupny
- Inteligentny ↔ Naiwny

**Charakter jest ukryty** — gracz poznaje go narracyjnie: przez dialogi, interakcje, wygląd, strój, decyzje NPC, plotki o nim.

### 5.3. Dług wdzięczności

- **Narracyjny, nieliczbowy.**
- NPC "pamięta" co gracz dla niego zrobił i reaguje kontekstowo.
- Szlachetny NPC: odwdzięczy się z dobrej woli, trudniej go przekupić.
- Szemrany NPC: odwdzięczy się gdy musi, łatwiej go przekupić.
- Biedak/złodziej: pieniądze grają główną rolę.

### 5.4. Zdrada NPC

Przyczyny:
- Charakter NPC (szemrany łatwiej zdradza)
- Decyzje gracza (podpadł komuś, kto przekupił NPC)
- Lepsza oferta od konkurencji
- Losowe wydarzenia
- Pomyłka (NPC źle zinterpretował rozkaz)

### 5.5. Kreowanie bohaterów

**Proces (zwykle długi, kilka interakcji):**
1. Gracz daje NPC coś wartościowego: informację, towar, pieniądze
2. NPC wykorzystuje to → awansuje (np. zwykły żołnierz zostaje dowódcą po tym, jak gracz dał mu cynk o ataku)
3. NPC ma dług wdzięczności u gracza
4. NPC służy celom gracza: dostarcza informacji, handluje, manipuluje, jest przeciwnikiem dla wrogów gracza

**Wartość "daru":** Informacja > Towar > Pieniądze. (Informacja może dać największy awans — np. uratowanie księżniczki.)

### 5.6. Działanie NPC

- **Aktywnie** — na żądanie gracza
- **Pasywnie** — przynoszą dochód, informacje, przewagę, działają w tle

---

## 6. System Handlu jako Wpływu

### 6.1. Realne limity towarów

- Miasto produkuje X towaru dziennie (np. 10 stali)
- Gdy gracz wykupuje wszystko → ceny rosną, ale magazyny się wypełniają
- Miasto-producent regeneruje szybciej (wydobywa)
- Miasto-importer regeneruje wolniej (musi kupić, mając mniejszy budżet)

### 6.2. Reakcje frakcji na ruchy gracza

- Oferty współpracy
- Szantaż
- Mechanizmy rynkowe (jak na giełdzie)
- Zależy od **charakteru frakcji** i jej przywódców

### 6.3. Celowe wywoływanie kryzysów

- Gracz MOŻE wywołać kryzys (np. głód przez wykup zboża)
- Budzi to **wrogość** (u poszkodowanych) lub **podziw** (u ich wrogów)
- Może też wykorzystać pozytywne wydarzenia

---

## 7. Informacja jako Towar i Broń

### 7.1. Termin ważności

- Informacje **dezaktualizują się**
- Im szybciej gracz się dowie (przed innymi), tym wyższa wartość
- Gdy informacja staje się powszechna → wartość = 0

### 7.2. Kłamstwo / Dezinformacja

- Gracz może AKTYWNIE stworzyć fałszywą informację
- Za pomocą **szablonu** (do zaprojektowania na późniejszym etapie)
- Opcje: przekupienie herolda, plotka w karczmie, fałszywy list

### 7.3. Konsekwencje kłamstwa

- Jeśli wyszło na jaw: utrata reputacji, zemsta frakcji
- Ryzyko proporcjonalne do skali kłamstwa

### 7.4. Informacja popycha do działania

- Gracz daje NPC informację
- NPC na podstawie swojego **charakteru** podejmuje autonomiczną akcję w świecie
- Gracz NIE kontroluje, CO dokładnie NPC zrobi — może przewidzieć na podstawie znajomości jego charakteru

---

## 8. System Walki — "Taktyczne Wybory Narracyjne"

### 8.1. Fundament

- **Nie zręcznościowa** — oparta na statystykach, nie skillu gracza
- **5 wyborów taktycznych** w kontekście narracyjnym
- **5-10 minut** na jedną walkę
- **Zawsze można uniknąć walki** — nie ma walk wymuszonych bez opcji wyboru
- Loot jest, ale **nie jest głównym źródłem nagród** (raczej informacje, artefakty)

### 8.2. Przebieg

Walka to seria **do 5 punktów decyzyjnych**, każdy z 2-4 opcjami:

```
== PUNKT 1/5 ==
Bandyci blokują trakt. Ich herszt szczerzy zęby.

Dostępne opcje:
[1] Strzał z kuszy (wymaga: kusza) — atak dystansowy
[2] Tarcza + kontratak (wymaga: tarcza) — defensywa
[3] Przekupić (koszt: ~50 zł, zależne od charakteru bandytów)
[4] Zastraszyć (szansa zależna od Reputacji + charakter bandytów)
[5] Rzucić bombą dymną (wymaga: bomba dymna w ekwipunku) — ucieczka
```

- Liczba opcji zależy od sprzętu, towarzyszy, statystyk
- Każdy towarzysz dodaje 1 opcję (narracyjną lub taktyczną)
- Sprzęt odblokowuje opcje (brak łuku = brak ataku dystansowego, brak tarczy = brak bloku)

### 8.3. Szanse powodzenia

- **70% statystyki + 30% los** (w stylu D&D)
- Gracz **NIE widzi** liczbowych szans
- Efekty są opisane narracyjnie: "Pewnym ruchem napinasz kuszę...", "Drżącą ręką sięgasz po miecz..."

### 8.4. Stawka

- Można **zginąć** (śmierć woźnicy)
- Można stracić **towar**
- Można stracić **towarzyszy / najemników**
- Można stracić **konia** (→ towar musi zostać ukryty, gracz wraca po niego później)

### 8.5. Konsekwencje — eskalacja

- Zabicie znaczącego przeciwnika → **reputacja rośnie** (u jednych), **chęć zemsty** (u innych)
- Gracz może dowiedzieć się, że zabił "kogoś" przez: loot, plotki, informacje, dialogi, atak zemsty
- Perki pozwalają rozpoznać ważne osoby (herby, insygnia)

### 8.6. Towar po stracie konia

- **Stała mechanika:** towar ukryty przy trakcie czeka X dni
- Gracz musi wrócić z nowym koniem/wózkiem zanim towar zniknie

---

## 9. Perki (szkielet)

### 9.1. Drzewko

- Perki w formie **drzewka** — są wymagania (nie można mieć siatki szpiegów bez pierwszego szpiega)
- Kupowane za punkty (zdobywane z progresją)
- **Powiązane z frakcjami** (osobne gałęzie: sieć w Unii, sieć w Zakonie)
- **Można stracić** (przez zdradę, złą decyzję, utratę reputacji)

### 9.2. Poziomy widoczności informacji

| Poziom | Perk | Co daje |
|--------|------|---------|
| 0 | Brak | Tylko ceny na targowisku i ogólne plotki |
| 1 | Znajomości | Dodatkowe wskazówki w dialogach, podstawowe informacje |
| 2 | Sieć informacyjna | Raporty, przybliżony poziom wpływów NPC |
| 3 | Siatka szpiegowska | Dokładne informacje, przewidywanie decyzji NPC |

---

## 10-14. Sekcje nierozstrzygnięte

> 🟡 Czekają na decyzje z checklist §9–§13:
> - Interfejs i prezentacja
> - Grafika i dźwięk
> - Techniczne (część rozstrzygnięta: Godot 4, platformy PC+Mac)
> - Narracja
> - Inspiracje i referencje
