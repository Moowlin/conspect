202104281333
Tags:
___
# Команда rm - удаляет файлы и папки  
>**Warning** 
Если нужно рекурсивное удаление, используйте опцию -r. Действия оператора rm необратимы.

Чтобы удалить все файлы, начинающиеся на слово file можно использовать специальный символ \*, означает любой символ в любом количестве:

`rm /home/user/file*`

Эта команда удаления файла в linux должна использоваться очень осторожно, чтобы не удалить ничего лишнего.

`-i` - заставляет программу спрашивать пользователя перед удалением
`-f` - будут удалены все файлы без вопросов
`-R` - для удаления директорий, вместе с файлами и поддиректориями

>**Consider This**
Permissions can have an impact on file management commands, such as the `rm` command.
To delete a file within a directory, a user must have write and execute permission on a directory. Regular users typically only have this type of permission in their home directory and its subdirectories.

___
##### Links


---
##### Источники
