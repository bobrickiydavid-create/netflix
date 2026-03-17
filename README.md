# Specyfikacja Projektu: Prywatny Katalog Filmowy (Platforma VOD)

## 1. Opis i Przeznaczenie Aplikacji
Projekt to aplikacja webowa pełniąca rolę interaktywnej bazy filmów i seriali. Głównym zadaniem systemu jest prezentacja multimediów (plakatów, opisów, zwiastunów) w przystępnej formie wizualnej oraz umożliwienie zarządzania tą bazą z poziomu dedykowanego panelu administratora (CMS), bez konieczności bezpośredniej ingerencji w kod źródłowy czy bazę danych (np. przez phpMyAdmin).

## 2. Główne Funkcjonalności (Use Cases)

### A. Moduł Użytkownika (Widok Główny / Front-end)
- **Przeglądanie katalogu:** Wyświetlanie wszystkich filmów pobranych z bazy danych w postaci responsywnej siatki plakatów.
- **Karta filmu (Szczegóły):** Dedykowana podstrona dla każdego tytułu, zawierająca szczegółowe informacje (rok produkcji, streszczenie fabuły) oraz zintegrowany odtwarzacz wideo ze zwiastunem (osadzony element iframe z YouTube).
- **Wyszukiwarka:** Pasek wyszukiwania pozwalający na odnalezienie filmu w bazie po fragmencie tytułu.

### B. Moduł Administratora (Zarządzanie / Back-end)
- **Autoryzacja:** Zabezpieczony dostęp do panelu dodawania filmów poprzez system logowania (sesje w PHP).
- **Dodawanie filmów (Create):** Interaktywny formularz HTML/PHP pozwalający na dodanie nowej produkcji do bazy (wprowadzenie tytułu, linku do plakatu, opisu i linku do zwiastuna). Formularz wykorzystuje JavaScript do walidacji danych przed wysłaniem.
- **Usuwanie filmów (Delete):** Funkcja pozwalająca na szybkie usunięcie wybranej pozycji z katalogu za pomocą jednego kliknięcia.

## 3. Wykorzystane Technologie (Stack Technologiczny)
- **Front-end:** HTML5, CSS3 (Flexbox/Grid), JavaScript (Vanilla JS do walidacji i interakcji).
- **Back-end:** PHP 8.x (obsługa formularzy, sesji, zapytań do bazy).
- **Baza Danych:** MySQL.
- **Środowisko:** Lokalny serwer XAMPP (Apache + MariaDB).

## 4. Struktura Bazy Danych (MySQL)
Aplikacja wykorzystuje jedną główną tabelę do przechowywania wszystkich metadanych o filmach.

**Baza:** `vod_platform_db` | **Tabela:** `movies`

| Kolumna       | Typ danych    | Opis / Atrybuty |
| :---          | :---          | :--- |
| `id`          | INT           | Klucz główny (PRIMARY KEY), Auto Increment |
| `title`       | VARCHAR(255)  | Pełny tytuł produkcji |
| `description` | TEXT          | Streszczenie fabuły |
| `year`        | INT(4)        | Rok premiery |
| `image_url`   | VARCHAR(500)  | Ścieżka URL do plakatu filmowego |
| `trailer_url` | VARCHAR(500)  | Adres URL do zwiastuna wideo (np. YouTube) |
