202104272259
Tags:
___
### etc/shadow запись о паролях зашифрованы пользователями
`/etc/shadow` – это текстовый файл, содержащий информацию о паролях пользователей системы. Он принадлежит пользователю root и группе shadow и имеет 640 разрешений.

Файл `/etc/shadow` содержит одну запись в каждой строке, каждая из которых представляет собой учетную запись пользователя. Вы можете просмотреть содержимое файла с помощью текстового редактора или команды, такой как cat

Как правило, первая строка описывает пользователя root, затем системные и обычные учетные записи пользователей. Новые записи добавляются в конец файла.

Каждая строка файла `/etc/shadow` содержит девять полей, разделенных запятыми:
![[Pasted image 20210427230057.png]]
           

- `Имя пользователя`. Строка, которую вы вводите при входе в систему. Учетная запись пользователя, которая существует в системе.

- `Зашифрованный пароль`. Пароль использует формату `$type$salt$hashed1`. `$type` является методом криптографического алгоритма хеширования и может иметь следующие значения:
	- `$1$` – MD5
	- `$2a$` – Blowfish
	- `$2y$` – Eksblowfish
	- `$5$` – SHA-256
	- `$6$` – SHA-512

Если поле пароля содержит звездочку ( \*) или восклицательный знак ( !), пользователь не сможет войти в систему с использованием аутентификации по паролю. Другие методы входа, такие как аутентификация на основе ключей или переключение на пользователя, по-прежнему разрешены

В старых системах Linux зашифрованный пароль пользователя хранился в файле /etc/passwd.

- `Последнее изменения пароля` - Это дата последнего изменения пароля. Количество дней исчисляется с 1 января 1970 года (дата эпохи).
- `Минимальный срок действия пароля`. Количество дней, которое должно пройти, прежде чем пароль пользователя может быть изменен. Как правило, он установлен на ноль, что означает отсутствие минимального срока действия пароля.
- `Максимальный срок действия пароля`. Количество дней после смены пароля пользователя. По умолчанию этот номер установлен на 99999.
- `Период предупреждения`. Количество дней до истечения срока действия пароля, в течение которого пользователь получает предупреждение о необходимости изменения пароля.
- `Период бездействия`. Количество дней после истечения срока действия пароля пользователя до отключения учетной записи пользователя. Обычно это поле пустое.
- `Срок хранения`. Дата, когда учетная запись была отключена. Это представляется как дата эпохи.
- `Неиспользованный`. Это поле игнорируется. Оно зарезервированно для будущего использования.

Файл `/etc/shadow` не стоит редактировать вручную, если вы не знаете, что вы делаете. Всегда используйте команду, которая предназначена для этой цели. Например, чтобы изменить пароль пользователя, используйте команду passwd, а для изменения информации об устаревании пароля используйте команду chage.


___
##### Links


---
##### Источники
