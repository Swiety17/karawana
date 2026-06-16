# Game Design Document — Karawana (SZKIELET)

> **Wersja:** 0.1.1 (szkielet — decyzje do podjęcia)  
> **Data:** 2026-06-16  
> **Jak czytać:** Każda sekcja zawiera pytania do decyzji, zamiast gotowych odpowiedzi.  
> **Pełna lista decyzji:** `docs/decisions-checklist.md` (56 punktów)

---

## 1. Elevator Pitch

> 🟡 **DO UZGODNIENIA** — checklist §1

Jedno zdanie opisujące grę: `[KTO] robi [CO] w [ŚWIECIE], żeby [CEL].`

Przykład (z briefu): *"Woźnica-handlarz przemierza dark fantasy świat, handlując artefaktami i zasobami między frakcjami, rozwijając swój tabor i broniąc go przed niebezpieczeństwami traktu."*

- [ ] 1.1 — Nazwa gry
- [ ] 1.2 — Dominanta rozgrywki (co jest najważniejsze?)
- [ ] 1.6 — Grupa docelowa

---

## 2. Core Loop — Pętla Rozgrywki

```text
KUPUJ → PODRÓŻUJ → [WYDARZENIA NA TRAKCIE] → SPRZEDAJ → UPGRADUJ → KUPUJ...
```

> 🟡 **DO UZGODNIENIA** — checklist §5, §6

- [ ] 5.1 — Jak działa czas podróży? (rzeczywisty, przyspieszony, turowy?)
- [ ] 5.2 — Swobodny ruch po mapie czy tylko po traktach?
- [ ] 5.4 — Czy gracz może biwakować? Co robi na postoju?
- [ ] 6.1 — Jak często występują wydarzenia/walka na trakcie?
- [ ] 6.2 — Jaki typ walki?

---

## 3. Setting — Świat

> 🟡 **DO UZGODNIENIA** — checklist §2

- [ ] 2.1 — Poziom fantasy (high / dark / low?)
- [ ] 2.2 — Skala świata (mały region / średni kontynent / duży świat?)
- [ ] 2.3 — Biomy — ile? jakie? klimat?
- [ ] 2.4 — Frakcje — ile? charakter?
- [ ] 2.5 — Magia — powszechna, rzadka, zakazana?
- [ ] 2.7 — Rasy — tylko ludzie? inne?
- [ ] 2.6 — Ile backstory/lore? (świat mówi przez otoczenie czy potrzebuje historii?)

---

## 4. Postać Gracza

> 🟡 **DO UZGODNIENIA** — checklist §3

- [ ] 3.1 — Kim jest gracz? Czy ma zdefiniowaną przeszłość?
- [ ] 3.2 — Personalizacja (płeć, imię, portret — czy coś wybieramy?)
- [ ] 3.3 — Statystyki postaci (są? ile?)
- [ ] 3.4 — Rozwój (leveluje? perki? czy tylko ekwipunek?)
- [ ] 3.5 — Reputacja u frakcji (jest? jak działa?)

---

## 5. System Handlu

> 🟡 **DO UZGODNIENIA** — checklist §4

- [ ] 4.1 — Ile towarów? (kilkanaście / dziesiątki?)
- [ ] 4.2 — Kategorie towarów — które?
- [ ] 4.3 — Czy towary się psują?
- [ ] 4.4 — Ceny statyczne czy dynamiczne?
- [ ] 4.5 — Czy gracz może negocjować ceny?
- [ ] 4.6 — Informacja jako towar — jak działa?
- [ ] 4.7 — Waluta(y)?

---

## 6. System Podróży

> 🟡 **DO UZGODNIENIA** — checklist §5

- [ ] 5.3 — Czy mapa jest od początku znana?
- [ ] 5.5 — Pogoda — wpływ mechaniczny czy tylko wizualny?
- [ ] 5.6 — Pora dnia — znaczenie mechaniczne?

---

## 7. System Walki / Obrony

> 🟡 **DO UZGODNIENIA** — checklist §6

