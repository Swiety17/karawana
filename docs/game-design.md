# Game Design Document — Karawana

> **Wersja:** 0.1.0 (draft)  
> **Data:** 2026-06-16  
> **Autor:** Przemek + Rychu (Alfred)  
> **Repo:** https://github.com/Swiety17/karawana

---

## 1. Elevator Pitch

**Karawana** to single-player RPG ekonomiczne w klimacie dark fantasy. Wcielasz się w woźnicę-handlarza przemierzającego mroczny, podzielony wojnami świat. Handlujesz artefaktami, surowcami i informacjami między frakcjami. Rozwijasz swój wóz, ulepszasz ekwipunek, bronisz taboru przed bandytami i potworami. Każda decyzja handlowa wpływa na geopolitykę — możesz nieświadomie dostarczyć broń stronie, która jutro podbije twoje rodzinne miasto.

**Gatunek:** Ekonomiczne RPG z elementami survivalu i taktycznej obrony taboru  
**Perspektywa:** Top-down 2D (jak Stardew Valley)  
**Styl graficzny:** Pixel art 32×32, mroczna paleta (dark fantasy)  
**Platforma:** PC + Mac  
**Gracze:** Single-player

---

## 2. Setting — Mroczny Świat Podzielony Wojną

### 2.1. Świat w pigułce

Świat nie ma jednej nazwy — różne kultury nazywają go inaczej. To kontynent rozbity na frakcje po upadku Starego Imperium. Od stu lat trwa era **Rozbicia** — pomniejsze królestwa, republiki kupieckie i teokracje walczą o wpływy. Nikt nie pamięta czasów jedności. Trakty handlowe, niegdyś bezpieczne, teraz są areną dla bandytów, dezerterów i plugawych kreatur, które wyczuły słabość cywilizacji.

### 2.2. Rola woźnicy-handlarza

W tym świecie karawaniarze to jedyna stała. Nie należą do żadnej frakcji — są solą ziemi, która trzyma resztki cywilizacji w kupie. Bez nich miasta głodują, armie rdzewieją bez stali, a wiedza ginie. Woźnica to zawód szanowany... i niebezpieczny. Każdy trakt może być tym ostatnim.

---

## 3. Core Loop — Pętla Rozgrywki

```
┌─────────────────────────────────────────────────────────┐
│                                                         │
│   KUPUJ                PODRÓŻUJ             SPRZEDAJ    │
│   ┌─────┐            ┌─────────┐           ┌───────┐   │
│   │Miasto│ ──trakt──→│  BIOM(Y) │──trakt──→│ Miasto│   │
│   │  A   │           │ • spotkania        │   B   │   │
│   │towary│           │ • obrona taboru    │ceny $$│   │
│   └─────┘            │ • wydarzenia       └───────┘   │
│       ↑              └─────────┘              │        │
│       │                                       ↓        │
│       │         ◄─── UPGRADUJ ────      ZARABIAJ      │
│       │         (wóz, osiołek, bronie)                 │
│       └───────────────────────────────────────────────│
└─────────────────────────────────────────────────────────┘
```

### 3.1. Fazy pętli

1. **W mieście (Faza handlu)**
   - Przeglądasz towary na rynku, sprawdzasz ceny
   - Kupujesz tanio, analizujesz popyt w innych miastach
   - Zbierasz plotki (informacje = przewaga handlowa)
   - Naprawiasz wóz, ulepszasz ekwipunek
   - Wybierasz cel podróży

2. **Na trakcie (Faza podróży)**
   - Wóz porusza się po mapie świata w czasie rzeczywistym (lub turowym?)
   - Przemierzasz biomy — każdy ma własne zagrożenia i tempo podróży
   - Losowe spotkania: bandyci, potwory, kupcy, uchodźcy, patrole
   - Obrona taboru — prosta walka taktyczna
   - Zarządzanie zasobami: żywność, pochodnie, części zamienne do wozu

3. **W mieście docelowym (Faza sprzedaży)**
   - Sprzedajesz towary — ceny zależne od lokalnego popytu/podaży i geopolityki
   - Aktualizujesz wiedzę o świecie (co się zmieniło)
   - Decydujesz: wracasz, jedziesz dalej, czy zostajesz na dłużej?

---

## 4. Systemy Gry

### 4.1. System Handlu

