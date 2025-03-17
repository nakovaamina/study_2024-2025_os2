---
## Front matter
title: "Отчёта по лабораторной работе 1"
subtitle: "Установка ОС"
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

Целью данной работы является приобретение практических навыков установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.

# Задание

Здесь приводится описание задания в соответствии с рекомендациями
методического пособия и выданным вариантом.

# Выполнение лабораторной работы

Произведём скачивание и установку виртуальной машины через сайт(рис. [-@fig:001]): 
https://www.virtualbox.org/

![Скачивание виртуальной машины](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\report\image\1.png){#fig:001 width=70%}


 Следующим шагом нужно скачать дистрибутив Linux Rocky, воспользовавшись сайтом(рис. [-@fig:002]): 
https://rockylinux.org/download

![Скачивание дистрибутива Linux Rocky.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\report\image\2.png){#fig:002 width=70%}


Переходим к настройкам установки операционной системы и выбираем английский язык для интерфейса(рис. [-@fig:003]).

![Установка английского языка интерфейса ОС.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\report\image\3.png){#fig:003 width=70%}
 

При выборе места установки оставляем параметры, которые были выставлены автоматически(рис. [-@fig:004]).

![Окно настройки установки: место установки.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\report\image\4.png){#fig:004 width=70%}
 

В разделе выбора программ указываем в качестве базового окружения Server with GUI , а в качестве дополнения — Development Tools(рис. [-@fig:005]).

![ Окно настройки установки: выбор программ.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\report\image\5.png){#fig:005 width=70%}


Отключаем KDUMP(рис. [-@fig:006]).

![Окно настройки установки: отключение KDUMP.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\report\image\6.png){#fig:006 width=70%}


Включаем сетевое соединение(рис. [-@fig:007]).

![Окно настройки установки: сеть и имя узла.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\report\image\7.png){#fig:007 width=70%}
 

Скорректируем раскладку клавиатуры (добавим русский язык, но в качестве языка по умолчанию укажем английский язык; зададим комбинацию клавиш для переключения между раскладками клавиатуры - Alt + Shift )(рис. [-@fig:008]).

![Окно настройки установки: язык клавиатуры и горячие клавиши.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\report\image\8.png){#fig:008 width=70%}

Устанавливаем пароль для root и пользователя с правами администратора (рис. [-@fig:009]) и (рис. [-@fig:010]).

![Установка пароля для root.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\report\image\9.png){#fig:009 width=70%}
 
![Установка пароля для пользователя с правами администратора.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\report\image\10.png){#fig:010 width=70%}


Начинаем процесс установки ОС (рис. [-@fig:011]) и (рис. [-@fig:012]).

![Запуск установки ОС.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\report\image\11.png){#fig:011 width=70%}

![Установка ОС.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\report\image\12.png){#fig:012 width=70%}


Дожидаемся и завершаем установку. После успешной установки выполняем перезагрузку системы. Последним пунктом нашей лабораторной работы становится подключение образа диска Дополнительной гостевой ОС (рис. [-@fig:013])

![Подключение образа диска Дополнительной гостевой ОС.](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab01\report\image\13.png){#fig:013 width=70%} 


Домашнее задание:
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


# Выводы

В ходе выполнения лабораторной работы были приобретены практические навыки установки операционной системы на виртуальную машину и настройки минимально необходимых для дальнейшей работы сервисов.

