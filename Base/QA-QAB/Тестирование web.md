202112060916
Tags:
___
# Тестирование web

**Тестирование веб приложений** включает:

-   [[Функциональное тестирование Functional Testing]].
-   [[тестирование безопасности Security and Access Control Testing]].
	-   нет ли у пользователей доступа к служебным/закрытым страницам
	-   проводить проверку защиты всех критически важных страниц (например, раздела администрирования сайта) от внешнего воздействия 
	-   присутствует ли в запросе токен аутентификации для авторизованных страниц
-   [[Тестирование производительности#Нагрузочное тестирование| Нагрузочное тестирование]].
-   [[Кроссбраузерное тестирование]].
-   [[Тестирование UI]]
-   [[Тестирование удобства пользования]]

Web-приложение — это [[Архитектура клиент-сервер|клиент-серверное]] приложение, в котором клиентом выступает браузер, а сервером [[Веб-сервер|web-сервер]], что уже является по сути двумя разнополыми программами, которые необходимо тестировать как отдельно, так и в связке.

**Можно выделить несколько особенностей при тестировании web-приложений:**

1. [[Тестирование web#Многопользовательская сущность web-приложений|Многопользовательская сущность web-приложений]] (разные права доступа к сайту).
2. [[Тестирование web#Локализация и интернационализация|Локализация и интернационализация]]
3. [[Тестирование web#Режим работы| Режим работы]]: логика web-приложения распределена между сервером и клиентом (хранение данных осуществляется на сервере)
4. [[Тестирование web#Структурная особенность|Структурная особенность]]: наличие отдельного сервера с базой данных
5. [[Тестирование web#Отличия формирования интерфейса|Отличия формирования интерфейса]]
6. [[Тестирование web#Особенности работы с сетью|Особенности работы с сетью]] (обмен информацией происходит по сети)
7. [[Тестирование web#Особенности запуска и остановки приложения|Особенности запуска и остановки приложения]]
8. [[Тестирование web#Особенности сбоев и отказов|Особенности сбоев и отказов]]
9. [[Тестирование web#Особенности кроссбраузерности и кроссплатформенности|Особенности кроссбраузерности и кроссплатформенности]]




## Многопользовательская сущность web-приложений
1. Одно приложение одновременно может использоваться огромным количеством людей - поэтому необходимо обязательно провести [[Тестирование производительности#Нагрузочное тестирование|нагрузочное тестирование]], чтобы оценить производительность и работоспособность приложения.
2. Каждый пользователь может иметь свои уровни доступа
3. Пользователи с одним уровнем доступа могут обращаться к одним и тем же сущностям, что приводит к конкурентному доступу

## Локализация и интернационализация
1. Необходимо проверить мультиязычный интерфейс сайта на наличие ошибок перевода, правильности почтовых адресов, имени и фамилии, валют, формата даты и времени и пр.
2. необходимо проверить, что сайт создан с учетом стандарта кодирования Unicode (который поддерживает практически все языки мира), есть возможность поддержки элементов приложения, которые невозможно локализовать стандартным образом (например, вертикально расположенные иероглифы или написание арабских предложений справа налево) и т.д.

## Режим работы
1. Использовать [[DevTools]] для проверки запросов
2. Тестирование части web-приложения, размещенной на web-сервере, можно провести и минуя графический (клиентский) интерфейс, например, когда верстка сайта еще не готова - использовать [[Postman]], [[FIDDLER]] и другие.


## Структурная особенность
1. При тестировании необходимо обращать внимание на следующие основные моменты:
		- Вносимая через интерфейс информация должна быть сохранена в базе данных в неизменном (первоначальном) виде.
		- Сохраненная в базе данных информация должна отображаться в любой части приложения одинаково (если иного не требует бизнес-логика приложения).
		- Названия таблиц и структура БД должны соответствовать проектной документации.
		- Необходимо следить за тем, чтобы запросы не обрабатывались слишком долго, а количество соединений было достаточным. Мониторинг состояния БД – один из важных моментов тестирования.
		- Стоит учитывать, что удаление записи в БД не всегда сопровождается полным удалением сущности. Иногда используется так называемое «псевдоудаление», и нужно проверить, правильно ли оно выполняется.
		- Пустую БД на тестовом стенде рекомендуется либо заполнять сгенерированными случайными данными, либо снимать дамп с продакшена и после обфускации (обезличивания) данных «заливать» их в тестируемую БД.
	2. Хорошим помощником в этом деле будет MySQL Workbench

## Отличия формирования интерфейса
Сейчас при [[Тестирование UI|тестировании UI]] web-приложения обязательно нужно обращать внимание на актуальные тенденции web-дизайна.
- Для сопоставления макета к доготовому дизайну поможет PerfectPixcel - полупрозрачное изображение макета накладывается поверх разработанного сайта и выполняется пиксельное идеальное сравнение между ними.
- Отдельно рекомендуется не забывать о всякого рода валидаторах верстки, например https://validator.w3.org/.

## Особенности работы с сетью
Особое внимание стоит обращать внимание на работу приложения:
- в различных сетях
-  при низкой скорости передачи данных (в браузер Google Chrome, например, встроена функция Throttling, которая позволяет сильно занижать скорость передачи данных)
-  в условиях потери пакетов
-  при отключении сети (способ имитации: сначала делаем скорость передачи данных с помощью Throttling минимальной, а потом прерываем сетевое соединение во время обработки запроса)
-  при доступе с разных IP адресов (в том числе не с русскоязычных)


## Особенности запуска и остановки приложения
Web-приложение запускается и останавливается по факту поступления каждого запроса, т.е. очень часто. Поэтому необходимо обращать на такие моменты, как:
- длительность запросов
- дублирование запросов
- длительность, сброс и обновление сессии при закрытии и остановки работы приложения

## Особенности сбоев и отказов
на сайте должны быть предусмотрены информационные страницы для пользователей - ошибка 404, 500 ...

## Особенности кроссбраузерности и кроссплатформенности
Смотри также [[Кроссбраузерное тестирование]].

1.  Перед началом работ рекомендуется выяснять у ответственных лиц необходимый для тестируемого ПО набор браузеров.
2.  Статистику использования браузеров можно посмотреть на ресурсе http://gs.statcounter.com/


**Что необходимо проверять при кроссбраузерном тестировании:**
- функциональные возможности продукта, реализуемые на стороне клиента;
- правильность отображения элементов графики;
- шрифты и размеры текстовых символов;
- доступность и функциональность разнообразных форм, включая их интерактивность.
	
	
**Тестирование мобильной версии приложения**
- Проверьте совместимость со смартфонами и планшетами
- Убедитесь, что навигация по сайту максимально проста
- Оптимизируйте время загрузки вашего сайта
- Убедитесь, что кнопки имеют достаточный размер для людей с большим пальцем 
- Оптимизируйте размер всех изображений 
- Не используйте Flash и всплывающие окна 
- Используйте маркеры и короткие предложения
- Убедитесь, что ваш номер телефона может быть набран с помощью одного клика
- Убедитесь, что web-сайт может получить доступ к вашему местоположению через GPS
- Проверьте, все ли умещается в разрешение экрана гаджета (на https://hotlog.ru/global/screen можно увидеть «картинку», сколько процентов пользователей имеют устройство с тем или иным количеством пикселей).

### План действий при отсутствии требований к окружению
Если на проекте не определены требования к окружению (браузеры, устройства, разрешения экрана, операционная система, среда разработки), либо определены устно и не зафиксированы в документации, то необходимо определить совместно с заказчиком и зафиксировать (в документации и/или эл.письмом) следующие пункты:
- Какие поддерживаются браузеры, их версии
- Какие поддерживаются разрешения экрана
- На какой ОС проводить тестирование
- Поддержку каких библиотек осуществляем
- Является ли верстка адаптивной
- Поддерживаем ли моб.устройства (какие ОС и их версии)



# Ссылки
___
##### Links
[[Глобальный чек-лист для Web-приложений]]
[[Вспомогательные инструменты для тестирования web-приложений ]]
[[Полезные инструменты для тестирования мобильной версии сайта]]
[[Полезные статьи по тестированию web]]



---
##### Источники
