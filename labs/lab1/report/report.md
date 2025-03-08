---
## Front matter
title: "Лабораторная работа №1"
subtitle: "Работа с git"
author: "Акопян Сатеник"

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

Целью данной лабораторной работы является получение практических навыков по работе с git.


# Выполнение лабораторной работы

1. Настройка core.autocrlf с параметрами true и input делает все переводы
строк текстовых файлов в главном репозитории одинаковы.

![рисунок 1 ](image/1.png){#fig:001 width=70%}

2. Установка отображения unicode

![рисунок 2 ](image/2.png){#fig:002 width=70%}

3. Начните работу в пустом рабочем каталоге с создания пустого каталога с именем
hello, затем войдите в него и создайте там файл с именем hello.html.

![рисунок 3 ](image/3.png){#fig:003 width=70%}

4. Чтобы создать git репозиторий из этого каталога, выполните команду git init.

5. Добавим файл в репозиторий

![рисунок 4](image/4.png){#fig:004 width=70%}

6. Проверка состояние репозитория

![рисунок 5](image/5.png){#fig:005 width=70%}

7. Добавим кое-какие HTML-теги к нашему приветствию. 

![рисунок 6](image/6.png){#fig:006 width=70%}

Проверьте состояние рабочего каталога.

![рисунок 7](image/7.png){#fig:007 width=70%}

8. Теперь выполните команду git, чтобы проиндексировать изменения. Проверьте
состояние.

![рисунок 8](image/8.png){#fig:008 width=70%}

9. Сделайте коммит и проверьте состояние.

![рисунок 9](image/9.png){#fig:009 width=70%}

Теперь еще раз проверим состояние.

![рисунок 10](image/10.png){#fig:010 width=70%}

![рисунок 11](image/11.png){#fig:011 width=70%}


10. Добавьте стандартные теги страницы

![рисунок 12](image/12.png){#fig:012 width=70%}

Теперь добавьте это изменение в индекс git

![рисунок 13](image/13.png){#fig:013 width=70%}

11. Теперь добавьте заголовки HTML (секцию <head>) к странице «Hello, World».

![рисунок 14](image/14.png){#fig:014 width=70%}

Проверьте текущий статус

![рисунок 15](image/15.png){#fig:015 width=70%}

12. Произведите коммит проиндексированного изменения

![рисунок 16](image/18.png){#fig:016 width=70%}

13. Получим список произведенных изменений

![рисунок 17](image/19.png){#fig:017 width=70%}

14. Изучите данные лога и найдите хэш для первого коммита.

![рисунок 18](image/20.png){#fig:018 width=70%}

![рисунок 19](image/21.png){#fig:019 width=70%}

15. Вернитесь к последней версии в ветке master

![рисунок 20](image/22.png){#fig:020 width=70%}

16. Давайте назовем текущую версию страницы hello первой (v1).

![рисунок 21](image/23.png){#fig:021 width=70%}

![рисунок 22](image/24.png){#fig:022 width=70%}

17. Давайте сделаем ее версией v1-beta

![рисунок 23](image/25.png){#fig:023 width=70%}

18. Теперь попробуйте попереключаться между двумя отмеченными версиями.

![рисунок 24](image/26.png){#fig:024 width=70%}

19. Вы можете увидеть, какие теги доступны, используя команду git tag

![рисунок 25](image/27.png){#fig:025 width=70%}

20. Вы также можете посмотреть теги в логе.

![рисунок 26](image/28.png){#fig:026 width=70%}

21. Внесите изменение в файл hello.html в виде нежелательного комментария

![рисунок 27](image/30.png){#fig:027 width=70%}

22. Сначала проверьте состояние рабочего каталога.

![рисунок 28](image/31.png){#fig:028 width=70%}

23. Используйте команду git checkout для переключения версии файла hello.html в репозитории.

![рисунок 29](image/32.png){#fig:029 width=70%}

24. Внесите изменение в файл hello.html в виде нежелательного комментария

![рисунок 30](image/33.png){#fig:030 width=70%}

Проиндексируйте это изменение, проверьте состояние нежелательного изменения

![рисунок 31](image/34.png){#fig:031 width=70%}

25. К счастью, вывод состояния показывает нам именно то, что мы должны сделать
![рисунок 32](image/35.png){#fig:032 width=70%}


# Выводы

Здесь кратко описываются итоги проделанной работы.

# Список литературы{.unnumbered}

::: {#refs}
:::
