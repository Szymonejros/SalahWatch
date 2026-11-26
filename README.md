# Salah – przewodnik modlitwy na Wear OS (Xiaomi Watch 2 Pro)

## Co jest w aplikacji
- **Ekran główny**: lokalizacja, następna modlitwa z odliczaniem, 5 modlitw (rak'ah + godzina), ustawienia.
- **Godziny modlitw** liczone offline w zegarku (bez internetu). Metody: MWL (domyślna), ISNA, Egipt, Umm al-Qura, Karaczi; Asr standard/Hanafi. Korekta dla wysokich szerokości (krótkie letnie noce w Polsce).
- **Lokalizacja**: GPS zegarka albo lista polskich miast.
- **Przewodnik krok po kroku** dla każdej modlitwy, generowany wg liczby rak'ah: figurka pozycji, tekst arabski, transliteracja, polskie tłumaczenie, ×3 przy powtórzeniach. Pierścień postępu na krawędzi ekranu.
- **Autoodtwarzanie** ▶: samo przechodzi do kolejnych kroków i daje krótką wibrację przy każdym — można modlić się bez patrzenia na ekran. Tempo ×0.75–×2 w ustawieniach. Ekran nie gaśnie w trakcie.
- **🔊 Odsłuchaj**: czyta tekst arabski syntezatorem mowy (jeśli w zegarku jest arabski głos TTS).

## Budowanie
1. Zainstaluj **Android Studio** (Ladybug lub nowszy).
2. `File → Open` → wskaż folder `SalahWatch`. Poczekaj na Gradle Sync (pobierze SDK i biblioteki).
3. `Build → Build APK(s)` → plik w `app/build/outputs/apk/debug/app-debug.apk`.
   (albo w terminalu: `./gradlew assembleDebug`)

## Wgranie na Xiaomi Watch 2 Pro (ADB przez Wi‑Fi)
1. Zegarek: **Ustawienia → System → Informacje → Wersje** → stuknij 7× w *Numer kompilacji* → włączone Opcje programisty.
2. **Ustawienia → Opcje programisty** → włącz *Debugowanie ADB* i *Debugowanie bezprzewodowe*. Zegarek i komputer w tej samej sieci Wi‑Fi.
3. W *Debugowaniu bezprzewodowym* → *Sparuj nowe urządzenie* → pokaże IP:port i kod.
4. Na komputerze:
   ```
   adb pair IP:PORT_PAROWANIA      # wpisz kod z zegarka
   adb connect IP:PORT              # port z głównego ekranu Debugowania bezprzewodowego
   adb install -r app-debug.apk
   ```
   Albo po `adb connect` po prostu kliknij ▶ Run w Android Studio — zegarek pojawi się na liście urządzeń.
5. Pierwsze uruchomienie: wybierz lokalizację (GPS wymaga zgody i bycia na zewnątrz przez chwilę).

## Struktura
- `PrayerTimes.kt` – obliczenia astronomiczne godzin modlitw
- `Guide.kt` – kroki modlitwy i teksty (arabski / transliteracja / PL)
- `Poses.kt` – rysowane figurki pozycji
- `Screens.kt` – ekrany (Compose for Wear OS)
- `Store.kt` – ustawienia, miasta, GPS
