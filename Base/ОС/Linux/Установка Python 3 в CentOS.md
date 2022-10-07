202102021608
Tags: #Python3 #Linux
___
#### Обновление программного обеспечения
В системе CentOS7 Python3 и Python2 должны установлены. так что только обновляемся:

	sudo yum update -y python36 python2
Флаг `-y` автоматически подтвердит любые запросы системы.
Если в сиетме не установлены Python 2.7 или Python 3.6,то устанавливаем:

	sudo yum install -y python2
	sudo yum install -y python36
#### Проверка версий
	python3 -V
#### Установка pip
Диспетчер пакетов Python <span style="color:red">*pip*</span> - инструмент, который помогает устанавливать необходимые для проекта библиотеки и модули и упралять ими.

	sudo yum install -y python3-pip
Установка пакета Python3 теперь:

	pip3 install имя_пакета
#### Установка [[venv]]
Используем модуль venv, часть стандартной библиотеки Python3

	sudo yum install -y python36-virtualenv

####  Создание виртуальной среды для приложения
Сначала создаём директорию, где хотим разместить все среды программирования. Для создания среды переходим в созданную директорию и создаем среду с именем, например, my_env

	mkdir myapp && cd myapp
	python3 -m venv my_env

#### Активация окружения виртуальной среды
Для этого введите следующую команду, вызывающую скрипт **activate** в директории `bin`:

	source my_env/bin/activate
В командной строке теперь будет отображаться имя вашей среды, в данном случае `my_env`:

	(my_env) [test_admin1@localhost myapp]$
Префикс сообщает нам, что среда `my_env` активна и что при создании программ они будут использовать настройки и пакеты этой конкретной среды.

>***Примечание.*** В виртуальной среде Python 3 вы можете использовать команду `python` вместо `python3` и `pip` вместо `pip3`. Если вы используете Python 3 или pip3 на компьютере вне среды, вы можете использовать только команды `python3` и `pip3`.
#### Тестирование виртуальной среды
Запустите интерпретатор Python и Воспользуйтесь функцией `print()`, чтобы создать стандартную программу «Hello, World»:

	(my_env) [test_admin1@localhost myapp]$ python
	Python 3.6.5 (default, Aug 24 2020, 17:57:11)
	[GCC 8.3.1 20191121 (Red Hat 8.3.1-5)] on linux
	Type "help", "copyright", "credits" or "license" for more information.
	>>> print("Hello, World!")
	Hello, World!
	>>> quit()
##### Декативация виртуальной среды
	(my_env) [test_admin1@localhost myapp]$ deactivate

___
##### Links
- [[venv]]
- [[00 Python]]
- [[00 Linux]]
---
##### Источники
- https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-programming-environment-on-centos-8-ru
- https://netpoint-dc.com/blog/python-3-venv-centos7/