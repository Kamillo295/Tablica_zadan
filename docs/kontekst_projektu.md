# 1. Kontekst projektu

## 1.1. Wizja systemu
**Kółko Zadań** to lekka, lokalna aplikacja konsolowa napisana w języku **C# (.NET)**, wykorzystująca plik **JSON** jako lokalną bazę danych. System służy do sprawnego zarządzania zadaniami projektowymi wewnątrz studenckiego koła naukowego (np. podczas budowy robotów, projektowania elektroniki lub organizacji wydarzeń).

Aplikacja eliminuje potrzebę korzystania z ciężkich, rozbudowanych narzędzi webowych wymagających stałego dostępu do internetu i konfiguracji serwerów. Umożliwia szybkie dodawanie zadań, przypisywanie ich do członków zespołu oraz śledzenie postępów prac w czytelnym widoku tablicy Kanban (`To Do`, `In Progress`, `Review`, `Done`, `Blocked`) bezpośrednio z poziomu terminala.

## 1.2. Lista aktorów
W systemie zdefiniowano dwóch głównych aktorów:

1. **Lider Projektu (Przewodniczący / Koordynator):**
   * Odpowiada za planowanie i nadzór nad realizacją prac w zespole.
   * Posiada pełne uprawnienia do zarządzania zadaniami: może tworzyć nowe zadania, edytować je, usuwać oraz przypisywać do konkretnych wykonawców.
   * Weryfikuje zadania zgłoszone do sprawdzenia (`Review`) i zatwierdza ich zakończenie (`Done`) lub cofa do poprawy.

2. **Członek Koła (Wykonawca):**
   * Realizuje przydzielone mu zadania projektowe.
   * Może przeglądać tablicę zadań, filtrować ją (np. po swoim nazwisku lub priorytecie) oraz aktualizować status swoich zadań (`In Progress`, `Review`).
   * W przypadku napotkania przeszkód (np. brak podzespołów, awaria sprzętu) może oznaczyć zadanie statusem wyjątkowym (`Blocked`) i zgłosić problem Liderowi.
