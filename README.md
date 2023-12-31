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
Для копирования файлов через терминал существует команда **cp** (от англ. copy — «копировать»).<br>
В простом виде cp принимает два параметра: что копируем и куда копируем.
```bash
$ cp что_копируем куда_копируем

$ cp index.html src/
# скопировали index.html в папку src
```
Но можно указать сразу несколько файлов.
```bash
$ cp что_копируем что_копируем что_копируем куда_копируем

$ cp index.html style.css script.js src/
# скопировали три файла (index.html, style.css и script.js) в папку src
```
### Перемещение файлов и папок - mv.
Для перемещения файлов используется команда **mv**(от англ. move — «переместить»).<br>
Синтаксис команды mv аналогичен синтаксису cp. После имени команды указывают список файлов<br>
и папок, которые нужно переместить, а затем — папку, в которую нужно выполнить перемещение.
```bash
$ mv table.csv ./very-important-files
# сначала указываем имя файла, который хотим переместить, потом путь — куда перемещаем 

$ cd very-important-files
$ ls
table.csv 
# перешли в папку very-important-files и проверили, что всё сработало
``` 
## Операции с файлами и папками (чтение и удаление).
### Чтение файлов.
**cat**(от англ. concatenate and print — «объединить и распечатать») - в консоль нужно ввести cat<br>
с именем файла. Команда распечатает то что содержится в нем.
```bash
$ cat myfile.txt # распечатали содержимое файла myfile.txt
file-content-1
file-content-2
```
Команда cat работает только с текстовыми файлами. Вывести этой командой файл другого типа<br>
(например, изображение) не получится.

### Удаление файлов и папок — rm, rmdir, rm -r.
Чтобы удалить файл, нужно напечатать команду **rm** и передать ей имя файла.
~~~bash
$ rm example.txt # удалили файл example.txt из текущей папки
~~~
Удалить папку можно командой **rmdir** (от англ. remove directory — «удалить директорию»),<br>
передав в качестве аргумента имя папки.
~~~bash
$ rmdir images # команда удалит папку images из текущей директории, 
               # если папка images пуста
~~~
Если папку нужно удалить со всем содержимым то используется команда **rm -r**(-r — от англ. recursive,<br>
«рекурсивный») рекурсивно удаляя файлы и папки.

## Эффективная работа с командной строкой.
### Выполнение сразу нескольких команд.
Команды можно указывать не по одной, а сразу списком. Для этого их нужно разделить двумя амперсандами (&&).
~~~bash
$ mkdir second-project && cd second-project && touch index.html style.css
# создаём папку second-project,
# переходим в папку second-project
# и создаём в ней два файла: index.html и style.css
~~~
### Вызов команд из буфера.
В буфере хранятся все команды, которые вызывались до этого. По их списку можно перемещаться.

Чтобы обратиться к последней введённой команде, нажмите на клавиатуре стрелку вверх (↑).

### Автозаполнение.
Если нужно найти какую-нибудь команду, достаточно вспомнить, с каких букв она начинается.<br>
Можно набрать их в командной строке и дважды нажать клавишу Tab. Терминал покажет список всех<br>
команд, которые начинаются с этих символов.

Tab автоматически дописывает не только команды, но и пути.
~~~bash
$ cd /Users/ # перешли в папку Users

$ cd U[Tab] # ввели первую букву имени пользователя и нажали Tab
# имя папки Username подставится автоматически

$ pwd # теперь проверим, где мы сейчас находимся 
/Users/Username # мы в папке Username!
~~~
## Настройка Git
### Работа с файлом настройки .gitconfig.
Чтобы было понятно, кто и какие изменения вносил, нужно представиться и указать имя пользователя<br>
и адрес электронной почты.

Сделать это можно при помощи следующих команд:
~~~bash
$ git config --global user.name "User Namovich" 
# имя или ник нужно написать латиницей и в кавычках

