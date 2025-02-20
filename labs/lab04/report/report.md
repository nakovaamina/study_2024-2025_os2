---
## Front matter
title: "Лабораторная работа 4"
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

Целью данной работы является получение навыков работы с репозиториями и менеджерами пакетов.


# Выполнение лабораторной работы
В консоли перейдём в режим работы суперпользователя (используем команду su -) далее перейдём в каталог /etc/yum.repos.d и изучим содержание каталога и файлов репозиториев: 
cd /etc/yum.repos.d 
ls
cat rocky-addons.repo 
cat rocky-devel.repo 
cat rocky-extras.repo 
cat rocky.repo 

![шаг 1](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab04\report\image\1.png){#fig:001 width=70%}
 
Открытие режима работа суперпользователя и последующие открытие каталога.

![шаг 2](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab04\report\image\2.png){#fig:002 width=70%}

 
Содержание файла cat rocky-addons.repo.

![шаг 3](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab04\report\image\3.png){#fig:003 width=70%}

 
Содержание файла cat rocky-devel.repo.

![шаг 4](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab04\report\image\4.png){#fig:004 width=70%}

 
Выведем на экран список репозиториев: dnf repolist и список пакетов, в названии или описании которых есть слово user: dnf search user:

![шаг 5](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab04\report\image\5.png){#fig:005 width=70%}
 
Список репозиториев и пакетов.

Установим nmap, предварительно изучив информацию по имеющимся пакетам: 
dnf search nmap 
dnf info nmap 
dnf install nmap 
dnf install nmap\* 


Выполнение команды dnf search nmap.

![шаг 6](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab04\report\image\6.png){#fig:006 width=70%}


 Выполнение команды dnf install nmap\*.

Удалим nmap: 
dnf remove nmap 
dnf remove nmap\* 

 
Выполнение команды dnf remove nmap.
Выполнение команды dnf remove nmap\*.

Получим список имеющихся групп пакетов, затем установим группу пакетов RPM Development Tools
Теперь удалим группы пакетов RPM Development Tools командой dnf groupremove "RPM Development Tools"

![шаг 7](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab04\report\image\6.png){#fig:007 width=70%}

 
Ответы на контрольные вопросы:
1. Какая команда позволяет вам искать пакет rpm, содержащий файл useradd? yum search useradd.

 
2. Какие команды вам нужно использовать, чтобы показать имя группы dnf, которая содержит инструменты безопасности и показывает, что находится в этой группе? yum info gcl.

 
3. Какая команда позволяет вам установить rpm, который вы загрузили из Интернета и который не находится в репозиториях? yum install.
4. Вы хотите убедиться, что пакет rpm, который вы загрузили, не содержит никакого опасного кода сценария. Какая команда позволяет это сделать? rpm -q -scripts.
5. Какая команда показывает всю документацию в rpm? rpm -qd.
6. Какая команда показывает, какому пакету rpm принадлежит файл? rpm -qf $(which).


# Выводы


В ходе выполнения лабораторной работы были получены навыки работы с репозиториями и менеджерами пакетов. 


# Список литературы{.unnumbered}

::: {#refs}
:::
