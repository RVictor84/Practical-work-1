# Шпаргалка по работе с Git

Git - это система контроля версий: он позволяет хранить, изменять и<br>
анализировать историю проекта.

## Команды навигации в командной строке.

1. **pwd**(от англ. print working directory — «показать рабочую папку») - выводит путь<br>
к текущей директории
2. **cd~**(от англ. change directory — «сменить директорию»)  - команда перехода в домашнюю<br>
директорию.
3. **cd** - меняет текущую рабочую директорию на ту, которая указана в качестве параметра: cd имя_папки.
4. **cd ..** - переход на уровень выше по иерархии.
5. **cd .** - переход в текущую директорию.
6. Также cd позволяет перемещаться сразу через несколько директорий. Для этого нужно разделить<br>
их названия знаком /.
7. **ls**(от англ. list directory contents — «отобразить содержимое директории») - вывести содержимое<br>
директории. Т.е. отобразить названия всех файлов и папок находящихся в ней.
8. **ls -a** - выводит расширенный список. В него входят и скрытые файлы и папки.
9. ls может работать с символом домашней директории (~) и предыдущей директории (..).<br>
Например, ls ~ выведет содержимое домашней директории вне зависимости от того, что показывает pwd.<br>
А ls .. покажет содержимое родительской директории.

## Операции с файлами и папками (создание, копирование, перемещение).

### Создание файлов и директорий.

1. **touch**(англ. «коснуться») - создает файл. В качестве параметра надо указать имя файла.<br>
```bash
$ touch my-new-file.txt # создали файл my-new-file.txt
```
Хорошей практикой при создании файла считается указывать его расширение (в примере — .txt).<br>
Это позволит операционной системе выбрать подходящую программу, чтобы открыть файл.<br> 
2. **mkdir**(от англ. make directory — «создать директорию») - создает директорию.
```bash
$ mkdir new-dir # создали директорию new-dir
```
Можно создать целую структуру директорий одной командой с помощью флага -p.
```bash
$ mkdir -p dir1/dir-inside/dir-deeper-inside
# создали папку dir-deeper-inside в папке dir-inside, которая находится в папке dir1
```
По умолчанию touch и mkdir создают файлы и папки в текущей рабочей директории. Например, если вы<br>
находитесь в директории abs, команда touch file.txt создаст файл именно там: abs/file.txt.

### Копирование файлов - cp.