# MCPS — Manager Career Progression System

Statyczna, responsywna strona z zasadami uprawnień menedżera w wyzwaniu Football Manager oraz kalkulatorem Job Eligibility Benchmark (JEB). Projekt nie wymaga Node.js, frameworka ani procesu buildowania — GitHub Pages publikuje bezpośrednio plik `index.html`.

## Publikacja na GitHub Pages

1. Utwórz repozytorium na GitHubie, np. `fm-mcps`.
2. Wgraj do głównego katalogu repozytorium pliki `index.html` i `README.md`.
3. Otwórz **Settings → Pages**.
4. W sekcji **Build and deployment** wybierz **Deploy from a branch**.
5. Jako branch wybierz `main`, a katalog `/ (root)`, następnie kliknij **Save**.
6. Po zakończeniu publikacji strona będzie dostępna pod adresem:

   `https://<twoj-login>.github.io/fm-mcps/`

Jeżeli repozytorium będzie miało inną nazwę, zastąp `fm-mcps` właściwą nazwą. Dla repozytorium użytkownika o nazwie `<twoj-login>.github.io` adres strony będzie krótszy: `https://<twoj-login>.github.io/`.

## Kalkulator JEB

Kalkulator korzysta bezpośrednio ze wzoru opisanego w wyzwaniu Behold the HUJ:

```text
max(
  Cn - Cpeak,
  (0.8 × Cn + 0.2 × (Ln / 2))
    - min(Jpeak, max(0.8 × Cp + 0.2 × (Lp / 2), M))
) ≤ 1.0
```

Reputację klubu i menedżera wybiera się z sześciostopniowej skali FM27 (wartości całkowite): 0 — Nieznana, 1 — Lokalna, 2 — Regionalna, 3 — Krajowa, 4 — Kontynentalna, 5 — Globalna. Reputacja ligi jest oceną całkowitą od 0 do 10: 0 — Brak oceny, 1 — Kiepska, 2 — Poniżej przeciętnej, 3 — Przeciętna, 4 — Przyzwoita, 5 — Całkiem dobra, 6 — Dobra, 7 — Imponująca, 8 — Świetna, 9 — Wyśmienita, 10 — Elitarna. Aby wszystkie wartości JEB były na wspólnej skali 0–5, kalkulator normalizuje ocenę ligi przez podzielenie jej przez 2. JPS pozostaje wartością ułamkową.

- `Cn` — reputacja nowego klubu.
- `Ln` — reputacja ligi nowego klubu.
- `Cp` — reputacja obecnego lub ostatniego klubu.
- `Lp` — reputacja ligi obecnego lub ostatniego klubu.
- `M` — osobista reputacja menedżera przeliczona na skalę 0–5.
- `Cpeak` — najwyższa reputacja klubu prowadzonego kiedykolwiek przez menedżera.
- `Jpeak` — najwyższy historyczny Job Prestige Score. Kalkulator wylicza go jako `0.8 × reputacja klubu + 0.2 × (ocena ligi / 2)` na podstawie dwóch osobnych pól.

Wynik JEB równy lub niższy niż `1.0` oznacza, że objęcie klubu jest dozwolone. Wynik powyżej `1.0` oznacza, że oferta nie spełnia warunku JEB. Próg JEB został dostosowany z `0.5` do `1.0` dla sześciostopniowej skali reputacji FM27. Nie ma scenariuszy ani dodatkowych wyjątków.

Jeżeli menedżer nigdy wcześniej nie prowadził klubu, wpisz `0` w polach dotyczących obecnego / ostatniego klubu oraz osiągnięć historycznych.

## Aktualizacja zasad

Edytuj odpowiedni wiersz w `index.html` i zatwierdź zmianę (commit). GitHub Pages automatycznie opublikuje nową wersję.

## Zawartość

- Taktyka i trening
- Transfery, scouting i sparingi
- Zarządzanie sztabem
- Legenda licencji, stażu i warunków alternatywnych
- Wyszukiwarka i filtrowanie kategorii
- Kalkulator JEB z rozbiciem wyniku na oba warunki

## Źródła zasad JEB

- [Behold the HUJ — oryginalne zasady i wzór JEB](https://community.sports-interactive.com/forums/topic/612310-challenge-behold-the-huj-the-ultimate-football-manager-27-challenge/)
- [Oryginalny kalkulator JEB — Vami](https://vami.fm/jeb-calculator.html)
