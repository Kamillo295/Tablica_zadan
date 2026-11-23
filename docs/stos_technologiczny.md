## Stos technologiczny z krótkim uzasadnieniem

### 1. Język i platforma: C#
* **Rola:** Główny język i środowisko uruchomieniowe aplikacji konsolowej.
* **Uzasadnienie:** Silne typowanie, dobra struktura obiektowa i lekkość bez konieczności stawiania serwerów czy dostępu do internetu.

### 2. Magazyn danych: Lokalny plik JSON
* **Rola:** Lokalna baza danych dla zadań i użytkowników.
* **Uzasadnienie:** Prosty zapis na dysku bez zewnętrznych baz i konfiguracji, wygodny w podglądzie podczas pracy w kole.

### 3. Interfejs użytkownika: Terminal / Konsola
* **Rola:** Obsługa poleceń, menu i widok tablicy Kanban.
* **Uzasadnienie:** Szybka praca w terminalu bez ciężkich narzędzi webowych, z możliwością czytelnego formatowania widoku.

### 4. Architektura: Podział na 3 warstwy
* **Rola:** Rozdzielenie widoku konsoli, zarządzania zadaniami i uprawnieniami ról oraz odczytu/zapisu JSON.
* **Uzasadnienie:** Porządek w kodzie, łatwiejsze testowanie i rozwój aplikacji.