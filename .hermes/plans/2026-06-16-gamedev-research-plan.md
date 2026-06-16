# GameDev Plan — "Karawana" — Dark Fantasy Trading RPG

> **Dla Rycha:** Research, wybór narzędzi, przygotowanie środowiska, spike walidacyjny.

**Goal:** Przygotować kompletne środowisko deweloperskie i zwalidować koncept gry o woźnicy-handlarzu w świecie dark fantasy.

**Architecture:** Godot 4 (silnik), LibreSprite (pixel-art), Python (tooling pomocniczy). Spike: mapa 2D z ruchem wozu + prosty handel między miastami.

**Tech Stack:** Godot 4.x (GDScript), LibreSprite / Aseprite, Git + GitHub

---

## 🎮 Brief gry (od Pana Przemka)

> Woźnica/handlarz w świecie **dark fantasy**. Jeździ traktami w swoim wozie z osiołkiem od miasta do miasta, handlując artefaktami, zasobami i innymi itemami. Czasem też informacjami. Różne biomy. Różna sytuacja geopolityczna. Upgrade'y wozu i osprzętu. Prosta mechanika walki/obrony taboru.

**Styl:** Stardew Valley (top-down 2D pixel-art, cozy w formie, dark w treści)
**Setting:** Czyste fantasy (własny świat)
**Gracze:** Single-player
**Platforma:** PC + Mac
**Assety:** Gotowe dozwolone (itch.io, OpenGameArt)

---

## 🎯 Koncept — „Karawana"

### Pętla rozgrywki

```
KUPUJ w mieście A → PODRÓŻUJ przez biom(y) → BROŃ się / UNIKAJ → SPRZEDAJ w mieście B → UPGRADUJ → KUPUJ...
```

### Główne systemy

| System | Opis |
|--------|------|
| **Handel** | Dynamiczne ceny między miastami. Arbitraż: kup tanio, sprzedaj drogo. Towary: artefakty, surowce, żywność, informacje |
| **Podróż** | Mapa świata z traktami między miastami. Ruch wozu w czasie rzeczywistym. Różne biomy (mroczne lasy, bagna, pustkowia, przełęcze) |
| **Geopolityka** | Frakcje w stanie wojny/pokoju. Blokady, cła, niedobory. Ceny i dostępność zależą od sytuacji politycznej |
| **Obrona taboru** | Losowe spotkania na trakcie — bandyci, potwory, żywiołaki. Prosta walka (turowa? akcyjna?) |
| **Upgrade'y** | Wóz (większy ładunek, pancerz), osiołek (szybkość, wytrzymałość), ekwipunek (broń, mapy, amulety) |
| **Informacje** | Handel plotkami i wiedzą. Wiedza o sytuacji geopolitycznej → lepsze decyzje handlowe |

---

## 🕹️ Gry-referencje

| Gra | Co podpatrzeć |
|-----|--------------|
| **Stardew Valley** | Pixel art, top-down 2D, pętla dnia, relacje, upgrade'y |
| **Battle Brothers** | Dark fantasy, podróżowanie po mapie, ekonomia najemników, losowe spotkania |
| **Vagrus - The Riven Realms** | Karawana handlowa w dark fantasy, zarządzanie zasobami, narracja |
| **Darkest Dungeon** | Mroczny klimat, mechanika stresu/zasobów, turowa walka |
| **Moonlighter** | Handel + lochy, dynamiczne ceny, system sklepowy |
| **FTL** | Podróż między punktami, losowe wydarzenia, zarządzanie zasobami |
| **Mount & Blade** | Ekonomia karawanowa, miasta z różnymi dobrami, geopolityka |

---

## Faza A: Silnik — Godot 4

### A1. Dlaczego Godot?

- ✅ Darmowy, open-source (MIT)
- ✅ Pierwszorzędne wsparcie 2D (tilemapy, parallax, pixel snap)
- ✅ GDScript podobny do Pythona (Rychu już pyknie)
- ✅ Scene-driven — idealne pod mapę świata + miasta + interfejs
- ✅ Lekki (~40 MB), szybki startup
- ✅ Ogromna społeczność, tutoriale, asset library

### A2. Zadania

- [ ] **A2.1** `brew install godot` na Macu
- [ ] **A2.2** Przejść oficjalny tutorial "Dodge the Creeps" (pierwsza gra 2D)
- [ ] **A2.3** Przejść tutorial "2D movement overview" (ruchy postaci)
- [ ] **A2.4** Obejrzeć tutorial o TileMap w Godot 4 (kluczowe dla mapy świata)
- [ ] **A2.5** Sprawdzić asset library: darmowe tilemapy dark fantasy, sprite'y postaci

---

## Faza B: Pixel-art toolchain