- [ ] 6.3 — Czy walkę można ominąć? (ucieczka, przekupstwo, skradanie?)
- [ ] 6.4 — Stawka walki (co się traci?)
- [ ] 6.5 — Przeciwnicy (bandyci, potwory, frakcje, inni handlarze?)
- [ ] 6.6 — Najemnicy/eskorta (są? jak działają?)

---

## 8. System Geopolityczny

> 🟡 **DO UZGODNIENIA** — checklist §7

- [ ] 7.1 — Czy geopolityka jest w MVP?
- [ ] 7.2 — Głębokość (prosta wojna/pokój czy złożona symulacja?)
- [ ] 7.3 — Czy gracz może wpływać na sytuację?
- [ ] 7.4 — Jak geopolityka wpływa na rozgrywkę?

---

## 9. Progresja i Upgrade'y

> 🟡 **DO UZGODNIENIA** — checklist §8

- [ ] 8.1 — Co można ulepszać? (wóz, koń, broń, ekwipunek...)
- [ ] 8.2 — Drzewko wyborów czy liniowe ulepszenia?
- [ ] 8.3 — Tempo progresji (ile godzin do pierwszego upgrade'u?)
- [ ] 8.4 — Czy wszystko można zmaksować?

---

## 10. Interfejs

> 🟡 **DO UZGODNIENIA** — checklist §9

- [ ] 9.1 — Jakie ekrany/widoki?
- [ ] 9.2 — HUD — co stale widoczne?
- [ ] 9.3 — Sterowanie (mysz, klawiatura, oba?)
- [ ] 9.4 — Minimalizm czy bogactwo informacji?
- [ ] 9.5 — Rozdzielczość?

---

## 11. Grafika i Dźwięk

> 🟡 **DO UZGODNIENIA** — checklist §10

- [ ] 10.1 — Rozmiar pixela (16×16 / 32×32?)
- [ ] 10.2 — Paleta kolorów?
- [ ] 10.3 — Animacje (płynne, statyczne, minimalne?)
- [ ] 10.4 — Assety własne vs gotowe?
- [ ] 10.5 — Dźwięk (od razu czy później?)
- [ ] 10.6 — Portrety NPC?

---

## 12. Narracja

> 🟡 **DO UZGODNIENIA** — checklist §12

- [ ] 12.1 — Fabuła główna? Jaka?
- [ ] 12.2 — Questy? Jakie?
- [ ] 12.3 — NPC z imionami/dialogami czy tylko interfejs?
- [ ] 12.4 — Dziennik podróży / codex?
- [ ] 12.5 — Endgame (jest? jaki?)

---

## 13. Techniczne

> 🟡 **DO UZGODNIENIA** — checklist §11

- [ ] 11.1 — Platformy: PC + Mac. Linux?
- [ ] 11.2 — Silnik: Godot 4 (już jest). Potwierdzamy?
- [ ] 11.3 — Metodyka: MVP → iteracje?
- [ ] 11.4 — Współpraca: Przemek + Rychu. Ktoś jeszcze?
- [ ] 11.5 — Testy automatyczne?

---

## 14. Ton, inspiracje, USP

> 🟡 **DO UZGODNIENIA** — checklist §13 + §2.8

- [ ] 2.8 — Ton narracji (grimdark / dark / sardoniczny?)
- [ ] 13.1 — Które gry są świadomą inspiracją?
- [ ] 13.2 — Czego NIE chcemy z gier referencyjnych?
- [ ] 13.3 — Unikalny punkt sprzedaży — co wyróżnia Karawanę?

---

## Etapy rozwoju (szkielet)

> 🟡 **DO UZGODNIENIA** — checklist §11.3

### MVP
- [ ] Co wchodzi? (do ustalenia na podstawie priorytetów z §1.2)

### v0.2
- [ ] Co dokładamy?

### v1.0
- [ ] Co w wersji finalnej?

---

## Model ekonomiczny

> Osobny dokument: `docs/economy-model.md`  
> Zawiera szczegółowe tabele towarów, cen, miast — do wypełnienia po decyzjach z checklist §4.

---

## Zarys świata

> Osobny dokument: `docs/world-lore.md`  
> Zawiera lore, frakcje, biomy — do wypełnienia po decyzjach z checklist §2.
