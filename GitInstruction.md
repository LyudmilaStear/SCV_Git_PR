![Logo](Git-Logo-1788C.png)

# **Работа с Git**
## 2 lvl
### 3 lvl
#### 4  lvl
##### 5 lvl
###### 6 lvl
####### 7 lvl : do not exist

## 0. Ошибки и их исправления.
### 0.1 команда для преименования файл
`git mv file_from file_to` 
### 0.1 Две команды одновременно
Если ошибка

"fatal: Unable to create 'C:/Users/Severova/Desktop/GitEducation/.git/index.lock': File exists.

Another git process seems to be running in this repository, e.g.
an editor opened by 'git commit'. Please make sure all processes
are terminated then try again. If it still fails, a git process
may have crashed in this repository earlier:
remove the file manually to continue./"
то может помочь команда  `rm -f .git/index.lock`

### 0.3 Замена коммита.
Была комманда `git commit -m "Add информацию 5 - Инициалиизация"` . Чтобы исправить коммит используем команду --amend, это выглядит так: `git commit -amend "Add раздел 5 - Инициализация"`

git add .  подготавливает к фиксации и добавляет все изменения и файлы

## 1. Проверка наличия установленного Git
в терминале вводим  `git version`  или  `git --version` (более универсальна)/
Если Git уcтановлен, то появится сообщение о версии программы. Иначе - сообщение об ошибке.

## 2. Установка Git
Загружаем последнюю версию Git с сайта [загркзка Git](https://git-scm.com/).  Устанавливаем с настройками по умолчанию.

## 3. Просмотор действий (логов)
* Ввести команду `git log` чтобы увидеть подробный список коммитов и информации
* Ввести команду `git log -oneline` чтобы увидеть номера изменений и комментарии
* Ввести команду`git log --oneline <file_name>` чтобы увидеть логи только по одному файлу

## 4. Настройка Git
При первом использовании необходимо "представиться". Для этого в терминале вводятся две команды:
```
git config --global user.name "<ваше_имя>"
git config --global user.email "<адрес_почты@email.com>"
```

```c
while(n < 0)
{
    n++;
}
```
## 5. Инициализация репозитория
В терминале переходим к папке, в которой хотим создать репозиторий. Выполняем комманду. 
```git init```


## 6. Запись изменений в репозитории
  *6.1 Узнать текущий статус*  
  `git status` покажет готов ли файл для коммита, или его надо вначале добавить в репозииторий после наших изменений (см.п. 7.2)

  *6.2 Добавить файл в репозиторий*  
  `git add .`  добавит все файлы и все изменения
  `git add <file_name>` будет добавлять только указанный файл  
  после добавления файла можно его коммитить с комментарием, чтобы не потерять

  *6.3 Коммит*  
  для того чтобы сохранить(записать) все изменения ии добавить к ним комментарий, по которому будет легко найти эту версию документа используется коменда **commit**  
  `git commit -- m "text"` используется **обязательно** после команды `git add`  
  две верхние команды можно объеденить в одну двумя способами  
  * `git command -a -m "text"` не добавляет новые файллы в отслежжование
  * `git command -am "text"`  

  *6.4 Просмотр разницы  
  Чтобы увидеть разницу между последней версией и текущей, т е чтобы показались все различия используем команду  
  ```
  git def
  ```

## 7. Перемещение между сохранениями
После того как мы посмотрелли наши сохранения/логи//действия (см. п. 3), мы можем перемещаться межжду версиями  
Для этого используется команда `git checkout <№log>`
чтобы вернуться в актуалльную версию используются комманды
```
git checkout master
or
git switch -
```
## 8. Как добавить изображение.
* добавить изображжение в игнор
* закоммитить вначале папку gitignore
* добавить команду `![Logo](relative__path)`
* комиттим изменения

## 9. Игнорирование файлов.
Длля того, чтобы исключить для отслеивания из репозитория определенные файлы или папки, в репозитории надо создать файл ***.gitignoree***. Туда записываем их названия ии шаблоны соответствующие таким файлам или папкам. Например *.jpg* *.png*

## 10. Создание веток в Git.
По умолчанию основная ветка *master*.  
```
git branch <name_new_branch> эта команда создает ветку <name_new_branch>
```
`git checout -b <name>` эта команда создает ветку *name* и сразу на нее переключает
`git merge -abort` прерывает слияние веток, если мы не закоммитили слияние

`git checout -b createBranches` эта команда создает ветку *createBranches* or *anotherName* и сразу на нее переключает

Список веток в репозитории показывает команда  
```
git branch
```  
текущая ветка будет отмечена __* master__

## 11. Слияние веток и разрешение конфликтов.
Переходим в ветку к которой будем добавлять информацию(текущая ветка)
`git merge <branchname>` команда используется для слияния выбранной ветки<branchname> с текущей
 если есть конфликт - его надо разрешить.
 Если была изменена одна и та же часть файла в обеих ветках,  то появляется конфликт. Он требует участия пользователя.  
 VSCode предложжит три варианта решения,плюс  ручное переписывание конфликтных участков.  
 Мы выбираем то, что надо оставить.
 Изменения Надо закоммитить!!!
 
???`git reset --merge ORIG_HEAD`??? отмена слияния веток, если оно не сохранено(закоммитено) еще
`git merge -abort` прерывает слияние веток, если мы не закоммитили слияние

`git branch -d <name>` работает только из другой ветки

### 12. Удаление веток.
В первую очередь перед удалением надо провести слияние законченной ветки перед ее удалением, чтобы сохранились файлы.  
Затем надо перейти в ветку, которая не будет удалена.  
Выполняем команду
```
git branch -d <branchname>

важно поинить, что эта команда работает только тогда, когда перед этим ветка была корректна merge и изменения после слияния были закоммичены.

Если нам надо принудительно удалить еще не слитую ветку, то используется принудительное удаление:
```
git branch -D <branchname>
```


## 13. Клонирование существующего репозитория.
Если проект уже настроен в центральном репозитории, наиболее распространенным способом создать его локальный клон является команда clone. Клонирование, как и команда git init, обычно выполняется один раз. Получив рабочую копию, разработчик в дальнейшем выполняет все операции контроля версий из своего локального репозитория.  

```
git clone <repo url>
```

Команду git clone выполняют для создания копии (клонирования) удаленного репозитория. В качестве параметра в команду git clone передается URL-адрес репозитория.Git поддерживает несколько различных сетевых протоколов и соответствующих форматов URL-адресов. В этом примере используется SSH-протокол Git. URL-адреса SSH в Git имеют следующий шаблон: git@HOSTNAME:USERNAME/REPONAME.git

Пример URL-адреса SSH в Git имеет вид: *git@bitbucket.org:rhyolight/javascript-data-store.git*, а ниже приведены значения шаблонных параметров:

```
HOSTNAME: bitbucket.org
USERNAME: rhyolight
REPONAME: javascript-data-store
```
После исполнения команды последние версии файлов из главной ветки удаленного репозитория будут загружены и помещены в новый каталог. Имя нового каталога будет соответствовать параметру REPONAME. В данном случае это javascript-data-store. В каталоге будет вся история удаленного репозитория и только что созданная главная ветка.
```

важно поинить, что эта команда работает только тогда, когда перед этим ветка была корректна merge и изменения после слияния были закоммичены.

Если нам надо принудительно удалить еще не слитую ветку, то используется принудительное удаление:
```
git branch -D <branchname>
```