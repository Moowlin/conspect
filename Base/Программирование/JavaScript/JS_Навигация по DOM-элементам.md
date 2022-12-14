202211062054
Tags:
___
# Навигация по DOM-элементам

DOM позволяет нам делать что угодно с элементами и их содержимым, но для начала нужно получить соответствующий DOM-объект.

Все операции с DOM начинаются с объекта `document`. Это главная «точка входа» в DOM. Из него мы можем получить доступ к любому узлу.

Так выглядят основные ссылки, по которым можно переходить между узлами DOM:
![[ссылки страницы.png]]

## Сверху: documentElement и body
Самые верхние элементы дерева доступны как свойства объекта `document`:
`<html>` = `document.documentElement`

Самый верхний узел документа: `document.documentElement`. В DOM он соответствует тегу `<html>`.
`<body>` = `document.body`

Другой часто используемый DOM-узел – узел тега `<body>`: `document.body`.
`<head>` = `document.head`

Тег `<head>` доступен как `document.head`.


>**Есть одна тонкость: `document.body` может быть равен `null`**
>Нельзя получить доступ к элементу, которого ещё не существует в момент выполнения скрипта.
>В частности, если скрипт находится в `<head>`, `document.body` в нём недоступен, потому что браузер его ещё не прочитал.
>Поэтому, в примере ниже первый `alert` выведет `null`:
```HTML
<html>
<head>
  <script>
    alert( "Из HEAD: " + document.body ); // null, <body> ещё нет
  </script>
</head>
<body>
  <script>
    alert( "Из BODY: " + document.body ); // HTMLBodyElement, теперь он есть
  </script>
</body>
</html>
```


>**В мире DOM `null` означает «не существует»**
>В DOM значение `null` значит «не существует» или «нет такого узла».


## Дети: childNodes, firstChild, lastChild
Здесь и далее мы будем использовать два принципиально разных термина:

-   **Дочерние узлы (или дети)** – элементы, которые являются непосредственными детьми узла. Другими словами, элементы, которые лежат непосредственно внутри данного. Например, `<head>` и `<body>` являются детьми элемента `<html>`.
-   **Потомки** – все элементы, которые лежат внутри данного, включая детей, их детей и т.д.

В примере ниже детьми тега `<body>` являются теги `<div>` и `<ul>` (и несколько пустых текстовых узлов):
```html
<html>
<body>
  <div>Начало</div>

  <ul>
    <li>
      <b>Информация</b>
    </li>
  </ul>
</body>
</html>
```
…А потомки `<body>`– это и прямые дети `<div>`, `<ul>` и вложенные в них: `<li>` (потомок `<ul>`) и `<b>` (потомок `<li>`) – в общем, все элементы поддерева.

**Коллекция `childNodes` содержит список всех детей, включая текстовые узлы.**

Пример ниже последовательно выведет детей `document.body`:
```html
<html>
<body>
  <div>Начало</div>

  <ul>
    <li>Информация</li>
  </ul>

  <div>Конец</div>

  <script>
    for (let i = 0; i < document.body.childNodes.length; i++) {
      alert( document.body.childNodes[i] ); // Text, DIV, Text, UL, ..., SCRIPT
    }
  </script>
  ...какой-то HTML-код...
</body>
</html>
```

Обратим внимание на маленькую деталь. Если запустить пример выше, то последним будет выведен элемент `<script>`. На самом деле, в документе есть ещё «какой-то HTML-код», но на момент выполнения скрипта браузер ещё до него не дошёл, поэтому скрипт не видит его.

**Свойства `firstChild` и `lastChild` обеспечивают быстрый доступ к первому и последнему дочернему элементу.**

Они, по сути, являются всего лишь сокращениями. Если у тега есть дочерние узлы, условие ниже всегда верно:

```javascript
elem.childNodes[0] === elem.firstChild
elem.childNodes[elem.childNodes.length - 1] === elem.lastChild
```
Для проверки наличия дочерних узлов существует также специальная функция `elem.hasChildNodes()`.


# Ссылки
___
##### Links


---
##### Источники
https://learn.javascript.ru/dom-navigation