# API Testing in Postman

Repozytorium zawiera kolekcję Postman do testowania API (JSONPlaceholder) oraz środowisko. Poniższa struktura i skrypty pozwalają uruchamiać testy lokalnie oraz w CI (GitHub Actions) przy użyciu Newmana.

Struktura
- postman/collections/*.postman_collection.json
- postman/environments/*.postman_environment.json

Wymagania
- Node.js (LTS, np. 18+)
- npm

Instalacja
1. Zainstaluj zależności:
   ```bash
   npm ci
   ```

Uruchamianie testów lokalnie
- Bezpośrednio przez npm:
  ```bash
  npm test
  ```
  Skrypt uruchamia Newmana na kolekcji i środowisku z katalogu postman/.

Import do Postman
- W Postman: File → Import → wybierz plik z postman/collections/ lub użyj linku/importu z pliku JSON.

Bezpieczeństwo
- Pliki środowiskowe nie powinny zawierać rzeczywistych sekretów. Używaj placeholderów (np. `<YOUR_API_KEY>`) i przechowuj prawdziwe wartości jako Secrets w CI.

CI (GitHub Actions)
- Po dodaniu workflow (/.github/workflows/newman.yml) testy będą uruchamiane na push/PR do gałęzi main. Wyniki JUnit będą zapisywane jako artefakt.

Dalsze kroki / sugestie
- Dodaj badge CI do README po skonfigurowaniu workflow.
- Rozbuduj asercje w kolekcji Postman (status codes, JSON schema).
- (Opcjonalnie) dodaj newman-reporter-html dla czytelnych raportów HTML.

Autor: Maciej Miszewski