**Towary** dzielą się na kategorie:

| Kategoria | Przykłady | Cechy |
|-----------|-----------|-------|
| **Surowce** | Ruda żelaza, drewno, węgiel, zioła | Ciężkie, tanie, stabilne ceny |
| **Artefakty** | Starożytne relikwie, magiczne komponenty, runy | Drogie, lekkie, zmienne ceny |
| **Żywność** | Zboże, suszone mięso, wino, przyprawy | Psuje się z czasem, sezonowe |
| **Towary wojenne** | Stal, broń, pancerze, proch | Ceny skaczą przy konfliktach |
| **Informacje** | Mapy, listy żelazne, plotki frakcyjne | Ważą nic, wartość zmienna |
| **Luksusy** | Jedwab, klejnoty, kadzidła | Ekstremalnie drogie, tylko bogate miasta |

**Mechanika cen:**
- Każde miasto ma **cenę bazową** dla każdego towaru
- Cena = cena_bazowa × **mnożnik lokalny** × **mnożnik geopolityczny** × **mnożnik sezonowy**
- Mnożnik lokalny: podaż (czy miasto produkuje towar) i popyt (czy potrzebuje)
- Mnożnik geopolityczny: wojna = +200% cena stali, pokój = -30%
- Mnożnik sezonowy: zima = +50% żywność, susza = +100% woda

**Ładowność wozu:**
- Bazowo: 100 jednostek
- Upgrade'y: +50 / +100 / +200
- Każdy towar ma wagę: surowce = 5, artefakty = 1, żywność = 3, broń = 4

### 4.2. System Podróży

**Mapa świata** — top-down 2D, tilemapa. Widoczne są:
- Miasta (węzły handlowe)
- Trakty (ścieżki między miastami)
- Biomy (zmieniające się tereny)
- Punkty orientacyjne (ruiny, źródła, warownie)

**Ruch wozu:**
- Kliknięcie na miasto → wóz jedzie traktem
- Szybkość zależna od: biomu, stanu wozu, kondycji osiołka, pogody
- Postoje: gracz może zatrzymać wóz w dowolnym momencie (biwak)

**Biomy — wpływ na podróż:**

| Biom | Szybkość | Zagrożenie | Efekt specjalny |
|------|----------|------------|-----------------|
| **Las Grozy** | 80% | Wysokie | Mgła — ograniczona widoczność |
| **Martwe Bagna** | 40% | Bardzo wysokie | Trujące opary — obrażenia pasywne |
| **Popioły (pustkowia)** | 100% | Niskie | Brak wody — zużycie zasobów ×2 |
| **Przełęcz Cieni** | 60% | Wysokie | Lawiny — losowe uszkodzenia wozu |
| **Równiny** | 120% | Niskie | Bezpieczna podróż |
| **Ziemie Przeklęte** | 50% | Bardzo wysokie | Nekrotyczne — szansa na utratę towaru |

### 4.3. System Walki / Obrony Taboru

**Koncepcja:** Walka nie jest główną mechaniką — to taktyczna minigra obrony taboru.

**Wyzwalanie:** Losowe spotkanie na trakcie. Przy złej pogodzie lub w niebezpiecznym biomie — wyższa szansa.

**Przebieg walki (dwa warianty do wyboru):**

*Wariant A — turowa, taktyczna:*
- Plansza 5×7 pól (wóz pośrodku)
- Gracz kontroluje woźnicę + ewentualnych najemników
- Przeciwnicy podchodzą z krawędzi planszy
- Cel: przetrwać X tur, chroniąc wóz i towar
- Umiejętności: strzał z kuszy, pułapka, tarcza, leczenie

*Wariant B — automatyczna z interwencją:*
- Walka rozgrywa się automatycznie (animacja + rzuty kośćmi)
- Gracz wybiera taktykę PRZED walką: agresywna / defensywna / ucieczka
- Podczas walki może użyć jednorazowych przedmiotów (bomba dymna, święcona woda)
- Wynik zależy od statystyk wozu, broni i wybranej taktyki

**Rekomendacja:** Wariant B na start (MVP) → wariant A jako rozwinięcie.

### 4.4. System Geopolityczny

**Frakcje (3-4):**

