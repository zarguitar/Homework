![Logo](accidentallyinspiredmusic.png)
# Работа с GIT

## 1. Проверка наличия установленного Git
В терминале выполнить команду `git version`.
Если Git установлен, появится сообщение с информацией о версии программы, иначе будет сообщение об ошибке.

## 2. Установка Git
Загружаем последнюю версию Git с сайта https://git-scm.com/downloads
Устанавливаем с настройками по умолчанию.

## 3. Настройка Git
При первом использовании Git необходимо представиться. Для этого нужно ввести в терминале 2 команды:
```
git config --global user name "Имя пользователя"
git config --global user email "почта@pochta.com"
```
## 4. Инициализация репозитория
Получить репозиторий можно двумя способами.
1. В терминале переходим к папке, в которой хотим создать репозиторий. Выполняем команду:
```
git init
```
2. Клонировать существующий репозиторий из любого места. Сделать это можно так:
```
git clone <адрес репозитория>
```

## 5. Запись изменений в репозиторий
Каждый файл в репозитории может находиться в одном из двух состояний: под версионным контролем (отслеживаемый) и нет(неотслеживаемый).

Отслеживаемые файлы могут быть измененными, неизмененными или подготовленные к коммиту.

Чтобы отобразить состояние рабочего каталога и раздела проиндексированных файлов нужно выполнить команду `git status`.
С ее помощью можно проверить индексацию изменений и увидеть 
файлы, которые не отслеживает Git.

Далее выполняем команду `git add`, чтобы перенести ожидающие изменения из рабочего каталога в раздел проиндексированных файлов.

Для фиксирования индексированных изменений в репозиторий Git выполним команду `git commit`.

Для инициализации функции сравнения источников данных Git - коммитов, веток, файлов и т.д. нужно выполнить команду `git diff`.

## 6. Просмотр истории коммитов
Чтобы вывести список коммитов, созданных в данном репозитории в обратном хронологическом порядке, выполняем команду `git log`.
Данная команда перечисляет коммиты с их хэш-кодами, именем и электронной почтой автора, дата создания и сообщением коммита.

## 7. Перемещение между сохранениями (коммитами)
Команда `git checkout` позволяет перемещаться между ветками, созданными командой `git branch`. При переключении ветки происходит обновление файлов в рабочем каталоге в соответствии с версией, хранящейся в этой ветке, а Git начинает записывать все новые коммиты в этой ветке.

## 8. Игнорирование файлов
Если есть файлы, которые по какой-то причине не должны попадать в коммиты, то нужно создать специальный файл 
```
.gitignore
```
в нём мы прописываем имена файлов, или же расширения файлов которые должны быть проигнорированы.

## 9. Работа с ветвлениями
Для того, чтобы создать новую ветку вводим:
```
git branch <название ветки>
```
или
```
git checkout -b <название ветки>
```
в последнем случае мы сразу переключаемся на данную ветку и начинаем работать в ней.

Команда 
```
git merge
```
 берет все изменения из той или иной ветки и позволяет добавить их в текущую.

 Иногда при слиянии возникают конфликты. Например, когда в двух ветках были изменения в одной и той же строчке кода, то необходимо разрешить конфликт вручную, или выбрать варианты разрешения, которые предложит сама программа с помощью специальной цветовой подсветкой. И далее необходимо выполнить коммит слияния с помощью знакомых нам команд `git add` и `git commit`.

 С помощью команды:
 ```
 git branch -d
 ```
 ветку можно удалить.
 При попытке удаления ветки с внесенными изменениями и не слитой с основной веткой, программа не даёт ее удалить сразу, а требует уточнения в виде команды:
 ```
 git branch -D
 ```
выполнив которую, ветку можно удалить принудительно, если вы убедились что удаляете ненужную вам информацию.

# Работа с удаленными репозиториями

1. Создать аккаунт на Github
2. Создать локальный репозиторий
3. Создать удаленный репозиторий
4. Связать удаленный репозиторий с локальным

Добавить удаленный репозиторий к проекту:

`git remote add origin <имя для репозитория> <адрес репозитория>`

С помощью команды 
```
git remote
```
проверяем, произошла ли привязка.

Команда 
```
git remote -v
```
показывает адреса для получения изменений из удаленного репозитория (`fetch`) и для отправки (`push`)

Далее нужно переименовать текущую ветку в `main`, т.к. ветки должны быть одноименными, чтобы выполнять обмен данными, для этого выполняем команду
```
git branch -M main
```

Связываем локальную ветку `main` с удаленной веткой `main`:
```
git push -u origin main
```
или если мы забыли выполнить эту команду перед отправкой из локального репозитория в удаленный, то программа подскажет нам выполнить аналогичную команду, но чуть более длинную:
```
git push --set upstream origin main
```
Для получения и слияния изменений из удаленного репозитория используется команда
```
git pull
```

 Попутно можно прописать любой код (псевдокод):
```C#
int count = 0;
while(count <= n)
{
count ++;
}
```

Отправить изменения из локального репозитория в удаленный:
```
git push
```
![Logo](pr-mid.jpg)
# Репозиторий для pull request

1. Чтобы выполнить `pull request`, в своём аккаунте на GitHub нужно создать локальную копию репозитория из другого аккаунта с помощью кнопки **Fork**
При копировании чужого репозитория его имя можно изменить.
2. Далее копируем его адрес из HTTPS. Делаем копию репозитория на локальный компьютер, перед этим убедившись что мы находимся в нужной директории - для этого выполним команду
```
cd <название директории>
```
или если нужно вернуться к исходному репозиторию, то
```
cd ..
```
и выполняем `git clone`. Затем переходим в директорию клонированного репозитория, снова выполнив команду `cd`.

3. Создаем новую ветку с помощью знакомой команды `git branch <название ветки>` и в нее вносим свои изменения. 

4. Снова проверяем командой `git remote -v` есть ли связь. И фиксируем изменения классическими командами `git add` и `git commit`.

5. Выполняем 
```
git push
```
тем самым отправляя все изменения в GitHub.
Если имена локальной ветки и ветки на удаленном репозитории не совпадают, то программой снова будет предложено выполнить команду
```
--set upstream origin <название ветки>
```
6. Заходим в GitHub и находим копию нужного репозитория.
Если появилась кнопка **Compare & pull request**, то выбираем её.

Если кнопка не появилось, то идём во вкладку *pull requests*, и жмём на **new pull request**

Сравнивая ветки, убедимся что слияние возможно (*Able to merge*)

Можно добавить любую информацию, например, название последнего коммита и комментарии к нему; и нажимаем на **Create pull request**
Проверяем наличие зеленых галочек и сообщений об отсутствии конфликтов.

Если все в порядке, то автор сможет изучить все изменения, скопировав их себе на локальный компьютер и потом принять решение о возможном слиянии.



