# Перевод "Руководство сотрудничества"

------

Оригинал смотри: https://golang.org/doc/contribute.html


`go version go1.8.3 linux/amd64`

# Оглавление
------

* [Как стать помощником(соучастником)](#Как-стать-помощником(соучастником))
	* [Настройка Git для использования Gerrit](#Настройка-Git-для-использования Gerrit)
		* [Шаг 1: Регистрация в googlesource для генерации пароля](#Шаг-1:-Регистрация-в-googlesource-для-генерации-пароля)
		* [Шаг 2: Запуск скрипта](#Шаг-2:-Запуск-скрипта)
		* [Шаг 3: Регистрация в Gerrit](#Шаг-3:-Регистрация-в-Gerrit)
	* [Лицензионное соглашение сотрудничества(Contributor License Agreement, CLA)](#Лицензионное-соглашение-сотрудничества(Contributor-License-Agreement,-CLA))
		* [Какое CLA](#Какое-CLA)
		* [Завершение CLA](#Завершение-CLA)
	* [Подготовка среды разработки](#Подготовка-среды-разработки)
	* [Настройка Git для отправки в Gerrit](#Настройка-Git-для-отправки-в-Gerrit)
		* [Установка команды git-codereview](#Установка-команды-git-codereview)
		* [Настройка git-псевдонимов(git aliases)](#Настройка-git-псевдонимов(git-aliases))
		* [Понимание команд git-codereview](#Понимание-команд-git-codereview)
* [Внесение вклада (Making a Contribution)](#Внесение-вклада-(Making-a-Contribution))
	* [Обсудите Ваш дизайн(вопрос)](#Обсудите-Ваш-дизайн(вопрос))
	* [Внесение изменений](#Внесение-изменений)
		* [Забирание исходных кодов проекта Go](#Забирание-исходных-кодов-проекта-Go)
		* [Довабление в основное дерево Go](#Довабление-в-основное-дерево-Go)
		* [Вклад в подрепозитории (golang.org/x/...)](#Вклад-в-подрепозитории-(golang.org/x/...))
		* [Создание изменений](#Создание-изменений)
		* [Авторские права](#Авторские-права)
		* [Фиксирование Ваших изменений](#Фиксирование-Ваших-изменений)
		* [Тестирование](#Тестирование)
		* [Отправка изменений на рассмотрение(review)](#Отправка-изменений-на-рассмотрение(review))
		* [Решение проблем](#Решение-проблем)
		* [Указание рецензента и заинтересованных сторон](#Указание-рецензента-и-заинтересованных-сторон)
	* [Прохождение процесса рассмотрения](#Прохождение-процесса-рассмотрения)
		* [Перепросмотр и повторная отправка](#Перепросмотр-и-повторная-отправка)
		* [Синхронизация своего клиента](#Синхронизация-своего-клиента)
		* [Устранение конфликтов](#Устранение-конфликтов)
		* [Просмотр кода другими пользователями](#Просмотр-кода-другими-пользователями)
	* [Использование изменений в ветке master](#Использование-изменений-в-ветке-master)
	* [Дополнительная информация](#Дополнительная-информация)

------

Проект Go приветствует всех помощников. Процесс внесения своего вклада в проект Go может отличаться от того к чему Вы привыкли. Данный документ предназначен для того чтобы помочь Вам разобраться в  том - как внести свой вклад. Данное руковоство предполагает, что у Вас уже есть общее знания работы в Git и Go.

(Примечание, Руководство сотрудничества для `gccgo` расположено [здесь](https://golang.org/doc/gccgo_contribute.html) )

(По воспросам связанным с безопасностью, обращайтесь по адресу security@golang.org).


# Как стать помощником(соучастником)

Прежде чем стать помощником для проекта Go, Вам необходимо выполнить несколько условий.
Проект Go использует [Gerrit](https://www.gerritcodereview.com/), как онлайн-инструмент с открытым исходным кодом для всестороннего рассмотрения кода.
Gerrit использует Ваш адрес электронной почты как уникальный идентификатор.
В проекте Go пока только настроен только на Google Accounts.
В связи с этим, Вам необходимо *предварительно* иметь хотя бы один Google Account.

## Настройка Git для использования Gerrit

Для этого Вам необходим веб-браузер и консоль командной строки.
Вам необходимо иметь установленный Git.

Gerrit использует Google Accounts для аутентификации.
Если у Вас нет Google Account, то Вы можете создать его [включая новый аккаунт почты Gmail](https://www.google.com/accounts/NewAccount) или создать ассоциированный аккаунт [с имеющийся у Вас адресом электронной почты](https://accounts.google.com/SignUpWithoutGmail).


### Шаг 1: Регистрация в googlesource для генерации пароля

Visit [go.googlesource.com](https://go.googlesource.com) и кликните на  "Generate Password" в верхней правой части меню страницы.
Вас потом перенаправит на accounts.google.com для авторизации.

### Шаг 2: Запуск скрипта

После регистрации, Вы попадеье на страницу [go.googlesource.com](https://go.googlesource.com) озаглавленный "Configure Git"(Настройка Git).
Эта страница включает область с Вашим персональным скриптом, который при локальном запуске (на Вашем компьютере) настроет git для Вас уникальный аутентификационный ключ.
Это ключ является одним из пары, причем один генерируется на стороне сервера, похоже на работу с ключами для ssh.

Скопируйте и запустите этот скрипт в Вашем терминале командной строки.
(На компьютере с Windows используйте программу `cmd` и используйте инструкцию в желтой области веб-страницы для запуска команд. Если же Вы используете git-bash то используйте тот же скрипт как для `*nix`)

Ваш секретный ключ после запуска скрипта расположен в файле `.gitcookie` и теперь Git настроен для использования этого файла.

### Шаг 3: Регистрация в Gerrit

Сейчас для регистрации своего ключа, Вам необходимо зарегистрировать свой аккаунт в Gerrit.
Для этого посетите страницу [ go-review.googlesource.com/login/](https://go-review.googlesource.com/login/).
Зарегистрируйтесь используя тот же Google Account, который использовали ранее.

## Лицензионное соглашение сотрудничества(Contributor License Agreement, CLA)

### Какое CLA

Перед отправкой Ваших первых изменений в проект Go Вы должны подтвердить один из двух CLA.
Какой именно CLA Вы подпишите зависит от того кто владеет авторскими правами на Вашу работу.

* Если Вы являетесь владельцем авторских прав, то Вам необходимо согласиться с  [individual contributor license agreement](https://developers.google.com/open-source/cla/individual), который допускают подтверждение в онлайн.
* Если владельцем Ваших авторских прав является организация, то организации необходимо согласиться с [corporate contributor license agreement](https://developers.google.com/open-source/cla/corporate).

*Если владелей авторских прав уже подтвердил соглашение в другом открытом проекте Google, то дополнительно подтверждать нет необходимости.*

### Завершение CLA

Вы можете увидеть подписанное Вами соглашение и подписать ещё одно через интерфейс Gerrit.
Для этого, [войдите в свой аккаунт Gerrit](https://go-review.googlesource.com/login/), кликните на Вашем имени в вверхнем правом углу и выбирете "Settings"("Настройки"), потом выбирете "Agreements"(Соглашения) слево вверху. Но если у Вас нет подписанных соглашений описанных тут, то Вы можете создать новый кликнув на "New Contributor Agreement" и действовать по следующим шагам.

Если Вы владелец авторских прав на код, который Вы будуте отправлять изменения - к примеру, если Вы начинаете вводить код от имени новой компании - то пожайлуста отправьте электронное письмо golang-dev и дайте нам знать, чтобы мы могли убедиться, что соответствующее соглашение будет завершено и обновим файл `AUTHORS`(авторы).

# Подготовка среды разработки

## Настройка Git для отправки в Gerrit

Изменения в Go должны пройти рассмотрение(review) для их принятия, в не зависимости от того кто создал данное изменение.
Команда git называется `git-codereview`, обсуждаемая ниже, поможет управлять рассмотрением кода, размещенный на Google-хост [экземляре](https://go-review.googlesource.com/) Gerrit.

### Установка команды git-codereview

Установка команды `git-codereview` происходит запуском,

```
$ go get -u golang.org/x/review/git-codereview
```

Убедитесь что `git-codereview` установился в Вашу папку, так чтобы команда `git` могла найти его. Проверим это:

```
$ git codereview help
```

напечатает текст помощи, не ошибку.

Если Вы используете git-bash в Windows убедитесь что программа `git-codereview.exe` расположена вашей папке git. Запустите `git --exec-path` для того чтобы открыть нужное место, затем создайте символическую ссылку или просто скопируйте исполняемый файл из $GOPATH/bin в этот каталог.


**Примечание для поклонников Git:**
Команда `git-codereview` не требуется для загрузки и управления кода Gerrit рассмотрение.
Для тех, кто предпочитает простой Git, то текст ниже предоставит эквивалентную Git команды для каждой git-codereview рассмотрения кода.

Если Вы используете простой Git, обратите внимание, что вам все равно потребуется настройка команд `git-codereview`. Эта настройка добавляет `Change-Id` для Gerrit в сообщение фиксирования(commit) и проверки всех исходных файлов Go, который отформатирован `gofmt`.
Даже если Вы собираетесь использовать простого Git для ежедневной работы, то настройте Git checkout запустив `git-codereview` `hooks`.

Показанный ниже рабочий процесс предполагает одно изменение на ветку(branch).
Это также предполагает подготовку последовательности (обычно связанных) изменений в одну ветку.
Смотрите детальнее [git-codereview documentation](https://golang.org/x/review/git-codereview).

### Настройка git-псевдонимов(git aliases)

Команда `git-codereview` может быть запущено прямо из командной строки, например:

```
$ git codereview sync
```

Но будет удобнее если настроить псевдонимы для команд `git-codereview`, так что выше превращается в:

```
$ git sync
```


Подкоманда `git-codereview` были выбраны таким образом чтобы отличились от собственных команд Git, так что использование безопастно.

Псевдонимы не обязательны, но в дальнейшем в этом документе, мы будем предполагать что они установлены.
Для установки их, необходимо скопировать следующий текст в Ваш конфигурационный файл Git(обычно это файл в домашней папке `.gitconfig`):

```
[alias]
	change = codereview change
	gofmt = codereview gofmt
	mail = codereview mail
	pending = codereview pending
	submit = codereview submit
	sync = codereview sync
```

### Понимание команд git-codereview

После установки комманд `git-codereview`, вы можете запустить

```
$ git codereview help
```

для того чтобы изучить эти комманды.
Вы также можете почитать [command documentation](https://godoc.org/golang.org/x/review/git-codereview).

# Внесение вклада (Making a Contribution)

## Обсудите Ваш дизайн(вопрос)

Проект приветствует Вашу работу, но пожайлуста дайте знать о том над чем Вы работаете в случаи если хотите что то изменить или добавить в репозитории Go.

До того как приступить к внесению изменений или добавлению чего-то нового, просьба записать Вашу проблему в [файл проблем (issue)](https://golang.org/issue/new) (или заявить в  файле [существующие проблемы](https://golang.org/issues)).
Существенные изменения должны пройти процесс [формирования предложения](https://golang.org/s/proposal-process) до того как они будут приняты.

Этот процесс даёт всем возможность проверить дизайн, позволяет избежать дублирования усилий, а также убедится что заложенная идея удовлетворяет целям языка и инструментарию.
Также это проверка на то что дизайн звучит хорошо, так как рассмотрение кода не место для высокоуровневой беседы.

При планировании Вашей работы, пожайлуста следите за [шести-месячным циклом разработки проекта Go](https://golang.org/wiki/Go-Release-Cycle).
Вторая половина каждого цикла - это трех месячная замораживание функций, в течение которого принимаются только исправления ошибок и обновляется документация. Новые вклады в проект могут быть отложены на время замораживания функций, и по ним не будут приниматься какие-либо решения до наступления разморозки.

## Внесение изменений

### Забирание исходных кодов проекта Go

Для начала Вам необходимо иметь локальную копию репозитория.
Как и Go builds проекту Go также потребуется рабочая и установленная версия Go  (некоторые изменения в документации могут быть не актуальны).
Это должна быть последняя, актуальная версия Go, которая может быть получена через любой пакет, исполняемый дистрибутив или Вы можете сформировать её из исходных кодов.

Вы можете выгрузить репозиторий Go куда Вас нравиться даже за пределами Вашего  $GOPATH.
Зайдите в папку, куда хотели бы выгрузить исходные коды и запустите следующую команду в теминале командной строки.

````
$ git clone https://go.googlesource.com/go
$ cd go
````

### Довабление в основное дерево Go

Неибольшее установок Go использует ветку release, но новые изменения должны основываться на ветве master.
(Позже они могут быть приняты в ветку release как чать процесса release, но большенство участников не сделают сами.)
До того как внести изменения, убедитесь что Вы начинаете с ветки master:

```
$ git checkout master
$ git sync
```

(В терминологии Git, `git` `sync` запускает `git` `pull` `-r`.)

### Вклад в подрепозитории (golang.org/x/...)

Если Вы хотите внести изменения в подрепозитории, то его можно получить используя `go get`. К примеру, для внесения изменений в `golang.org/x/oauth2`, необходимо запустить:

```
$ go get -d golang.org/x/oauth2/...
```

Затем Вы можете зайти в паку пакета (`$GOPATH/src/golang.org/x/oauth2`).


### Создание изменений

Все полученное дерево - изменяемо.
Сделайте Ваши изменения как Вы сочтете нужным, добавте тестов для Ваших изменений. Проверьте Ваши изменения как Вам кажется нужно.

### Авторские права

Файлы в репозитории Go не имеют списка авторов, для того чтобы избежать беспорядка и для того чтобы избежать обновления списков.
Вместо этого, Ваше имя будет внесено в [файл изменений (change log)](https://golang.org/change), а также в список [помощников(CONTRIBUTORS)](https://golang.org/CONTRIBUTORS) и возможно в список [авторов(AUTHORS)](https://golang.org/AUTHORS).
Данные файлы генерируются автоматически исходя из `commit logs`.
Файл [авторов(AUTHORS)](https://golang.org/AUTHORS) определяет кто такие "The Go Authors(Авторы Go)" - владельцы авторских прав.

Для новых файлов, которые Вы вносите, должен быть использован стандартный заголовок авторских прав:

```
// Copyright 2017 The Go Authors. All rights reserved.
// Use of this source code is governed by a BSD-style
// license that can be found in the LICENSE file.
```

В заголовке авторских прав в файлах репозитория участвует число - год.
Не обновляйте год в файлах, которые меняете.

### Фиксирование Ваших изменений

После того как измените файлы, необходимо сообщить Git об изменениях.
Также Вам необходимо сообщить Git о всех добавленных, удаленных или переименованных файлах.
Данные операции выполняються обычными командами Git: `git` `add`, `git` `rm`, and `git` `mv`.

После того как все изменения были внесены и поставленны в очередь, необходимо их зафиксировать(commit).
В рабочем процессе внесения изменений в проект Go это производиться командой `git change`, которая создает локальльную ветку и фиксирует изменения напрямую в этой локальной ветке.

```
$ git change <branch>
```

Имя ветки(*<branch>*) может быть любым для идентификации локальной ветки Ваших изменений и не может быть использовано в любом другом месте.
Это операция локальная, при которой ничего не будет отправлено на сервер.

(В терминологии Git, `git` `change` `<branch>` запускает `git` `checkout` `-b` `branch`, потом `git` `branch` `--set-upstream-to` `origin/master`, и потом `git` `commit`.)



Поскольку `git commit` является конечным шагом, то Git откроет для Вас редактор для запроса фиксирующего сообщения (commit message).
(Он использует редактор под именем `$EDITOR` в Вашей среде, по умолчанию используется `vi`.)

Файл будет выглядить следующим образом:

```
# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
# On branch foo
# Changes not staged for commit:
#	modified:   editedfile.go
#
```

В начале данного файла будет пустая строка, дополните её описанием Вашего изменения.
Данная строка будет использоваться для однострочного суммарного изменения, префиксом для основнго изменяемого пакета, а также будет использоваться в качестве темы электронных писем при рассмотрению кода.
Он должен заканчиваться предложением "This change modifies Go to _____."
Остальная часть описания должна описывать процесс разработки, изменения и пояснения как это работает.
Запись должна производиться с правильной пунктуацией, как и Ваши комментратии в Go.
Если уВас есть поясняющая ссылка, то добавьте её.
Если Вы исправляете проблему(issue), то укажите её номер прежде всего.

После редактирования, шаблон можно будут читать:

```
math: improve Sin, Cos and Tan precision for very large arguments

The existing implementation has poor numerical properties for large arguments, so use the McGillicutty algorithm to improve accuracy above 1e10.

The algorithm is described at http://wikipedia.org/wiki/McGillicutty_Algorithm

Fixes #159

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
# On branch foo
# Changes not staged for commit:
#	modified:   editedfile.go
#
```

Закомментирована секция файла со списком всех измененных файлов.
Хорошей практикой будет разделять несвязанные изменения по разным изменениям, поэтому если Вы видете что в списке появляется файл которого не должно быть, то отмените команду и разделите файлы по разным веткам.

Специальное обозначение "Fixes #159" означает ссылку на проблему(issue) 159
[Go issue tracker](https://golang.org/issue/159).
Когда изменение будет принято, то трекер проблем (the issue tracker) автоматически отметит проблему решенной.
(Существует множество соглашений, подробно описанных в [GitHub Issue Tracker documentation](https://help.github.com/articles/closing-issues-via-commit-messages/).)


```
GitHub Issue Tracker documentation:

Вы можете добавить в Ваше сообщение фиксации(commit) специальные ключевые слова для автоматического закрытия проблем(issue) в GitHub.
Для примера, если в сообщении фиксации добавить Fixes #45, то проблема 45 в этом репозитории будет слит в ветку по-умолчанию.
Ключевые слова:
close
closes
closed
fix
fixes
fixed
resolve
resolves
resolved
```

Закончив писать сообщение фиксации(the commit message), созраните файл и выйдите из редактора.

Вы должны быть уверены, что имеете в своей среде переменную $EDITOR и работает правильно для успешного завершения.
Если Вы столкнетесь к какими либо проблемами, то выйдите из редактора некорректно. Тогда попробуйте настроить другой редактор в переменную $EDITOR Вашей среды.

Если Вы желаете отредоктировать больше, то перегруппируйте(re-stage) свои изменения с помощью  `git` `add`, и потом запустите

```
$ git change
```

для обновления описания изменения и включить поэтапные изменения.
Описание изменений включает в себя строку `Change-Id` где-то внизу, добавленный `git` `change`.
Данная строка используется Gerrit как признак соответствия (match) для загрузки одинаковых изменений. Не редактируйте и не удаляйте его.

(В терминологии Git, `git` `change` без имени ветки запускает `git` `commit` `--amend`.)


### Тестирование

Вы должны [написать и протестировать свой код](https://golang.org/doc/code.html), но перед отправкой кода на рассмотрение, запустите Ваши тесты для всего дерева для того чтобы убедиться что Ваше изменение не ломает другие пакеты и программы:

```
$ cd go/src
$ ./all.bash
```

(Для проветки в Windows используйте`all.bat`.)

После прохождения всех команд должно напечататься:

```
"ALL TESTS PASSED".
```

### Отправка изменений на рассмотрение(review)

Как только изменение будет готово, отправляйте их на рассмотрение.
Это похоже на `git push` в стиле рабочего процесса GitHub.
Это делается с помощью настройки псевдонима `mail`, которая не смотря на своё имя не отправляет почту, а лишь отправляет изменения в Gerrit как git push.

```
$ git mail
```

(В терминологии Git, `git` `mail` отправляет локальные зафиксированные изменения в Gerrit используя `git` `push` `origin` `HEAD:refs/for/master`.)

Если Ваше изменение связано с открытой проблемой(issue), то добавьте комментарий в проблему(issue) о предлагаемом исправлении, включая ссылку на Ваш CL.

Сервер рассмотрения кода присваевает Вашему изменению номер и URL, который `git` `mail` напечатает, приблизительно следующим образом:

```
remote: New Changes:
remote:   https://go-review.googlesource.com/99999 math: improved Sin, Cos and Tan precision for very large arguments
```

### Решение проблем

Самая распространенная причина по которой команда `git mail` даёт сбой, заключается в том, что используемый адрес электронной почты не прошел через вышеприведённую настройку.

Вы увидите что то вроде...

```
remote: Processing changes: refs: 1, done
remote:
remote: ERROR:  In commit ab13517fa29487dcf8b0d48916c51639426c5ee9
remote: ERROR:  author email address XXXXXXXXXXXXXXXXXXX
remote: ERROR:  does not match your user account.
```

Для решения Вам нужно либо добавить адрес электронной почты, указанный в CLA, либо установить данный репозитарий для  использования другого утверждённого адреса электронной почты.

Во первых давайте изменим адрес электронной почты для данного репозитария, чтобы этого не повторялось, и используйте следующую команду:

```
$ git config user.email email@address.com
```

После этого измените предедущую фиксацию(commit) для использования альтернативного адреса электронной почты.
Вы можете сделать это с помощью:

```
$ git commit --amend --author="Author Name <email@address.com>"
```

И теперь попробуйте повторно отправить:

```
$ git mail
```

### Указание рецензента и заинтересованных сторон

Если явно не указано иное, например, в обсуждении, предшествовавшем отправке в список изменений, лучше не указывать рецензента.
Все изменения автоматически включаются в список рассылки [golang-codereviews@googlegroups.com](https://groups.google.com/group/golang-codereviews). Если это ваше первое изменение, возможно, задержка перед появлением в списке рассылки, это сделано для предотвращения спама в рассылке.

Вы можете указать рецензент или заинтересованные стороны CC, используя опции `-r` или` -cc`.
Оба принимают список адресов электронной почты, разделенный запятыми:

```
$ git mail -r joe@golang.org -cc mabel@example.com,math-nuts@swtch.com
```

## Прохождение процесса рассмотрения

Запустив `git` `mail` будет отослано электронное писмо Вам и рецензентам с просьбой посетить URL проблемы и сделать комментарии к изменению.
Когда это будет сделано, то рецензент добавляет комментарий через пользовательский интерфейс Gerrit и кликнув "Ответить"("Reply") для того чтобы отправить комментари.
Когда это произойдет, Вы получите письмо с уведомлением.
Вы должны отвечать только через веб-интерфейс.
(К сожалению, использование старой системы рассмотрений Rietveld, отвечая на письма показывала свою не эффективность.)

### Перепросмотр и повторная отправка

Рабочий рабочий процесс Go оптимизирован для итеративных изменений на основе обратной связи.
Редко, что первоначальный взнос будет готов к применению, как есть.
По мере того, как вы пересматриваете свои изменения и отправляете повторно, Gerrit сохранит историю всех изменений и комментариев, в одном URL-адресе.

Вы должны отвечать только через веб-интерфейс.

Когда вы пересмотрели код и готовы к очередному раунду рассмотрения, сделайте эти изменения и используйте `git`` change` для обновления фиксации(commit).
Чтобы отправить список изменений для другого раунда рассмотрения, снова запустите `git`` mail`.

Рецензент может прокомментировать новую копию, и процесс повторяется.
Рецензент одобряет изменение, давая ему положительный результат (+1 или +2) и отвечающий `LGTM`: выглядит хорошо для меня.

Вы можете просмотреть список ожидающих изменений, запустив `git`` pending` и переключаться между ветвями изменений с помощью `git`` change` `* <branch> *`.

### Синхронизация своего клиента

Пока вы работали, другие могли внести изменения в репозиторий.
Чтобы обновить локальную ветвь, запустите:

```
$ git sync
```

(В терминалогии Git, `git` `sync` запускает `git` `pull` `-r`.)

### Устранение конфликтов

Если файлы, которые вы редактировали, изменились, Git делает все возможное, чтобы объединить удаленные изменения в ваши локальные изменения.
Он может оставить некоторые файлы для объединения вручную.

Например, предположим, что вы отредактировали `sin.go`, но кто-то еще совершил независимое изменение.
Когда вы запускаете `git`` sync`, вы получите (страшный) вывод:

```
$ git sync
Failed to merge in the changes.
Patch failed at 0023 math: improved Sin, Cos and Tan precision for very large arguments The copy of the patch that failed is found in:
   /home/you/repo/.git/rebase-apply/patch

When you have resolved this problem, run "git rebase --continue".
If you prefer to skip this patch, run "git rebase --skip" instead.
To check out the original branch and stop rebasing, run "git rebase --abort".
```

Если это произойдет, запустите

```
$ git status
```

чтобы посмотреть, какие файлы не удалось слить.
Результат будет выглядеть примерно так:

```
rebase in progress; onto a24c3eb
You are currently rebasing branch 'mcgillicutty' on 'a24c3eb'.
  (fix conflicts and then run "git rebase --continue")
  (use "git rebase --skip" to skip this patch)
  (use "git rebase --abort" to check out the original branch)

Unmerged paths:
  (use "git reset HEAD <file>..." to unstage)
  (use "git add <file>..." to mark resolution)

	*both modified: sin.go*
```

Единственная важная часть в этом расшифровке - это выделенная курсивом «измененная» строка: Git не смог объединить ваши изменения с конфликтующими изменениями.
Когда это произойдет, Git оставляет оба набора изменений в файле,
С конфликтами, отмеченными `<<<<<<<` и `>>>>>>>`.
Теперь ваша работа заключается в редактировании файла для их объединения.
Продолжая пример, поиск этих строк в `sin.go` может появиться:

```
	arg = scale(arg)
<<<<<<< HEAD
	if arg < 1e9 {
=======
	if arg < 1e10 {
>>>>>>> mcgillicutty
		largeReduce(arg)
```

Git не показывает это, но предположим, что исходный текст, который начался с обеих редакций, был 1e8; Вы изменили его на 1e10, а другое изменилось на 1e9, поэтому правильный ответ теперь может быть 1e10.
Сначала отредактируйте раздел, чтобы удалить маркеры и оставить правильный код:

```
	arg = scale(arg)
	if arg < 1e10 {
		largeReduce(arg)
```

Затем сообщите Git, что конфликт разрешен путем запуска

```
$ git add sin.go
```

Если вы редактировали файл, скажем, для отладки, но не хотите сохранять свои изменения, вы можете запустить `git`` reset`` HEAD`` sin.go`, чтобы отказаться от ваших изменений.
Затем запустите `git`` rebase`` -continue`, чтобы восстановить фиксацию(commit) изменений.

### Просмотр кода другими пользователями

В рамках процесса обзора рецензенты могут предлагать изменения напрямую (в рабочем процессе GitHub это будет кто-то другой, связанный с запросом на перенос(pull request)).

Вы можете импортировать эти изменения, предложенные кем-то еще, в свой локальный репозиторий Git.
На странице обзора Gerrit нажмите ссылку "Download ▼" в правом верхнем углу, скопируйте командой «Checkout» и запустите ее в своем локальном репозитории Git. Он должен выглядеть примерно так:

```
$ git fetch https://go.googlesource.com/review refs/changes/21/1221/1 &amp;&amp; git checkout FETCH_HEAD
```

Для того, чтобы вернуться в ветку с которой Вы работали.

## Использование изменений в ветке master

После того, как код был `LGTM`, одобритель может применить его к мастер-ветке с использованием интерфейса Gerrit.
На веб-странице есть кнопка «Отправить» для изменения, которое появляется после утверждения изменения (с пометкой +2).

Эти изменения проверяються в репозитарии.
Описание изменения будет содержать ссылку на обзор кода, а обзор кода будет обновлен ссылкой на изменение в репозитории.
Поскольку метод, используемый для интеграции изменений, - «Cherry Pick», хеши фиксации в репозитории будут изменены операцией «Отправить».

## Дополнительная информация

В дополнение к информации здесь, сообщество Go поддерживает страницу вики-страницы [CodeReview](https://golang.org/wiki/CodeReview). Не стесняйтесь вносить свой вклад в эту страницу, когда вы изучаете процесс обзора.
