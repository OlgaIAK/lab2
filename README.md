# Лабораторная работа №2: Изучение систем контроля версий на примере Git

**Выполнила:** Алексеева Ольга (IU8-25)

---

## Part I

### 1. Создание пустого репозитория
Создан публичный репозиторий на GitHub с названием `lab2` (с лицензией MIT).

### 2. Первый коммит
Выполнена инструкция по инициализации репозитория и созданию первого коммита на странице репозитория.

### 3. Создание `hello_world.cpp` (плохой стиль)

```bash
$ nano hello_world.cpp
$ cat hello_world.cpp
```

```cpp
#include <iostream>

using namespace std;

int main() {
    cout << "Hello world" << endl;
    return 0;
}
```

### 4. Добавление файла в локальную копию

```bash
$ git add hello_world.cpp
```

### 5. Коммит изменений

```bash
$ git commit -m "create hello_world program in c++ (needs refactoring)"
```

```
[main f93f8a5] create hello_world program in c++ (needs refactoring)
 1 file changed, 8 insertions(+)
 create mode 100644 hello_world.cpp
```

### 6. Изменение кода (запрос имени пользователя)

```bash
$ nano hello_world.cpp
$ cat hello_world.cpp
```

```cpp
#include <iostream>
#include <string>

using namespace std;

int main() {
    string name;
    cout << "Enter your name: ";
    cin >> name;
    cout << "Hello world from " << name << endl;
    return 0;
}
```

### 7. Коммит новой версии (без `git add`)

```bash
$ git commit -am "add name prompt to hello_world"
```

```
[main 16275df] add name prompt to hello_world
 1 file changed, 5 insertions(+), 1 deletion(-)
```

> **Почему не нужен `git add`?**  
> Флаг `-a` включает в коммит все изменения в уже отслеживаемых файлах.

### 8. Пуш в удалённый репозиторий

```bash
$ git push
```

### 9. Проверка истории коммитов

История коммитов доступна в удалённом репозитории на вкладке `Commits`.

---

## Part II

### 1. Создание локальной ветки `patch1`

```bash
$ git checkout -b patch1
```

### 2. Исправление кода (избавление от `using namespace std;`)

```bash
$ nano hello_world.cpp
$ cat hello_world.cpp
```

```cpp
#include <iostream>
#include <string>

int main() {
    std::string name;
    std::cout << "Enter your name: ";
    std::cin >> name;
    std::cout << "Hello world from " << name << std::endl;
    return 0;
}
```

### 3. Коммит и пуш ветки

```bash
$ git commit -am "remove using namespace std, add std::prefix"
$ git push -u origin patch1
```

### 4. Проверка доступности ветки

Ветка `patch1` доступна в удалённом репозитории на GitHub.

### 5. Создание pull-request `patch1 -> master`

PR создан через интерфейс GitHub.

### 6. Добавление комментариев в коде

```bash
$ nano hello_world.cpp
$ cat hello_world.cpp
```

```cpp
#include <iostream>
#include <string>

int main() {
    std::string name; // name of the user will be stored here
    std::cout << "Enter your name: "; // prompt the user to enter their name
    std::cin >> name; // read the name
    std::cout << "Hello world from " << name << std::endl; // print greetings
    return 0; // end program
}
```

### 7. Коммит и пуш

```bash
$ git commit -am "add comments to hello_world.cpp"
$ git push
```

### 8. Проверка PR

Новые изменения появились в созданном pull-request.

### 9. Слияние PR и удаление ветки

PR `patch1 -> master` слит через интерфейс GitHub. Ветка `patch1` удалена в удалённом репозитории.

### 10. Локальное обновление

```bash
$ git checkout master
$ git pull
```

### 11. Просмотр истории

```bash
$ git log --oneline
```

### 12. Удаление локальной ветки `patch1`

```bash
$ git branch -d patch1
```

---

## Part III

### 1. Создание локальной ветки `patch2`

```bash
$ git checkout -b patch2
```

### 2. Изменение code style через `clang-format`

```bash
$ clang-format -style=Mozilla -i hello_world.cpp
```

### 3. Коммит, пуш и создание PR

```bash
$ git commit -am "apply clang-format with Mozilla style"
$ git push -u origin patch2
```

PR `patch2 -> master` создан через интерфейс GitHub.

### 4. Изменение комментариев в ветке `master`

В ветке `master` на GitHub изменены комментарии (переведены на русский язык, расставлены знаки препинания).

### 5. Появление конфликтов

В PR `patch2 -> master` появились конфликты.

### 6. Разрешение конфликтов через `rebase`

```bash
$ git checkout patch2
$ git fetch origin
$ git rebase origin/master
```

Конфликты в файле `hello_world.cpp` разрешены вручную.

```bash
$ git add hello_world.cpp
$ git rebase --continue
```

### 7. Force push в ветку `patch2`

```bash
$ git push --force origin patch2
```

### 8. Проверка PR

Конфликты в PR исчезли.

### 9. Слияние PR `patch2 -> master`

PR слит через интерфейс GitHub.

```bash
$ git checkout master
$ git pull
```

---

## Вывод

**Все части лабораторной работы выполнены успешно!**