| Frakcja | Charakter | Specjalizacja |
|---------|-----------|---------------|
| **Żelazna Unia** | Militarystyczna republika kupiecka | Stal, broń, najemnicy |
| **Zakon Płomienia** | Teokracja, fanatycy religijni | Artefakty, relikwie, informacje |
| **Wolne Grody** | Luźna federacja miast | Żywność, rzemiosło, luksusy |
| **Wyklęci** | Banici, heretycy, uchodźcy | Wszystko po okazyjnych cenach, wysokie ryzyko |

**Relacje między frakcjami:**
- Pokój → handel kwitnie, ceny stabilne
- Napięcie → cła, kontrole na granicach
- Wojna → blokady, ceny stali +200%, dostępność -50%

**Wydarzenia geopolityczne (losowe, periodyczne):**
- Wybuch wojny między frakcjami
- Podpisanie rozejmu
- Odkrycie złoża (ceny surowca spadają)
- Zaraza (miasto zamknięte, handel wstrzymany)
- Zamach na przywódcę (chaos, zmiana cen)

**Wpływ gracza:** Handel z frakcją podczas wojny → poprawa relacji, lepsze ceny. Sprzedaż broni → eskalacja konfliktu.

### 4.5. System Progresji

**Wóz — upgrade'y:**

| Poziom | Ładowność | Pancerz | Cecha specjalna |
|--------|-----------|---------|-----------------|
| Bieda-wóz | 100 | 0 | Brak |
| Wzmocniony | 150 | 10 | Mniej uszkodzeń w walce |
| Karawana | 200 | 25 | +1 najemnik |
| Forteca na kołach | 300 | 50 | +2 najemnicy, pułapki |

**Osiołek:**

| Poziom | Szybkość | Wytrzymałość | Cecha |
|--------|----------|-------------|-------|
| Stary osioł | 100% | 100% | — |
| Młody muł | 120% | 120% | Szybszy na równinach |
| Koń bojowy | 140% | 150% | Nie płoszy się w walce |
| Rumak cienia | 160% | 200% | Szybszy nocą, ignoruje strach |

**Ekwipunek woźnicy:**

- Broń: kusza (atak dystansowy), szabla (atak wręcz), bicz (odstraszanie)
- Pancerz: skórzany, kolczuga, napierśnik
- Narzędzia: zestaw naprawczy, pochodnie, lina, kompas
- Przedmioty specjalne: kości wróżebne, mapa skarbów, glejt kupiecki

**Reputacja:**
- U każdej frakcji osobno (0-100)
- Wysoka reputacja → lepsze ceny, dostęp do zakazanych towarów, eskorta
- Niska → cła, odmowa handlu, ataki

---

## 5. Postać Gracza

### 5.1. Kim jest woźnica?

Gracz zaczyna z niczym — starym wozem, kulawym osiołkiem i kilkoma monetami. Nie ma imienia, przeszłości ani domu. To **tabula rasa** — sami definiujemy, kim jesteśmy poprzez wybory.

- **Płeć:** Do wyboru (mężczyzna / kobieta) — kosmetyczne
- **Start:** Losowe miasto graniczne, podstawowy wóz, 50 złota
- **Cel:** Nie ma jednego. To sandbox. Cele gracza: przetrwanie, bogactwo, reputacja, odkrycie tajemnic świata

### 5.2. Statystyki

| Statystyka | Opis |
|------------|------|
| **Targowanie** | Lepsze ceny kupna/sprzedaży |
| **Percepcja** | Wykrywanie zagrożeń na trakcie, lepsze okazje handlowe |
| **Walka** | Skuteczność w obronie taboru |
| **Wiedza** | Znajomość artefaktów, języków frakcji, geopolityki |
| **Charyzma** | Negocjacje, dostęp do informacji, rekrutacja najemników |

---

## 6. Interfejs — szkic

### 6.1. Widok mapy świata

```
┌────────────────────────────────────────────────────┐
│  ☀ Dzień 47   🪙 2345 zł   🛡️ Rep: Unia 45       │
│                                                    │
│              🌲 Las Grozy 🌲                       │
│    [Miasto A]─────🚜──────[Ruiny]                  │
│         │                              🏔️         │
│         │                           Przełęcz      │
│    [Miasto B]──────[Miasto C]                     │
│              🌫️ Martwe Bagna 🌫️                   │
│                                                    │
│  🛞 Stan wozu: 85%  🐴 Kondycja: 90%              │
│  📦 Ładunek: 67/100  🍞 Żywność: 12 dni           │
└────────────────────────────────────────────────────┘
```