$ git config --global user.email username@yandex.ru
# здесь нужно указать свой настоящий email
~~~
Все глобальные настройки Git хранит в файле .gitconfig в домашней директории. Команда запишет в этот  
файл указанные имя и почту. 

Чтобы просмотреть содержимое файла .gitconfig можно воспользоваться следующей командой:
~~~bash
$ cat ~/.gitconfig
~~~
Другой способ проверки — вывести содержимое файла конфигурации Git той же командой git config  
с флагом --list (англ. «список»).
~~~bash
$ git config --list
~~~
В ответ командная строка покажет текущие значения настроек.
~~~bash
user.name=Username
user.email=username@yandex.ru
~~~
## Инициализируем репозиторий.
### Сделать папку репозиторием — git init.
Чтобы Git начал отслеживать изменения в проекте, папку с файлами этого проекта нужно  
сделать Git-репозиторием (от англ. repository — «хранилище»). Для этого следует переместиться  
в неё и ввести команду git init (от англ. initialize — «инициализировать»).

Например, создайте папку first-project и сделайте её Git-репозиторием: перейдите в неё с  
помощью команды cd и выполните git init.
~~~bash
$ cd ~/dev/first-project # перешли в нужную папку

$ git init # создали репозиторий
~~~
### «Разгитить» папку, если что-то пошло не так, — rm -rf .git
Если вы случайно сделали Git-репозиторием не ту папку, её можно «разгитить». Для этого нужно  
удалить скрытую подпапку .git.
~~~bash
$ cd <папка с репозиторием> # перешли в папку

$ rm -rf .git # удалили подпапку .git
~~~
Разберём подробнее, что такое -rf:
* ключ -r (от англ. recursive — «рекурсивно») позволяет удалять папки вместе с их содержимым;
* ключ -f (от англ. force — «заставить») избавит вас от вопросов вроде «Вы точно хотите удалить этот файл?  
А этот? И этот тоже?».

Будьте осторожны: в подпапке .git хранится история изменений. Если удалить .git, то вся история проекта будет  
стёрта без возможности восстановления — останется только последняя версия файлов.
### Проверить состояние репозитория — git status.
Команду git status (от англ. status — «статус», «состояние») — показывает текущее состояние репозитория.

Команда git status выведет:
- название текущей ветки: On branch master или On branch main;
- сообщение о том, что в репозитории ещё нет коммитов: No commits yet;
- сообщение, которое говорит: «чтобы что-нибудь закоммитить (то есть зафиксировать), нужно сначала это  
создать» — nothing to commit (create/copy files and use "git add" to track).
## Добавляем файлы в репозиторий.
### Подготовить файлы к сохранению — git add.
Добавим в репозиторий два файла. Например, файл todo.txt, в котором будет список дел, и readme.txt для  
информации о проекте.

Запустите git status, чтобы посмотреть, что изменилось.
~~~bash
$ git status # проверили статус
~~~
Git сообщит, что в папке first-project есть untracked files (от англ. track — «следить»,  
untracked — «неотслеженный», «неотслеживаемый») — ещё не отслеживаемые файлы readme.txt и todo.txt.  
Состояние untracked значит, что Git ещё не хранит информацию о версиях файла и не может отследить, как он изменялся.

Чтобы отслеживать состояние обоих файлов, можем использовать команду git add --all  
(от англ. add — «добавить» + от англ. all — «всё»). Ключ, или флаг, --all позволяет подготовить к сохранению  
все файлы в репозитории.
~~~bash
$ git add --all # подготовили к сохранению все файлы в репозитории
$ git status # проверили статус
~~~
Добавлять файлы можно и по одному, без ключа --all.
~~~bash
$ git add todo.txt
$ git add readme.txt
$ git status
~~~
Также можно добавить текущую папку целиком — в этом случае все файлы в ней тоже будут добавлены.  
Обратиться к текущей папке в Bash позволяет точка (.).
~~~bash
$ git add . # добавить всю текущую папку
$ git status
~~~
Команда git add только запоминает текущее содержимое (контент) файла, но не сохраняет его.
## Первый коммит.
Коммит — это одна из основных сущностей в Git (и в других системах контроля версий). Коммит гарантирует,  
что изменения будут сохранены в истории и при необходимости к ним можно будет «откатиться».
### Выполнить коммит — git commit.
Сделать коммит можно командой git commit c ключом -m (от англ. message — «сообщение»),  
который присваивает коммиту сообщение.
~~~bash
$ git commit -m ‘Мой первый коммит!’
~~~
Команда git commit выведет информацию о коммите:

* [master (root-commit) baa3b6e] значит:
коммит был в ветке master;
* root-commit — это самый первый, или «корневой» (англ. root), коммит в ветке, у следующих коммитов  
такой надписи не будет;
* baa3b6e — сокращённый идентификатор коммита (подробнее об этом мы ещё расскажем).
* 2 files changed, 1 insertion(+) значит:  
изменились два файла (readme.txt и todo.txt);
* одна строка была добавлена (1. Пройти пару уроков по Git.).
* Строки вида create mode 100644 readme.txt — это более подробная информация о новых (добавленных в Git) файлах.
* create (англ. «создать») говорит, что файл был создан. Если бы файл был удалён, на этом месте было  
бы слово delete (англ. «удалить»).
* mode 100644 сообщает, что это обычный файл. Также возможны варианты 100755 для исполняемых
файлов (например, что-нибудь.exe) и 120000 для файлов-ссылок в Linux. Файлы-ссылки не содержат  
данных сами по себе, а только ссылаются на другие файлы — как «ярлыки» в Windows.
## История коммитов.
### Просмотреть историю коммитов — git log.
Чтобы просмотреть историю коммитов, введите команду git log (от англ. log — «журнал [записей]»).

Обратите внимание, что по умолчанию git log выводит коммиты в обратном хронологическом  
порядке — последние коммиты оказываются первыми сверху.
## Синхронизируем локальный и удалённый репозитории.
### Отправить изменения на удалённый репозиторий — git push.
Вы уже прошли весь «цикл коммита»: подготовили файлы с помощью git add, закоммитили их  
с комментарием командой git commit -m. Осталось загрузить содержимое локального  
репозитория на GitHub. За это отвечает команда git push (от англ. push — «толкать»).

В первый раз эту команду нужно вызвать с флагом -u и параметрами origin  
(имя удалённого репозитория) и main или master (название текущей ветки).  
Флаг -u свяжет локальную ветку с одноимённой удалённой.
~~~bash
$ git push -u origin main # Если команда приведёт к ошибке, попробуйте 
                          # заменить main на master. 
~~~
При взаимодействии с удалёнными репозиториями Git выводит в консоль отладочную  
информацию: количество объектов (файлов), которые отправляются на сервер, информацию  
о прогрессе сжатия и записи и так далее.
## Хеш — идентификатор коммита.
### Что такое хеш. Хеширование коммитов.
**Хеширование** (от англ. hash, «рубить», «крошить», «мешанина») — это способ преобразовать  
набор данных и получить их «отпечаток» (англ. fingerprint).

Информация о коммите — это набор данных: когда был сделан коммит, содержимое файлов в  
репозитории на момент коммита и ссылка на предыдущий, или родительский (англ. parent), коммит.

Git хеширует (преобразует) информацию о коммите с помощью алгоритма SHA-1  
(от англ. Secure Hash Algorithm — «безопасный алгоритм хеширования») и получает для каждого  
коммита свой уникальный хеш — результат хеширования.

