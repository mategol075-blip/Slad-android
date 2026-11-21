# Ślad — projekt Android 0.2

To projekt źródłowy, NIE gotowy APK. Zawiera aktualny prototyp: sterowanie dotykowe, ścieżki, szlamy, walkę, XP i poziomy. Gra działa offline. Zapis postępu i balans mocniejszych przeciwników pozostają do dodania. Zamknięcie aplikacji może wyzerować rozgrywkę.

## Instalator bez komputera: GitHub Actions
1. Utwórz repozytorium na własnym koncie GitHub.
2. Prześlij ZAWARTOŚĆ katalogu slad-android do katalogu głównego repozytorium. Koniecznie zachowaj `.github/workflows/android.yml` (jest w ZIP).
3. W zakładce Actions wybierz „Zbuduj instalator Android”, potem „Run workflow”. Może być wymagane włączenie Actions na koncie/repozytorium; dostępność i limity zależą od konta.
4. Po pomyślnym zakończeniu pobierz artefakt `Slad-Android-APK`, rozpakuj i otwórz `app-debug.apk` na telefonie. Zezwól na instalację z wybranego źródła, jeśli Android o to poprosi.

Ten workflow nie został tutaj uruchomiony. Błędy kompilacji wymagają sprawdzenia logu. Nie utworzono repozytorium i nic nie opublikowano.

## Budowanie lokalne
Potrzebne: JDK 17, Gradle 8.9, Android SDK Platform 35 i Build Tools 34.0.0. Ustaw ANDROID_HOME na folder SDK. W katalogu projektu:

    gradle :app:assembleDebug :app:lintDebug

Wynik: `app/build/outputs/apk/debug/app-debug.apk`.
Projekt nie zawiera Gradle Wrapper. Użyj zainstalowanego Gradle 8.9 lub workflow powyżej.

## Test na telefonie
- Uruchom w trybie samolotowym; mapa powinna być widoczna.
- Sprawdź wszystkie strzałki, dłuższe przytrzymanie i atak.
- Pokonaj szlama i zdobądź drugi poziom.
- Przełącz aplikacje; powrót nie powinien powodować zablokowanego ruchu.
- Sprawdź pasek systemowy, obrót telefonu i przewijanie ekranu.

## Przed Google Play
To tylko wydanie testowe z podpisem debug. Wymaga dopracowania gry, testów urządzeń, docelowego identyfikatora aplikacji, prywatnego klucza podpisującego i wydania AAB. Wymagania Google Play, w tym target API, trzeba sprawdzić ponownie przed publikacją. Nie jest to gotowy pakiet do sklepu.

## Źródła techniczne
- https://developer.android.com/develop/ui/views/layout/webapps/load-local-content
- https://developer.android.com/build/releases/agp-8-7-0-release-notes
