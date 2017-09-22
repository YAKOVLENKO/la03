## Laboratory work III

Данная лабораторная работа посвещена изучению систем контроля версий на примере **Git**.

```bash
$ open https://git-scm.com
```

## Tasks

- [X] 1. Создать публичный репозиторий с названием **lab03** и с лиценцией **MIT**
- [X] 2. Ознакомиться со ссылками учебного материала
- [X] 3. Выполнить инструкцию учебного материала
- [X] 4. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial
Присваивание переменным GITHUB_USERNAME и GITHUB_EMAIL значения, после настройка редактор
```ShellSession
$ export GITHUB_USERNAME=YAKOVLENKO # Присваиваем GITHUB_USERNAME значение YAKOVLENKO
$ export GITHUB_EMAIL=<адрес_почтового_ящика> # Присваиваем GITHUB_EMAIL значение, равное почте аккаунта
$ alias edit=nano # Настраиваем редактор nano
```
Создаем папку lab03, работаем с ней (созданий файлов), работаем с репозиторием
```ShellSession
$ mkdir lab03 && cd lab03 # Создаем папку lab03 и переходим в нее
$ git init # Инициализируем
$ git config --global user.name ${GITHUB_USERNAME} # Включаем GITHUB_USERNAME в файл .gitconfig
$ git config --global user.email ${GITHUB_EMAIL} # Включаем GITHUB_EMAIL в файл .gitconfig
$ git config -e --global # Проверяем правильность данных
$ git remote add origin https://github.com/${GITHUB_USERNAME}/la03 # Добавляем репозиторий
$ git pull origin master # Обновляем
$ touch README.md # Создаем файл
$ git status # Узнаем статус проекта
$ git add README.md # Добавляем файл
$ git commit -m"added README.md" # Коммитим файл
$ git push origin master # Добавляем в репозиторий
```

Добавляем на сервисе **GitHub** в репозитории **la03** файл **.gitignore**
со следующим содержимым:

```ShellSession
*build*/
*install*/
*.swp
```
Проверка
```ShellSession
$ git pull origin master # Обновляем
$ git log # Узнаем, что происходило с репозиторием
```
Создание папок sources, include, examples; добавление в них файлов
```ShellSession
$ mkdir sources # Создание папки sources
$ mkdir include # Создание папки include
$ mkdir examples # Создание папки examples
$ cat > sources/print.cpp <<EOF # Создание файла print.cpp в папке sources, его заполнение
#include <print.hpp>

void print(const std::string& text, std::ostream& out) {
  out << text;
}

void print(const std::string& text, std::ofstream& out) {
  out << text;
}
EOF
```

```ShellSession
$ cat > include/print.hpp <<EOF # Создание файла print.hpp в папке include и его заполнение
#include <string>
#include <fstream>
#include <iostream>

void print(const std::string& text, std::ostream& out = std::cout);
void print(const std::string& text, std::ofstream& out);
EOF
```

```ShellSession
$ cat > examples/example1.cpp <<EOF # Создание файла example1.cpp в папке examples и его заполнение
#include <print.hpp>

int main(int argc, char** argv) {
  print("hello");
}
EOF
```

```ShellSession
$ cat > examples/example2.cpp <<EOF # Создание файла example2.cpp в папке examples и его заполнение
#include <fstream>
#include <print.hpp>

int main(int argc, char** argv) {
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
EOF
```
Редактирование
```ShellSession
$ edit README.md # Редактируем README.md
```
Загрузка созданного в репозиторий
```ShellSession
$ git status # Узнаем статус проекта
$ git add . # Добавляем все файлы 
$ git commit -m"added sources" # Коммитим файлы
$ git push origin master # Добавляем в репозиторий
```

## Report

```ShellSession
$ cd ~/workspace/labs/ # Переходим в папку labs
$ export LAB_NUMBER=02 # Присваиваем LAB_NUMBER значение 03
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER} # Получаем информацию с github
$ mkdir reports/lab${LAB_NUMBER} # Создаем новую папку
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md # Переименовываем README.md и копируем в созданную папку
$ cd reports/lab${LAB_NUMBER} # Входим в папку
$ edit REPORT.md # Редактируеме файл
$ gistup -m "lab${LAB_NUMBER}" # Коммитим
```

## Links

- [GitHub](https://github.com)
- [Bitbucket](https://bitbucket.org)
- [Gitlab](https://about.gitlab.com)
- [LearnGitBranching](http://learngitbranching.js.org/)

```
Copyright (c) 2017 Братья Вершинины
```
