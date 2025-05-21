# Instrukcje wdrożenia i uruchomienia aplikacji do zarządzania notatkami

## Wymagania wstępne

Przed uruchomieniem aplikacji upewnij się, że masz zainstalowane następujące oprogramowanie:

1. **Java JDK 11** lub nowsza
2. **PostgreSQL** (wersja 12 lub nowsza)
3. **Maven** (opcjonalnie, skrypt używa wbudowanego Maven Wrapper)

## Konfiguracja bazy danych

1. Uruchom PostgreSQL
2. Utwórz nową bazę danych o nazwie `notesdb`:
   ```sql
   CREATE DATABASE notesdb;
   ```
3. Upewnij się, że użytkownik PostgreSQL ma odpowiednie uprawnienia do bazy danych
4. Jeśli chcesz zmienić domyślne dane dostępowe do bazy danych, edytuj plik `src/main/resources/application.properties`

## Uruchomienie aplikacji

### Sposób 1: Używając skryptu .bat (Windows)

1. Kliknij dwukrotnie na plik `run.bat` w głównym katalogu projektu
2. Skrypt automatycznie sprawdzi wymagania i uruchomi aplikację
3. Otwórz przeglądarkę i przejdź do adresu: http://localhost:8080

### Sposób 2: Używając Maven (Windows/Linux/Mac)

1. Otwórz terminal/wiersz poleceń
2. Przejdź do głównego katalogu projektu
3. Uruchom aplikację za pomocą Maven:
   ```
   ./mvnw spring-boot:run   # Linux/Mac
   mvnw.cmd spring-boot:run # Windows
   ```
4. Otwórz przeglądarkę i przejdź do adresu: http://localhost:8080

### Sposób 3: Używając IDE (IntelliJ IDEA, Eclipse, itp.)

1. Otwórz projekt w swoim IDE
2. Uruchom klasę `com.notesapp.NotesApplication` jako aplikację Java
3. Otwórz przeglądarkę i przejdź do adresu: http://localhost:8080

## Testowanie REST API

Możesz testować REST API za pomocą narzędzi takich jak Postman lub cURL:

### Przykładowe zapytania cURL

1. **Pobieranie wszystkich notatek**:
   ```
   curl -X GET http://localhost:8080/data
   ```

2. **Pobieranie notatek posortowanych**:
   ```
   curl -X GET "http://localhost:8080/data?sortBy=title&direction=asc"
   ```

3. **Dodawanie nowej notatki**:
   ```
   curl -X POST http://localhost:8080/data -H "Content-Type: application/json" -d "{\"title\":\"Nowa notatka\",\"content\":\"Treść nowej notatki\"}"
   ```

4. **Aktualizacja notatki**:
   ```
   curl -X PUT http://localhost:8080/data/1 -H "Content-Type: application/json" -d "{\"title\":\"Zaktualizowana notatka\",\"content\":\"Nowa treść notatki\"}"
   ```

5. **Usuwanie notatki**:
   ```
   curl -X DELETE http://localhost:8080/data/1
   ```

## Rozwiązywanie problemów

1. **Problem z połączeniem do bazy danych**:
   - Sprawdź, czy PostgreSQL jest uruchomiony
   - Sprawdź dane dostępowe w pliku `application.properties`
   - Upewnij się, że baza danych `notesdb` istnieje

2. **Problem z uruchomieniem aplikacji**:
   - Sprawdź, czy Java jest zainstalowana i dostępna w PATH
   - Sprawdź logi aplikacji w konsoli

3. **Problem z dostępem do aplikacji**:
   - Upewnij się, że aplikacja jest uruchomiona
   - Sprawdź, czy port 8080 nie jest zajęty przez inną aplikację