- [ ] **B2.1** `brew install libresprite` (darmowy)
- [ ] **B2.2** Stworzyć testowe sprite'y 32×32: wóz, osiołek, handlarz
- [ ] **B2.3** Wyeksportować PNG, zaimportować do Godota, sprawdzić pixel-perfect
- [ ] **B2.4** Przeszukać itch.io / OpenGameArt pod dark fantasy tilemapy 32×32

---

## Faza C: Mechaniki ekonomiczne — projekt

### C1. System handlu

- Każde miasto ma: **podaż** (co produkuje), **popyt** (czego potrzebuje), **ceny bazowe**
- Ceny modyfikowane przez: **geopolitykę** (wojna = droższa stal), **biom** (pustynia = droga woda), **sezon**
- Towary: artefakty, surowce (drewno, ruda, kamień), żywność, informacje, luksusy

### C2. Model geopolityczny

- 3-4 frakcje, między nimi relacje (pokój / napięcie / wojna)
- Wydarzenia losowe zmieniające relacje (zamach, odkrycie złoża, blokada)
- Gracz może wpływać przez handel (sprzedaż broni = eskaluje konflikt)

### C3. Zadania

- [ ] **C3.1** Rozpisać 4 biomy: Las Grozy, Martwe Bagna, Popioły, Przełęcz Cieni
- [ ] **C3.2** Rozpisać 5 miast z profilami ekonomicznymi (co produkują, czego potrzebują)
- [ ] **C3.3** Zaprojektować 15-20 towarów z kategoriami
- [ ] **C3.4** Naszkicować formułę cenową: `cena_bazowa × mod_geopolityka × mod_biom × mod_relacja`

---

## Faza D: Spike walidacyjny

### Cel

Udowodnić w 2-3h, że Godot 4 nadaje się do tego projektu.

### Kroki

- [ ] **D1.** Stworzyć nowy projekt Godot 2D
- [ ] **D2.** Zaimportować darmową tilemapę (lub placeholder — kolorowe kwadraty)
- [ ] **D3.** Zbudować mapę: 3 "miasta" połączone "traktami" na tilemapie
- [ ] **D4.** Dodać wóz gracza (sprite placeholder — kwadrat 32×32)
- [ ] **D5.** Ruch wozu po trakcie (kliknięcie na miasto → wóz jedzie)
- [ ] **D6.** Po dotarciu: prosty ekran handlu (lista towarów, kup/sprzedaj)
- [ ] **D7.** HUD: złoto, ładowność wozu (x/100), nazwa lokacji
- [ ] **D8.** Zapisać jako commit `spike/karawana-petla-podstawowa`

---

## Faza E: Narzędzia pomocnicze (Python)

- [ ] **E1.** `tools/price-sim.py` — symulator cen z supply/demand (do balansowania)
- [ ] **E2.** `tools/route-calc.py` — kalkulator opłacalności trasy (czas × cena)
- [ ] **E3.** `tools/event-gen.py` — generator losowych wydarzeń na trakcie

---

## Struktura projektu

```
~/Projects/hajer-game/          # ← zmienić nazwę? "karawana"?
├── godot/                      # Projekt Godot
│   ├── project.godot
│   ├── scenes/
│   │   ├── world.tscn          # Mapa świata
│   │   ├── wagon.tscn          # Wóz gracza
│   │   ├── city.tscn           # Scena miasta
│   │   └── trade_ui.tscn       # UI handlu
│   ├── scripts/
│   │   ├── wagon.gd
│   │   ├── economy.gd
│   │   ├── world_map.gd
│   │   └── events.gd
│   ├── assets/
│   │   ├── sprites/
│   │   ├── tilesets/
│   │   └── sfx/
│   └── .godot/
├── art/                        # Pliki .ase (źródłowe)
├── docs/
│   ├── game-design.md
│   ├── economy-model.md
│   └── world-lore.md
├── tools/
│   ├── price-sim.py
│   ├── route-calc.py
│   └── event-gen.py
├── README.md
└── .hermes/plans/
    └── 2026-06-16-gamedev-research-plan.md
```

---

## Github repo

- Nazwa repo: `karawana` (albo `dark-caravan`? — do decyzji)
- Opis: "Dark fantasy trading RPG — wóz, osiołek i niebezpieczne trakty"
- Visibility: public / private? (do decyzji)

---

## Harmonogram

| Faza | Czas | Co |
|------|------|-----|
| A. Godot + tutoriale | 1-2h | Instalacja, nauka podstaw |
| B. Pixel art toolchain | 1h | LibreSprite + test sprite |
| C. Projekt mechanik | 2h | Ekonomia, geopolityka, towary |
| D. Spike walidacyjny | 2-3h | Prototyp: mapa + ruch + handel |
| E. Narzędzia Python | 1h | Symulatory ekonomii |
| **RAZEM** | **~8h** | Środowisko gotowe, koncept zwalidowany |

---

## Następny krok

**Faza A** — `brew install godot` + tutorial "Dodge the Creeps". Rychu startuje.
