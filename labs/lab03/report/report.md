---
## Front matter
title: "ЛАБОРАТОРНАЯ РАБОТА №2"
subtitle: "Отчёт"
author: "Глобин Никита Анатольевич"

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

Целью работы является изучение идеологии и применение средств контроля версий.
Приобретение практических навыков с системой git.

# Задание

Базовая настройка git  
Задание №2. Создание SSH ключа  
Задание №3. Создание рабочего пространства и репозитория курса на основе шаблона  
Задание №4. Создание репозитория курса  
Задание №5. Настройка каталога курса  

# Выполнение лабораторной работы
## Задание №1. Базовая настройка git

1. Сначала сделаем предварительную конфигурацию git. Откройте терминал и введите
следующие команды, указав имя и email владельца репозитория:
```
git config --global user.name “<Name Surname>” git
config --global user.email “<work@mail>”
```

![](/![](/home/dodo/work/study/2023-2024/Архитектура компьютера/arch-pc/arch-pc/labs/lab02/report/image/image 1 for lab02.png){#fig:001 width=70%}
Рис. 1.1. Задаём имя и email репозитория.



2. Настроим utf-8 в выводе сообщений git:

```
git config --global core.quotepath false
```


![](/![](/home/dodo/work/study/2023-2024/Архитектура компьютера/arch-pc/arch-pc/labs/lab02/report/image/image 2 for lab02.png ""){#fig:fig1 width=70% }
Рис. 1.2. Настраиваем utf-8.


3. Зададим имя начальной ветки (будем называть её master):

```
git config --global init.defaultBranch master
```

![](/![](/home/dodo/work/study/2023-2024/Архитектура компьютера/arch-pc/arch-pc/labs/lab02/report/image/image 3 for lab02.png ""){#fig:fig1 width=70% }
Рис. 1.3. Задаём имя начальной ветки (master).


4. Параметр autocrlf:


```
git config --global core.autocrlf input
```
![](/![](/home/dodo/work/study/2023-2024/Архитектура компьютера/arch-pc/arch-pc/labs/lab02/report/image/image 4 for lab02.png ""){#fig:fig1 width=70% }
Рис. 1.4. Устанавливаем параметр autocrlf.


5. Параметр safecrlf:

![](/![](/home/dodo/work/study/2023-2024/Архитектура компьютера/arch-pc/arch-pc/labs/lab02/report/image/image 5 for lab02.png ""){#fig:fig1 width=70% }
Рис. 1.5. Устанавливаем настройку safecrlf.




## Задание №2. Создание SSH ключа.

Для последующей идентификации пользователя на сервере репозиториев необходимо
сгенерировать пару ключей (приватный и открытый):
ssh-keygen -C “Имя Фамилия <work@mail>”


![](/![](/home/dodo/work/study/2023-2024/Архитектура компьютера/arch-pc/arch-pc/labs/lab02/report/image/image 6 for lab02.png ""){#fig:fig1 width=70% }
Рис. 2.1. Генерируем пару ключей.


Ключи сохранятся в каталоге ~/.ssh/.
Далее необходимо загрузить сгенерённый ключ.
Скопировав ключ из локальной сети в буфер обмена, вставляем его в поле на сайте. cat
~/.ssh/id_rsa.pub | xclip -sel clip

![](/![](/home/dodo/work/study/2023-2024/Архитектура компьютера/arch-pc/arch-pc/labs/lab02/report/image/image 7 for lab02.png ""){#fig:fig1 width=70% }
Рис. 2.1. Генерируем пару ключей.


Заходим в свой аккаунт на сайте github и переходим в настройки, добавляем
скопированный ключ и указываем имя ключа (Title).

![](/![](/home/dodo/work/study/2023-2024/Архитектура компьютера/arch-pc/arch-pc/labs/lab02/report/image/image 8 for lab02.png ""){#fig:fig1 width=70% }
Рис. 2.4. Проверяем добавление ключа.


## Задание №3. Создание рабочего пространства и репозитория курса на основе шаблона.

Открываем терминал для создания рабочего пространства.

![](/![](/home/dodo/work/study/2023-2024/Архитектура компьютера/arch-pc/arch-pc/labs/lab02/report/image/image 9 for lab02.png ""){#fig:fig1 width=70% }
Рис. 3.1. Создаём каталог для предмета «Архитектура компьютера».




## Задание №4. Создание репозитория курса.

Переходим на страницу репозитория с шаблоном.

![](/![](/home/dodo/work/study/2023-2024/Архитектура компьютера/arch-pc/arch-pc/labs/lab02/report/image/image 10 for lab02.png ""){#fig:fig1 width=70% }
Рис. 4.1. Создаём репозиторий по шаблону и называем его «study_2024–2025_arh-pc».


Открываем терминал:

![](/![](/home/dodo/work/study/2023-2024/Архитектура компьютера/arch-pc/arch-pc/labs/lab02/report/image/image 11 for lab02.png ""){#fig:fig1 width=70% }

Рис. 4.2. Переходим в каталог курса и клонируем созданный репозиторий.




## Задание №5. Настройка каталога курса.

![](/![](/home/dodo/work/study/2023-2024/Архитектура компьютера/arch-pc/arch-pc/labs/lab02/report/image/image 12 for lab02.png ""){#fig:fig1 width=70% }
Рис. 5.1. Переходим в каталог курса.


![](/![](/home/dodo/work/study/2023-2024/Архитектура компьютера/arch-pc/arch-pc/labs/lab02/report/image/image 13 for lab02.png ""){#fig:fig1 width=70% }
Рис. 5.2. Удаляем лишние файлы.

![](/![](/home/dodo/work/study/2023-2024/Архитектура компьютера/arch-pc/arch-pc/labs/lab02/report/image/image 14 for lab02.png ""){#fig:fig1 width=70% }
Рис. 5.3. Создаем необходимые каталоги.

![](/![](/home/dodo/work/study/2023-2024/Архитектура компьютера/arch-pc/arch-pc/labs/lab02/report/image/image 15 for lab02.png ""){#fig:fig1 width=70% }
Рис. 5.4. Отслеживаем файл и записываем изменения в репозиторий.

![](/![](/home/dodo/work/study/2023-2024/Архитектура компьютера/arch-pc/arch-pc/labs/lab02/report/image/image 16 for lab02.png ""){#fig:fig1 width=70% }
Рис. 5.5. Отправляем файлы на сервер.

![](/![](/home/dodo/work/study/2023-2024/Архитектура компьютера/arch-pc/arch-pc/labs/lab02/report/image/image 16 for lab02.png ""){#fig:fig1 width=70% }




# Выводы

В ходе выполнения лабораторной работы я познакомился с системой git, и научился ей
пользоваться.


::: {#refs}
:::
