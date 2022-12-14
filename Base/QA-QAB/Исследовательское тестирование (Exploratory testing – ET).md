202204041934
Tags:
___
# Основные определения
**Исследовательское тестирование** - это тестирование без предварительно подготовленных сценариев, включающее в себя одновременное изучение программного продукта, проектирование тестов и их выполнение.

**Когда следует применять исследовательское тестирование**
1. Когда нужно обеспечить быструю обратную связь для нового продукта или новой функциональности продукта.
2. Когда нужно быстро ознакомиться с продуктом.
3. Когда уже были проведены основные виды тестирования и время позволяет разнообразить методы тестирования.
4. Когда нужно найти дефект, локализованный в определенном модуле в кратчайшие сроки.
5. Когда проверяется работа другого специалиста по тестированию.
6. Когда нужно изучить состояние конкретного риска для принятия решения о необходимости покрытия конкретной области тестами.

**Преимущества:**
1. Рождает идеи для новых тест-кейсов.
2. Отлично подходит для проектов без четко описанных требований.
3. Экономит время за счет отсутствия формализованной тестовой документации.
4. Находит ошибки, в то время, как сценарное тестирование может только подтвердить их отсутствие.
5. Ограничено только фантазией QA- специалиста.

**Недостатки:**
1. Полностью опирается на опыт QA- специалиста.
2. Требует от QA- специалиста творческого, нестандартного мышления.
3. По сравнению со сценарным тестированием, процесс почти не контролируется.
4. Тест-кейсы сложно поделить между различными QA- специалистами или командами.
5. Важные кейсы могут остаться не пройденными.
6. Сложно оценить процент покрытия проекта тестированием и понять, какая часть уже протестирована.

**Примеры ошибок при использовании этой техники**
1. Потеря сценария, если он не обнаружил багов.
2. Бесконечное тестирование.

Примерный алгоритм использования техники:
1. Изучаем продукт, разрабатываем и выполняем тесты одновременно.
2. Записываем идеи тестов и используем их в дальнейшем.
3. Если времени на прохождение тестов нет, нужно выбирать наиболее критичные области приложения, которые реально протестировать за имеющееся время.
4. Записываем выполненные тест-кейсы для того, чтобы иметь возможность воспроизводить найденные ошибки и определять тестовое покрытие приложения. Нет времени на кейсы – пишем чек-лист!

> Сценарное и исследовательское тестирование – невзаимоисключающие. Они являются полностью совместимыми икомпенсируют недостатки друг друга. Особенно, если хочется убедиться в том, что ничего не было упущено.

### Методика систематического поиска багов по Джеймсу Уиттакеру (James A. Whittaker)

**Методика туров**
Приложение — незнакомый город.  
Тестировщик — турист.

**Как пользоваться методикой**
1. Выбрать тур из списка ниже.  
2. Изучить его цели.  
3. Поставить таймер на 2 часа (час, полчаса).  
4. Провести исследование системы строго по целям тура. Ни на что не отвлекаясь, только “миссия” тура.  
5. При необходимости повторить.


####  [[Туры по деловому центру (Tours of the Business District)]]
Деловой центр — это те функции, ради которых пользователи покупают и используют приложение. Это те killer-feature, которые описывают маркетологи, и которые упомянет любой из ваших пользователей при опросе, зачем им ваше приложение.

>Тур по деловому центру фокусирует внимание на главных частях вашего приложения и показывает сценарии их использования вашими клиентами.

#### [[Туры по историческим районам, Tours Through the Historical District]]
В ПО исторические районы могут быть также слабо соединены, как в Бостоне или сосредоточены в одном месте, как в Кёльне. Исторические районы в ПО представляют собой:

-   унаследованный код (legacy code);
-   функции, созданные в предыдущих версиях;
-   исправления багов.
    
Последние особенно важны, потому что баги существа социальные и любят скапливаться в одном месте. Бажные секции в коде надо тестировать особенно тщательно.
Туры по историческим районам проверяют старую функциональность и исправления ошибок.


#### [[Туры по развлекательным районам, Tours Through the Entertainment District]]
Например, деловой район для текстового редактора — набор функций для создания документа, подготовки текста, вставки графики, таблиц и рисунков. Развлекательный район — функции для разметки страницы, форматирования, изменения фона. Другими словами, работа заключается в создании документа, а развлечение — в наведении красоты.

Туры по развлекательным районам исследуют скорее второстепенные, нежели основные функции, и убеждаются, что они дополняют друг друга без противоречий.

#### [[Туры по туристическим районам, Tours Through the Tourist District]]
Туры по туристическим районам имеют несколько разновидностей. Это и короткие забеги для покупки сувениров, аналог кратких тест-кейсов для тестирования специфичных функций. Это и длинные поездки для посещения списка мест, которые хочется увидеть. Эти туры не о том, как заставить приложение работать, они о том, как посетить функциональность быстро… только чтобы сказать “мы тут были”!


#### [[Туры по отельным районам, Tours Through the Hotel District]]
Отель — убежище для туриста. Это место, куда можно сбежать из давки и суеты популярных мест для небольшого отдыха и расслабления.  
Сюда приходит тестировщик, уйдя от главной функциональности, чтобы потестировать второстепенные или сопутствующие основным фичам функции, которые часто игнорируются в тест-плане.

#### [[Туры по захудалым районам, Tours Through the Seedy District]]
Для тестировщика обязателен тур по этим районам для выявления тех опасностей, которые могут подстерегать пользователей продукта. Для тура отлично подойдут входные данные, ломающие приложение или способные каким-либо образом ему навредить.



# Ссылки
___
##### Links
https://software-testing.ru/library/testing/other-testing/2890-pathway-exploratory-testing

---
##### Источники
