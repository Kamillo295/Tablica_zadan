# Wymagania funkcjonalne oraz niefunkcjonalne

## Przegląd procesu i ról

System odwzorowuje cykl życia zadania w ramach koła/zespołu projektowego z podziałem na dwie role:
* **Lider Projektu** – tworzy zadania, przypisuje wykonawców, analizuje blokady oraz weryfikuje wykonane prace.
* **Członek Koła** – podejmuje przypisane zadania, realizuje je, zgłasza ewentualne blokady oraz przekazuje gotowe zadania do weryfikacji.

### Statusy zadania
* `To Do` – zadanie utworzone i przypisane do wykonawcy.
* `In Progress` – zadanie podjęte i aktualnie realizowane.
* `Blocked` – wystąpił problem lub brak zasobów (oczekuje na analizę Lidera).
* `Review` – zadanie zgłoszone do weryfikacji przez wykonawcę.
* `Done` – stan końcowy (sukces); zadanie zatwierdzone przez Lidera.

---

## 1. Wymagania funkcjonalne

### Zestawienie wymagań i priorytetów

| ID | Nazwa wymagania | Rola | Priorytet |
| :--- | :--- | :--- | :--- |
| **US-01** | Wybór roli i identyfikacja użytkownika | Użytkownik | **Must Have** |
| **US-02** | Utworzenie zadania i przypisanie wykonawcy | Lider Projektu | **Must Have** |
| **US-03** | Wyświetlanie listy zadań | Lider Projektu / Członek Koła | **Must Have** |
| **US-04** | Podjęcie zadania do realizacji | Członek Koła | **Must Have** |
| **US-05** | Zgłoszenie blokady i opisanie problemu | Członek Koła | **Must Have** |
| **US-06** | Analiza blokady – odblokowanie lub anulowanie zadania | Lider Projektu | **Must Have** |
| **US-07** | Zgłoszenie zadania do weryfikacji | Członek Koła | **Must Have** |
| **US-08** | Weryfikacja – zatwierdzenie lub cofnięcie do poprawy | Lider Projektu | **Must Have** |
| **US-09** | Zapis i odczyt danych z pliku lokalnego | Użytkownik | **Should Have** |
| **US-10** | Filtrowanie zadań (po statusie i wykonawcy) | Lider Projektu / Członek Koła | **Should Have** |
| **US-11** | Podgląd historii zmian statusów zadania | Lider Projektu | **Could Have** |

---

### Szczegółowy opis User Stories i kryteria akceptacji

#### US-01: Wybór roli i identyfikacja użytkownika `Must Have`
> **Jako** Użytkownik, **chcę** wybrać swoją rolę (`Lider Projektu` lub `Członek Koła`) oraz podać swoje imię/identyfikator przy uruchomieniu programu, **aby** uzyskać dostęp do odpowiednich opcji w menu.

**Kryteria akceptacji:**
- [ ] Po uruchomieniu aplikacja wyświetla menu wyboru roli: `Lider Projektu` lub `Członek Koła`.
- [ ] W przypadku wyboru `Członka Koła` użytkownik podaje swoją nazwę lub wybiera profil z listy, aby widzieć przypisane do siebie zadania.
- [ ] Użytkownik może w dowolnym momencie wrócić do menu głównego i zmienić rolę bez zamykania programu.

---

#### US-02: Utworzenie zadania i przypisanie wykonawcy `Must Have`
> **Jako** Lider Projektu, **chcę** utworzyć nowe zadanie ze statusem `To Do` i przypisać do niego wykonawcę, **aby** delegować pracę w zespole.

**Kryteria akceptacji:**
- [ ] Lider wprowadza tytuł, opis zadania oraz wskazuje wykonawcę (Członka Koła).
- [ ] System automatycznie generuje unikalne ID zadania i ustawia status początkowy na `To Do`.
- [ ] System uniemożliwia utworzenie zadania, jeśli tytuł lub pole wykonawcy są puste.

---

#### US-03: Wyświetlanie listy zadań `Must Have`
> **Jako** Lider Projektu / Członek Koła, **chcę** przeglądać listę zadań wraz z ich statusami i wykonawcami, **aby** znać aktualny postęp prac.

