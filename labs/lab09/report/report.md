---
## Front matter
title: "Лабораторная работа 9"
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

Целью данной работы является получение навыков работы с
планировщиками событий cron и at.


# Выполнение лабораторной работы

Планирование задач с помощью cron:
Мониторинг журнала системных событий в реальном времени:
Запустим терминал и получим полномочия администратора: su -.
Просмотрим статус демона crond: systemctl status crond -l и содержимое файла
конфигурации /etc/crontab: cat /etc/crontab 

![шаг 1](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\report\image\1.png){#fig:001 width=70%}
 
Теперь просмотрим список заданий в расписании: crontab -l. Ничего не
отобразилось, так как расписание ещё не задано. Далее откроем файл расписания
на редактирование: crontab -e

![шаг 2](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\report\image\2.png){#fig:002 width=70%}

Предыдущая команда запустила интерфейс редактора (по умолчанию
используется vi). Добавим следующую строку в файл расписания (запись
сообщения в системный журнал), используя Ins для перехода в vi в режим ввода:
*/1 * * * * logger This message is written from root cron. Закроем сеанс
редактирования vi и сохраним изменения, используя команду vi: Esc : wq

![шаг 3](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\report\image\3.png){#fig:003 width=70%}

Просмотрим список заданий в расписании: crontab -l (в расписании
появилась запись о запланированном событии). Не выключая систему, через
некоторое время (2–3 минуты) просмотрим журнал системных событий: grep
written /var/log/messages

![шаг 4](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\report\image\4.png){#fig:004 width=70%}

Вернёмся в текстовый редактор vi и изменим запись в расписании crontab на
следующую: 0 */1 * * 1-5 logger This message is written from root cron 
 
![шаг 5](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\report\image\5.png){#fig:005 width=70%}
 
Теперь просмотрим список заданий в расписании: crontab -l

![шаг 6](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\report\image\6.png){#fig:006 width=70%}


Перейдём в каталог /etc/cron.hourly и создадим в нём файл сценария с именем
eachhour :
cd /etc/cron.hourly
touch eachhour
Далее откроем файл eachhour для редактирования и пропишем в нём
следующий скрипт (запись сообщения в системный журнал) (Рис. 1.8):
#!/bin/sh
logger This message is written at $(date) 

![шаг 7](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\report\image\7.png){#fig:007 width=70%}

![шаг 8](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\report\image\8.png){#fig:008 width=70%}

Сделаем файл сценария eachhour исполняемым:
chmod +x eachhour
Теперь перейдём в каталог /etc/crond.d и создадим в нём файл с расписанием
eachhour :
cd /etc/cron.d
touch eachhour
Откроем этот файл для редактирования и поместим в него следующее
содержимое:
11 * * * * root logger This message is written from /etc/cron.d
Сохраним изменения

![шаг 9](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab09\report\image\9.png){#fig:009 width=70%}

 
Ответы на контрольные вопросы:
1. Как настроить задание cron, чтобы оно выполнялось раз в 2 недели? 00 00
1,15 * * logger task
2. Как настроить задание cron, чтобы оно выполнялось 1-го и 15-го числа
каждого месяца в 2 часа ночи? 00 02 1,15 * * logger task
3. Как настроить задание cron, чтобы оно выполнялось каждые 2 минуты
каждый день? */2 * * * * logger task
4. Как настроить задание cron, чтобы оно выполнялось 19 сентября
ежегодно? * * 19 9 logger task
5. Как настроить задание cron, чтобы оно выполнялось каждый четверг
сентября ежегодно? * * * * 4 logger task
6. Какая команда позволяет вам назначить задание cron для пользователя
alice? Приведите подтверждающий пример. * * * * alice logger task
7. Как указать, что пользователю bob никогда не разрешено назначать
задания через cron? Приведите подтверждающий пример. записать его в
/etc/cron.deny
9
8. Вам нужно убедиться, что задание выполняется каждый день, даже если
сервер во время выполнения временно недоступен. Как это сделать? Найти
задание в логах grep cron /var/log/messages
9. Какая команда позволяет узнать, запланированы ли какие-либо задания
на выполнение планировщиком atd? atq

# Выводы


В ходе выполнения лабораторной работы были получены навыки работы с
планировщиками событий cron и at.

# Список литературы{.unnumbered}

::: {#refs}
:::
