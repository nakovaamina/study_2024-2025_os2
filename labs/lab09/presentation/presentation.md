---
## Front matter
lang: ru-RU
title: Лабораторная работа 9
subtitle: 1132232887
author:
  - Накова А. М.
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 17 февраля 2025

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
---

# Цель работы

# Цель работы

Целью данной работы является получение навыков работы с контекстом безопасности и политиками SELinux.


# Выполнение лабораторной работы



Запустим терминал и получим полномочия администратора: su -. Затем просмотрим текущую информацию о состоянии SELinux: sestatus -v : 

![шаг 1](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\presentation\image\1.png){#fig:001 width=70%}



#Посмотрим, в каком режиме работает SELinux: getenforce. По умолчанию SELinux находится в режиме принудительного исполнения (Enforcing). Изменим режим работы SELinux на разрешающий (Permissive): setenforce 0 и снова введём getenforce. Откроем файл /etc/sysconfig/selinux с помощью текстового редактора mcedit: 

![шаг 2](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\presentation\image\2.png){#fig:002 width=70%}

#В открытом в редакторе файле /etc/sysconfig/selinux установим SELINUX=disabled. После чего сохраним изменения :

![шаг 3](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\presentation\image\3.png){#fig:003 width=70%}
 

#Выполним перезагрузку системы:

![шаг 4](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\presentation\image\4.png){#fig:004 width=70%}
 


#После перезагрузки запустим терминал и получим полномочия администратора. Далее посмотрим статус SELinux: getenforce. Мы видим, что SELinux теперь отключён. Попробуем переключить режим работы SELinux: setenforce 1. Система пишет, что SELinux отключён, так как мы не можете переключаться между отключённым и принудительным режимом без перезагрузки системы. Откроем файл /etc/sysconfig/selinux с помощью текстового редактора mcedit

![шаг 5](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\presentation\image\5.png){#fig:005 width=70%}

#В открытом в редакторе файле /etc/sysconfig/selinux установим SELINUX=enforcing. После чего сохраним изменения:

![шаг 6](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\presentation\image\6.png){#fig:006 width=70%}
 

#Выполним перезагрузку системы:

![шаг 7](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\presentation\image\7.png){#fig:007 width=70%}
 


#Во время загрузки системы мы получили предупреждающее сообщение о необходимости восстановления меток SELinux:

![шаг 8](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\presentation\image\8.png){#fig:008 width=70%}



#После перезагрузки в терминале с полномочиями администратора просмотрим текущую информацию о состоянии SELinux: sestatus -v. Убедимся, что система работает в принудительном режиме (enforcing) использования SELinux:

![шаг 9](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\presentation\image\9.png){#fig:009 width=70%}
 


#Использование restorecon для восстановления контекста безопасности:
Запустим терминал и получим полномочия администратора. Просмотрим контекст безопасности файла /etc/hosts: ls -Z /etc/hosts. Мы видим, что у файла есть метка контекста net_conf_t. Скопируем файл /etc/hosts в домашний каталог: cp /etc/hosts ~/. Затем проверим контекст файла ~/hosts: ls -Z ~/hosts. Поскольку копирование считается созданием нового файла, то параметр контекста в файле ~/hosts, расположенном в домашнем каталоге, стал admin_home_t. Попытаемся перезаписать существующий файл hosts из домашнего каталога в каталог /etc: mv ~/hosts /etc и подтвердим, что мы хотим сделать это. После чего нам нужно убедиться, что тип контекста по-прежнему установлен на admin_home_t: ls -Z /etc/hosts. Исправим контекст безопасности: restorecon -v /etc/hosts. Опция -v покажет процесс изменения. Убедимся, что тип контекста изменился: ls -Z /etc/hosts. Для массового исправления контекста безопасности на файловой системе введём touch /.autorelabel и перезагрузим систему.

![шаг 10](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\presentation\image\10.png){#fig:010 width=70%}


#Во время перезапуска не забываем нажать клавишу Esc на клавиатуре, чтобы мы видели загрузочные сообщения. Мы видим, что файловая система автоматически перемаркирована
![шаг 11](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\presentation\image\11.png){#fig:011 width=70%}





# Выводы

получили навыков работы с контекстом безопасности и политиками SELinux.




