#### Symfony

##### Klonowanie repozytorium [https://github.com/the-fast-track/book-6.4-1](https://github.com/the-fast-track/book-6.4-1)
```bash
symfony new --version=6.4-1 --book guestbook
```

##### Przejście do kodu z końca kroku 10 / podkroku 10.2
```bash
symfony book:checkout 10
symfony book:checkout 10.2
```

##### Tworzenie nowej aplikacji Symfony
```bash
symfony new guestbook --version=6.4 --php=8.3 --webapp --docker --cloud
```
- `--version=6.4` - wersja Symfony
- `--php=8.3` - wersja PHP
- `--webapp` - domyślnie tworzona jest aplikacja z minimalną ilością zależności - dla większości projektów webowych zaleca się dodanie pakietu webapp, który zawiera potrzebne pakiety, m.in. Symfony Messenger i PostgreSQL przez Doctrine
- `--docker` - na lokalnym komputerze używamy Dockera do zarządzania usługami, takimi jak PostgreSQL - ta opcja automatycznie dodaje odpowiednie konfiguracje dla Dockera
- `--cloud` - jeśli chcesz wdrożyć projekt na Platform.sh, ta opcja generuje pliki konfiguracyjne niezbędne do tego środowiska

##### Uruchomienie lokalnego serwera w tle
```bash
symfony server:start -d
```

##### Otwarcie strony aplikacji w przeglądarce (lokalnie)
```bash
symfony open:local
```

##### Tworzenie nowego zdalnego projektu na Platform.sh
```bash
symfony cloud:project:create --title="Guestbook" --plan=development
```

##### Deployowanie projektu
```bash
symfony cloud:deploy
```

##### Otwarcie strony aplikacji w przeglądarce (zdalnej na Platform.sh)
```bash
symfony cloud:url -1
```

##### Usunięcie projektu z Platform.sh
```bash
symfony cloud:project:delete
```

##### Uruchonienie logów lokalnego serwera w konsoli
```bash
symfony server:log
```

##### Wyświetlenie w konsoli logów z serwera produkcyjnego Platform.sh
```bash
symfony cloud:log --tail
```

##### Nawiązanie połączenia SSH z kontenerem na Platform.sh
```bash
symfony cloud:ssh
```

##### Wyświetlenie listy wszystkich generatowów kodu Symfony
```bash
symfony console list make
```

#### Git

##### Wyświetlenie różnic w kodzie pomiędzy podanymi krokami (branchami)
```bash
git diff step-10-1...step-10-2
git diff step-9...step-10-1
```

##### Sprawdzanie kiedy dany plik został utworzony lub zmodyfikowany
```bash
git log -- src/Controller/ConferenceController.php
```

#### Docker

##### Wyświetlenie logów Docker Compose
```bash
docker compose logs
```
