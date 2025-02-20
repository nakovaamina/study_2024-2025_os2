---
## Front matter
title: "Отчёта по лабораторной работе 3"
subtitle: 1132232887
author: "Накова Амина Михайловна"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Целью данной работы является получение навыков настройки базовых и
специальных прав доступа для групп пользователей в операционной системе
типа Linux.

# Выполнение лабораторной работы

Открываем терминал с учётной записью root: su -. В корневом каталоге
создаём каталоги /data/main и /data/third командой: mkdir -p /data/main
/data/third. Посмотрим, кто является владельцем этих каталогов. Для этого
используем: ls -Al /data. Владельцем каталогов является суперпользователь.
Прежде чем устанавливать разрешения, изменим владельцев этих каталогов с
root на main и third соответственно: chgrp main /data/main и chgrp third
/data/third. Теперь владельцем этих каталогов является main и third. Далее
установим разрешения, позволяющие владельцам каталогов записывать файлы в
эти каталоги и запрещающие доступ к содержимому каталогов всем другим
пользователям и группам: chmod 770 /data/main и chmod 770 /data/third.
Проверим установленные права доступа (рис. [-@fig:001]):

![шаг 1](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab03\report\image\1.png){#fig:001 width=70%}

В другом терминале перейдём под учётную запись пользователя bob: su –
bob. Под пользователем bob попробуем перейти в каталог /data/main и создать
файл emptyfile в этом каталоге: cd /data/main и touch emptyfile. Так как
пользователь bob является владельцем каталога main, нам удалось перейти в этот
каталог и создать в нём новый файл. Теперь под пользователем bob попробуем
перейти в каталог /data/third и создать файл emptyfile в этом каталоге. Так как
пользователь bob не является владельцем каталога third, нам не удалось перейти
в этот каталог и создать в нём новый файл (рис. [-@fig:002]):

![шаг 2](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab03\report\image\2.png){#fig:002 width=70%}

В другом терминале, под учётной записью пользователя bob (пользователь
bob является членом группы main, как и alice) перейдём в каталог /data/main: cd
/data/main (данный каталог уже был открыт в нашем терминале) и в этом
каталоге введём: ls. Мы увидим два файла, созданные пользователем alice.
Теперь попробуем удалить файлы, принадлежащие пользователю alice
командой: rm -f alice*. Убедимся, что файлы будут удалены пользователем bob.
После проверки командой ls создадим два файла, которые принадлежат
пользователю bob: touch bob1 и touch bob2 (рис. [-@fig:003]):

![шаг 3](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab03\report\image\3.png){#fig:003 width=70%}

Переключаемся на учётную запись пользователя alice командой: su alice. Создаём пользователя bob: sudo useradd bob. При запросе вводим пароль пользователя. Проверяем, что пользователь bob создан (id bob) и устанавливаем пароль для пользователя: sudo passwd bob (рис. [-@fig:004]):

![шаг 4](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab03\report\image\4.png){#fig:004 width=70%}

В терминале под пользователем root установим для каталога /data/main бит
идентификатор группы, а также stiky-бит для разделяемого (общего) каталога
группы: chmod g+s,o+t /data/main (рис. [-@fig:005]):

![шаг 5](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab03\report\image\5.png){#fig:005 width=70%}

Переходим в терминал под пользователем alice и создаём в каталоге
/data/main файлы alice3 и alice4: touch alice3 и touch alice4. Теперь мы должны
увидеть, что два созданных вами файла принадлежат группе main, которая
является группой-владельцем каталога /data/main: ls и ls -Al /data. В этом же
терминале попробуем удалить файлы, принадлежащие пользователю bob: rm -rf
bob*. Убедимся, что sticky-bit предотвратит удаление этих файлов
пользователем alice, поскольку этот пользователь не является владельцем этих
файлов (Operation not permitted) (рис. [-@fig:006]):

![шаг 6](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab03\report\image\6.png){#fig:006 width=70%}

Откроем терминал с учётной записью root и установим права на чтение и
выполнение в каталоге /data/main для группы third и права на чтение и
выполнение для группы main в каталоге /data/third: setfacl -m g:third:rx
/data/main и setfacl -m g:main:rx /data/third (Рис. 7.1). Теперь используем
команду getfacl, чтобы убедиться в правильности установки разрешений: getfacl
/data/main и getfacl /data/third (рис. [-@fig:007]):

![шаг 7](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab03\report\image\7.png){#fig:007 width=70%}

Установим ACL по умолчанию для каталога /data/main: setfacl -m
d:g:third:rwx /data/main и для каталога /data/third: setfacl -m d:g:main:rwx
/data/third. Убедимся, что настройки ACL работают, добавив новый файл в
каталог /data/main: touch /data/main/newfile2. Используем getfacl
/data/main/newfile2 (Рис. 9.1) для проверки текущих назначений полномочий.
Выполним аналогичные действия для каталога /data/third (рис. [-@fig:008]):

![шаг 8](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab03\report\image\8.png){#fig:008 width=70%}



Ответы на контрольные вопросы:
1. Как следует использовать команду chown, чтобы установить владельца
группы для файла? Приведите пример. chown bob:main /data/third/newfile.
2. С помощью какой команды можно найти все файлы, принадлежащие
конкретному пользователю? Приведите пример. find ~ -user bob -print.
3. Как применить разрешения на чтение, запись и выполнение для всех
файлов в каталоге /data для пользователей и владельцев групп, не устанавливая
9
никаких прав для других? Приведите пример. chmod 770 /data (скриншот из
лабораторной работы).
4. Какая команда позволяет добавить разрешение на выполнение для файла,
который необходимо сделать исполняемым? chmod +x file.
5. Какая команда позволяет убедиться, что групповые разрешения для всех
новых файлов, создаваемых в каталоге, будут присвоены владельцу группы
этого каталога? Приведите пример. getfacl “имя каталога” 
6. Необходимо, чтобы пользователи могли удалять только те файлы,
владельцами которых они являются, или которые находятся в каталоге,
владельцами которого они являются. С помощью какой команды можно это
сделать? Приведите пример. chmod g+s,o+t /data/main 
7. Какая команда добавляет ACL, который предоставляет членам группы
права доступа на чтение для всех существующих файлов в текущем каталоге?
setfacl -m g:group:r <file/dir> .
10
8. Что нужно сделать для гарантии того, что члены группы получат
разрешения на чтение для всех файлов в текущем каталоге и во всех его
подкаталогах, а также для всех файлов, которые будут созданы в этом каталоге
в будущем? Приведите пример. setfacl -dm g:group:r /dir.
9. Какое значение umask нужно установить, чтобы «другие» пользователи
не получали какие-либо разрешения на новые файлы? Приведите пример. 007.
10. Какая команда гарантирует, что никто не сможет удалить файл myfile
случайно? sudo chattr +i myfile.

# Выводы

В ходе выполнения лабораторной работы были получены навыкы настройки
базовых и специальных прав доступа для групп пользователей в операционной
системе типа Linux

# Список литературы{.unnumbered}

::: {#refs}
:::
