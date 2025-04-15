## Akceptowanie opinii za pomocą formularzy

Czas pozwolić uczestnikom konferencji wyrazić swoją opinię. Będą oni przekazywać swoje komentarze za pomocą formularza HTML.

### Tworzenie klasy formularza

Użyj pakietu Maker, aby wygenerować klasę formularza:

```bash
symfony console make:form CommentType Comment
```

```
created: src/Form/CommentType.php


 Success!


Next: Add fields to your form and start using it.
Find the documentation at https://symfony.com/doc/current/forms.html
```




### Sprawdź również:
- [Przepływ żądania i odpowiedzi](https://symfony.com/doc/current/components/http_kernel.html#the-workflow-of-a-request) w aplikacjach Symfony;
- [Wbudowane zdarzenia HTTP w Symfony](https://symfony.com/doc/current/reference/events.html);
- [Wbudowane zdarzenia konsoli w Symfony](https://symfony.com/doc/current/components/console/events.html).

---

- **Poprzednia strona:** [Zarządzanie cyklem życia obiektów Doctrine](13-lifecycle.md)
- **Następna strona:** [Zabezpieczanie panelu administracyjnego](15-security.md)
