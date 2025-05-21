# Schemat bazy danych PostgreSQL dla aplikacji do zarządzania notatkami

## Tabela: notes

| Kolumna      | Typ danych      | Ograniczenia                 | Opis                                |
|--------------|-----------------|------------------------------|-------------------------------------|
| id           | SERIAL          | PRIMARY KEY                  | Unikalny identyfikator notatki      |
| title        | VARCHAR(255)    | NOT NULL                     | Tytuł notatki                       |
| content      | TEXT            | NOT NULL                     | Treść notatki                       |
| created_at   | TIMESTAMP       | NOT NULL, DEFAULT NOW()      | Data i czas utworzenia notatki      |
| updated_at   | TIMESTAMP       | NOT NULL, DEFAULT NOW()      | Data i czas ostatniej aktualizacji  |

## Skrypt SQL do utworzenia tabeli

```sql
CREATE TABLE notes (
    id SERIAL PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    content TEXT NOT NULL,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
);
```

## Indeksy

```sql
-- Indeks dla szybkiego wyszukiwania po tytule
CREATE INDEX idx_notes_title ON notes(title);

-- Indeks dla sortowania po dacie utworzenia
CREATE INDEX idx_notes_created_at ON notes(created_at);

-- Indeks dla sortowania po dacie aktualizacji
CREATE INDEX idx_notes_updated_at ON notes(updated_at);
```

## Przykładowe dane testowe

```sql
INSERT INTO notes (title, content) VALUES 
('Pierwsza notatka', 'To jest treść pierwszej notatki.'),
('Spotkanie projektowe', 'Omówić wymagania projektu z zespołem.'),
('Lista zakupów', 'Mleko, chleb, jajka, ser, owoce.'),
('Pomysły na projekt', 'Aplikacja do zarządzania notatkami z REST API.');
```

## Diagram ER

```
+---------------+
|     notes     |
+---------------+
| id            |
| title         |
| content       |
| created_at    |
| updated_at    |
+---------------+
```

## Konfiguracja połączenia w Spring Boot

W pliku `application.properties` należy dodać następujące ustawienia:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/notesdb
spring.datasource.username=postgres
spring.datasource.password=password
spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect
```

Gdzie:
- `notesdb` to nazwa bazy danych
- `postgres` to nazwa użytkownika
- `password` to hasło użytkownika
