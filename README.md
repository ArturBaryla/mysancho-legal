# mysancho-legal

Dokumenty prawne aplikacji **MySancho**, wystawione publicznie przez GitHub Pages.

To repozytorium jest publiczne **celowo i wyłącznie** po to, żeby Google Play i App Store
miały dostęp do dokumentów bez logowania. Kod aplikacji leży w prywatnych repozytoriach
`SplitTrip` (klient) i `SplitTrip-Backend` (serwer) — tutaj nie trafia nic poza treścią
dokumentów.

| Plik | Adres | Dokument |
|---|---|---|
| `index.html` | https://arturbaryla.github.io/mysancho-legal/ | Polityka prywatności (PL) |
| `privacy-en.html` | https://arturbaryla.github.io/mysancho-legal/privacy-en.html | Privacy policy (EN) |
| `terms.html` | https://arturbaryla.github.io/mysancho-legal/terms.html | Regulamin (PL) |
| `terms-en.html` | https://arturbaryla.github.io/mysancho-legal/terms-en.html | Terms of service (EN) |
| `style.css` | — | Wspólne style wszystkich czterech stron |

## Dlaczego polska polityka siedzi w `index.html`

Bo ten adres jest już **wpisany w Play Console** jako URL polityki prywatności. Zamiana
korzenia na stronę-rozdroże albo przeniesienie polityki do `privacy.html` zerwałaby ten
link — Google sprawdza, czy pod zadeklarowanym adresem faktycznie jest polityka
prywatności, i potrafi z tego powodu odrzucić wydanie.

Stąd asymetria w nazwach: polski dokument nie ma sufiksu, angielski ma `-en`. Brzydkie,
ale wynika z ograniczenia, którego nie warto łamać dla estetyki. Nie zmieniaj nazwy
`index.html` ani nie przenoś polityki gdzie indziej bez równoczesnej aktualizacji wpisu
w Play Console.

## Wersje językowe

Polska wersja jest **wiążąca**, angielska to tłumaczenie dla wygody — obie strony EN
mówią to wprost w ramce na górze. Przy każdej zmianie treści aktualizuj **obie** wersje
naraz i podbij datę na obu. Rozjazd między nimi jest gorszy niż brak tłumaczenia.

Przełącznik języka to para linków na górze każdej strony (`.langbar`), plus odnośniki
w stopce. Nie ma automatycznego wykrywania języka przeglądarki — aplikacja linkuje
bezpośrednio do wersji zgodnej z ustawionym w niej językiem.

## Zanim coś tu zmienisz

**Polityka prywatności** opisuje **rzeczywiste** zachowanie aplikacji: jakie dane trafiają
na serwer, kto je widzi i którym firmom są przekazywane (Google, Google Play, RevenueCat,
Cloudflare R2, Anthropic). Przy migracji hostingu (Google Cloud, Cloudflare → DigitalOcean)
zmień tabelę dostawców w punkcie 4. Odpowiedzi do formularza *Bezpieczeństwo danych* są
w repo aplikacji: `docs/play-data-safety.md`.
Rozjazd między tym dokumentem a tym, co apka faktycznie robi, jest jednym z częstszych
powodów odrzucenia przez Google Play — a przy danych finansowych i zdjęciach potrafi
skończyć się zdjęciem aplikacji ze Sklepu.

Zmieniasz zakres zbieranych danych albo dokładasz zewnętrznego dostawcę? Zaktualizuj
ten dokument **i** formularz *Bezpieczeństwo danych* w Play Console, a na górze strony
podbij datę ostatniej aktualizacji.

**Regulamin** opiera się na dwóch założeniach, które trzeba zweryfikować przy każdej
większej zmianie w aplikacji:

- MySancho **nie przelewa pieniędzy** — salda są wyłącznie zapisem, rozliczenie dzieje się
  poza aplikacją. Gdyby to się kiedyś zmieniło (własne płatności, escrow, cokolwiek
  dotykające cudzych środków), regulamin wymaga przepisania od zera, a usługa najpewniej
  wchodzi pod przepisy o usługach płatniczych.
- **Tokeny (dawniej tickety) są płatne tylko przez Google Play.** Od 2026-10-14 punkt 7
  opisuje abonament (Plan 20 / 50 / 100), dokupienie, zmianę planu, zwroty i skutki usunięcia
  konta. Ceny celowo **nie** są w regulaminie — widać je w aplikacji i w oknie zakupu Google
  Play. Gdy zmienią się plany, zasady odnowienia albo okres ważności dokupienia, popraw punkt 7
  razem z `docs/subscriptions.md` w repo backendu.
- **Sprzedawca.** Punkt 1 nie mówi już „osoba fizyczna, projekt niekomercyjny”, ale dane
  sprzedawcy (firma, adres, NIP) trzeba uzupełnić, jeśli sprzedaż pójdzie przez działalność
  gospodarczą — decyzja po odpowiedzi księgowej. W `terms.html` i `terms-en.html` jest o tym
  komentarz `TODO` w HTML. **Nie publikuj tych zmian na produkcję, dopóki to nie jest
  rozstrzygnięte.**

> Te dokumenty nie są opiniowane przez prawnika. Przed wejściem na produkcję z realnymi
> użytkownikami warto je dać do przejrzenia komuś, kto się na tym zna — zwłaszcza punkty
> 9 (odpowiedzialność) i 11 (reklamacje).
