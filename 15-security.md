## Zabezpieczanie panelu administracyjnego

Interfejs panelu administracyjnego powinien być dostępny wyłącznie dla zaufanych osób. Zabezpieczenie tej części witryny można zrealizować za pomocą komponentu Symfony Security.

### Tworzenie encji użytkownika

Chociaż użytkownicy nie będą mogli zakładać własnych kont na stronie, stworzymy w pełni funkcjonalny system uwierzytelniania dla administratora. Będziemy zatem mieć tylko jednego użytkownika — administratora strony.

Pierwszym krokiem jest zdefiniowanie encji `User`. Aby uniknąć nieporozumień, nazwijmy ją `Admin`.

Aby zintegrować encję `Admin` z systemem uwierzytelniania Symfony Security, musi ona spełniać określone wymagania. Na przykład, musi zawierać właściwość `password`.

Zamiast używać tradycyjnego polecenia `make:entity`, użyj dedykowanego polecenia `make:user`, aby utworzyć encję `Admin`:

```bash
symfony console make:user Admin
```

Odpowiedz na pytania interaktywne: chcemy użyć Doctrine do przechowywania administratorów (`yes`), używać nazwy użytkownika (`username`) jako unikalnej nazwy wyświetlanej administratorów, oraz każdy użytkownik będzie posiadał hasło (`tak`).

Wygenerowana klasa zawiera takie metody jak `getRoles()`, `eraseCredentials()` i kilka innych, wymaganych przez system uwierzytelniania Symfony.

Jeśli chcesz dodać więcej właściwości do użytkownika `Admin`, użyj komendy `make:entity`.

Oprócz wygenerowania encji `Admin`, komenda ta zaktualizowała również konfigurację bezpieczeństwa, aby powiązać encję z systemem uwierzytelniania:

```diff
--- a/config/packages/security.yaml
+++ b/config/packages/security.yaml
@@ -5,14 +5,18 @@ security:
         Symfony\Component\Security\Core\User\PasswordAuthenticatedUserInterface: 'auto'
     # https://symfony.com/doc/current/security.html#loading-the-user-the-user-provider
     providers:
-        users_in_memory: { memory: null }
+        # used to reload user from session & other features (e.g. switch_user)
+        app_user_provider:
+            entity:
+                class: App\Entity\Admin
+                property: username
     firewalls:
         dev:
             pattern: ^/(_(profiler|wdt)|css|images|js)/
             security: false
         main:
             lazy: true
-            provider: users_in_memory
+            provider: app_user_provider

             # activate different ways to authenticate
             # https://symfony.com/doc/current/security.html#the-firewall
```

Pozostawiamy Symfony wybór najlepszego dostępnego algorytmu do haszowania haseł (co będzie się zmieniać w czasie).

Czas wygenerować migrację i zastosować ją do bazy danych:

```bash
symfony console make:migration
symfony console doctrine:migrations:migrate -n
```


[...]

### Sprawdź również:
- [...]

---

- **Poprzednia strona:** [Akceptowanie opinii za pomocą formularzy](14-form.md)
- **Następna strona:** [Zapobieganie spamowi za pomocą API](16-spam.md)
