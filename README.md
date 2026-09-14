# NowoczesneAuta.pl — dane otwarte: Radar zmian rynku nowych marek aut w Polsce

Publiczny zbiór danych serwisu [NowoczesneAuta.pl](https://nowoczesneauta.pl/): bieżące ceny z oficjalnych
cenników, gwarancje (pojazd, bateria, próg SOH), dostępność i liczba salonów dla modeli nowych marek na
polskim rynku, oraz dziennik zmian tych danych z dokumentem źródłowym przy każdym zdarzeniu.

Źródło prawdy i metodologia: <https://nowoczesneauta.pl/radar-zmian/> (sekcja „Metodologia").
Zbiór jest odświeżany automatycznie przy każdej publikacji serwisu.

<!-- STATS:START -->
- Wersja zbioru: **2026-09-14** (stan danych źródłowych: 2026-09-08, zrzut: 2026-09-14)
- Modele: **174** (official_pl_current 148, official_pl_announced 23, official_pl_presale 2, private_import 1)
- Zdarzenia w Radarze: **83** (availability 28, promotion 22, price 12, correction 8, versions 7, warranty 5, equipment 1)
- Sieć sprzedaży: 606 punktów w 149 miastach
<!-- STATS:END -->

## Pliki

| Plik | Co zawiera | Dla kogo |
|---|---|---|
| [`data/radar-zmian.json`](data/radar-zmian.json) | pełny zbiór: metadane, `models` (stan bieżący per model), `changes` (zdarzenia) | programiści, analitycy |
| [`data/modele.csv`](data/modele.csv) | spłaszczony stan bieżący: jeden wiersz na model (cena od, gwarancje, SOH, salony, data stanu danych) | Excel / Google Sheets, dziennikarze |
| [`data/zmiany.csv`](data/zmiany.csv) | dziennik zdarzeń Radaru: co, kiedy, z jakiego dokumentu, wartość przed i po | redakcje, analizy trendów |

Opis pól: [`SCHEMA.md`](SCHEMA.md). Kodowanie UTF-8 (CSV z BOM, otwiera się poprawnie w Excelu).

## Jak cytować

> NowoczesneAuta.pl — Radar zmian, wersja RRRR-MM-DD, https://nowoczesneauta.pl/radar-zmian/

Wersja zbioru to pole `version` w JSON (data ostatniej aktualizacji rejestru zdarzeń). Przy cytowaniu
konkretnej liczby warto podać też `observedAt` (data stanu danych modelu) i dokument z `sourceReferences`.

## Czego tu nie ma

Dokumenty producentów (cenniki, katalogi, karty gwarancyjne) pozostają własnością ich wydawców i nie są
częścią zbioru; `sourceReferences` to identyfikatory dokumentów w archiwum redakcji. Ceny to ceny katalogowe
z dokumentów, nie oferty dealerskie. Zbiór nie zawiera danych osobowych.

## Licencja

Dane: [Creative Commons Uznanie autorstwa 4.0 (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/deed.pl)
— możesz kopiować, analizować i publikować, także komercyjnie, z podaniem źródła jak w sekcji „Jak cytować".
Szczegóły: [`LICENSE.md`](LICENSE.md).

## Kontakt

Korekty, pytania o dane, API: kontakt@nowoczesneauta.pl · Serwis prowadzi Marek Bochenek (BeCode, Kraków).

---

**English summary.** Open dataset from NowoczesneAuta.pl, an independent guide to new car brands entering the
Polish market: current prices from official price lists, vehicle and battery warranties with SOH thresholds,
availability and dealer counts per model, plus a change log with a source document for every entry.
Files: `data/radar-zmian.json` (full), `data/modele.csv` (one row per model), `data/zmiany.csv` (change log).
Licence CC BY 4.0, cite as “NowoczesneAuta.pl — Radar zmian, version YYYY-MM-DD, https://nowoczesneauta.pl/radar-zmian/”.
