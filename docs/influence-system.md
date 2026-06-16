# System Wpływu — Wagoner

> **Wersja:** 0.2.0  
> **Formuła:** WPŁYW = FINANSE + REPUTACJA

---

## 1. Dwie statystyki

```
WPŁYW = FINANSE + REPUTACJA
```

| Statystyka | Co to | Jak rośnie | Jak spada | Widoczność |
|------------|-------|------------|-----------|------------|
| **Finanse** | Złoto, majątek, faktorie, kompania | Handel, inwestycje | Straty, kradzież, wojna | Zawsze widoczna (HUD) |
| **Reputacja** | Postrzeganie przez świat: szacunek, strach, sława | Dobre decyzje, pomoc NPC, wygrane walki, dotrzymywanie umów | Zdrada, kłamstwo, ucieczka, złe decyzje | Ukryta liczbowo (widoczna przez reakcje NPC, perki) |

### 1.1. Reputacja — jak gracz ją wyczuwa?

| Poziom perków | Co gracz widzi |
|---------------|----------------|
| 0 (brak) | Tylko nastawienie NPC: wrogo / neutralnie / przyjaźnie / ze strachem |
| 1 (Znajomości) | Subtelne wskazówki w dialogach, plotki o graczu |
| 2 (Sieć informacyjna) | Raporty: "Twoje imię jest znane wśród kupców Unii" |
| 3 (Siatka szpiegowska) | Dokładne liczby, przewidywanie reakcji NPC |

---

## 2. Poziomy wpływu (dla NPC i gracza)

```
Poziom 0: Nieznany      (0-20)
Poziom 1: Lokalny       (21-40)
Poziom 2: Regionalny    (41-60)
Poziom 3: Znany         (61-80)
Poziom 4: Legendarny    (81-100)
```

- Każdy NPC, władca, heros, a nawet miasto ma swój poziom wpływu
- **Wpływ NPC jest UKRYTY** — gracz szacuje go przez perki i obserwację

---

## 3. Mechanika: wpływanie na NPC

### 3.1. Zasada progowa

```
Gracz może wpłynąć na NPC tylko gdy: WPŁYW_GRACZA > WPŁYW_NPC
```

**Siła wpływu** rośnie z różnicą:
- Mała przewaga (1-20 pkt różnicy): drobny efekt — NPC wysłucha, ale może odmówić
- Średnia przewaga (21-40 pkt): znaczący efekt — NPC zwykle się zgadza
- Duża przewaga (41+ pkt): dominacja — NPC praktycznie nie odmawia

### 3.2. Wyjątki od progu

Gracz może wpłynąć na silniejszego NPC gdy:

| Wyjątek | Warunek |
|---------|---------|
| **Szantaż** | Gracz ma kompromitującą informację o NPC |
| **Dług wdzięczności** | NPC jest "winien" graczowi (dług narracyjny) |
| **Charakter NPC** | Szemrany/przekupny → łatwiej wpłynąć pieniędzmi mimo różnicy wpływów |
| **Wspólny cel** | NPC i gracz chcą tego samego → NPC chętniej współpracuje |

---

## 4. Skala wpływu — co gracz może

| Poziom gracza | Co może |
|---------------|---------|
| **Nieznany** | Handlować, słuchać plotek |
| **Lokalny** | Wpływać na pojedynczych NPC i małe miasta |
| **Regionalny** | Wpływać na miasta, organizować faktorie, kreować pomniejszych bohaterów |
| **Znany** | Wpływać na frakcje, kreować znaczących bohaterów |
| **Legendarny** | Endgame: księstwo, monopol, siatka szpiegowska, zmiana biegu historii |

---

## 5. Mechanika wpływu przez handel

### 5.1. Wykup towarów

- Gracz wykupuje cały towar z miasta → miasto nie ma zasobu
- Miasto-producent: ceny rosną krótkoterminowo, magazyny się wypełniają → ceny wracają
- Miasto-importer: dłuższa regeneracja, mniejszy budżet na inne zakupy

### 5.2. Reakcje frakcji

- **Oferta współpracy** — "Potrzebujemy twoich dostaw. Zapłacimy premium."
- **Szantaż** — "Sprzedajesz naszym wrogom? To będzie cię kosztować."
- **Mechanizmy rynkowe** — konkurencja obniża ceny, ktoś wchodzi w twój segment
- **Charakter frakcji determinuje reakcję** — militarna grozi, kupiecka negocjuje

### 5.3. Celowe kryzysy

- Gracz może wywołać kryzys (głód przez wykup zboża, brak broni przez wykup stali)
- **Wrogość** u poszkodowanych
- **Podziw i szacunek** u ich wrogów
- Reputacja rośnie/spada w obu frakcjach

---

## 6. Mechanika wpływu przez informacje

### 6.1. Informacja jako towar

- Ma **termin ważności** — dezaktualizuje się
- Wartość maleje z czasem i z rozpowszechnieniem
- Gdy wszyscy wiedzą → wartość = 0

### 6.2. Informacja jako narzędzie wpływu

| Akcja | Mechanika |
|-------|-----------|
| **Sprzedaż informacji** | Gracz zarabia, informacja się rozchodzi |
| **Wykorzystanie informacji** | Gracz daje info NPC → NPC działa autonomicznie |
| **Dezinformacja** | Gracz tworzy fałszywą informację (szablon, koszt) |
| **Wstrzymanie informacji** | Gracz wie, ale nie mówi → opóźnia reakcję frakcji |

### 6.3. Dezinformacja (szkielet)