### 6.2. Widok handlu (w mieście)

```
┌────────────────────────────────────────────────────┐
│  Rynek — Żelazna Unia (Twierdza Korin)             │
│                                                    │
│  Twoje złoto: 2345 🪙    Ładowność: 67/100        │
│                                                    │
│  ┌─────────────────────────────────────────────┐  │
│  │ Towar          │ Kupno  │ Sprzedaż │ Waga   │  │
│  │─────────────────────────────────────────────│  │
│  │ Ruda żelaza    │  12 zł │   8 zł   │   5    │  │
│  │ Stal 🚀        │  45 zł │  35 zł   │   4    │  │
│  │ Artefakt ✨     │ 200 zł │ 150 zł   │   1    │  │
│  │ Suchary        │   5 zł │   3 zł   │   3    │  │
│  │ ...            │        │          │        │  │
│  └─────────────────────────────────────────────┘  │
│                                                    │
│  [KUP] [SPRZEDAJ] [PLOTKI] [WYJEDŹ]              │
└────────────────────────────────────────────────────┘
```

🚀 = cena wzrosła (wojna), ✨ = okazja, 📉 = cena spadła

### 6.3. Widok obrony taboru (koncepcyjny)

```
┌────────────────────────────────────────────────────┐
│  ⚔️ OBRONA TABORU — Bandyci atakują!              │
│                                                    │
│     🏹  ⚔️  💣                                    │
│    [strzał] [atak] [przedmiot]                     │
│                                                    │
│   🛡️ Wóz: 85%    ❤️ Woźnica: 3/3                 │
│                                                    │
│   [UC IEKAJ]  — 30% szansy, stracisz część ładunku│
└────────────────────────────────────────────────────┘
```

---

## 7. Inspiracje — co z czego czerpiemy

| Gra | Co czerpiemy |
|-----|-------------|
| **Stardew Valley** | Pixel art, top-down, relacje z NPC, pętla dnia, upgrade'y, klimat |
| **Battle Brothers** | Dark fantasy, mapa świata, losowe spotkania, zarządzanie drużyną |
| **Vagrus** | Karawana handlowa, dark fantasy, narracja, zarządzanie zasobami |
| **Moonlighter** | System handlu, dynamiczne ceny, łączenie walki i ekonomii |
| **FTL** | Podróż między punktami, losowe wydarzenia, zarządzanie kryzysowe |
| **Mount & Blade** | Ekonomia karawanowa, geopolityka, frakcje |
| **Darkest Dungeon** | Mroczny klimat, zarządzanie stresem, świadome ryzyko |

---

## 8. Etapy rozwoju

### MVP (Minimum Viable Product)

1. Mapa świata z 3 miastami, 2 biomami, traktami
2. Ruch wozu (kliknięcie na miasto)
3. System handlu: towary, ceny, kupno/sprzedaż
4. Podstawowy HUD: złoto, ładowność, stan wozu
5. Jedno losowe spotkanie (bandyci) + automatyczna walka
6. Jeden upgrade (lepszy wóz)

### v0.2

1. Wszystkie biomy i miasta
2. System geopolityczny (relacje frakcji)
3. Informacje/plotki jako towar
4. Więcej spotkań na trakcie
5. Progresja (statystyki, reputacja)

### v1.0

1. Pełna walka taktyczna
2. Fabuła / questy
3. Sezony i pogoda
4. Najemnicy
5. Tajemnice świata (endgame)

---

## 9. Otwarte pytania projektowe

1. **Czas w grze:** Rzeczywisty (jak Stardew — dzień trwa X minut) czy system turowy (dzień mija po każdym trakcie)?
2. **Walka:** Wariant A (taktyczna, turowa) czy B (automatyczna z wyborem taktyki)?
3. **Nazwa gry:** Karawana, Mroczny Trakt, Woźnica, Karawaniarz...?
4. **Permadeath?** Czy śmierć woźnicy to koniec gry (roguelike) czy restart od ostatniego miasta?
5. **Narracja:** Czy są dialogi, questy, fabuła główna? Czy czysty sandbox?
6. **NPC w miastach:** Czy są postaci z twarzami/portretami i dialogami? Czy tylko interfejs handlowy?
