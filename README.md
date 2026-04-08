# Legalize PL

### Polskie akty prawne w formacie Markdown, wersjonowane w Git.

Każdy akt prawny to plik. Każda reforma to commit.

**~34 100 aktów prawnych Dziennika Ustaw** · Dane otwarte z [api.sejm.gov.pl/eli](https://api.sejm.gov.pl/eli)

Część projektu [Legalize](https://github.com/legalize-dev/legalize) · [legalize.dev/pl](https://legalize.dev/pl)

> **Wczesny etap** — To repozytorium jest w fazie aktywnego rozwoju. Struktura plików, historia commitów i treść mogą ulec istotnym zmianom, włącznie z pełną regeneracją.

## Szybki start

```bash
# Sklonuj polskie akty prawne
git clone https://github.com/legalize-dev/legalize-pl.git

# Wyszukaj w Ustawie o ochronie ludności i obronie cywilnej
grep -A 3 "Art. 1" pl/DU-2024-1907.md

# Historia konkretnego aktu
git log --oneline -- pl/DU-2024-1907.md

# Tekst jednolity Kodeksu karnego (Obwieszczenie Marszałka Sejmu)
cat pl/DU-2024-17.md
```

## Struktura

```
pl/
  DU-2024-1907.md    — Ustawa o ochronie ludności i obronie cywilnej
  DU-2024-1976.md    — Ustawa o wypowiedzeniu Porozumienia...
  DU-2024-17.md      — Obwieszczenie ws. tekstu jednolitego Kodeksu karnego
  DU-2024-706.md     — Obwieszczenie ws. tekstu jednolitego Kodeksu karnego wykonawczego
  ...                — ~34 100 aktów prawnych Dziennika Ustaw
```

Rodzaj aktu (ustawa, rozporządzenie, obwieszczenie, uchwała, …) jest podany w nagłówku YAML każdego pliku, a nie w strukturze katalogów.

## Format

Każdy plik zawiera:

- **Nagłówek YAML** — tytuł, identyfikator ELI, adres Dziennika Ustaw, data ogłoszenia, data wejścia w życie, status, organ wydający, słowa kluczowe, odniesienia do dyrektyw UE itd.
- **Treść w Markdown** — artykuły, paragrafy, punkty i litery z oryginalnym numerowaniem. Tabele renderowane jako tabele Markdown pipe. Cytowane fragmenty (teksty zmieniane) jako blockquote.

Przykład:

```markdown
---
title: "Ustawa z dnia 5 grudnia 2024 r. o ochronie ludności i obronie cywilnej"
identifier: "DU-2024-1907"
country: "pl"
rank: "ustawa"
publication_date: "2024-12-05"
status: "in_force"
source: "https://api.sejm.gov.pl/eli/acts/DU/2024/1907"
display_address: "Dz.U. 2024 poz. 1907"
keywords: "obrona cywilna, ochrona ludności, …"
---
# Ustawa z dnia 5 grudnia 2024 r. o ochronie ludności i obronie cywilnej

### Rozdział 1. Przepisy ogólne

##### Art. 1.

Ustawa określa:

  1) zadania ochrony ludności i obrony cywilnej;
  2) organy i podmioty realizujące zadania ochrony ludności i obrony cywilnej;
  …
```

## Zakres

**Wersja 1:**

- Publikator: **Dziennik Ustaw (DU)** — powszechnie obowiązujące akty prawne (art. 87 Konstytucji).
- Akty z tekstem HTML dostępnym w API ELI Sejmu (praktycznie wszystko od ~2012 plus wybrane wcześniejsze, w tym **teksty jednolite kodeksów** publikowane przez Marszałka Sejmu).
- Łącznie ~34 100 aktów od 2000 roku.
- Obejmuje skonsolidowane teksty m.in. **Kodeksu karnego**, **Kodeksu postępowania cywilnego**, **Kodeksu spółek handlowych**, **Kodeksu karnego wykonawczego** w wersjach Obwieszczeń Marszałka Sejmu z dostępnym HTML.

**Obecnie poza zakresem (planowane na v2):**

- **Konstytucja z 1997 r.** — API udostępnia ją wyłącznie jako PDF.
- **Niektóre starsze teksty jednolite kodeksów** publikowane wyłącznie jako PDF.
- **Monitor Polski (MP)** — uchwały, zarządzenia i inne akty nie będące powszechnie obowiązującym prawem.
- Poszczególne akty historyczne sprzed 2000 r.

## Źródło

Dane pochodzą z oficjalnego API ELI (European Legislation Identifier) Kancelarii Sejmu:

```
https://api.sejm.gov.pl/eli
```

API jest publiczne, nie wymaga uwierzytelnienia i udostępnia zarówno metadane w formacie JSON jak i skonsolidowany tekst HTML każdego aktu.

Polskie publikacje prawne są w domenie publicznej zgodnie z art. 4 ustawy z dnia 4 lutego 1994 r. o prawie autorskim i prawach pokrewnych (Dz.U. 1994 nr 24 poz. 83).

## Licencja

[MIT License](LICENSE) — treść aktów prawnych jest w domenie publicznej; licencja obejmuje format repozytorium (skrypty, struktura, metadane).

## Zobacz też

- [legalize.dev](https://legalize.dev) — przeglądarka internetowa wszystkich krajów objętych projektem Legalize
- [legalize-pipeline](https://github.com/legalize-dev/legalize-pipeline) — silnik generujący to repozytorium
- [api.sejm.gov.pl/eli](https://api.sejm.gov.pl/eli/openapi/) — dokumentacja API źródłowego
