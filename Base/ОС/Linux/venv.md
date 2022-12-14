202102031114
Tags: #Python3 #Linux  
___
## Использование virtualenv

*Virtualenv* - утилита, позволяющая создавать изолированные виртуальные окружения для Python. По сути, внутри проекта создаёт каталог, куда кладётся нужная версия Python и необходимые пакекты.
Виртуальная среда обеспечивает изолировнноае пространство для проектов Python на сервере, то есть все необходимые зависимости копируются в некоторый выбранный каталог, а приложение испотзует их, а не установленные в системе.

#### Установка

	$ sudo pip install virtualenv
	$ virtualenv --version
#### Создание окружения
Переходим в диреторию, где будут хранится среды и создаем среду

	$ cd /home/dmrlx/Projects/my_project
	$ virtualenv venv --python=python3.8
	
>“venv” в данном случае — это название директории, в которой будет развёрнуто ваше виртуальное окружение, по сути его имя. Часть после “venv” вообще можно опустить. В этом случае виртуальное окружение установится с той версией, которая задана у вас в системе по умолчанию.
#### Активация

	$ source venv/bin/activate
#### Работаем как обычно
Например, вам нужно установить некоторое количество пакетов, чтобы использовать в вашем фреймворке. Возьму что-нибудь из своих рабочих: paramiko, pycodestyle, pydocstyle, pylint, pytest, pytest-html, requests, SQLAlchemy. Устанавливаем (здесь “(venv) $” обращает внимание, что мы выполняем операцию с активированным виртуальным окружением):

	(venv) $ pip install paramiko pycodestyle pydocstyle pylint pytest pytest-html requests SQLAlchemy
Когда процесс установки завершится, мы можем поглядеть список установленых пакетов:

	(venv) $ pip list
Их будет больше, чем мы устанавливали, т.к. большинство из них подтянет свои зависимости + что-то устанавливается, когда вы только создаёте окружение.

Теперь вы работаете, пишете код, устанавливаете в ваше виртуальное окружение ещё какие-то пакеты. Снова пишете. Снова устанавливаете…
#### Перенос окружения
Для начала делаем “слепок” списка пакетов с их версиями:

	(venv) $ pip freeze > requirements.txt

>где
pip freeze — команда, которая выводит список всех установленных пакетов с их версиями\> — символ перенаправления выводаrequirements.txt — имя файла, куда мы складываем список пакетов из pip freeze; можно назвать иначе, но так принято )

>Файл “requirements.txt” можно и нужно хранить в корне вашего проекта (прямо в директории my\_project) и отдавать его в продакшн вместе с кодом. Это хороший тон. А вот класть в репозиторий папку с вашим виртуальным окружением — моветон и “так уже не носят”. Чтобы избежать этого, можете использовать файл [.gitignore](https://ru.hexlet.io/courses/git_base/lessons/git_gitignore/theory_unit).

Итак, вы скачали файл requirements.txt вместе с вашим репозиторием на новую машину, и теперь вам нужно развернуть точно такое же окружение, какое было у вас на рабочей системе. Для этого вы по очереди выполняете команды из этого мануала, чтобы создать виртуальное окружение:

	$ sudo pip install virtualenv  
	$ cd <путь\_к\_репозиторию>  
	$ virtualenv venv --python=<ваша\_версия\_python>  
	$ source venv/bin/activate
и теперь устанавливаете необходимые вам пакеты, используя requirements.txt:

	$ pip install -r requirements.txt
#### Декативация окружения

	$ deactivate



___
##### Links
- [[Установка Python 3 в CentOS]]
- [[00 Linux]]

---
##### Источники
- https://medium.com/@dmrlx/%D0%B8%D1%81%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-virtualenv-b6e56696eb58