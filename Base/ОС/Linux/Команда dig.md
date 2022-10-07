202106301602
Tags:
___
# Описание
==Dig (Domain Information Groper)== – мощный инструмент командной строки для запросов к именам DNS-серверов.С помощью команды **dig** Вы можете запросить информацию о доменном имени у DNS-серверов

По-умолчанию при обычном запросе выводятся А записи, как показано ниже в выводе
```shell
$ dig google.com

; <<>> DiG 9.11.3-1ubuntu1.11-Ubuntu <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 35727
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             73      IN      A       172.217.16.142

;; Query time: 16 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Sun Jan 05 12:00:54 +03 2020
;; MSG SIZE  rcvd: 55
```
Команда dig содержит следующие секции:

`Заголовок (Header)`: Здесь отображается версия dig, глобальные параметры, используемые командой dig, и несколько дополнительных сведений о заголовке.  
`Секция запроса (QUESTION SECTION)`: Отображает вопрос, который он задал DNS. То есть это Ваш запрос.  
`Секция ответа (ANSWER SECTION)`: Отображает ответ, который он получает от DNS. A записи в нашем случае.  
`Секция полномочий (AUTHORITY SECTION)`: Здесь отображается сервер DNS, который имеет полномочия отвечать на этот запрос. Отображает доступные NS серверы для google.com в нашем случае.  
`Секции дополнительные (ADDITIONAL SECTION)`: Здесь отображается IP адреса серверов имен, перечисленных в разделе полномочия.  
`В секции Статистика (Stats section)` внизу отображается немного информации о команде dig включая сколько времени потребовалось для выполнения этого запроса.

Можно отключать разные секции этими параметрами:
`+nocomments` – отключить комментарии  
`+noauthority` – отключить AUTHORITY SECTION  
`+noadditional` – отключить ADDITIONAL SECTION  
`+nostats` – отключить Stats section  
`+noanswer` – отключить ANSWER SECTION (но нам это не надо, конечно)
>Вместо отключения каждой секции мы можем отключить все с помощью `+noall` и включить только секцию ответа `+answer`

___
##### Links


---
##### Источники
[Dig — команда Linux (DNS Lookup)](https://unlix.ru/dig-%D0%BA%D0%BE%D0%BC%D0%B0%D0%BD%D0%B4%D0%B0-linux-dns-lookup/)
[Как использовать команду Dig для запроса DNS в Linux](https://andreyex.ru/linux/komandy-linux-i-komandy-shell/kak-ispolzovat-komandu-dig-dlya-zaprosa-dns-v-linux/)