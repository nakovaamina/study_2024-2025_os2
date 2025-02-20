---
## Front matter
title: "Отчёта по лабораторной работе 2"
subtitle: "Управление пользователями
и группами"
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

Получить представление о работе с учётными записями пользователей и группами
пользователей в операционной системе типа Linux.
# Задание

Здесь приводится описание задания в соответствии с рекомендациями
методического пособия и выданным вариантом.

# Теоретическое введение

В операционных системах типа Linux чаще всего применяется дискреционное управление доступом субъектов к объектам системы. В качестве субъектов системы чаще всего
выступают пользователи или группы пользователей, а в качестве объектов — файлы (в
том числе системные), каталоги, устройства и т.п. В качестве особого субъекта выделяется
суперпользователь (пользователь root), имеющий право устанавливать права владения
для всех остальных субъектов системы.
Под доступом к ресурсу системы понимают чтение (read), запись (write) и выполнение
(eXecute). Тот или иной тип доступа может быть применён к пользователю и/или группе,
владеющими тем или иным ресурсом операционной системы, а также ко всем остальным
субъектам, не являющимся владельцами ресурса.
Механизм пользователей был разработан по соображениям безопасности, для ограничения доступа к различным частям системы. Суперпользователь (root) имеет полный
доступ к операционной системе и её настройкам и используется только для целей
системного администрирования. Обычные пользователи работают с ограниченными правамит.е. сокращается их влияние на их собственную среду и на операционную систему
в целом. Один из способов изменения прав доступа пользователя к ресурсам системы —
добавление пользователя в определённую группу. Например, члены группы wheel используют административные привилегии пользователя root, в частности, они могут
использовать команду sudo, чтобы не входить в систему как пользователь root, но при
этом выполнять административные задачи в операционной системе

# Выполнение лабораторной работы

Войдём в систему как обычный пользователь и откроем терминал. Определим, какую учётную запись пользователя мы используем, введя команду whoami (используем учётную запись ismakhorin). Выведем на экран более подробную информацию, используя команду id (UID – id пользователя равный 1000. GID – id группы равный 1000). Используем команду su для переключения к учётной записи root. При запросе пароля вводим пароль пользователя root. Наберём id (UID – id пользователя равный 0. GID – id группы равный 0). Далее просмотрим в безопасном режиме файл /etc/sudoers. Мы хотим использовать mcedit, поэтому в терминале для запуска visudo указываем: EDITOR=mcedit visudo (рис. [-@fig:001]):

