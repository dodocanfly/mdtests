## Konfigurowanie zaplecza administratora

Dodawanie nadchodzących konferencji do bazy danych należy do zadań administratorów projektu. Zaplecze administratora to chroniona sekcja strony internetowej, w której administratorzy projektu mogą zarządzać danymi strony, moderować zgłoszenia opinii i nie tylko.


Jak możemy to zrobić szybko? Korzystając z pakietu, który potrafi wygenerować zaplecze administratora na podstawie modelu projektu. EasyAdmin idealnie się do tego nadaje.

### Instalowanie dodatkowych zależności

Chociaż pakiet webapp automatycznie dodał wiele przydatnych pakietów, do niektórych bardziej specyficznych funkcji musimy dodać dodatkowe zależności. Jak możemy dodać więcej zależności? Za pomocą Composera. Oprócz "zwykłych" pakietów Composera, będziemy pracować z dwoma "specjalnymi" rodzajami pakietów:

 
- **Komponenty Symfony**: Pakiety, które implementują funkcje podstawowe i niskopoziomowe abstrakcje, które są potrzebne większości aplikacji (routing, konsola, klient HTTP, mailer, cache, ...);
 
- **Bundle Symfony**: Pakiety, które dodają funkcje wysokiego poziomu lub zapewniają integrację z bibliotekami zewnętrznymi (bundles są głównie tworzone przez społeczność).


Dodajmy EasyAdmin jako zależność projektu:



```bash
symfony composer req "easycorp/easyadmin-bundle:4.x-dev"
```

`admin` to alias dla pakietu `easycorp/easyadmin-bundle`.

Alias to nie funkcja Composera, ale koncepcja dostarczona przez Symfony, mająca na celu ułatwienie pracy. Aliasy to skróty dla popularnych pakietów Composera. Chcesz ORM dla swojej aplikacji? Wymagaj `orm`. Chcesz rozwijać API? Wymagaj `api`. Te aliasy są automatycznie przekształcane na jeden lub więcej standardowych pakietów Composera. Są to wybory dokonane przez zespół rdzenia Symfony.
Kolejną przydatną funkcją jest to, że zawsze możesz pominąć prefiks symfony. Wymagaj `cache` zamiast `symfony/cache`.

> [!NOTE]
> Pamiętasz, że wcześniej wspomnieliśmy o wtyczce Composera o nazwie `symfony/flex`? Aliasy to jedna z jej funkcji.
