# Лабораторная работа №2: Изучение систем контроля версий на примере Git

## Выполнила: Алексеева Ольга

---

## Цель работы

Изучить основные возможности системы контроля версий Git: создание репозитория, работа с файлами, ветвление, разрешение конфликтов, оформление отчётов.

---

## Часть 1. Базовые настройки и структура репозитория (Tutorial)

### 1.1. Настройка окружения

```bash
export GITHUB_USERNAME=OlgaIAK
export GITHUB_EMAIL=ovalekseeva07@mail.ru
mkdir -p ~/OlgaIAK/workspace/projects/lab02
cd ~/OlgaIAK/workspace/projects/lab02
git init
git remote add origin https://github.com/OlgaIAK/lab02.git
cat > .gitignore <<EOF
*build*/
*install*/
*.swp
.idea/
EOF
mkdir sources include examples
#include <print.hpp>

void print(const std::string& text, std::ostream& out)
{
  out << text;
}

void print(const std::string& text, std::ofstream& out)
{
  out << text;
}
#include <fstream>
#include <iostream>
#include <string>

void print(const std::string& text, std::ofstream& out);
void print(const std::string& text, std::ostream& out = std::cout);
#include <print.hpp>

int main(int argc, char** argv)
{
  print("hello");
}
#include <print.hpp>
#include <fstream>

int main(int argc, char** argv)
{
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}git add .
git commit -m "added sources and basic structure"
git push -u origin master
#include <iostream>
using namespace std;

int main()
{
    cout << "Hello world!" << endl;
    return 0;
}
git add hello_world.cpp
git commit -m "added hello_world.cpp with using namespace std"
git push
#include <iostream>
#include <string>

int main()
{
    std::string name;
    std::cout << "Enter your name: ";
    std::cin >> name;
    std::cout << "Hello world from @" << name << std::endl;
    return 0;
}
git commit -a -m "improved: request user name, removed using namespace std"
git push
git log --oneline
abc1234 improved: request user name, removed using namespace std
def5678 added hello_world.cpp with using namespace std
git checkout -b patch1
#include <iostream>
#include <string>

int main()
{
    std::string name;
    // Request user name from standard input stream
    std::cout << "Enter your name: ";
    std::cin >> name;
    // Print greeting to standard output stream
    std::cout << "Hello world from @" << name << std::endl;
    return 0;
}
git commit -a -m "added comments to hello_world.cpp"
git push -u origin patch1
git checkout master
git pull
git branch -d patch1
git log --oneline
git checkout -b patch2
clang-format -style=Mozilla -i hello_world.cpp
git commit -a -m "applied clang-format with Mozilla style"
git push -u origin patch2
git checkout patch2
git fetch origin
git rebase origin/master
git add hello_world.cpp
git rebase --continue
git push --force origin patch2
