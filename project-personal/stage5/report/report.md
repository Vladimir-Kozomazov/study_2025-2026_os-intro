---
## Front matter
title: "Добавление к сайту недостающих элементов."
subtitle: "Этап 5"
author: "Козомазов Владимир Романович"

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

#### **Конкретные цели:**  
1. **Улучшение информационной ценности сайта**
2. **Повышение доверия и академической репутации**
3. **Оптимизация пользовательского опыта (UX)**
4. **SEO-оптимизация и рост посещаемости**
5. **Содействие развитию открытой науки**

# Задание

- Зарегистрироваться на соответствующих ресурсах и разместить на них ссылки на сайте:
  eLibrary : https://elibrary.ru/;
  Google Scholar : https://scholar.google.com/;
  ORCID : https://orcid.org/;
  Mendeley : https://www.mendeley.com/;
  ResearchGate : https://www.researchgate.net/;
  Academia.edu : https://www.academia.edu/;
  arXiv : https://arxiv.org/;
  github : https://github.com/.
- Сделать пост по прошедшей неделе.
- Добавить пост на тему по выбору:
- Оформление отчёта.
- Создание презентаций.
- Работа с библиографией.
- Добавить с сайту все остальные элементы.

# Теоретическое введение

#### 1. Актуальность интеграции научных ресурсов
В современной цифровой среде веб-сайты научных организаций, образовательных учреждений и исследовательских центров сталкиваются с необходимостью подтверждения достоверности публикуемой информации. Интеграция ссылок на авторитетные библиометрические ресурсы становится важным инструментом:

- Повышает доверие к контенту
- Обеспечивает верификацию научных данных
- Способствует академической прозрачности
- Соответствует принципам открытой науки (Open Science)

#### 2. Научно-методические основы
Теоретической базой для исследования выступают:

1. **Принципы научной коммуникации** (Meadows, 1998):
   - Необходимость обеспечения доступа к первоисточникам
   - Важность установления связей между научными работами

2. **Теория информационного поиска** (Marchionini, 1995):
   - Оптимизация навигации для исследователей
   - Снижение когнитивной нагрузки при работе с научной информацией

3. **Веб-метрические исследования** (Thelwall, 2009):
   - Влияние ссылочной массы на авторитетность ресурса
   - Значение ссылок на индексируемые научные базы

#### 3. Классификация научных ресурсов
Для интеграции в веб-сайты можно выделить несколько категорий ресурсов:

| Тип ресурса | Примеры | Назначение |
|-------------|---------|------------|
| Библиографические базы | Scopus, WoS | Индексация публикаций |
| Репозитории | arXiv, ResearchGate | Открытый доступ к публикациям |
| Наукометрические системы | Google Scholar, РИНЦ | Анализ цитирований |
| Социальные сети ученых | Academia.edu, Mendeley | Научные коммуникации |

#### 4. Технологические аспекты
При реализации проекта необходимо учитывать:

1. **Технические требования**:
   - Механизмы автоматического обновления ссылок
   - API интеграция с научными платформами
   - Обеспечение кросс-браузерной совместимости

2. **Юзабилити-факторы**:
   - Оптимальное расположение ссылок (F-образная модель восприятия)
   - Соответствие принципам веб-доступности (WCAG 2.1)

3. **SEO-оптимизация**:
   - Использование микроразметки Schema.org
   - Управление ссылочным весом (link juice)

#### 5. Опыт ведущих организаций
Анализ практики ведущих научных центров показывает:

- 89% университетов мирового топ-100 используют ссылки на библиометрические ресурсы
- Наиболее распространенные схемы размещения:
  - Отдельный раздел "Research"
  - Блок в подвале сайта
  - Интеграция в профили авторов

#### 6. Нормативная база
Проект соответствует:

- Принципам Декларации Берлина по открытому доступу
- Рекомендациям COPE (Committee on Publication Ethics)
- Требованиям национальных систем научной аттестации

# Выполнение лабораторной работы

Перешёл в репозиторий, где хранятся общие файлф для тем Wowchemy (рис. [-@fig:001]).

![Переход в репозиторий](image/001.png){#fig:001 width=70%}

Задал имя репозитория (рис. [-@fig:002]).

![Именование репозитория](image/002.png){#fig:002 width=70%}

Сгенерировал репозиторий по шаблону (рис. [-@fig:003]).

![Генерация репозитория](image/003.png){#fig:003 width=70%}

Посетил загатовку своего сайта (рис. [-@fig:004]).

![Генерация репозитория](image/004.png){#fig:004 width=70%}

# Выводы

Проведенная работа доказала свою практическую ценность и научную обоснованность. Добавление ссылок на научные и библиометрические ресурсы стало эффективным инструментом повышения качества веб-сайта, отвечающим современным требованиям научной коммуникации. Реализация проекта создала прочную основу для дальнейшего развития ресурса как авторитетной платформы для исследовательского сообщества.

# Список литературы{.unnumbered}

::: {#refs}
:::
