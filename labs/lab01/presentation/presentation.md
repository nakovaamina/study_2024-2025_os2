---
## Front matter
lang: ru-RU
title: Лабораторная работа 1
subtitle: Установка ОС
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

Целью данной работы является приобретение практических навыков установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.



# Скачивание виртуальной машины

![Скачивание виртуальной машины](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\presentation\image\1.png){#fig:001 width=70%}


# Скачивание дистрибутива Linux Rocky.

![Скачивание дистрибутива Linux Rocky.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\presentation\image\2.png){#fig:002 width=70%}

# Установка английского языка интерфейса ОС.

![Установка английского языка интерфейса ОС.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\presentation\image\3.png){#fig:003 width=70%}
 
# Окно настройки установки: место установки.

![Окно настройки установки: место установки.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\presentation\image\4.png){#fig:004 width=70%}

# Окно настройки установки: выбор программ.


![ Окно настройки установки: выбор программ.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\presentation\image\5.png){#fig:005 width=70%}

# Окно настройки установки: отключение KDUMP.

![Окно настройки установки: отключение KDUMP.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\presentation\image\6.png){#fig:006 width=70%}


# Окно настройки установки: сеть и имя узла.

![Окно настройки установки: сеть и имя узла.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\presentation\image\7.png){#fig:007 width=70%}
 
# Окно настройки установки: язык клавиатуры и горячие клавиши.

![Окно настройки установки: язык клавиатуры и горячие клавиши.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\presentation\image\8.png){#fig:008 width=70%}

# Установка пароля для root.

![Установка пароля для root.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\presentation\image\9.png){#fig:009 width=70%}

# Установка пароля для пользователя с правами администратора.
 
![Установка пароля для пользователя с правами администратора.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\presentation\image\10.png){#fig:010 width=70%}

# Запуск установки ОС.

![Запуск установки ОС.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\presentation\image\11.png){#fig:011 width=70%}

# Установка ОС.

![Установка ОС.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\presentation\image\12.png){#fig:012 width=70%}

# Установка ОС.

![Подключение образа диска Дополнительной гостевой ОС.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\presentation\image\13.png){#fig:013 width=70%} 


# Домашнее задание

1)	Версия ядра Linux (Linux version).
Версию ядра можно посмотреть командой dmesg | grep “linux version”.
Ответы на контрольные вопросы
1) Содержит информацию об идентификаторе учетной записи пользователя и ее имени, идентификаторе основной группы пользователя и ее названии
2) 
•	для получения справки по команде – info "название команды" или "название команды"  --help
•	для перемещения по файловой системе – cd "путь"
•	для просмотра содержимого каталога – dir либо ls
•	для определения объема каталога – du -sh "путь"
•	для создания каталога -  mkdir "название" для удаления – rmdir "название"      
для создания файла touch "название"  или cat > "название" для удаления rm "название"
•	для создания каталога с правами mkdir  –mode="идентификатор" "название каталога" для правки прав доступа для файла chmod
•	для просмотра истории команд - history
3) Файловая система определяет способ хранения, организации данных/информации на определенных носителях. 
4) dmesg | grep “filesystem”
5) pkill «название процесса»


```
# Вывод

В ходе выполнения лабораторной работы были приобретены практические навыки установки операционной системы на виртуальную машину и настройки минимально необходимых для дальнейшей работы сервисов.


