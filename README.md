# Ziarno i Mgła — publikacja BEZ Node.js i BEZ komputera

Ta metoda działa w całości w przeglądarce — da się ją zrobić nawet z telefonu.
Zamiast Node.js/Android Studio używamy:
1. **GitHub Pages** — darmowy hosting Twojej gry pod publicznym adresem URL.
2. **PWABuilder.com** — darmowe narzędzie w przeglądarce, które samo
   generuje plik `.aab` gotowy do wgrania na Google Play.

W tym folderze masz już wszystko, czego to wymaga: `index.html` (gra),
`manifest.json`, `sw.js` i dwie ikony.

## Krok 1 — wrzuć pliki na GitHub Pages
1. Załóż darmowe konto na **github.com** (jeśli nie masz).
2. Kliknij **+** → **New repository**. Nazwij je np. `ziarno-i-mgla`,
   ustaw jako **Public**, kliknij **Create repository**.
3. Na stronie repozytorium kliknij **Add file** → **Upload files**.
4. Wgraj WSZYSTKIE pliki z tego folderu: `index.html`, `manifest.json`,
   `sw.js`, `icon-192.png`, `icon-512.png` (na telefonie: wybierz je
   z pamięci, jeśli wcześniej wyodrębniłeś je z paczki — dokładnie tak,
   jak robiłeś to do maila).
5. Kliknij **Commit changes**.
6. Wejdź w **Settings** repozytorium → w menu po lewej **Pages**.
7. Przy "Branch" wybierz `main` i folder `/ (root)`, kliknij **Save**.
8. Po chwili GitHub pokaże Ci adres, np.:
   `https://twojnick.github.io/ziarno-i-mgla/`
   To jest publiczny link do Twojej gry — otwórz go, sprawdź czy gra
   działa.

## Krok 2 — wygeneruj plik .aab przez PWABuilder
1. Wejdź na **pwabuilder.com** (działa w przeglądarce telefonu lub
   komputera — bez instalacji).
2. Wklej swój link z Kroku 1 (np. `https://twojnick.github.io/ziarno-i-mgla/`)
   w pole na stronie głównej i kliknij **Start**.
3. PWABuilder przeanalizuje stronę i pokaże wynik dla trzech platform —
   znajdź kartę **Android** i kliknij **Package for stores** / **Generate**.
4. W ustawieniach pakietu Android:
   - **Package ID** — ustaw własny, unikalny (np. `com.twojnick.ziarnoimgla`)
     — nie da się go zmienić po publikacji.
   - Zostaw resztę domyślnie (PWABuilder sam ustawi nazwę, ikony z
     manifestu itd.).
   - Zaznacz opcję wygenerowania/pobrania **signing key** (klucza
     podpisującego) — PWABuilder może go stworzyć za Ciebie. **Pobierz
     i zachowaj go bezpiecznie** — będzie potrzebny do każdej przyszłej
     aktualizacji.
5. Kliknij **Generate** / **Download**. Dostaniesz plik `.aab` gotowy
   do wgrania na Google Play.

## Krok 3 — Google Play Console
1. Wejdź na **play.google.com/console**, załóż konto deweloperskie
   (jednorazowa opłata 25 USD).
2. Utwórz nową aplikację, uzupełnij kartę sklepu (opis, ikona, zrzuty
   ekranu — możesz zrobić zrzuty z telefonu, na którym testowałeś grę
   pod linkiem z Kroku 1).
3. Dodaj link do **polityki prywatności** (prosta strona: aplikacja nic
   nie wysyła, cała progresja gracza zapisywana jest lokalnie na
   urządzeniu). Możesz taką stronę też wrzucić na GitHub Pages tą samą
   metodą co grę.
4. Wgraj plik `.aab` z Kroku 2, najlepiej najpierw w sekcji
   **Internal testing**.
5. Wypełnij kwestionariusz oceny treści i wyślij do weryfikacji.

## Aktualizacje w przyszłości
Podmieniasz plik na GitHub (Upload files → nowa wersja `index.html`),
wracasz na PWABuilder, generujesz nowy `.aab` (musisz użyć **tego
samego** klucza podpisującego z Kroku 2), zwiększasz numer wersji w
ustawieniach pakietu, wgrywasz nowy `.aab` do Google Play Console.

## Uwaga
Ta metoda tworzy tzw. Trusted Web Activity — aplikację, która wyświetla
Twoją stronę w pełnoekranowym oknie bez paska adresu przeglądarki,
o ile GitHub Pages i PWABuilder poprawnie powiążą ze sobą domenę i
podpis aplikacji (PWABuilder robi to automatycznie, generując plik
`assetlinks.json` — jeśli podczas generowania pokaże Ci ten plik do
pobrania, wrzuć go też na GitHub, do folderu `.well-known/` w
repozytorium, dokładnie tak jak pozostałe pliki).
