### UC3: Utworzenie zadania i przypisanie wykonawcy
* **Aktor:** Lider Projektu
* **Cel:** Dodanie nowego zadania i wyznaczenie osoby odpowiedzialnej.
* **Przebieg:**
  1. Lider wybiera opcję dodania zadania i wypełnia formularz (tytuł, opis, priorytet, termin).
  2. Przypisuje wykonawcę z listy Członków Koła i zatwierdza.
  3. System zapisuje zadanie i aktualizuje tablicę (`UC1`).

### UC5: Zmiana statusu zadania
* **Aktor:** Członek Koła (Wykonawca)
* **Cel:** Aktualizacja postępu prac nad zadaniem.
* **Przebieg:**
  1. Wykonawca otwiera tablicę zadań (`UC1`) i wybiera swoje zadanie.
  2. Zmienia jego status (np. na „In progress” lub „Review”).
  3. System weryfikuje uprawnienia, zapisuje zmianę i odświeża tablicę.

### UC7: Weryfikacja zadania (Zatwierdzenie / Cofnięcie)
* **Aktor:** Lider Projektu
* **Cel:** Kontrola wykonania zadania i jego zamknięcie lub zwrot do poprawy.
* **Przebieg:**
  1. Lider otwiera zadanie ze statusem „Rewiew” i sprawdza efekty pracy.
  2. Zatwierdza zadanie (status „Done”) lub cofa je z uwagami (status „In progress”).
  3. System aktualizuje tablicę (`UC1`).