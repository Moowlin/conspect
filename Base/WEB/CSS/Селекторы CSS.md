202205092306
Tags:
___
# CSS селекторы, свойства, значения
Каскадная таблица стилей состоит из CSS правил. Каждое CSS _правило_ состоит из _селектора_ и _блока декларации_.

![[img_selector.jpg]]

CSS _селекторы_ очень похожи на HTML _теги_. Селектор указывает на [[Элементы и теги в HTML5|HTML элемент]], для которого вы определяете визуальный стиль.

_Блок декларации_ содержит одну или несколько деклараций свойств, разделенных точкой с запятой. Блок деклараций заключают в фигурные скобки.

Каждая декларация состоит из имени _свойства_ и его _значения_, разделенных двоеточием.

_Свойства_ – это ключевые слова, такие как `color`, `font-weight` или `background-color`, которым присвоены определенные значения:

```css
body {
   font-size: 0.8em;
   color: navy;
}
```
В данном примере создается CSS селектор `body`, который соотносится с HTML тегом `<body>`. В этом селекторе определяется два свойства – `font-size` и `color`, которым присваиваются соответствующие значения. Таким образом, если этот стиль подключить к HTML документу, то текст внутри элемента `<body>` (что на самом деле весь контент в основном окне браузера) будет отображаться шрифтом размером 0.8em и темно-синим цветом.

## Категории CSS селекторов

CSS селекторы можно разделить на пять категорий:
- [[Простые селекторы]] (элементы отбираются по имени, идентификатору или классу)
- [[Комбинированные селекторы]] (элементы отбираются по специфическим отношениям между ними)
- [[Селекторы псевдоклассов]] (элементы отбираются по определенному состоянию)
- [[Селекторы псевдоэлементов]] (отбирается и стилизуется часть элемента)
- [[Селекторы атрибутов]] (элементы отбираются по атрибутам или значениям атрибутов)

# Группирование селекторов
Группирование селекторов позволяет объединить одно и то же определение стиля для нескольких HTML элементов в одну декларацию.

Посмотрите на следующий код CSS (для элементов h1, h2 и p заданы одинаковые стили):

```css

h1 {
  text-align: center;
  color: red;
}

p {
  text-align: center;
  color: red;
}

h2 {
  color: green;
}

.thisOtherClass {
   color: green;
}

.yetAnotherClass {
   color: green;
}
```

Чтобы уменьшить количество кода, мы можем сгруппировать эти селекторы в одну декларацию.

Чтобы сгруппировать селекторы, нужно в головной части перечислить их через запятую.

В следующем примере мы группируем селекторы из предыдущего примера:

```css
h1, p {
  text-align: center;
  color: red;
}

h2, .thisOtherClass, .yetAnotherClass {
   color: green;
}
```







