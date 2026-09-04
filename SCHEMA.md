# Opis pól

## `data/radar-zmian.json`

| Pole | Znaczenie |
|---|---|
| `schemaVersion` | wersja schematu (1) |
| `name`, `version`, `dateModified` | nazwa zbioru; `version` = data ostatniej aktualizacji rejestru zdarzeń |
| `methodology`, `license` | adresy sekcji metodologii i zasad wykorzystania na stronie Radaru |
| `scope` | zakres: marki i modele na rynku polskim, rozdzielenie cen oficjalnych, prognoz i archiwalnych |
| `observation.snapshotDate` | data zrzutu stanu bieżącego |
| `observation.sourceDataDate` | data stanu danych źródłowych (ostatni przegląd dokumentów) |
| `observation.monitoredModels`, `dealers`, `cities` | liczba modeli, punktów sprzedaży i miast |
| `models[]` | stan bieżący per model — pola niżej |
| `changes[]` | zdarzenia Radaru — pola niżej |

### `models[]`

| Pole | Znaczenie |
|---|---|
| `slug`, `name`, `url` | identyfikator, nazwa wyświetlana, strona modelu w serwisie |
| `marketStatus` | `official_pl_current` (w ofercie), `official_pl_presale`, `official_pl_announced`, `withdrawn`, `historical`, `cancelled_before_launch`, `private_import` |
| `current.pricePln` | najniższa cena katalogowa brutto w PLN (null = brak oficjalnej ceny) |
| `current.versions[]` | wersje z cenami (`name`, `price`) |
| `current.availability` | dostępność wg dokumentów (tekst lub null) |
| `current.warrantyVehicle`, `warrantyBattery`, `warrantySoh` | gwarancja pojazdu, baterii i próg SOH — tekst z dokumentu |
| `current.dealerCount` | liczba punktów sprzedaży marki w katalogu serwisu |
| `observedAt` | data stanu danych modelu (ostatni przegląd redakcyjny) |
| `sourceReferences[]` | identyfikatory dokumentów źródłowych w archiwum redakcji |

### `changes[]`

| Pole | Znaczenie |
|---|---|
| `id` | identyfikator zdarzenia (data-model-temat) |
| `modelSlug`, `modelUrl` | model |
| `observedAt` | data odnotowania zmiany |
| `effectiveFrom` | data obowiązywania wg dokumentu (może być pusta) |
| `category` | `price`, `promotion`, `warranty`, `availability`, `versions`, `equipment`, `correction` |
| `kind` | rodzaj zdarzenia (np. `changed`) |
| `materiality` | istotność: `high`, `medium`, `low` |
| `confidence` | pewność: `confirmed`, `high`, `medium`, `low`, `conflict` |
| `title`, `summary` | tytuł i opis zmiany |
| `before`, `after` | wartość przed i po |
| `editorialNote` | nota redakcyjna (m.in. czego NIE twierdzimy) |
| `sourceLabel`, `sourceReference` | dokument źródłowy |
| `reviewedAt` | data przeglądu wpisu |

## `data/modele.csv`

Jeden wiersz na model: `slug, nazwa, url, status_rynkowy, cena_od_pln, liczba_wersji, dostepnosc,
gwarancja_pojazdu, gwarancja_baterii, prog_soh, liczba_salonow, stan_danych` — odpowiedniki pól `models[]`.

## `data/zmiany.csv`

Kolumny jak `changes[]` w notacji snake_case (`model_slug`, `model_url`, `observed_at`, …), eksport
identyczny z <https://nowoczesneauta.pl/radar-zmian/dane.csv>.