![шаг 1](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab02\report\image\1.png){#fig:001 width=70%}

После мы должны убедиться, что в открытом с помощью visudo файле присутствует строка %wheel ALL=(ALL) ALL (данная строка присутствует) (рис. [-@fig:002]):

![шаг 2](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab02\report\image\2.png){#fig:002 width=70%}

По закрытию файла создаём пользователя alice, входящего в группу wheel с помощью команды: useradd -G wheel alice. Нужно убедиться, что пользователь alice добавлен в группу wheel. Для этого введём команду id alice (Groups = 1001(alice),10(wheel)). Следующим шагом зададим пароль для пользователя alice, набрав passwd alice. Пароль требуется ввести дважды (рис. [-@fig:003]):

![шаг 3](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab02\report\image\3.png){#fig:003 width=70%}

Переключаемся на учётную запись пользователя alice командой: su alice. Создаём пользователя bob: sudo useradd bob. При запросе вводим пароль пользователя. Проверяем, что пользователь bob создан (id bob) и устанавливаем пароль для пользователя: sudo passwd bob (рис. [-@fig:004]):

![шаг 4](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab02\report\image\4.png){#fig:004 width=70%}

Теперь применим общие решения для создания учётных записей пользователей. Для этого переключимся в терминале на учётную запись пользователя root: su. Далее открываем файл конфигурации /etc/login.defs для редактирования, используя: vim /etc/login.defs (рис. [-@fig:005]):

![шаг 5](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab02\report\image\5.png){#fig:005 width=70%}

В файле требуется изменить несколько параметров. Для начала найдём параметр CREATE_HOME и убедимся, что он установлен в значение yes. Теперь установим параметр USERGROUPS_ENAB no. Это позволит не добавлять нового пользователя в группу с тем же именем, что и пользователь, а использовать группу users (рис. [-@fig:006]):

![шаг 6](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab02\report\image\6.png){#fig:006 width=70%}

После закрытия файла перейдём в каталог /etc/skel: cd /etc/skel. В этом каталоге создаём подкаталоги Pictures и Documents: mkdir Pictures Documents (это позволит добавить эти каталоги по умолчанию во все домашние каталоги пользователей). Выполняем проверку создания командой: ls. Теперь нам нужно изменить содержимое файла .bashrc, добавив строку: export EDITOR=/usr/bin/vim (рис. [-@fig:007]):

![шаг 7](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab02\report\image\7.png){#fig:007 width=70%}

Используя утилиту useradd, создаём пользователя carol: useradd carol и установим пароль для пользователя carol: passwd carol. Посмотрим информацию о пользователе carol: id carol (carol находится в группе users). Теперь нам нужно убедитесь, что каталоги Pictures и Documents были созданы в домашнем каталоге пользователя carol: su carol и ls (рис. [-@fig:008]):

![шаг 8](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab02\report\image\8.png){#fig:008 width=70%}


Изменим свойства пароля пользователя carol следующим образом: passwd -n 30 -w 3 -x 90 carol (в этой записи срок действия пароля истекает через 90 дней (-x 90). За три дня до истечения срока действия пользователь получит предупреждение (-w 3). Пароль должен использоваться как минимум за 30 дней (-n 30) до того, как его можно будет изменить) (рис. [-@fig:009]):

![шаг 9](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab02\report\image\9.png){#fig:009 width=70%}

Создаём ещё несколько пользователей: dan, dave, david, используя скрипт: for i in dan dave david; do useradd $i; done. Для этого создадим файл script.sh: touch script.sh. Командой mcedit открываем файл в редакторе. Теперь вносим скрипт в наш файл и выполняем сохранение
8
Переходим к запуску нашего скрипта командой bash. После успешного выполнения нам нужно убедиться, что идентификатор alice существует во всех трёх файлах: grep alice /etc/passwd /etc/shadow /etc/group и то, что идентификатор carol существует не во всех трёх файлах: grep carol /etc/passwd /etc/shadow /etc/group (рис. [-@fig:010]):

![шаг 10](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab02\report\image\10.png){#fig:010 width=70%}

На данном этапе требуется создать две группы и добавить некоторых пользователей в эти группы. Находясь под учётной записью пользователя root, создаём группы main и third: groupadd main, groupadd third. Затем, используем usermod для добавления пользователей alice и bob в группу main, а carol, dan, dave и david - в группу third:
usermod -aG main alice
usermod -aG main bob
usermod -aG third carol
usermod -aG third dan
usermod -aG third dave
usermod -aG third david
9
Убеждаемся, что пользователь carol правильно добавлен в группу third: id carol (пользователю carol должна быть назначена основная группа с идентификатором gid = 100 (users)) (рис. [-@fig:011])

![шаг 11](C:\Users\Nakov\work\study\2024-2025\OAOS\os2\labs\lab02\report\image\11.png){#fig:011 width=70%}

Ответы на контрольные вопросы
1. При помощи какой команды можно получить информацию о номере, назначенном пользователю Linux, о группах, в которые включён пользователь? id.
2. Какой UID имеет пользователь root? UID=0.
3. В чём состоит различие между командами su и sudo? Основное различие между ними заключается в пароле, который им требуется: в то время как "sudo" требует пароля текущего пользователя, " su " требует ввода пароля пользователя root. Совершенно очевидно, что "sudo" является лучшей альтернативой между ними с точки зрения безопасности.
4. В каком конфигурационном файле определяются параметры sudo? /etc/sudoers.
5. Какую команду следует использовать для безопасного изменения конфигурации sudo? Visudo.
10
6. Если вы хотите предоставить пользователю доступ ко всем командам администратора через sudo, членом какой группы он должен быть? Admin.
7. Какие файлы/каталоги можно использовать для определения параметров, которые будут использоваться при создании учётных записей пользователей? /etc/login.defs и /etc/default/useradd.
8. В каких файлах хранятся пароли пользователей, учётные записи групп? /etc/shadow /etc/group.
9. Какие команды вы можете использовать для изменения информации о пароле пользователя? passwd и gpasswd.
10. Сколько групп вы можете создать в файле /etc/passwd? Поясните свой ответ. Любое количество.
11. Какую команду следует использовать для изменения файла /etc/group вручную? emacs /etc/group или vim /etc/group.

# Выводы

В ходе выполнения лабораторной работы были получены представление о работе с учётными записями пользователей и группами пользователей в операционной системе типа Linux.

# Список литературы{.unnumbered}

::: {#refs}
:::