**Kryteria akceptacji:**
- [ ] Widok w konsoli wyświetla co najmniej: ID, tytuł, przypisanego wykonawcę, aktualny status oraz opis blokady (jeśli dotyczy).
- [ ] Członek Koła ma szybki podgląd zadań przypisanych bezpośrednio do niego.
- [ ] Lider Projektu widzi wszystkie zadania w projekcie, ze szczególnym uwzględnieniem statusów `Blocked` i `Review`.

---

#### US-04: Podjęcie zadania do realizacji `Must Have`
> **Jako** Członek Koła, **chcę** podjąć przypisane mi zadanie ze statusem `To Do`, **aby** zmienić jego status na `In Progress`.

**Kryteria akceptacji:**
- [ ] Akcja jest dostępna wyłącznie dla zadań w statusie `To Do` przypisanych do aktualnego Członka Koła.
- [ ] Po wyborze zadania i potwierdzeniu podjęcia jego status zmienia się na `In Progress`.
- [ ] Próba podjęcia zadania o innym statusie zwraca czytelny komunikat błędu.

---

#### US-05: Zgłoszenie blokady i opisanie problemu `Must Have`
> **Jako** Członek Koła, **chcę** zgłosić problem lub brak zasobów podczas pracy nad zadaniem, **aby** zmienić jego status na `Blocked` i przekazać informację Liderowi.

**Kryteria akceptacji:**
- [ ] Akcja jest dostępna dla zadań w statusie `In Progress`.
- [ ] System wymaga podania niepustego opisu problemu lub brakujących zasobów.
- [ ] Po zatwierdzeniu status zadania zmienia się na `Blocked`, a opis problemu zapisuje się przy zadaniu i jest widoczny dla Lidera Projektu.

---

#### US-06: Analiza blokady – odblokowanie lub anulowanie zadania `Must Have`
> **Jako** Lider Projektu, **chcę** przeanalizować zablokowane zadanie i ocenić jego wykonalność, **aby** móc je odblokować lub anulować.

**Kryteria akceptacji:**
- [ ] Lider może wybrać dowolne zadanie w statusie `Blocked` i zapoznać się z opisem problemu dodanym przez wykonawcę.
- [ ] Jeśli Lider uzna zadanie za wykonalne (wznowienie), jego status wraca do `In Progress`, umożliwiając dalszą realizację.
- [ ] Jeśli Lider uzna zadanie za niewykonalne, wybiera anulowanie – zadanie otrzymuje status końcowy `Cancelled` i nie podlega już dalszej edycji.

---

#### US-07: Zgłoszenie zadania do weryfikacji `Must Have`
> **Jako** Członek Koła, **chcę** zgłosić zrealizowane zadanie do weryfikacji, **aby** Lider Projektu mógł je sprawdzić.

**Kryteria akceptacji:**
- [ ] Akcja jest dostępna wyłącznie dla zadań w statusie `In Progress`.
- [ ] Po zgłoszeniu status zadania zmienia się na `Review`.
- [ ] Członek Koła nie może samodzielnie zmienić statusu zadania na `Done`.

---

#### US-08: Weryfikacja – zatwierdzenie lub cofnięcie do poprawy `Must Have`
> **Jako** Lider Projektu, **chcę** zweryfikować wykonane zadanie ze statusem `Review`, **aby** je zatwierdzić lub cofnąć do poprawy.

**Kryteria akceptacji:**
- [ ] Lider może wybrać dowolne zadanie w statusie `Review`.
- [ ] Jeśli zadanie spełnia wymagania, Lider je zatwierdza – status zmienia się na końcowy `Done`.
- [ ] Jeśli zadanie wymaga poprawek, Lider cofa je do poprawy (opcjonalnie dodając komentarz) – zadanie wraca do statusu `In Progress` u przypisanego Członka Koła.

---

#### US-09: Zapis i odczyt danych z pliku lokalnego `Should Have`
> **Jako** Użytkownik, **chcę**, aby stan zadań zapisywał się w pliku lokalnym (np. `tasks.json`), **aby** nie tracić danych po zamknięciu aplikacji.