Обычно хеш - это короткая(40 символов в случае SHA-1) строка, которая состоит  
из цифр 0-9 и латинских букв A-F (неважно, заглавных или строчных). Она обладает  
следующими важными свойствами:
* если хеш получить дважды для одного и того же набора входных данных, то результат  
будет гарантированно одинаковый;
* если хоть что-то в исходных данных поменяется (хотя бы один символ), то хеш тоже  
изменится (причем сильно).
### Хеш — основной идентификатор коммита.
Git хранит таблицу соответствий хеш → информация о коммите. Если вы знаете хеш,  
вы можете узнать всё остальное: автора и дату коммита и содержимое закоммиченных файлов.
## Исследуем лог.
### Сокращённый лог — git log --oneline.
Получить сокращённый лог можно с помощью команды git log с флагом --oneline (англ. «одной строкой»).  
В терминале появятся только первые несколько символов хеша каждого коммита и их комментарии.

Сокращённый лог полезен, если в репозитории уже много коммитов — например, сотни или тысячи.  
В этом случае можно быстро найти нужный по описанию.
## HEAD — всему голова.
### Файл HEAD.
Файл HEAD (англ. «голова», «головной») — один из служебных файлов папки .git. Он указывает  
на коммит, который сделан последним (то есть на самый новый).

В этом можно убедиться с помощью терминала.
~~~bash
$ pwd # посмотрели, где мы
/Users/user/dev/first-project

$ cd .git/
$ ls # посмотрели, какие есть файлы
COMMIT_EDITMSG  ORIG_HEAD  description  index  logs/     refs/
HEAD            config     hooks/       info/  objects/

$ cat HEAD # команда cat показывает содержимое файла
ref: refs/heads/master # в файле вот такая ссылка
~~~
Внутри HEAD — ссылка на служебный файл: refs/heads/master  
(или refs/heads/main в зависимости от названия ветки). Если заглянуть в этот файл,  
можно увидеть хеш последнего коммита.
~~~bash
$ cat refs/heads/master # взяли ссылку из файла HEAD
# внутри хеш
e007f5035f113f9abca78fe2149c593959da5eb7

$ git log 
# сверяем с хешем последнего коммита
commit e007f5035f113f9abca78fe2149c593959da5eb7
Author: John Doe <johndoe@example.com>
Date:   Tue Mar 28 00:26:53 2023 +0300

    Добавить амбиций в список дел

... # другие коммиты
~~~
Когда вы делаете коммит, Git обновляет refs/heads/master — записывает в него хеш  
последнего коммита. Получается, что HEAD тоже обновляется, так как ссылается на refs/heads/master.

Если нужно передать последний коммит, то вместо его хеша можно просто написать  
слово HEAD — Git поймёт, что вы имели в виду последний коммит.
## Статусы файлов.
### Статусы untracked/tracked, staged и modified.
Одна из ключевых задач Git — отслеживать изменения файлов в репозитории.  
Для этого каждый файл помечается каким-либо статусом. Рассмотрим основные.
* untracked (англ. «неотслеживаемый»)  
Мы говорили, что новые файлы в Git-репозитории помечаются как untracked, то есть неотслеживаемые.  
Git «видит», что такой файл существует, но не следит за изменениями в нём. У untracked-файла  
нет предыдущих версий, зафиксированных в коммитах или через команду git add.

* staged (англ. «подготовленный»).
После выполнения команды git add файл попадает в staging area (от англ.
stage — «сцена», «этап [процесса]» и area — «область»), то есть в список файлов, которые  
войдут в коммит.

* tracked (англ. «отслеживаемый»).
Состояние tracked — это противоположность untracked. Оно довольно
широкое по смыслу: в него попадают файлы, которые уже были зафиксированы с помощью git commit,  
а также файлы, которые были добавлены в staging area командой git add. То есть все файлы,  
в которых Git так или иначе отслеживает изменения.

* modified (англ. «изменённый»).
Состояние modified означает, что Git сравнил содержимое файла  
с последней сохранённой версией и нашёл отличия. Например, файл был закоммичен  
и после этого изменён.

~~~mermaid
graph LR;
  untracked -- "команда: git add <имя_файла>" --> staged
  staged -- "команда: git commit -m "комментарий"" --> tracked
  tracked -- "файл изменен" --> modified
