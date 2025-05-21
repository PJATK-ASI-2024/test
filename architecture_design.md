# Architektura MVC dla aplikacji do zarządzania notatkami

## Model-View-Controller (MVC)

Architektura MVC dzieli aplikację na trzy główne komponenty:

### Model
- Reprezentuje dane i logikę biznesową aplikacji
- Definiuje strukturę danych notatek
- Obsługuje operacje na danych (CRUD)
- Komunikuje się z bazą danych

### View (Widok)
- Odpowiada za prezentację danych użytkownikowi
- Wyświetla listę notatek
- Umożliwia interakcję z aplikacją (formularze, przyciski)
- Prezentuje dane w sposób przyjazny dla użytkownika

### Controller (Kontroler)
- Pośredniczy między Modelem a Widokiem
- Obsługuje żądania HTTP (GET, POST, PUT, DELETE)
- Przetwarza dane wejściowe od użytkownika
- Wywołuje odpowiednie metody Modelu
- Przekazuje dane do Widoku

## Przepływ danych w aplikacji

1. Użytkownik wykonuje akcję w interfejsie (np. dodaje notatkę)
2. Kontroler odbiera żądanie
3. Kontroler przetwarza żądanie i wywołuje odpowiednie metody Modelu
4. Model aktualizuje dane w bazie danych
5. Kontroler pobiera zaktualizowane dane z Modelu
6. Kontroler przekazuje dane do Widoku
7. Widok prezentuje zaktualizowane dane użytkownikowi

## Implementacja w Java/Groovy

### Struktura projektu

```
notes_app/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   ├── com/
│   │   │   │   ├── notesapp/
│   │   │   │   │   ├── model/
│   │   │   │   │   │   ├── Note.java
│   │   │   │   │   │   └── NoteRepository.java
│   │   │   │   │   ├── controller/
│   │   │   │   │   │   ├── NoteController.java
│   │   │   │   │   │   └── ApiController.java
│   │   │   │   │   ├── service/
│   │   │   │   │   │   └── NoteService.java
│   │   │   │   │   └── NotesApplication.java
│   │   ├── resources/
│   │   │   ├── static/
│   │   │   │   ├── css/
│   │   │   │   │   └── style.css
│   │   │   │   ├── js/
│   │   │   │   │   └── script.js
│   │   │   │   └── index.html
│   │   │   └── application.properties
├── pom.xml (dla Maven) lub build.gradle (dla Gradle)
└── run.bat
```

### Technologie

- **Backend**: Java/Groovy z Spring Boot
- **ORM**: Spring Data JPA
- **Baza danych**: PostgreSQL
- **Frontend**: HTML, CSS, JavaScript
- **Narzędzie budowania**: Maven lub Gradle
- **Serwer aplikacji**: Wbudowany serwer Tomcat (Spring Boot)