**Kryteria akceptacji:**
- [ ] Każda modyfikacja listy zadań lub zmiana statusu jest zapisywana w pliku JSON.
- [ ] Przy uruchomieniu program automatycznie wczytuje zapisane dane; w przypadku braku pliku uruchamia się z pustą listą bez rzucania wyjątku.

---

#### US-10: Filtrowanie zadań `Should Have`
> **Jako** Lider Projektu / Członek Koła, **chcę** filtrować zadania według statusu lub wykonawcy, **aby** szybciej znajdować zadania wymagające uwagi.

**Kryteria akceptacji:**
- [ ] Użytkownik może wybrać status z listy (np. `Blocked`, `Review`) lub wpisać nazwę wykonawcy.
- [ ] Konsola wyświetla wyłącznie pasujące zadania lub komunikat o braku wyników.

---

#### US-11: Podgląd historii zmian statusów zadania `Could Have`
> **Jako** Lider Projektu, **chcę** podejrzeć historię zmian statusu wybranego zadania, **aby** wiedzieć, ile razy było blokowane lub cofane do poprawy.

**Kryteria akceptacji:**
- [ ] Każda zmiana statusu dopisuje wpis zawierający datę, godzinę, rolę/użytkownika oraz nowy status.
- [ ] W widoku szczegółów zadania można wyświetlić chronologiczną historię zdarzeń.

---

## 2. Macierz dozwolonych przejść statusów

| Status początkowy | Akcja / Decyzja | Rola wykonująca | Status docelowy |
| :--- | :--- | :--- | :--- |
| *(brak)* | Utworzenie zadania i przypisanie wykonawcy | Lider Projektu | `To Do` |
| `To Do` | Podjęcie zadania | Członek Koła | `In Progress` |
| `In Progress` | Wystąpił problem / brak zasobów | Członek Koła | `Blocked` |
| `In Progress` | Zgłoszenie do weryfikacji | Członek Koła | `Review` |
| `Blocked` | Zadanie wykonalne (odblokowanie / wznowienie) | Lider Projektu | `In Progress` |
| `Review` | Zadanie nie spełnia wymagań (cofnięcie do poprawy) | Lider Projektu | `In Progress` |
| `Review` | Zadanie spełnia wymagania (zatwierdzenie) | Lider Projektu | `Done` |

---

## 3. Wymagania niefunkcjonalne

* **Technologia i przenośność:** Aplikacja zaimplementowana w języku C# na platformie .NET (zalecane .NET 10), bez zewnętrznych płatnych bibliotek, uruchamiana w standardowym terminalu (Windows, Linux, macOS).
* **Integralność logiki biznesowej:** System wymusza wyłącznie przejścia opisane w macierzy statusów. Zadania w stanach końcowych `Done` muszą być trwale zablokowane przed dalszą zmianą statusu.
* **Odporność na błędy i walidacja wejścia:** Wprowadzenie nieprawidłowych danych w konsoli (np. tekstu zamiast liczby, pustej wartości, nieistniejącego ID) nie może powodować awaryjnego zakończenia programu – aplikacja musi obsłużyć błąd, wyświetlić komunikat i pozwolić na ponowną próbę.
* **Użyteczność:** Nawigacja oparta na prostym, numerowanym menu, przejrzyste czyszczenie ekranu między widokami (`Console.Clear()`), czytelne formatowanie tabelaryczne oraz wyróżnienie kluczowych statusów kolorami (np. `Blocked` – żółty/pomarańczowy, `Done` – zielony).
* **Kontrola dostępu oparta na rolach:** Menu oraz warstwa logiki biznesowej muszą uniemożliwiać wywołanie akcji przypisanych do innej roli (np. Członek Koła nie może anulować ani zatwierdzać zadań, a Lider Projektu nie podejmuje zadań za wykonawcę).
* **Wydajność:** Czas realizacji operacji w aplikacji (dodawanie, zmiana statusu, filtrowanie, zapis/odczyt JSON) powinien wynosić poniżej 200 ms przy zbiorze do 1000 zadań.
* **Łatwość utrzymania i pracy grupowej:** Kod źródłowy podzielony na logiczne katalogi/moduły (np. `Models`, `Services`, `Storage`, `UI`), zgodny z konwencjami nazewniczymi C# i rozwijany w repozytorium Git z podziałem na gałęzie.
