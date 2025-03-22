---
## Front matter
title: "Лабораторная работа №3"
subtitle: "Модель боевых действий"
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
# Задание

Между страной $Х$ и страной $У$ идет война. Численность состава войск
исчисляется от начала войны, и являются временными функциями $x(t)$ и $y(t)$. В
начальный момент времени страна $Х$ имеет армию численностью $45 000$ человек, а
в распоряжении страны $У$ армия численностью в $50 000$ человек. Для упрощения
модели считаем, что коэффициенты $a, b, c, h$ постоянны. Также считаем $P(t)$  и $Q(t)$ 
непрерывные функции.

Постройте графики изменения численности войск армии Х и армии У для
следующих случаев:

1. Модель боевых действий между регулярными войсками

$$
\dfrac{dx}{dt} = -0.29x(t) - 0.67y(t) + |sin(t) + 1|
$$

$$
\dfrac{dy}{dt} = -0.6x(t) - 0.38y(t) + |cos(t) + 1|
$$

2. Модель ведение боевых действий с участием регулярных войск и
партизанских отрядов

$$
\dfrac{dx}{dt} = -0.31x(t) - 0.67y(t) + 2|sin(t)|
$$

$$
\dfrac{dy}{dt} = -0.42x(t) - 0.53y(t) + |cos(t) + 1|
$$


# Теоретическое введение

Рассмотрим некоторые простейшие модели боевых действий – модели
Ланчестера. В противоборстве могут принимать участие как регулярные войска,
так и партизанские отряды. В общем случае главной характеристикой соперников
являются численности сторон. Если в какой-то момент времени одна из
численностей обращается в нуль, то данная сторона считается проигравшей (при
условии, что численность другой стороны в данный момент положительна)


# Выполнение лабораторной работы

В первом случае численность регулярных войск определяется тремя
факторами:

* скорость уменьшения численности войск из-за причин, не связанных с
боевыми действиями (болезни, травмы, дезертирство);

* скорость потерь, обусловленных боевыми действиями
противоборствующих сторон (что связанно с качеством стратегии,
уровнем вооружения, профессионализмом солдат и т.п.);

* скорость поступления подкрепления (задаётся некоторой функцией от
времени).

В этом случае модель боевых действий между регулярными войсками
описывается следующим образом

$$
\dfrac{dx}{dt} = -0.29x(t) - 0.67y(t) + |sin(t) + 1|
$$

$$
\dfrac{dy}{dt} = -0.6x(t) - 0.38y(t) + |cos(t) + 1|
$$

Потери, не связанные с боевыми действиями, описывают члены $-0.29x(t)$ и $- 0.38y(t)$
, члены $- 0.67y(t)$ и $-0.6x(t)$
отражают потери на поле боя.
Коэффициенты $- 0.67$ и $-0.6$ указывают на эффективность боевых действий со
стороны у и х соответственно, $-0.29$ $- 0.38$ - величины, характеризующие степень
влияния различных факторов на потери. Функции  учитывают $|sin(t) + 1|$ и $|cos(t) + 1|$
возможность подхода подкрепления к войскам $Х$ и $У$ в течение одного дня.

Программный код для 1 случая выглядит следующим образом:

```Julia
using DifferentialEquations, Plots;

function reg(u, p, t)
    x, y = u
    a, b, c, h = p
    dx = -a*x - b*y+ abs(sin(t) + 1)
    dy = -c*x -h*y+abs(cos(t)+1)
    return [dx, dy]
end

u0 = [45000, 50000]
p = [0.29, 0.67, 0.6, 0.38]
tspan = (0,1)

prob = ODEProblem(reg, u0, tspan, p)

sol = solve(prob, Tsit5())

plot(sol, title = "Модель боевых действий между регулярными войсками",  label = ["Армия X" "Армия Y"], xaxis = "Время", yaxis = "Численность армии")
```

![Модель боевых действий между регулярными войсками](image/image.png)

Во втором случае в борьбу добавляются партизанские отряды. Нерегулярные
войска в отличии от постоянной армии менее уязвимы, так как действуют скрытно,
в этом случае сопернику приходится действовать неизбирательно, по площадям,
занимаемым партизанами. Поэтому считается, что тем потерь партизан,
проводящих свои операции в разных местах на некоторой известной территории,
пропорционален не только численности армейских соединений, но и численности
самих партизан. В результате модель принимает вид:

$$
\dfrac{dx}{dt} = -0.31x(t) - 0.67y(t) + 2|sin(t)|
$$

$$
\dfrac{dy}{dt} = -0.42x(t) - 0.53y(t) + |cos(t) + 1|
$$

Программный код для 2 случая выглядит следующим образом:

```Julia
function reg_2(u, p, t)
    x, y = u
    a, b, c, h = p
    dx = -a*x - b*y+ 2*abs(sin(2t))
    dy = -c*x -h*y+abs(cos(t)+1)
    return [dx, dy]
end

u0 = [45000, 50000]
p = [0.31, 0.67, 0.42, 0.53]
tspan = (0,1)

prob = ODEProblem(reg_2, u0, tspan, p)

sol = solve(prob, Tsit5())

plot(sol, title = "Модель боевых действий c участием регулярных войск и партизанских отрядов",  label = ["Армия X" "Армия Y"], xaxis = "Время", yaxis = "Численность армии")
```

![Модель боевых действий c участием регулярных войск и партизанских отрядов](image/image-1.png)

# Выводы

В результате данной лабораторной работы была построена модель боевых действий на языке прогаммирования Julia.

# Список литературы{.unnumbered}

::: {#refs}
:::
