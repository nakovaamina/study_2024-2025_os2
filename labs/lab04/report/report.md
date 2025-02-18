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
В консоли перейдём в режим работы суперпользователя (используем команду su -) далее перейдём в каталог /etc/yum.repos.d и изучим содержание каталога и файлов репозиториев (Рис. 1.1): 
cd /etc/yum.repos.d 
ls
cat rocky-addons.repo (Рис. 1.2)
cat rocky-devel.repo (Рис. 1.3)
cat rocky-extras.repo (Рис. 1.4)
cat rocky.repo (Рис. 1.5)
 
Рис. 1.1. Открытие режима работа суперпользователя и последующие открытие каталога.

 
Рис. 1.2. Содержание файла cat rocky-addons.repo.


 
Рис. 1.3. Содержание файла cat rocky-devel.repo.


 
Рис. 1.4. Содержание файла cat rocky-extras.repo.

 
Рис. 1.5. Содержание файла cat rocky.repo.

	Выведем на экран список репозиториев: dnf repolist и список пакетов, в названии или описании которых есть слово user: dnf search user (Рис. 2): 

 
Рис. 2. Список репозиториев и пакетов.

Установим nmap, предварительно изучив информацию по имеющимся пакетам: 
dnf search nmap (Рис. 3.1)
dnf info nmap (Рис. 3.2)
dnf install nmap (Рис. 3.3)
dnf install nmap\* (Рис. 3.4)


 
Рис. 3.1. Выполнение команды dnf search nmap.



 
Рис. 3.2. Выполнение команды dnf info nmap.


 
Рис. 3.3. Выполнение команды dnf install nmap.


 
Рис. 3.4. Выполнение команды dnf install nmap\*.

Удалим nmap: 
dnf remove nmap (Рис. 4.1)
dnf remove nmap\* (Рис. 4.2)

 
Рис. 4.1. Выполнение команды dnf remove nmap.


 
Рис. 4.2. Выполнение команды dnf remove nmap\*.

Получим список имеющихся групп пакетов, затем установим группу пакетов RPM Development Tools: 
dnf groups list (Рис. 5.1)
LANG=C dnf groups list (Рис. 5.2)
dnf groups info "RPM Development Tools" (Рис. 5.3)
dnf groupinstall "RPM Development Tools" (Рис. 5.4)
Теперь удалим группы пакетов RPM Development Tools командой dnf groupremove "RPM Development Tools" (Рис. 5.5).

 
Рис. 5.1. Получение списков имеющихся групп пакетов (выполнение команды dnf groups list).


 
Рис. 5.2. Выполнение команды LANG=C dnf group list.


 
Рис. 5.3. Получение информации (выполнение команды dnf groups info “RPM Development Tools”.


Рис. 5.4. Установка группы пакетов RPM Development Tools (выполнение команды dnf groupinstall “RPM Development Tools”).

 
Рис. 5.5. Удаление группы пакетов RPM Development Tools (выполнение команды dnf groupremove “RPM Development Tools”).

   Посмотрим историю использования команды dnf: dnf history и отменим шестое по счёту, действие: dnf history undo 6 (Рис. 6).


 
Рис. 6. Просмотр использования команды dnf и отмена шестого по счёту действия.

Скачаем rpm-пакет lynx: 
dnf list lynx 
dnf install lynx –downloadonly (Рис. 7). 


 
Рис. 7. Скачивание rpm-пакета lynx.

Найдём каталог, в который был помещён пакет после загрузки: find /var/cache/dnf/ -name lynx* и перейдём в этот каталог командой cd. Затем установим rpm-пакет: rpm -Uhv lynx-.rpm и определим расположение исполняемого файла: which lynx. Используя rpm, определим по имени файла, к какому пакету принадлежит lynx: rpm -qf $(which lynx) (Рис. 8).



 
Рис. 8. Нахождение каталога с пакетом, установка rpm-пакета, определение расположения исполняемого файла, определение к какому пакету принадлежит lynx.

Получим дополнительную информацию о содержимом пакета, введя: rpm -qi lynx (Рис. 9.1). Далее получим список всех файлов в пакете, используя: rpm -ql lynx (Рис. 9.2), а также выведем перечень файлов с документацией пакета, введя: rpm -qd lynx (Рис. 9.3). Посмотрим файлы документации, применив команду man lynx (Рис. 9.4).

 
Рис. 9.1. Получение дополнительной информации о содержимом пакета.


 
Рис. 9.2. Получение списка всех файлов в пакете.


 
Рис. 9.3. Вывод перечня файлов с документацией пакета.

 
Рис. 9.4. Просмотр файлов документации.

Выведем на экран перечень и месторасположение конфигурационных файлов пакета: rpm -qc lynx и расположение, и содержание скриптов, выполняемых при установке пакета: rpm -q --scripts lynx (скрипты отсутствуют) (Рис. 10).

 
Рис. 10. Вывод на экран перечень и месторасположение конфигурационных файлов пакета, вывод расположения и содержание скриптов.
В отдельном терминале под своей учётной записью запустим текстовый браузер lynx, чтобы проверить корректность установки пакета (Рис. 11.1). Вернёмся в терминал с учётной записью root и удалим пакет: rpm -e lynx и ls (Рис. 11.2). Предположим, что требуется из rpm-пакетов установить dnsmasq (DNS-, DHCPи TFTP-сервер). Для этого установим пакет dnsmasq: dnf list dnsmasq, dnf install dnsmasq и определим расположение исполняемого файла: which dnsmasq. Определим по имени файла, к какому пакету принадлежит dnsmasq: rpm -qf $(which dnsmasq) (Рис. 11.3).

 
Рис. 11.1. Запуск текстового браузера lynx.



 
Рис. 11.2. Удаление пакета и проверка.


 
Рис. 11.3. Установка пакета dnsmasq, определение расположение исполняемого файла, определение к какому пакету принадлежит dnsmasq.

Теперь получим дополнительную информацию о содержимом пакета: rpm -qi dnsmasq (Рис. 12.1). Далее получим список всех файлов в пакете: rpm -ql dnsmasq (Рис. 12.2), а также выведем перечень файлов с документацией пакета: rpm -qd dnsmasq (Рис. 12.3). Посмотрим файлы документации, применив команду man dnsmasq (Рис. 12.4) и выведем на экран перечень и месторасположение конфигурационных файлов пакета: rpm -qc dnsmasq (Рис. 12.5).


 
Рис. 12.1. Получение дополнительной информации о содержимом пакета.


 
Рис. 12.2. Получение списка всех файлов в пакете.

 
Рис. 12.3. Вывод перечня файлов с документацией пакета.


 
Рис. 12.4. Просмотр файлов документации.


 
Рис. 12.5. Вывод на экран перечень и месторасположение конфигурационных файлов пакета.
Выведем на экран расположение и содержание скриптов, выполняемых при установке пакета: rpm -q --scripts dnsmasq (Рис. 13.1). Вернёмся в терминал с учётной записью root и удалим пакет: rpm -e dnsmask (Рис. 13.2).

 
Рис. 13.1. Вывод на экран расположение и содержание скриптов, выполняемых при установке пакета.


 
Рис. 13.2. Удаление пакета.

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