~~~


### Про staged и modified.
Команда git add добавляет в staging area только текущее содержимое файла. Если вы, например,  
сделаете git add file.txt, а затем измените file.txt, то новое содержимое файла не будет  
находиться в staging.

Git сообщит об этом с помощью статуса modified: файл изменён относительно той версии,  
которая уже в staging. Чтобы добавить в staging последнюю версию, нужно выполнить  
git add file.txt ещё раз.
## Как читать git status.
### Какие состояния показывает git status.
Большинство файлов в типичном проекте будут находиться в состоянии tracked  
(то есть закоммичены и не изменены после коммита). Вы не увидите это состояние  
в выводе команды git status — иначе она бы каждый раз выводила список вообще  
всех файлов проекта.

В итоге git status показывает только следующие состояния файлов:
* staged (Changes to be committed в выводе git status);
* modified (Changes not staged for commit);
* untracked (Untracked files).
## Оформление сообщений к коммитам.
### Зачем вообще писать сообщения.
У каждого коммита в Git есть сообщение — то, что передаётся после  
параметра -m. Например: git commit -m "Добавить урок про оформление сообщений коммитов".

Сообщения коммитов можно сравнить с надписями на коробках в кладовке.  
Если надписей нет, то нужную коробку будет сложно найти. А если надписи есть,  
то нужная найдётся сразу.

Есть общие рекомендации по тому, как правильно составить сообщение. Оно должно быть:  
* относительно коротким, чтобы его было легко прочитать;
* информативным.
### Стили оформления.
Без единообразия коммитов нет и эффективной работы в Git. Это может показаться  
мелочью, но когда коммиты с сообщениями в разных стилях идут друг за другом,  
их может быть сложно читать.

Есть много подходов к оформлению сообщений коммитов, но мы расскажем  
о нескольких популярных. Их используют как отдельные команды, так и целые проекты.
#### Корпоративный.
Во многих компаниях применяется Jira — система для организации проектов и задач.  
У каждой задачи в Jira есть идентификатор из нескольких заглавных латинских  
букв и номера. Например, LGS-239 значит, что это 239-я задача в проекте LGS  
(сокращение от англ. logistics — «логистика»).

В корпоративном стиле в начале сообщения обычно указывают Jira-ID,  
а после — текст сообщения.
~~~bash
$ git commit -m "LGS-239: Дополнить список пасхалок новыми числами"
~~~
Требование о наличии Jira-ID обычно строгое: оно позволяет автоматически  
связывать коммиты с задачами и проектами.
#### Conventional Commits.
Стандарт Conventional Commits (англ. «соглашение о коммитах») отличается  
качественной документацией и подробной проработкой. Он подходит для репози-  
-ториев с исходным кодом программ.

Conventional Commits предлагает такой формат коммита: <type>: <сообщение>.  
Первая часть type — это тип изменений. Таких типов достаточно много.  
Вот два примера:
* feat (сокращение от англ. feature) — для новой функциональности;
* fix (от англ. «исправить», «устранить») — для исправленных ошибок.

Например, сообщение может быть таким.
~~~bash
git commit -m "feat: добавить подсчёт суммы заказов за неделю"
~~~
#### GitHub-стиль.
GitHub можно использовать не только для хранения файлов проекта,  
но и для ведения списка задач (англ. issue) этого проекта. Если коммит  
«закрывает» или «решает» какую-то задачу, то в его сообщении удобно  
указывать ссылку на неё. Для этого в любом месте сообщения нужно  
указать #<номер задачи>. Например, вот так.
~~~bash
$ git commit -m "Исправить #334, добавить график температуры"
~~~
В таком случае GitHub свяжет коммит и задачу.

Правильно описывать коммиты — искусство, к которому стоит приобщиться  
как можно раньше. Хорошо, когда:
* сообщение коммита легко читается;
* оно информативное;
* все сообщения оформлены в одном стиле.


