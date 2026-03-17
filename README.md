Projekt Szkolny: Interaktywny Katalog Filmowy (Baza VOD) 🎬
1. Szczegółowy opis i cel projektu
Aplikacja to autorski katalog filmów i seriali, działający w środowisku lokalnym (XAMPP). Głównym założeniem jest stworzenie dynamicznej strony, która zamiast statycznego kodu HTML, pobiera treści bezpośrednio z bazy danych MySQL. Projekt celowo nie posiada systemu rejestracji dla wielu użytkowników – skupia się na solidnym wykonaniu panelu administratora (Single-User CMS), co pozwala zaprezentować pełne zrozumienie operacji CRUD (Create, Read, Delete) oraz bezpiecznej obsługi formularzy w PHP.

2. Wykorzystane technologie i ich rola
HTML5 & CSS3: Wykorzystanie CSS Grid do stworzenia elastycznej siatki plakatów (Responsive Web Design). Zastosowanie ciemnego motywu wizualnego (Dark Mode), przypominającego popularne serwisy VOD.

JavaScript (Vanilla JS): Walidacja formularzy po stronie klienta (np. blokowanie wysłania formularza, jeśli nie podano tytułu filmu) oraz implementacja prostej wyszukiwarki (filtrowanie widocznych kafelków).

PHP: Przetwarzanie żądań GET/POST, zarządzanie sesją logowania ($_SESSION) dla administratora. Zastosowanie podstawowych zabezpieczeń (np. Prepared Statements lub htmlspecialchars), aby chronić formularze przed atakami typu SQL Injection.

MySQL: Relacyjna baza danych obsługiwana przez phpMyAdmin w pakiecie XAMPP.

3. Architektura bazy danych
Cała logika opiera się na jednej, zoptymalizowanej tabeli filmy. Kolumny:

id (INT, PRIMARY KEY, AUTO_INCREMENT) – unikalny numer produkcji.

tytul (VARCHAR) – nazwa filmu.

rok_produkcji (INT) – rok premiery.

opis (TEXT) – streszczenie fabuły.

plakat_url (VARCHAR) – ścieżka do pliku ze zdjęciem (lub link URL).

zwiastun_url (VARCHAR) – link do osadzenia wideo (np. iframe z YouTube).

4. Funkcjonalności Front-end (Dla widza)
Dynamiczny katalog: Skrypt PHP łączy się z bazą i za pomocą pętli (while) generuje kafelki z filmami na stronie głównej.

Karta produkcji: Po kliknięciu w plakat, użytkownik widzi pełne informacje o filmie oraz zintegrowany odtwarzacz wideo, który płynnie wpasowuje się w stronę.

5. Funkcjonalności Back-end (Panel Administratora)
Autoryzacja: Dostęp do panelu możliwy tylko po podaniu poprawnego hasła. Brak zalogowania powoduje przekierowanie na stronę główną.

Dodawanie (Create): Formularz HTML połączony ze skryptem PHP, który po poprawnej walidacji wykonuje zapytanie INSERT INTO i dodaje nowy film do bazy.

Usuwanie (Delete): Obok każdego filmu w panelu admina znajdzie się przycisk "Usuń", który wykonuje zapytanie DELETE FROM filmy WHERE id = ..., pozwalając na szybkie zarządzanie biblioteką.
