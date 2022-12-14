202104242319
Tags:
___
### Байты (bytes и bytearray)
Байтовые строки очень похожи на обычные строки [[String]], но с некоторыми отличиями.
==Байт== - минимальная единица хранения и обработки цифровой информации. Последовательность байт представляет собой какую-либо информацию (текст, картинку, мелодию...).

`bytes` - неизменяемая последовательность байтов. Каждый элемент последовательности может хранить целое число от 0 до 255, которое обозначает код символа. Объект типа bytes поддерживает большинство строковых методов и, если это возможно, выводится как последовательность символов. Однако доступ по индексу возвращает целое число, а не символ.
Объект типа bytes может содержать как однобайтовые, так и многобайтовые символы. Обратите внимание на то, что функции и методы строк некорректно работают с многобайтовыми кодировками, — например, функция len() вернет количество байтов, а не символов.

**Синтаксис метода bytes()**:
`bytes ([data_source [, encoding [, errors]]])`
Три аргумента этого метода необязательны. Первый аргумент используется для инициализации списка байтов. Если первым аргументом является строка, то второй аргумент используется для кодирования. Наконец, третий аргумент используется для отображения ошибки в случае сбоя кодирования.


`bytearray` - изменяемая последовательность байтов. Тип bytearray аналогичен типу bytes, но позволяет изменять элементы по индексу и содержит дополнительные методы, дающие возможность добавлять и удалять элементы.
**Синтаксис метода bytearray()**:
`bytearray ([ data_source [, encoding [, errors]]])`
Три аргумента этого метода необязательны. Первый аргумент используется для инициализации списка байтов. Если первым аргументом является строка, то второй аргумент используется для кодирования. Наконец, третий аргумент используется для отображения ошибки в случае сбоя кодирования.

Во всех случаях, когда речь идет о текстовых данных, следует использовать тип str. ==Типы bytes и bytearray следует задействовать для записи двоичных данных (например, изображений) и промежуточного хранения строк.==


___
##### Links
[[Типы данных]]

---
##### Источники