- Wymaga: złota, kontaktu, czasu
- Gracz wybiera z szablonu: cel (kto ma uwierzyć), treść (co ma uwierzyć), kanał (herold, list, plotka)
- Konsekwencje: jeśli wyjdzie → utrata reputacji, zemsta. Jeśli nie → wpływ rośnie.
- Pełny szablon do zaprojektowania na późniejszym etapie.

### 6.4. NPC działają na informacje

- Gracz daje NPC informację → NPC na podstawie **swojego charakteru** podejmuje akcję
- Gracz NIE kontroluje co NPC zrobi, ale może przewidzieć (znając charakter)
- Przykład: informacja o ruchach armii → szlachetny NPC ostrzeże wioski, szemrany sprzeda info dalej

---

## 7. NPC-bohaterowie — kreowanie i zarządzanie

### 7.1. Statusy NPC

| Status | Opis |
|--------|------|
| **Zwykły NPC** | Szeregowa postać: żołnierz, kupiec, chłop |
| **Protegowany** | NPC, któremu gracz pomógł — ma dług wdzięczności |
| **Bohater** | NPC wyniesiony przez gracza (lub świat) — ma własny wpływ i działa niezależnie |
| **Agent** | NPC pracujący dla gracza — dostarcza informacji, handluje, manipuluje |
| **Rywal** | NPC przeciwny graczowi |

### 7.2. Proces kreowania bohatera (długi, 3-5 interakcji)

1. Gracz identyfikuje obiecującego NPC
2. Gracz daje mu coś: informację (najcenniejsze), towar, pieniądze (najsłabsze)
3. NPC wykorzystuje to i **awansuje**
4. NPC ma **dług wdzięczności** (narracyjny, nie liczbowy)
5. NPC służy celom gracza: dostarcza informacji, handluje, jest przeciwnikiem dla wrogów

### 7.3. Wartość "daru"

```
Informacja > Towar > Pieniądze
```

- **Informacja:** uratowanie księżniczki, ostrzeżenie o ataku, cynk o okazji → NPC zostaje szeroko znany
- **Towar:** broń dla zbrojnego, zboże dla głodującej wioski → lokalny wzrost reputacji NPC
- **Pieniądze:** pożyczka, łapówka → najsłabszy efekt, NPC może się odwdzięczyć tylko finansowo

### 7.4. Działanie NPC-agentów

| Typ działania | Przykład |
|---------------|----------|
| **Pasywne** | Agent handluje w mieście → pasywny dochód. Agent zbiera plotki → co tydzień raport. |
| **Aktywne** | Gracz wydaje polecenie: "dowiedz się o ruchach armii" → agent działa. |

---

## 8. Relacje gracz-NPC

### 8.1. Typy charakterów (osie)

| Oś | Biegun A | Biegun B |
|----|----------|----------|
| Moralność | Szlachetny | Szemrany |
| Odwaga | Odważny | Tchórzliwy |
| Lojalność | Lojalny | Przekupny |
| Inteligencja | Bystry | Naiwny |
| Ambicja | Ambitny | Poddany |
| Mściwość | Wybaczający | Mściwy |

Każdy NPC ma pozycję na każdej osi (np. "Generał Korin — szlachetny 80%, odważny 90%, lojalny 70%, bystry 60%, ambitny 50%, wybaczający 40%").

### 8.2. Jak charakter wpływa na interakcje

Przykład: próba przekupstwa.

| Charakter NPC | Reakcja |
|---------------|---------|
| Szlachetny + Lojalny | **Odmawia i traci szacunek** do gracza |
| Szlachetny + Przekupny | Konflikt wewnętrzny → szansa 50/50 |
| Szemrany + Przekupny | **Akceptuje**, negocjuje wyższą cenę |
| Szemrany + Lojalny (wobec swojego szefa) | Może donieść swojemu szefowi |

### 8.3. Dług wdzięczności

- **Narracyjny, nieliczbowy**
- Szlachetny NPC: pamięta, odwdzięcza się z dobrej woli, trudniej go przekupić
- Szemrany NPC: odwdzięcza się gdy musi, łatwiej go przekupić
- Biedak/złodziej: pieniądze grają główną rolę

### 8.4. Zdrada NPC

Przyczyny:
- Charakter NPC (szemrany + przekupny = wysokie ryzyko)
- Lepsza oferta od konkurencji
- Gracz podpadł komuś, kto przekupił NPC
- Losowe wydarzenie (NPC został postawiony przed trudnym wyborem)
- Pomyłka (NPC źle zinterpretował intencje gracza)

---

## 9. Endgame — 4 szablony wpływu

| Szablon | Dominująca statystyka | Jak osiągnąć |
|---------|----------------------|-------------|
| **Król Kupców** | Finanse | Monopol, faktorie, wykup rynków |
| **Władca** | Finanse + Reputacja | Sojusze, przewroty, małżeństwa polityczne |
| **Mistrz Intryg** | Reputacja (ukryta) | Informacje, szantaż, dezinformacja, siatka szpiegowska |
| **Niezależny Magnat** | Finanse | Czysty handel, ignorowanie polityki |

- Szablon **nie jest wybierany** — kształtuje się przez decyzje gracza
- Endgame to **stan sandboksowy** — grasz dalej, osiągnąwszy szczyt
- Większa skala mechanik, nie nowe systemy

---

## 10. Do rozpisania (przyszłe iteracje)

- [ ] Pełna lista charakterów NPC (wszystkie kombinacje osi)
- [ ] Formuła siły wpływu (dokładne progi: mała/średnia/duża przewaga)
- [ ] Szablon dezinformacji (koszty, kanały, ryzyko)
- [ ] System długu wdzięczności (jak "pamiętać" bez liczb — eventy, flagi)
- [ ] Pasywny dochód od agentów
- [ ] Drzewko perków wpływów
