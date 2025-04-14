## Zarządzanie cyklem życia obiektów Doctrine

Podczas tworzenia nowego komentarza dobrze by było, gdyby data `createdAt` była automatycznie ustawiana na bieżącą datę i godzinę.

Doctrine oferuje różne sposoby manipulowania obiektami i ich właściwościami w trakcie ich cyklu życia (przed utworzeniem wiersza w bazie danych, po jego aktualizacji itp.).

### Definiowanie callbacków cyklu życia

Gdy dane zachowanie nie wymaga żadnych usług i powinno być stosowane tylko do jednego rodzaju encji, należy zdefiniować callback bezpośrednio w klasie encji:

```diff
--- a/src/Controller/Admin/CommentCrudController.php
+++ b/src/Controller/Admin/CommentCrudController.php
@@ -57,8 +57,6 @@ class CommentCrudController extends AbstractCrudController
         ]);
         if (Crud::PAGE_EDIT === $pageName) {
             yield $createdAt->setFormTypeOption('disabled', true);
-        } else {
-            yield $createdAt;
         }
     }
 }
--- a/src/Entity/Comment.php
+++ b/src/Entity/Comment.php
@@ -7,6 +7,7 @@ use Doctrine\DBAL\Types\Types;
 use Doctrine\ORM\Mapping as ORM;

 #[ORM\Entity(repositoryClass: CommentRepository::class)]
+#[ORM\HasLifecycleCallbacks]
 class Comment
 {
     #[ORM\Id]
@@ -86,6 +87,12 @@ class Comment
         return $this;
     }

+    #[ORM\PrePersist]
+    public function setCreatedAtValue()
+    {
+        $this->createdAt = new \DateTimeImmutable();
+    }
+
     public function getConference(): ?Conference
     {
         return $this->conference;
```

*Zdarzenie* `ORM\PrePersist` jest wywoływane, gdy obiekt jest zapisywany w bazie danych po raz pierwszy. W tym momencie wywoływana jest metoda `setCreatedAtValue()`, a bieżąca data i godzina zostaje użyta jako wartość właściwości `createdAt`.
