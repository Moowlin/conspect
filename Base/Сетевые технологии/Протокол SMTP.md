202104292044
Tags:
___

**SMTP (англ. Simple Mail Transfer Protocol** — простой протокол передачи почты) — это сетевой протокол, предназначенный для передачи электронной почты между сервером отправителя и почтовым клиентом/сервером получателя

## Порты
- Порт 25 - Это стандартный порт, который по умолчанию используется для работы SMTP протокола. Иногда интернет-провайдеры закрывают к нему доступ с целью блокировки спам-рассылок.
-  Порт 465 — порт требует защищенного SSL соединения,    
-  Порт 587 — прием почты от клиентов

## Формат электронного письма
**Конверт** - тут находятся команды протокола SMTP, используется при передачи почты между серверами и почтовыми клиентами и данные в конверты определяются, как почта будет передаваться
**Заголовки** - формально не являются частью протокола SMTP, они задаются в отдельном документе RFC2822.
**Тело письма** 

Протокол SMTP, также как и протокол HTTP работает в текстовом режиме, это означает, что нет специального формата пакета, клиент и сервер взаимодействуют друг с другом в режиме запрос-ответ передавая друг другу обычные текстовые строки.

### Команды SMTP
Команды SMTP состоят из 4-х символов.

| Команда | Назначение | Пример | Описание |
| --- | --- |--- | --- |
| HELO | Установка соединения | `HELO example.com` | клиент должен указать свой домен и свой почтовый адрес |
| MAIL | Адрес отправителя | `MAIL FROM: sender@example.com` |
| RCPT | Адрес получателя | `RCTP TO: recipient@mail.ru` | Одно и то же письмо можно передать нескольким получателям для этого нужно использовать команду RCPT несколько раз |.
| DATA | Передача письма | `DATA` | сообщаем принимающему серверу, что конверт закончился и дальше пойдет письмо |
| QUIT | Выход | `QUIT` | разрыв соединения с сервером, после того, как передача письма закончена |

### Ответы SMTP
Также как и протокол HTTP, SMTP использует ответы состоящие из двух частей:
-   код сообщения, который говорит о том, что произошло;
-   текстовое сообщение поясняющее, что именно произошло и больше предназначенное для людей, чем для серверов.

*2хх* - предыдущая команда выполнена успешно
*3хх* - текущее состояние успешное, но для продолжения работы требуются дополнительные данные
>Например ответ с кодом 354 (*End data with \<CR>\<LF>.\<CR>\<LF>*) выдается после того, как клиент ввел команду DATA. Сервер приглашает клиента вводить письмо и закончить письмо строкой, где находится одна точка.

*5хх* - произошла какая-то ошибка

| Код | Назначение | Пример |
| --- | --- | --- |
| 220 | Подключение к серверу успешно | `220 smtp.example.com ECMTP Postfix` |
| 250 | Успешное выполнение предыдущей команды | `250 Hello example.com 250 Ok` |
| 354 | Начало передачи письма | `354 End data with <CR><LF>.<CR><LF>` |
| 502 | Команда не реализована | `502 5.5.2 Error: command not recognized` |
| 503 | Неправильная последовательность команд | `503 5.5.1 Error: need MAIL command` |
| 221 | Закрытие соединения | `221 2.0.0 So long, and thanks for all fish` |

### Заголовки письма
*Заголовки письма формально не являются частью стандарта SMTP.*

| Код | Назначение | 
| --- | --- |
| From: | отправитель (имя и адрес) |
| To: | Получатель |
| CC: | Получатель копии письма |
| BCC: | Получатель копии, адрес которого не должен быть показан |
| Reply-To: | Адрес для ответа |
| Subject: | Тема письма |
| Date: | Дата отправки письма |


> #### Пример сеанса SMTP
> ![[primer.jpg]]
> 1. Подключаемся к почтовому серверу по адресу **_220 smtp.example.ru ESMTP Postfix_** на 25 порт.
> 2. Выдаем команду **_HELO_** в которой указываем свой домен.
> 3. Сервер отвечает сообщением со статусом **_250_** это означает, что соединение установлено и в текстовом сообщении сервер еще раз пишет свое доменное имя.
> 4. Выдаем команду **_MAIL FROM_** для указания адреса отправителя.
> 5. Сервер отвечает сообщением со статусом **_250_**, текстовая часть сообщения **_ok_**, команда выполнена успешно.
> 6. Затем задаем адрес получателя письма с помощью команды **_RCPT TO_**.
> 7. Сервер снова отвечает сообщением **_250 ok_**
> 8. выдаем команду **_DATA_** для ввода письма.
> 9. Ответ сервера 354 приглашение вводить текст письма, которое должно закончиться отдельной строкой содержащей одну точку.
> 
> Само письмо состоит из двух частей, заголовок и тело сообщения.
> ![[primer-smtp.jpg]]
> 
> 1. Используем заголовок **_FROM_** адрес отправителя, причем указываем не только почтовый адрес, но и имя.
> 2. И заголовок **_subject_**, который используется для указания темы
> 3. Пустая строка, отделяет заголовки от тела сообщения.
> 4. Тело состоит из двух строк **_Hello, email world_**! и **_Hello, SMTP_**!
> 5. Завершается письмо строкой в которой находится одна точка, эта строка не является частью письма и будет удалена при передаче.
> 6. После того, как введена точка, сервер понимает, что письмо закончено и выдает сообщение со статусом **_250 2.0.0 Ok: queued as 7FD9DC2E0060_** сообщение поставлено в очередь для передачи.
> 7. Выдаем команду QUIT, чтобы закончить сеанс связи. Сервер отвечает сообщением со статусом 221 пока.


## Расширение SMTP - ESMTP
- Вместо команды HELO предлагается использовать команду EHLO — Extended HELO.
- Команда STARTTLS используется для того, чтобы начать зашифрованное соединение.
- SIZE может использоваться для того, чтобы узнать максимальный размер письма, который принимает почтовый сервер.
- DSN применяется, чтобы получить подтверждение о доставки письма.


## Безопасность и спам
Протокол SMTP не содержит механизмов для защиты данных.

По умолчанию, протокол SMTP не использует шифрование и все письма, которые передаются через интернет могут быть прочитаны. В расширенной версии протокола SMTP появилась возможность использовать шифрование с помощью команды STARTTLS, но эту возможность мало кто использует.

Протокол SMTP не содержит никаких механизмов защиты от спама, но современные почтовые серверы пытаются использовать внешние механизмы.

Многие почтовые серверы настроены так, чтобы принимать почту только для локальных пользователей, т.е. для тех, у которых есть почтовые ящики в том домене, который они обслуживают. Серверы, которые работают в другом режиме и позволяют передавать почту на любые email адреса в интернете называются открытые релеи. Спамеры с помощью специальных программ ищут открытые релеи в интернете и используют их с помощью массовой рассылки писем. Если почтовый сервер работает в режиме открытого релея, это серьезная недоработка администратора этого сервера.

Также есть возможность проверки адреса отправителя с помощью цифровой подписи, для этого также используются взаимодействия с системой DNS. В DNS записях специального вида хранится открытый ключ электронной подписи для данного домена и этот открытый ключ можно использовать для проверки подлинности адреса отправителя.



# Ссылки
___
##### Links
[[Электронная почта]]

---
##### Источники
[Видеолекция по протоколу передачи электронной почты SMTP](https://www.youtube.com/watch?v=xUTmwcSDvSE)
[Протокол SMTP что такое и для чего он нужен](https://zvondozvon.ru/tehnologii/protokoli/smtp)