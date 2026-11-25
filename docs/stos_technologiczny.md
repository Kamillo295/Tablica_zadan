# 1. Kontekst projektu

## 1.1. Wizja systemu
**Kółko Zadań** to lekka, lokalna aplikacja konsolowa napisana w języku **C# (.NET)**, wykorzystująca plik **JSON** jako lokalną bazę danych. System służy do sprawnego zarządzania zadaniami projektowymi wewnątrz studenckiego koła naukowego (np. podczas budowy robotów, projektowania elektroniki lub organizacji wydarzeń).

Aplikacja eliminuje potrzebę korzystania z ciężkich, rozbudowanych narzędzi webowych wymagających stałego dostępu do internetu i konfiguracji serwerów. Umożliwia szybkie dodawanie zadań, przypisywanie ich do członków zespołu oraz śledzenie postępów prac w czytelnym widoku tablicy Kanban (`To Do`, `In Progress`, `Review`, `Done`, `Blocked`) bezpośrednio z poziomu terminala.

## 1.2. Lista aktorów
W systemie zdefiniowano dwóch głównych aktorów:

1. **Lider Projektu (Przewodniczący / Koordynator):**
  - Odpowiada za planowanie i nadzór nad realizacją prac w zespole.
  - Posiada pełne uprawnienia do zarządzania zadaniami: może tworzyć nowe zadania, edytować je, usuwać oraz przypisywać do konkretnych wykonawców.
  - Weryfikuje zadania zgłoszone do sprawdzenia (`Review`) i zatwierdza ich zakończenie (`Done`) lub cofa do poprawy.

2. **Członek Koła (Wykonawca):**
  - Realizuje przydzielone mu zadania projektowe.
  - Może przeglądać tablicę zadań, filtrować ją (np. po swoim nazwisku lub priorytecie) oraz aktualizować status swoich zadań (`In Progress`, `Review`).
  - W przypadku napotkania przeszkód (np. brak podzespołów, awaria sprzętu) może oznaczyć zadanie statusem wyjątkowym (`Blocked`) i zgłosić problem Liderowi.

## 1.3. Stos technologiczny

1. **Język i platforma: C#**
  - Główny język programowania oraz środowisko uruchomieniowe aplikacji konsolowej.
  - **Uzasadnienie:** Wybrany ze względu na silne typowanie, bezpieczeństwo kompilacji oraz dojrzały model programowania obiektowego, który ułatwia odwzorowanie encji domenowych takich jak zadania, statusy czy role użytkowników. Platforma zapewnia wysoką wydajność przy minimalnym narzucie zasobów oraz pozwala na stworzenie samodzielnej, przenośnej aplikacji działającej lokalnie bez konieczności konfiguracji serwerów aplikacyjnych czy stałego dostępu do sieci.

2. **Magazyn danych: Lokalny plik JSON**
  - Lokalna baza danych przechowująca stan tablicy Kanban, zadania oraz informacje o członkach zespołu.
  - **Uzasadnienie:** Pozwala na trwałe przechowywanie danych bezpośrednio na dysku bez konieczności instalowania, uruchamiania i administrowania zewnętrznymi serwerami bazodanowymi. Czytelna, tekstowa struktura formatu JSON ułatwia weryfikację stanu danych podczas prac rozwojowych, upraszcza tworzenie kopii zapasowych oraz pozwala na bezproblemowe wersjonowanie lub przenoszenie pliku między stanowiskami w kole naukowym.

3. **Interfejs użytkownika: Terminal / Konsola**
  - Warstwa prezentacji obsługująca menu, polecenia użytkownika oraz wyświetlanie kolumn tablicy Kanban.
  - **Uzasadnienie:** Gwarantuje natychmiastowe uruchamianie aplikacji, niskie zużycie pamięci oraz brak zależności od przeglądarek internetowych i ciężkich frameworków graficznych. Bezpośrednia obsługa z poziomu terminala doskonale wpisuje się w środowisko pracy zespołów technicznych i programistycznych, umożliwiając szybką nawigację oraz filtrowanie zadań za pomocą prostych komend.

4. **Architektura: Podział na 3 warstwy**
  - Logiczny podział systemu na **Interfejs Konsolowy**, **Logikę Aplikacji** oraz **Moduł Obsługi Danych**.
  - **Uzasadnienie:** Wyraźna separacja odpowiedzialności oddziela sposób prezentacji danych w terminalu oraz mechanizm zapisu plików od kluczowych reguł biznesowych, takich jak walidacja zmian statusów czy egzekwowanie uprawnień między Liderem Projektu a Członkiem Koła. Dzięki temu kod pozostaje czytelny, łatwy w testowaniu jednostkowym oraz odporny na błędy przy dalszej rozbudowie systemu, na przykład w przypadku zmiany sposobu przechowywania danych w przyszłości[cite: 1, 2].