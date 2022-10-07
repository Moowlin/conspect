202106191909
Tags:
___
# Listing Files
The `ls` command is used to list the contents of a directory. To learn the details about a file, such as the type of file, the permissions, ownerships or the timestamp, perform a long listing using the `-l` option to the `ls` command.

**File Type**
>==-==rw-r--r-- 1 root   root  18047 Dec 20  2017 alternatives.log                
>==d==rwxr-x--- 2 root   adm    4096 Dec 20  2017 apache2

The file types are:

| Symbol | File Type | Description |
| --- | --- | --- |
| `d` | directory | A file used to store other files. |
| `-` | regular file | Includes readable files, images files, binary files, and compressed files. |
| `l` | symbolic link | Points to another file. |
| `s` | socket | Allows for communication between processes. |
| `p` | pipe | Allows for communication between processes. |
| `b` | block file | Used to communicate with hardware. |
| `c` | character file | Used to communicate with hardware. |

**Permissions**
>d==rwxr-xr-x== 2 root   root   4096 Apr 11  2014 upstart

More infotmation in [[Права пользователей]]

**Hard Link Count**
>-rw-r----- ==1== syslog adm    1346 Oct  2 22:17 auth.log

This number indicates how many hard links point to this file.
More infotmation in [[Символические и жесткие ссылки]]

**User Owner**
>-rw-r----- 1 ==syslog== adm     106 Oct  2 19:57 kern.log

User `syslog` owns this file. Every time a file is created, the ownership is automatically assigned to the user who created it.
More infotmation in [[Пользователи]]

**Group Owner**
>-rw-rw-r-- 1 root   ==utmp== 292584 Oct  2 19:57 lastlog

Indicates which group owns this file
More infotmation in [[Группы пользоватей]]

**File Size**
>-rw-r----- 1 syslog adm   ==19573== Oct  2 22:57 syslog

**Timestamp**
>drwxr-xr-x 2 root   root   4096 ==Dec  7  2017== fsck

This indicates the time that the file's contents were last modified.

**Filename**
>-rw-r--r-- 1 root   root  47816 Dec  7  2017 ==bootstrap.log==

**Consider This**
In the case of symbolic links, a file that points to another file, the link name will be displayed along with an arrow and the pathname of the original file.
> lrwxrwxrwx. 1 root root 22 Nov 6 2012 /etc/grub.conf ==->== ../boot/grub/grub.conf

More infotmation in [[Символические и жесткие ссылки]]
___
##### Links
[[differences between pipes and sockets]]


---
##### Источники
