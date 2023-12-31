# Шпаргалка GIT

## Выделение текста

Вы можете выделять текст в markdown с помощью символов `_` или `*`. Например:

Пример _курсива_ и **жирного** текста.

## Заголовки

Заголовки можно создавать с помощью символа `#`. Чем больше `#`, тем меньше заголовок. Например:

# Заголовок первого уровня
## Заголовок второго уровня
### Заголовок третьего уровня

## Выделение кода

Чтобы выделить текст как код, поместите его в тройные кавычки ` ``` `. 

```
mkdir my_project
cd my_project
git init
```
### Изменение коммита:
Оно возможно с использованием команды `git commit --amend`

`git commit --amend -m` в таком формате команда позволит изменить название коммита (_его описание_)

При добавлении ключа `--no-edit` мы указываем, что не меняем описание, а меняем лишь **содержимое**

Этот блок в README был добавлен, кстати, с помощью _`git commit --amend --no-edit`_

### Откат изменений:

Удалить файл из списка `add` можно при помощи команды ` git restore --staged <file>`

Где `<file>` - то, что надо удалить

### Откат коммита:

Откатить коммит (_удалить его_) можно с помощью комманды `git reset --hard <commit hash>`

Состояние проекта вернется на указанный в <> коммит 

### Откат несохраненных изменений:

Чтобы откатить изменения, не попавшие ни в один список, воспользуйся командой<br>`git restore <file>`

Где `<file>` - то, что надо удалить

### Просмотр изменений:

Команда `git diff` сравнит последнюю закоммиченную версию файла с текущей (изменённой) версией.

Чтобы сравнить последнюю закоммиченную версию файла со staged, нужно использовать флаг _--staged_: `git diff --staged`

Чтобы сравнить два коммита, передай команде `git diff` хеши обоих коммитов. Состояние файлов на момент первого переданного коммита будет сравниваться с состоянием файлов на момент второго. Вместо хеша самого нового коммита можно использовать `HEAD`: `git diff 1c29af6 HEAD`.

### Git Ignore:

Символ звёздочки (`*`) соответствует любой строке, включая пустую.

Вопросительный знак `?` соответствует одному любому символу.

Квадратные скобки `[…]`, как и вопросительный знак, соответствуют одному символу. При этом символ не любой, а только из списка, который указан в скобках.

Косая черта, или слеш (`/`), указывает на каталоги. Если шаблон в .gitignore начинается со слеша, то Git проигнорирует файлы или каталоги только в корневой директории.

Функция парных звёздочек (`**`) похожа на функцию одинарной (`*`). Отличие в том, как они работают с вложенными папками. Двойная звёздочка может соответствовать любому количеству таких папок (в том числе нулю). Одинарная может соответствовать только одной.

Любое правило в файле .gitignore можно инвертировать с помощью восклицательного знака (`!`).

# Шпора из урока

## Инициализация репозитория

git init (от англ. initialize, «инициализировать») — инициализируй репозиторий.

### Синхронизация локального и удалённого репозиториев

git remote add origin https://github.com/YandexPracticum/first-project.git (от англ. remote, «удалённый» + add, «добавить») — привяжи локальный репозиторий к удалённому с URL https://github.com/YandexPracticum/first-project.git;

git remote -v (от англ. verbose, «подробный») — проверь, что репозитории действительно связались;

git push -u origin main (от англ. push, «толкать») — в первый раз загрузи все коммиты из локального репозитория в удалённый с названием origin.

💡 _Ваша ветка может называться master, а не main. Подправьте команду, если это необходимо._

git push (от англ. push, «толкать») — загрузи коммиты в удалённый репозиторий после того, как он был привязан с помощью флага -u.

### Подготовка файла к коммиту

git add todo.txt (от англ. add, «добавить») — подготовь файл todo.txt к коммиту;

git add --all (от англ. add, «добавить» + all, «всё») — подготовь к коммиту сразу все файлы, в которых были изменения, и все новые файлы;

git add . — подготовь к коммиту текущую папку и все файлы в ней.

### Создание и публикация коммита

git commit -m "Комментарий к коммиту." (от англ. commit, «совершать», фиксировать» + message, «сообщение») — сделай коммит и оставь комментарий, чтобы было проще понять, какие изменения сделаны;

git push (от англ. push, «толкать») — добавь изменения в удалённый репозиторий.

### Просмотр информации о коммитах

git log (от англ. log, «журнал [записей]») — выведи подробную историю коммитов;

git log --oneline (от англ. log, «журнал [записей]» + oneline, «одной строкой») — покажи краткую информацию о коммитах: сокращённый хеш и сообщение.

### Просмотр состояния файлов

git status (от англ. status, «статус», «состояние») — покажи текущее состояние репозитория.

### Добавление изменений в последний коммит

git commit --amend --no-edit (от англ. amend, «исправить») — добавь изменения к последнему коммиту и оставь сообщение прежним;

git commit --amend -m "Новое сообщение" — измени сообщение к последнему коммиту на Новое сообщение.

💡 _Выйти из редактора Vim: нажать Esc, ввести :qa!, нажать Enter._

### «Откат» файлов и коммитов

git restore --staged hello.txt (от англ. restore, «восстановить») — переведи файл hello.txt из состояния staged обратно в untracked или modified;

git restore hello.txt — верни файл hello.txt к последней версии, которая была сохранена через git commit или git add;

git reset --hard b576d89 (от англ. reset, «сброс», «обнуление» + hard, «суровый») — удали все незакоммиченные изменения из staging и «рабочей зоны» вплоть до указанного коммита.

### Просмотр изменений

git diff (от англ. difference, «отличие», «разница») — покажи изменения в «рабочей зоне», то есть в modified-файлах;

git diff a9928ab 11bada1 — выведи разницу между двумя коммитами;

git diff --staged — покажи изменения, которые добавлены в staged-файлах.


**_Это лишь некоторые функции Goddamn Idiotic Truck of shit._**