# Базовые селекторы
К базовым селекторам можно отнести селектор по [[Селекторы CSS#Селектор по элементу тегу|тегу]], [[Селекторы CSS#Селектор по классу|классу]], [[Селекторы CSS#Селектор по идентификатору id|идентификатору]], [[Селекторы CSS#Селектор по атрибуту|атрибуту]] и [[Селекторы CSS#Универсальный селектор|универсальный селектор]].


### Селектор по атрибуту
Не самый популярный селектор, но иногда он полезен:

```css
<button data-my-custom-attribute="my-custom-value">
 Нажми на меня
</button>
```

 Имя и значение атрибута пишется в квадратных скобках. Работает с любым атрибутом:

```css
[data-my-custom-attribute="my-custom-value"] {
   color: red;
}
```

Селекторы по атрибуту предназначены для выбора элементов по имени атрибута и (или) его значению.

Типы селекторов по атрибуту:

-   `[attr]` – по имени атрибута;
-   `[attr=value]` – по имени и значению атрибута;
-   `[attr^=value]` – по имени и значению, с которого оно должно начинаться;
-   `[attr|=value]` – по имени атрибута и его значению, которое равно `value` или начинается со `value-`;
-   `[attr$=value]` – по имени атрибута и значению, на которое оно должно заканчиваться;
-   `[attr*=value]` – по указанному атрибуту и значению, которое должно содержать `value`;
-   `[attr~=value]` – по имени атрибута и значению, которое содержит `value` отделённое от других с помощью пробела.

#### [attr]

Пример задания правила для всех элементов на странице, имеющих атрибут `target`:

```css
/* селектор [target] выберет все элементы на странице, имеющих атрибут target */
[target] {
  background-color: red;
}
```

#### [attr=value]

Пример задания правила для всех элементов на странице, имеющих атрибут `rel` со значением `nofollow`:

```css
/* селектор [rel="nofollow"] выберет все элементы на странице, имеющих атрибут rel со значением nofollow */
[rel="nofollow"] {
  background-color: green;
}
```

#### [attr^=value]

Пример задания правила для всех элементов на странице, имеющих атрибут `class`, значение которого начинается с `col`:

```css
/* селектор [class^="col"] выберет все элементы на странице, имеющих атрибут class, значение которого начинается с col */
[class^="col"] {
  background-color: yellow;
}
```

#### [attr|=value]

Пример задания правила для всех элементов на странице, имеющих атрибут `class`, значение которого равно `test` или начинается с `test-` (т.е. с обязательным дефисом, после которого идёт остальное содержимое значения):

```css
/* селектор [class|="test"] выберет все элементы на странице, имеющих атрибут class, значение которого равно test или начинается с test- */
[class|="test"] {
  background-color: orange;
}
```

#### [attr$=value]

Пример задания правила для всех элементов на странице, имеющих атрибут `class`, значение которого заканчивается на `color`:

```css
/* селектор [class$="color"] выберет все элементы на странице, имеющих атрибут class, значение которого заканчивается на color */
[class$="color"] {
  background-color: yellow;
}
```

#### [attr*=value]

Пример задания правила для всех элементов на странице, имеющих атрибут `href`, значение которого содержит подстроку `youtu.be` (например будет выбран элемент, если атрибут `href` у него равен `https://youtu.be/TEOSuiNfUMA`):

```css
/* селектор [href*="youtu.be"] выберет все элементы на странице, имеющих атрибут href, значение которого содержит youtu.be */
[href*="youtu.be"] {
  background-color: green;
}
```

#### [attr~=value]

Пример задания правила для всех элементов на странице, имеющих атрибут `data-content`, значение которого содержит `news`, отделённое от других с помощью пробела (например будет выбран элемент, если у него атрибут `data-content` равен `hot-news news news-football`):

```css
/* селектор [data-content~="news"] выберет все элементы на странице, имеющих атрибут data-content, значение которого содержит news, отделённое от других с помощью пробела */
[data-content~="news"] {
  background-color: brown;
} 
```
# Составные селекторы
Составные селекторы состоят из комбинации простых.
## Группировка селекторов

Один и тот же набор свойств можно применить к разным селекторам. Пример:

```css
/* селектор h3, h4 выберет все элементы на странице, имеющих тег h3 и h4 */
h3, h4 {
  font-size: 20px;
  margin-top: 15px;
  margin-bottom: 10px;
}
```
  
Нужно просто указать через запятую все селекторы, к которым ты хочешь применить стили.

## Элемент с классом

Можно стилизовать конкретный элемент, если у него есть определённый класс. Примеры:

```xml
p.example {}
```

Селектор выберет все p, у которых есть класс example.

```xml
.main.active {}
```

Селектор выберет все элементы с классом main, у которых также есть и класс active. Пример такого элемента:  

```xml
<div class="main active">Пример</div>
```

## Селекторы отношений
В HTML документе каждый элемент всегда связан с другими элементами.

Виды отношений между HTML элементами:

-   **родитель**– элемент, непосредственно в котором находится рассматриваемый элемент;
-   **предок** – это элемент, который расположен на одном из уровней иерархии элементов, до которого можно дойти двигаясь от рассматриваемого элемента к его родителю, от его родителя к родителю его родителя и т.д.
-   **дети** – это элементы, непосредственно расположенные в текущем рассматриваемом элементе;
-   **потомки (дочерние элементы)** – это любые элементы, которые находятся в текущем элементе вне зависимости от уровня иерархии, в котором они расположены;
-   **соседи (сиблинги)** – это элементы, расположенные на том же уровне вложенности (иерархии), что и рассматриваемый элемент; или другими словами — это все другие элементы, которые имеют того же родителя что и текущий рассматриваемый элемент.

Более наглядно про отношения элементов приведено на рисунке. На этом рисунке отношения рассмотрены относительно элемента выделенного синим цветом.

![[types-of-relations.png]]

В CSS имеется 4 вида селекторов отношений.

Первые два из них `X Y` и `X > Y` относятся к вложенным селекторам. Они предназначены для поиска элементов в зависимости от их нахождения внутри других.

Остальные два `X + Y` и `X ~ Y` являются CSS селекторами для выбора соседних элементов.

Эти селекторы называют составными или комбинацией селекторов. Так как они на самом деле состоят из нескольких селекторов, разделённых между собой с помощью специальных символов (комбинаторов). Всего различают 4 символа: пробел, знак `>` (больше), знак `+` и `~` (тильда).

### Селектор X Y (для выбора вложенных или дочерних элементов)

Селектор `X Y` (предок потомки) предназначен для выбора элементов `Y`, находящихся в `X`.

Другими словами, селектор `X Y` предназначен для выбора элементов `Y`, являющихся потомками элементов определяемым селектором `X`.

Селекторы `X Y` называют контекстными или вложенными.

Например, селектор дочерних элементов `div p` выберет все элементы `p`, расположенные в `div`.

### Селектор X > Y

Селектор `X > Y` (родитель > дети) предназначен для выбора элементов, определяемым селектором `Y` непосредственно расположенных в элементе, определяемым селектором `X`.

По другому можно сказать, что селектор `X > Y` предназначен для выбора `Y`, у которых родителем является элемент, определяемым `X`.

Например, комбинация селекторов `li > ul` выберет все элементы `ul`, которые непосредственно расположены в `li`.

### Селектор X + Y

Селектор `X + Y` предназначен для выбора элементов `Y`, каждый из которых расположен сразу же после `X`. Элементы определяемым селектором `X` и `Y` должны находиться на одном уровне вложенности, т.е. быть по отношению друг к другу соседями (сиблингами).

Например, комбинация селекторов `input + label` выберет все элементы `label`, которые расположены сразу же за элементом `input`, и являющиеся друг по отношению к другу соседями (сиблингами).

### Селектор X ~ Y

Селектор `X ~ Y` предназначен для выбора элементов `Y`, которые расположены после `X`. При этом элементы, определяемые селектором `X` и `Y`, должны являться по отношению друг к другу соседями (сиблингами).

Например, `p ~ span` выберет все элементы `span`, расположенные после элемента `p` на том же уровне вложенности.

## Приоритет селекторов
Когда в CSS имеется несколько правил, устанавливающих одно и тоже CSS свойство некоторому элементу, приоритетным из них является то, в котором селектор имеет большую специфичность (вес).

Специфичность селекторов удобно представлять в виде 4 чисел: `0,0,0,0`.

При этом сравнение селекторов по весу нужно выполнять слева направо. Если первая цифра одного селектора больше, чем у другого, то он является более специфичным и к элементу будет применяться CSS-свойство, заданное в нём. Если цифры равны, то выполняем сравнение следующих цифр селекторов и т.д.

Если у сравниваемых селекторов все цифры равны, то будет применяться тот, который ниже из них расположен по коду.

Как считать эти цифры? Каждый селектор в зависимости от типа имеет вес:

-   универсальный селектор (не добавляет вес) – `0,0,0,0`;
-   селекторы по тегу, псевдоэлемент добавляют единичку к четвёртой цифре – `0,0,0,1`;
-   селекторы по классу и по атрибуту, псевдоклассы добавляют единичку ко третьей цифре – `0,0,1,0`;
-   селектор по идентификатору добавляют единичку ко второй цифре – `0,1,0,0`;

Стили, расположенные в атрибуте `style` элемента, являются более специфичными по сравнению с селекторами. Вес этих стилей определяется единицей в первой цифре – `1,0,0,0`.

Например:

-   `*` – `0,0,0,0`;
-   `li` – `0,0,0,1`;
-   `li::before` – `0,0,0,2`;
-   `ul > li` – `0,0,0,2`;
-   `div input+label` – `0,0,0,3`;
-   `h1 + div[data-target]` – `0,0,1,2`;
-   `.btn.show` – `0,0,2,0`;
-   `ul li a.item` – `0,0,1,3`;
-   `#aside div.show` – `0,1,1,1`;
-   `style="..."` – `1,0,0,0`;

Повысить важность определённого CSS свойства можно с помощью ключевого слова `!important`. В этом случае будет использоваться именно данное CSS-свойство.

Например:

```
<div class="alert-warning" style="background-color: #ffc107;"> ... </div>
```

В CSS:

```
.alert-warning {
  background-color: #ffa000 !important;
}
```

В этом примере элементу будет установлен тот фон к которому добавлено слово `!important`. `!important` перебивает любой вес.

Интересный случай, когда нужно определить какое значение CSS-свойства будет применено к элементу, если `!important` добавлено к нескольким из них.

В этом случае будет применено то значение CSS-свойства c `!important` у которого больше вес селектора.

К примеру, если добавить `!important` к CSS-свойству расположенному в `style`, то получим максимальную возможную специфичность, которую уже никак не перебьёшь.

Например:

```
<p id="message" style="font-size: 20px !important;">...</p>
```

CSS:

```
p#message {
  font-size: 16px !important;
}
```

В этом примере к элементу `#message` будет применено CSS-свойство `font-size` со значением 20px, т.к. хоть у каждого из них имеется состояние `!importants`, но специфичность style (`1,0,0,0`) больше чем у селектора `p#message` (`0,1,0,1`).

# Ссылки
___
##### Links


---
##### Источники
https://msiter.ru/tutorials/css-srednego-urovnya/psevdoklassy