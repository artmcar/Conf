# Практическое задание №4. Системы контроля версий

## Задача 1

На сайте https://onlywei.github.io/explain-git-with-d3 или http://git-school.github.io/visualizing-git/ (цвета могут отличаться, есть команды undo/redo) с помощью команд эмулятора git получить следующее состояние проекта (сливаем master с first, перебазируем second на master): см. картинку ниже. Прислать свою картинку.


```
git commit
git tag in
git branch first
git branch second
git commit
git commit
git checkout first
git commit
git commit
git checkout master
git merge first
git checkout second
git commit
git commit
git rebase master
git checkout master
git merge second
git checkout in

```
![41](https://github.com/artmcar/Conf/blob/main/im/z1.png?raw=true)


## Задача 2

Создать локальный git-репозиторий. Задать свои имя и почту (далее – coder1). Разместить файл prog.py с какими-нибудь данными. Прислать в текстовом виде диалог с git.

![42](https://github.com/artmcar/Conf/blob/main/im/z2.png?raw=true)


## Задача 3

Создать рядом с локальным репозиторием bare-репозиторий с именем server. Загрузить туда содержимое локального репозитория. Команда git remote -v должна выдать информацию о server! Синхронизировать coder1 с server.

Клонировать репозиторий server в отдельной папке. Задать для работы с ним произвольные данные пользователя и почты (далее – coder2). Добавить файл readme.md с описанием программы. Обновить сервер.

Coder1 получает актуальные данные с сервера. Добавляет в readme в раздел об авторах свою информацию и обновляет сервер.

Coder2 добавляет в readme в раздел об авторах свою информацию и решает вопрос с конфликтами.

Прислать список набранных команд и содержимое git log.

```
git init --bare server.git
git remote add server ../server.git/
git remote -v
git push server master
git clone server.git coder2
echo "Test" >> readme.md
git add readme.md
git commit -m "test info"
git push server master
echo "Test2" >> readme.md
git add readme.md
git config user.name "Artur"
git config user.email "makaryan.a.a@edu.mirea.ru"
git commit -m "test2 info"
git pull --no-rebase origin master
git add readme.md
git commit -m "Final"
git push origin master
git log --graph --all
```
![43](https://github.com/artmcar/Conf/blob/main/im/z3.png?raw=true)

## Задача 4

Написать программу на Питоне (или другом ЯП), которая выводит список содержимого всех объектов репозитория. Воспользоваться командой "git cat-file -p". Идеальное решение – не использовать иных сторонних команд и библиотек для работы с git.

![44](https://github.com/artmcar/Conf/blob/main/im/z4.png?raw=true)
