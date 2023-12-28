# Основные команды git

## Полезные ссылки:
- [Статья про параметр core.autocrlf](https://habr.com/ru/articles/703072/)
- [Разница между switch и checkout](https://stackoverflow.com/questions/57265785/whats-the-difference-between-git-switch-and-git-checkout-branch)


---

## help - получение справки по командам Git.
Для получения подробной информации по конкретной команде, используйте следующий синтаксис:
```shell
git <command> --help
```
Например, чтобы получить справку по команде `commit`, выполните:
```shell
git commit --help
```
Мануал откроется в вашем веб-браузере по умолчанию, предоставляя подробное описание команды, ее параметров и использования.


## init - инициализация репозитория.
Используется для создания нового Git-репозитория или инициализации существующей папки как репозитория. Если выполнить команду без аргументов, Git создаст репозиторий в текущей рабочей папке. Просто введите:
```shell
git init
```
Если вы хотите задать имя для репозитория, используйте следующий формат:
```shell
git init <имя-репозитория>
```
Например:
```shell
git init basic-git
```
Где `basic-git` - это имя вашего репозитория. Это полезно, если вы хотите явно указать имя репозитория вместо использования имени текущей папки.


## clone - клонирование репозитория.
Используется для создания локальной копии удаленного Git-репозитория. Для клонирования репозитория введите:
```shell
git clone <remote-url>
```
Пример:
```shell
git clone https://github.com/LpilinAlexandr/basic-git.git
```
Эта команда создаст локальную копию удаленного репозитория в новой папке, имя которой будет таким же, как у удаленного репозитория (в данном случае, basic-git). Если вы хотите, чтобы локальная папка имела другое имя, просто добавьте желаемое имя после URL:
```shell
git clone <удаленный-URL> <желаемое-имя-папки>
```


## config - настройки.

- **Список настроек:**
  - `git config -l` - выводит список текущих настроек.
  - `git config --global -l` - список глобальных настроек.
  - `git config --local -l` - список локальных настроек репозитория.

- **Установка глобальных параметров пользователя:**
  - `git config --global user.name "Name"` - устанавливает имя пользователя в глобальной области.
  - `git config --global user.email "email@example.com"` - устанавливает email пользователя в глобальной области.

- **Удаление переменной из настроек:**
  - `git config --unset <переменная>` - удаляет переменную из настроек.

- **Создание алиасов:**
  - `git config alias.<ваш-алиас> <команда>` - создает алиас для команды.
  - Пример: `git config alias.st status` - теперь можно использовать `git st` вместо `git status`.

- **Настройка окончаний строк:**
  - `git config --global core.autocrlf <input|false|true>` - управляет обработкой окончаний строк.

Эти команды позволяют управлять настройками Git в различных контекстах, что полезно для настройки работы с репозиториями и предоставляет гибкость в использовании Git.


## status - статус файлов и директорий в репозитории.
Используется для отображения состояния файлов в вашем рабочем каталоге и индексе (staging area). Для получения статуса выполните:
```shell
git status
```
- `git status -s` - предоставляет статус в короткой форме, обеспечивая более компактный вывод.

Результат команды `git status` содержит информацию о:

- Файлах, которые были изменены.
- Неотслеживаемых файлах.
- Файлах, готовых к коммиту (в индексе).
- Текущей ветке и многое другое.

Эта команда полезна для отслеживания изменений в вашем проекте и предоставляет обзор состояния вашего рабочего каталога.


## log - логи репозитория.
- `git log` - отображает историю коммитов репозитория в порядке их создания.
  
- `git log <имя-ветки>` - просмотр истории коммитов для конкретной ветки.

- `git log --grep <шаблон>` - поиск коммитов, содержащих подходящую подстроку в сообщении коммита.

- `git log --invert-grep <шаблон>` - поиск коммитов, у которых отсутствует указанная подстрока в сообщении.

- `git log --oneline` - выводит каждый коммит в одной строке, предоставляя краткую информацию о коммите.

Эта команда полезна для отслеживания изменений в истории проекта, просмотра информации о коммитах и понимания того, как эволюционирует ваш репозиторий.


## add | restore | rm - управление файлами и директориями.
- `git add <путь>` - добавляет указанный файл или директорию в индекс (staging area) для будущего коммита.

- `git add .` - добавляет все измененные файлы и директории в текущей рабочей директории в индекс.

- `git restore --staged <путь>` - исключает из индекса изменения для указанного файла или директории, отменяя их добавление.

- `git restore <путь>` - отменяет изменения в указанном файле или директории, восстанавливая их к состоянию последнего коммита.

- `git rm <путь>` - удаляет файл или директорию из рабочей директории и добавляет изменение в индекс. Фактически, это сокращенная форма для удаления и добавления в индекс.

Эти команды позволяют эффективно управлять изменениями в вашем проекте и подготавливать их к будущим коммитам.


## remote - управление удаленными адресами.
Если репозиторий был инициализирован, но не клонирован, ему может не быть присвоен адрес удаленного репозитория, который указывает, куда отправлять код при выполнении команды `git push` и откуда извлекать код при выполнении команды `git pull`. Для добавления удаленного адреса в локальный репозиторий используйте:
```shell
git remote add origin <remote-url>
```
Пример полной команды:
```shell
git remote add origin https://github.com/LpilinAlexandr/basic-git123.git
```
Если вы хотите изменить удаленный адрес, выполните:
```shell
git remote set-url origin <новый-удаленный-URL>
```
Пример полной команды:
```shell
git remote set-url origin https://github.com/LpilinAlexandr/basic-git123.git
```
Для просмотра списка всех удаленных адресов используйте:
```shell
git remote -v
```
Эти команды позволяют эффективно управлять удаленными репозиториями, с которыми взаимодействует ваш локальный репозиторий.


## stash - добавить изменения в стэш (почти стэк).
- `git stash -m 'название-стеша'` - спрячет все изменения в стеше (временном хранилище).

- `git stash pop` - извлечет последние изменения из стеша, удалив их оттуда (по умолчанию, стеш с индексом 0).

- `git stash apply` - применит последние изменения из стеша, сохранив его (по умолчанию, стеш с индексом 0).

- `git stash list` - отображает список всех стешей, предоставляя обзор сохраненных изменений.

- `git stash show <индекс-стеша>` - показывает изменения в указанном стеше (по умолчанию, стеш с индексом 0).

- `git stash drop <индекс-стеша>` - удаляет указанный стеш (по умолчанию, стеш с индексом 0).

Примечание: Индексы стешей начинаются с 0 и увеличиваются с каждым новым стешем.

Эти команды позволяют временно сохранять изменения, что полезно, например, при необходимости переключения между ветками без создания бесполезных коммитов.


## branch - управление ветками.
- `git branch` - отображает список всех локальных веток в репозитории. Текущая ветка будет выделена звездочкой.

- `git branch <имя-ветки>` - создает новую ветку с указанным именем от текущей ветки.

- `git branch -a` - выводит полный список веток, включая удаленные (remote) ветки.

- `git branch -m <новое-имя>` - переименовывает текущую ветку на новое имя.

- `git branch -d <имя-ветки>` - удаляет указанную ветку мягким способом (предполагает, что изменения внесенные в ветке уже были слиты в другие ветки).

- `git branch -D <имя-ветки>` - удаляет указанную ветку жестким способом, даже если изменения в ветке не были слиты в другие ветки.

Эти команды позволяют управлять ветками в Git, создавать новые, переключаться между ними, переименовывать и удалять.


## commit - сохранить изменения.

- `git commit -m 'заголовок-коммита'` - создает коммит с указанным заголовком.

- `git commit -m 'заголовок' -m 'текст-под-заголовком'` - создает коммит с заголовком и дополнительным текстом.

- `git commit <путь> -m 'заголовок'` - коммитит выбранный каталог, указанный по пути, с указанным заголовком.

- `git commit --amend` - позволяет внести изменения в предыдущий коммит. Если используется с `-m`, позволяет изменить заголовок коммита. При использовании `--no-edit` изменяет коммит, не изменяя заголовок и описание.

Эта команда предоставляет способ сохранить текущие изменения в истории репозитория, создавая новый коммит.


## push - отправка локальных изменений на удаленный репозиторий.

- `git push <удаленный-репо> <ветка>` - отправляет локальные изменения из указанной ветки на удаленный репозиторий.

- `git push -f <удаленный-репо> <ветка>` - принудительно отправляет локальные изменения, перезаписывая историю в удаленном репозитории. Используйте осторожно, так как это может привести к потере данных.

- `git push -u <удаленный-репо> <ветка>` - отправляет локальные изменения на удаленный репозиторий и устанавливает отслеживание (upstream) для данной ветки. Это означает, что в будущем вы можете использовать `git push` и `git pull` без указания удаленного репозитория и имени ветки.

Эти команды позволяют вам взаимодействовать с удаленным репозиторием, отправляя и получая изменения.


## switch | checkout - переключение между ветками и коммитами.

- `git checkout <ветка> | <коммит>` - переключается на указанную ветку или коммит по его хешу. Может также использоваться для создания новых веток и переключения между ними.

- `git checkout -b <новая_ветка>` - создает новую ветку от текущей и автоматически переключается на нее, сохранив все текущие изменения.

- `git switch <ветка> | <коммит>` - альтернативная команда для переключения между ветками или коммитами. 

- `git switch -c <новая_ветка>` - альтернативная команда для создания новой ветки от текущей и автоматического переключения на нее, сохранив все текущие изменения.

### Отличия между `switch` и `checkout`:

- `switch` предоставляет более ясный и безопасный интерфейс для переключения между ветками, а `checkout` используется для различных операций, что может привести к недопониманиям.

- `switch` предназначен прежде всего для переключения между ветками, в то время как `checkout` может использоваться для создания веток, перехода на конкретные коммиты и даже временного отмены изменений (с использованием `git checkout -- <файл>`).

### Когда использовать `switch` и `checkout`:

- Используйте `switch` для простого переключения между ветками. Это делает код более ясным и предотвращает путаницу.

- Используйте `checkout` для более сложных операций, таких как создание новых веток, переход на конкретные коммиты или временной откат изменений.

Важно отметить, что в Git версии 2.23 и выше `switch` и `restore` стали предпочтительными для использования вместо `checkout` для переключения веток и управления файлами соответственно.
```shell
git switch <ветка> | <коммит>  # Предпочтительно в Git версии 2.23 и выше
git restore <файл>  # Предпочтительно в Git версии 2.23 и выше
```

## merge
```shell
git merge <branch>  # Слить изменения из ветки <branch> в текущую ветку
git merge --continue  # Продолжить слияние в случае решения конфликтов
git merge --abort  # Отменить merge
```
Наличие нескольких веток чрезвычайно удобно для того, чтобы новые изменения были отделены друг от друга, а также чтобы вы случайно не запушили несанкционированные или поврежденные изменения в продакшин. Как только изменения будут одобрены, мы хотим получить эти изменения в нашей прод ветке!

Один из способов получить изменения из одной ветки в другую - выполнить `git merge`! Есть два типа менж команд, которые может выполнять Git: **fast-forward** или **no-fast-forward** 

### Fast-forward (--ff)

Fast-forward merge когда текущая ветка не имеет дополнительных коммитов по сравнению с веткой, которую мы мержим. Git у нас ленив и сначала попытается выполнить самый простой вариант: Fast-forward! Этот тип менжа не создает новый коммит, а скорее объединяет коммит(ы) в ветку, которую мы объединяем прямо в текущей ветке

<img src="/img/merge_ff.gif" alt="" style="max-width: 100%;">

Отлично! Теперь у нас есть все изменения, которые были сделаны в ветке `dev`, в ветке `master`. Итак, что же такое  **no-fast-forward**?

### No-fast-foward (--no-ff)

Хорошо, если ваша текущая ветка не имеет каких-либо дополнительных коммитов по сравнению с веткой, которую вы хотите смержить, но, к сожалению, это случается редко! Если мы зафиксировали изменения в текущей ветке, которых нет в ветке, которую мы хотим объединить, git выполнит объединение без fast-forward merge. При слиянии без fast-forward Git создает новый коммит мержа в активную ветку. Родительский коммит указывает на активную ветку и ветку, которую мы хотим объединить!

<img src="/img/merge_noff.gif" alt="" style="max-width: 100%;">

### Merge конфликты

Хотя Git хорошо решает, как объединять ветки и добавлять изменения в файлы, он не всегда может принять это решение сам по себе. Это может произойти, когда две ветки, которые мы пытаемся смержить, имеют изменения в одной строке в одном и том же файле, или если одна ветка удалила файл, который изменила другая ветка, и так далее.

В этом случае Git попросит вас помочь решить, какой из двух вариантов мы хотим сохранить. Допустим, что в обеих ветках мы отредактировали первую строку в файле README.md.

<img src="/img/mc.png" alt="" style="max-width: 100%;">

Если мы хотим смержить `dev` в `master`, это приведет к конфликту: хотите, чтобы заголовок был Hello! или hey!?

При попытке объединить ветки, Git покажет вам, где происходит конфликт. Мы можем вручную удалить изменения, которые не хотим сохранять, сохранить изменения, снова добавить файл и закоммитить изменения.

<img src="/img/conflict.gif" alt="" style="max-width: 100%;">


## rebase
```shell
git rebase <commit>  # Встать коммитами текущей ветки на выбранный коммит 
git rebase <branch>  # Встать коммитами текущей ветки на выбранную ветку
git rebase --continue  # Продолжить слияние в случае решения конфликтов
git rebase --abort  # Отменить rebase
```

Мы только что увидели, как можно применить изменения из одной ветки в другую, выполнив `git merge`. Другой способ добавить изменения из одной ветки в другую - выполнить `git rebase`.

**Git rebase** копирует коммиты из текущей ветки и помещает эти скопированные коммиты поверх указанной ветки.

<img src="/img/rebase.gif" alt="" style="max-width: 100%;">

Отлично, теперь у нас есть все изменения, которые были сделаны в `master` ветке и в `dev` ветке.

Большая разница по сравнению с мержем заключается в том, что Git не будет пытаться выяснить, какие файлы сохранить и не сохранить. В ветке, которую мы обновляем, всегда есть последние изменения, которые мы хотим сохранить! Таким образом, вы не столкнетесь ни с какими мерж конфликтами и у вас будет хорошая линейная история.

Этот пример показывает rebase в `master` ветке. Однако в больших проектах вы обычно не захотите этого делать. Git rebase изменяет историю проекта, поскольку для скопированных коммитов создаются новые хэши.

Rebase отлично подходит, когда вы работаете над feature branch, а master ветка была обновлена. Вы можете получить все обновления в своей ветке, которые предотвратят будущие merge конфликты

### Interactive Rebase

Перед rebas'ом коммитов мы можем их изменить! 😃 Мы можем сделать это с помощью Interactive Rebase. Interactive Rebase также может быть полезен для ветки, над которой вы сейчас работаете, и хотите изменить некоторые коммиты.

Есть 6 действий, которые мы можем выполнить над коммитами, которые мы rebas'им:

- `reword`: Изменить коммит меседж
- `edit`: Изменить коммит
- `squash`: Объеденить коммит в предыдущий коммит
- `fixup`: Объединить коммит с предыдущим коммитом, не сохраняя commit's log message
- `exec`: Запустить команду для каждого коммита, который мы хотим rebase
- `drop`: Удалить коммит

Таким образом, мы можем иметь полный контроль над нашими коммитами. Если мы хотим удалить коммит, мы можем просто drop'нуть его.

<img src="/img/interactive.gif" alt="" style="max-width: 100%;">

Или, если мы хотим объединить несколько коммитов вместе, чтобы получить более чистую историю, нет проблем!

<img src="/img/comb.gif" alt="" style="max-width: 100%;">

Interactive rebasing дает вам большой контроль над коммитами, которые вы пытаетесь rebase'нуть, даже в текущей активной ветке.


## reset
```shell
git reset <commit>  # Сбросить коммиты в индекс до указанного коммита
--soft  # Изменения сбрасываются в индекс (Дефолтное значение)
--hard  # Изменения удаляются
git reset --soft HEAD~  # Сбросить последний коммит в индекс
git reset --hard HEAD~4  # Убить последние 4 коммита

# squash life-hack
git reset --soft HEAD~3  # Сбрасываем 3 последних коммита в 1
git commit -m 'Обьединили 3 коммита'  # Коммитим заново, тем самым объединяя 3 коммита в 1
```

Может случиться так, что мы допустили изменения, которые мы не хотели заливать. Может быть, это коммит еще в работе или коммит, в котором есть ошибки! В этом случае мы можем выполнить `git reset`.

`git reset` избавляет от всех текущих промежуточных файлов и дает нам контроль над тем, куда должен указывать HEAD.

### Soft reset

Soft reset перемещает HEAD к указанному коммиту (или индексу коммита по сравнению с HEAD), не избавляясь от изменений, которые были внесены в коммиты позже.

Допустим, мы не хотим сохранять коммит `9e78i`, в который был добавлен файл `style.css`, и мы также не хотим сохранять коммит `035cc`, в который был добавлен файл `index.js`. Однако мы хотим сохранить недавно добавленные файлы `style.css` и `index.js`. Идеальный кейс для sort reset.

<img src="/img/sr.gif" alt="" style="max-width: 100%;">

Набрав git status, вы увидите, что у нас все еще есть доступ ко всем изменениям, которые были сделаны во время предыдущих коммитов. Это здорово, так как это означает, что мы можем исправить содержимое этих файлов и закоммитить их позже.

### Hard reset

Иногда мы не хотим сохранять изменения, внесенные некоторыми коммитами. В отличие от soft reset, нам не нужно больше иметь к ним доступ. Git должен просто сбросить свое состояние обратно туда, где он был в указанном коммите: это даже включает изменения в вашей working directory и stage файлах!

<img src="/img/hard.gif" alt="" style="max-width: 100%;">

Git отменил изменения, которые были внесены в `9e78i` и `035cc`, и сбросил свое состояние до того, где он был при коммите `ec5be`.


## revert
```shell
git revert <commit>  # Отменить коммит
git revert -n <commit>  # Отменить коммит и оставить изменения в индексе
```

Другой способ отменить изменения - выполнить `git revert`. Отменяя определенный коммит, мы создаем новый коммит, который содержит отмененные изменения.

Допустим, `ec5be` добавил файл `index.js`. Позже мы на самом деле понимаем, что больше не хотим, чтобы это изменения были в ветке! Давайте ревертнем коммит `ec5be`.


## cherry-pick
```shell
git cherry-pick <commit>  # Перенести коммит в HEAD текущей ветки
git cherry-pick -n <commit>  # Перенести коммит в HEAD текущей ветки, но не делать коммит
```

Когда определенная ветка содержит коммит, который внес изменения, которые нам нужны в нашей активной ветке, мы можем черипинуть коммит в нашу ветку. Cherry-pick создает новый коммит в нашей активной ветке, который содержит изменения, которые были в чери-пикнутом коммите.

Предположим, что коммит `76d12` в ветке `dev` добавил изменение в файл `index.js`, которое мы хотим добавить в `master`:

<img src="/img/cp.gif" alt="" style="max-width: 100%;">


## fetch
```shell
git fetch # Запросить все изменения из origin 
git fetch <remote> # Запросить все изменения из remote
git fetch <remote> --prune # Запросить все изменения из remote и синхронизировать их
```

Если у нас есть remote Git ветка, например ветка на Github, может случиться так, что remote ветка имеет коммиты, которых нет у текущей ветки! Возможно, другая ветка была объединена, или ваш коллега добавил hot fix и так далее.

Мы можем получить эти изменения локально, выполнив git fetch на remote ветке. Это никак не влияет на вашу локальную ветку: fetch просто загружает новые данные.

<img src="/img/fetch.gif" alt="" style="max-width: 100%;">


## pull
```shell
git pull origin <branch>  # Стянуть из remote актуальную ветку <branch> (По умолчанию режим merge)
git pull origin <branch> --rebase  # Стянуть из remote актуальную ветку в режиме rebase
```

Хотя git fetch очень полезен для получения remote информации о ветке, мы также можем выполнить `git pull`. Git pull - это две команды в одной: `git fetch` и `git merge`. Когда мы извлекаем изменения из origin, мы сначала fetch'им все данные, как мы делали с помощью git fetch, после чего последние изменения автоматически мержатся в локальную ветку.

<img src="/img/pull.gif" alt="" style="max-width: 100%;">


## reflog
```shell
git reflog  # Показать историю
git reflog <branch> # Показать историю по конкретной ветке
```

Все делают ошибки, и это совершенно нормально! Иногда может показаться, что вы испортили свой репозиторий Git настолько сильно, что просто хотите полностью его удалить.

`git reflog` - очень полезная команда для отображения журнала всех выполненных действий! Это включает в себя слияния, перезагрузки, возвраты: в основном, любые изменения в вашей ветке.

<img src="/img/reflog.gif" alt="" style="max-width: 100%;">

Если вы допустили ошибку, вы можете легко отменить ее, сбросив HEAD на основе информации, которую нам предоставляет reflog.

Скажем, мы на самом деле не хотели мержить origin ветку. Когда мы выполняем команду `git reflog`, мы видим, что состояние репозитория до мержа- `HEAD@{1}`. Давайте выполним `git reset`, чтобы указать HEAD туда, где он был.

<img src="/img/resh.gif" alt="" style="max-width: 100%;">

Как мы видим, последнее действие было перенесено в рефлог.
