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
Cloudflare R2, Anthropic). Rozjazd między tym dokumentem a tym, co apka faktycznie robi,
jest jednym z częstszych powodów odrzucenia przez Google Play — a przy danych finansowych
i zdjęciach potrafi skończyć się zdjęciem aplikacji ze Sklepu. Przy migracji hostingu
(Google Cloud, Cloudflare → DigitalOcean) zmień tabelę dostawców w punkcie 4. Odpowiedzi do
formularza *Bezpieczeństwo danych* są w repo aplikacji: `docs/play-data-safety.md`.

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
- **Komentarzy nie ma** (od 2026-10-15). Usunięto je z aplikacji, więc polityka, regulamin i strony
  o usuwaniu konta już ich nie wspominają, a zgłaszanie i blokowanie dotyczą wpisów, zdjęć, grup
  i osób. Gdyby komentarze wróciły — wróci też punkt o treściach, które widzą pozostali członkowie,
  i wiersz w formularzu *Bezpieczeństwo danych* (zob. `docs/play-data-safety.md` w repo aplikacji).
- **Osoby bez konta** (od 2026-10-15). Admin grupy może wpisać imię kogoś, kto nie ma aplikacji
  (funkcja „Dodaj osobę bez konta”). Regulamin (punkt 4, „Osoby bez konta”) robi wyjątek od zakazu
  wprowadzania danych osób, które nie wyraziły zgody; polityka ma osobną kategorię danych, podstawę
  (prawnie uzasadniony interes), okres przechowywania i prawa takiej osoby. Zmieniając zasady —
  usuwanie z historią zostawia osobę jako nieaktywną do usunięcia grupy — popraw te miejsca razem
  z `docs/group-api.md` (sekcja 13) w repo backendu.
- **Sprzedawca.** Punkt 1 regulaminu i polityki podaje dziś tylko „Art Technology — Artur Baryła”
  i e-mail kontaktowy — taka jest decyzja właściciela (pełne dane firmy i adres są w sklepach). Czy to wystarcza wobec obowiązków
  informacyjnych wobec konsumenta, ma ocenić prawnik (lista niżej).

## Do zrobienia przed otwarciem aplikacji dla realnych użytkowników

Dokumenty **nie były opiniowane przez prawnika**. Zanim aplikacja wyjdzie poza zamknięty test:

1. **Przegląd prawnika: regulamin i polityka prywatności (RODO), po polsku** (angielska to
   tłumaczenie). Szczególnie:
   - regulamin: punkt 7 (abonament, odnowienie automatyczne, zmiana planu, zwroty, prawo
     odstąpienia od umowy przy treściach cyfrowych — Google Play pisze o utracie prawa
     odstąpienia „z wyjątkiem usług”), punkt 9 (odpowiedzialność), punkt 11 (reklamacje),
     punkt 10 (zawieszanie kont), punkt 4 (wyjątek dla osób bez konta — czy wystarczy
     „osoba o tym wie”, czy trzeba dodatkowych zastrzeżeń);
   - polityka: podstawy prawne (punkt 5, w tym imię osoby bez konta na podstawie prawnie
     uzasadnionego interesu), okresy przechowywania danych o zakupach (punkt 6),
     przekazywanie danych poza EOG (RevenueCat, Anthropic — punkt 4), usuwanie danych
     w RevenueCat i w grupach (punkt 8).
2. **Zakres danych sprzedawcy w punkcie 1 regulaminu i polityki** — czy sama nazwa firmy i
   e-mail wystarczają, czy trzeba dopisać więcej. Księgowa ma też rozstrzygnąć okres
   przechowywania danych o zakupach (polityka mówi „przez czas wymagany przepisami”).
3. **Spójność z Play Console:** formularz *Bezpieczeństwo danych* wg `docs/play-data-safety.md`
   w repo aplikacji, adres kontaktowy w karcie sklepu taki sam jak w dokumentach
   (`mysancho.support@gmail.com`).
4. **Po migracji na DigitalOcean:** zmień tabelę dostawców (punkt 4 polityki) i podbij daty.
5. **Luki w backendzie opisane w dokumentach** — zob. `docs/TODO.md` w repo backendu
   (usuwanie klienta w RevenueCat przy usuwaniu konta, czyszczenie danych zakupów).
