202106301526
Tags:
___
#  Описание
Синтаксис достаточно прост:
`$ sudo nslookup опции домен сервер`

[[Система доменных имен DNS | Домен]] - это то доменное имя, для которого необходимо посмотреть информацию, а сервер - необязательный параметр, который указывает, что нужно использовать другой dns сервер. 

==Опции:==
-   **-type** - тип информации, которую хотим получить, возможные типы: txt, soa, ptr, ns, mx, mr, minfo, mg, mb, hinfo, gid, cname, a, any;
-   **-port** - другой порт DNS сервера;
-   **-recurse** - использоваться другие DNS серверы, если на этом нет ответа;
-   **-retry** - количество попыток получить нужную информацию;
-   **-timeout** - время между попытками запросов к серверу;
-   **-fail** - пробовать другой сервер имен, если этот вернул ошибку.

SOA или Start Of Authority предоставляет техническую информацию о домене, для получения этого поля используйте тип запроса soa:
 `nslookup -type=soa losst.ru`

Здесь будет выведена такая информация:
-   **origin** - происхождение полученной информации;
-   **mail addr** - адрес электронной почты администратора домена;
-   **serial** - время с момента последнего обнволения домена в формате timestamp;
-   **refresh** - количество секунд, с момента последнего обновления, когда его нужно повторить;
-   **retry** - количество секунд, через которое нужно повторить попытку подключения, если DNS сервер недоступен;
-   **expire** - количество секунд, по истечении которых полученная от первичного DNS информация будет считаться устаревшей;
-   **minimum** - минимальное количество секунд до следующего обновления.


___
##### Links


---
##### Источники
[КАК ПОЛЬЗОВАТЬСЯ NSLOOKUP](https://losst.ru/kak-polzovatsya-nslookup)