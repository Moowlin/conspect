202111291601
Tags:
___
# Основы Git
**Git** - это консольная утилита, для отслеживания и ведения истории изменения файлов, в вашем проекте.
 **Репозиторий** - хранилище проекта и истории его изменений. 
 
 Git работает локально и все репозитории хранятся в определенных папках на жестком диске. А можно и в интернете:
-   [GitHub](https://github.com/)
-   [Bitbucket](https://bitbucket.org/)  
-   [GitLab](https://gitlab.com/)

Коммит (commit) - каждая точка сохранения проекта. У каждого commit есть *hash* (уникальный id) и *комментарий*.
Из commit-ов собирается ветка. *Ветка* - это история изменений. У каждой ветки есть *название*. Репозиторий может содержать несколько веток.

## Установка, настройка, создание репозитория

```bash
#установка:
sudo pacman install git

#Установим имя для вашего пользователя 
#Вместо <ваше_имя> можно ввести, например, Grisha_Popov 
#Кавычки оставляем 

git config --global user.name "<ваше_имя>" 

#Теперь установим email. Принцип тот же. 
git config --global user.email "<адрес_почты@email.com>"

cd <путь_к_вашему_проекту> 

#Инициализация/создание репозитория 
git init

#Добавим все файлы проекта в нам будующий 
commit git add . 
#Или так git add --all 
#Если хотим добавить конкретный файл то можно так 
git add <имя_файла> 
#Теперь создаем commit. Обязательно указываем комментарий. 
#И не забываем про кавычки 
git commit -m "<комментарий>"
```

> Чаще всего commit создают, когда:
> -  Создан новый функционал
> -  Добавлен новый блок на верстке
> -  Исправлены ошибки по коду
> -  Вы завершили рабочий день и хотите сохранить код

> Это поможет держать вашу ветки в чистоте и порядке. Тем самым, вы будете видеть историю изменений по каждому нововведению в вашем проекте, а не по каждому файлу.

При инициализации git в текущем каталоге создается новый подкаталог *.git* со следующи мсодеражнием:
- *config* - содержатся настройки git репозитория
- *description* - предназначен для GitWeb и содержит в себе информацию о проекте (название проекта и его описание). GitWeb - это веб интерфейс, написанный для просмотра Git репозитория используя веб-браузер. Если вы не пользуетесь GitWeb, то это не столь важно.
- *hooks* - предоставляет набор скриптов, которые могут автоматически запускаться во время выполнения git команд. В некоторых случаях это значительно упрощает разработку. Например, вы можете написать скрипт, который будет редактировать сообщение коммита согласно вашим требованиям.
- *info - exclude* - Каталог info содержит файл exclude, в котором можно указывать любые файлы, и Git не станет добавлять их в свою историю. Это почти то же самое что и .gitingnore (возможно вы сталкивались с ним. Его можно найти в корневом каталоге вашего проекта), за тем исключением, что exclude не сохраняется в истории проекта, и вы не сможете им поделиться с другими.
- *refs* - хранит в себе копию ссылок на объекты коммитов в локальных и удаленных ветках
- *logs* - хранит в себе историю проекта для всех веток в вашем проекте
- *objects* - Каталог objects хранит в себе BLOB объекты, каждый из которых проиндексирован уникальным SHA
- *index* - Промежуточная область с метаданными, такими как временные метки, имена файлов, а также SHA файлов, которые уже упакованы Git. В эту область попадают файлы, над которыми вы работали, при выполнение команды `git add`.
- *HEAD* - Файл содержит ссылку на текущую ветку, в которой вы работаете
- *ORIG_HEAD* - Каждый раз во время слияния в этот файл попадает SHA ветки, с которой проводилось слияние
- *FETCH_HEAD* - Файл хранит в себе ссылки в виде SHA на ветки, которые участвовали в `git fetch`
- *MERGE_HEAD* - Файл хранит в себе ссылки в виде SHA на ветки, которые участвовали в `git merge`
- *COMMIT_EDITMSG* - Файл содержит в себе последнее введенное вами сообщение коммита



___
##### Links
[[Основные команды]]
[[gitflow]]
https://habr.com/ru/post/60347/
https://www.atlassian.com/ru/git/tutorials
---
##### Источники
https://learngitbranching.js.org/?locale=ru_RU