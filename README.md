# jiip-2026
Robimy grę zręcznościową na platfornie Microbit. Wynik i identyfikator użytkownika ma by przesyłany online => zapisywany w bazie, ranking ma by dostępny online webowo i na fizycznym urządzeniu. Do dyspozycji mamy Microbity i Arduino. Wybór narzędzi typu bazy danych, frameworki, protokoły komunikacyjne, chmury, wirtualizacja dowolne.

KONCEPT
Gra: micro:bit z grą zręcznościową „Unik”.
Zasady gry: gracz porusza się kropką w dolnym rzędzie ekranu (przechylając micro:bita albo przyciskami A/B) i omija przeszkody spadające z góry. Każda ominięta przeszkoda daje 1 punkt, a tempo gry stopniowo rośnie. Zderzenie kończy grę.

Identyfikacja gracza: po grze gracz wybiera przyciskami 3 litery inicjałów (A zmienia literę, B ją zatwierdza).
Wysyłka wyniku: micro:bit wysyła przez kabel USB do komputera linię z inicjałami i wynikiem, np. „ABC,950”.
Strona na komputerze: strona otwarta w przeglądarce, połączona z micro:bitem przez Web Serial, odbiera wynik.
Zapis do bazy: strona zapisuje wynik w bazie PostgreSQL w usłudze Supabase przez gotowe REST API.
Baza danych: tabela „scores” (inicjały, wynik, data) oraz widok „leaderboard” z najlepszym wynikiem każdego gracza (top 10).
Zabezpieczenia: reguły RLS pozwalają tylko dodawać i odczytywać wyniki, bez edycji i usuwania. Ograniczenia w tabeli pilnują formatu inicjałów i dopuszczalnego zakresu punktów.
Ranking WWW: ta sama strona pokazuje top 10 odświeżane na żywo przez Supabase Realtime i jest dostępna z dowolnego urządzenia z przeglądarką.
Ranking na urządzeniu: strona odsyła przez USB top 3 do micro:bita, który po naciśnięciu A+B przewija ranking na diodach.
Kod źródłowy: cały projekt jest przechowywany w repozytorium GitHub.
Publikacja strony: repozytorium GitHub jest podpięte pod darmowy hosting Netlify, który automatycznie publikuje stronę po każdej zmianie w repozytorium.
Infrastruktura: micro:bit, komputer z przeglądarką, Supabase, GitHub i Netlify.
