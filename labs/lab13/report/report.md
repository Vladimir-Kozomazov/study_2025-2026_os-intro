---
## Front matter
title: "Программирование в командном процессоре ОС UNIX. Ветвления и циклы"
subtitle: "Лабораторная работа №13"
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

**Главная цель:**  
Изучить и практически освоить использование **ветвлений и циклов** в командных процессорах UNIX (Bash, sh, zsh) для создания эффективных и надежных shell-скриптов, автоматизирующих задачи в UNIX-подобных системах.  

### **Конкретные цели работы**  

1. **Теоретическое освоение конструкций ветвления и циклов**  
2. **Практическое применение знаний**  
3. **Оптимизация и отладка скриптов**  
4. **Автоматизация реальных задач**  
5. **Сравнение и анализ**  

Цель работы — не просто изучить синтаксис, а **научиться применять ветвления и циклы для решения реальных задач** в UNIX-системах.

# Задание

### **Практическое задание**  
**по теме:**  
**«Программирование в командном процессоре ОС UNIX. Ветвления и циклы»**  

---

## **Цель задания**  
Закрепить навыки написания shell-скриптов с использованием:  
✔ **Ветвлений** (`if-else`, `case`)  
✔ **Циклов** (`for`, `while`, `until`)  
✔ **Управляющих команд** (`break`, `continue`, `exit`)  

---

## **Задачи**  

### **1. Базовые упражнения**  
**1.1. Скрипт с ветвлением (`if-else`)**  
**1.2. Скрипт с `case`**  
### **2. Работа с циклами**  
**2.1. Скрипт с циклом `for`**  
**2.2. Скрипт с циклом `while`**  
**2.3. Скрипт с `until`**  
### **3. Комбинированные задания**  

# Теоретическое введение

## **1. Командные процессоры UNIX**  
Командные процессоры (shell) — это интерпретаторы команд, обеспечивающие взаимодействие пользователя с операционной системой UNIX/Linux. Наиболее распространенные:  
- **Bash** (Bourne-Again SHell) — стандартный в большинстве дистрибутивов.  
- **sh** (Bourne Shell) — более старый, но обеспечивает совместимость.  
- **zsh**, **ksh** — расширенные версии с дополнительными функциями.  

**Особенности shell-скриптов:**  
- Интерпретируются построчно.  
- Не требуют компиляции.  
- Могут включать команды ОС, переменные и управляющие конструкции.  

---

## **2. Ветвления в shell-скриптах**  
Ветвления позволяют изменять порядок выполнения скрипта в зависимости от условий.  

### **2.1. Конструкция `if-elif-else`**  
```bash
if [ условие ]; then  
    # команды при истинности  
elif [ другое_условие ]; then  
    # альтернативные команды  
else  
    # команды по умолчанию  
fi  
```  
**Пример:**  
```bash
if [ -f "file.txt" ]; then  
    echo "Файл существует."  
else  
    echo "Файл не найден."  
fi  
```  

### **2.2. Конструкция `case`**  
Используется для множественного ветвления:  
```bash
case $переменная in  
    шаблон1) команды ;;  
    шаблон2) команды ;;  
    *) команды_по_умолчанию ;;  
esac  
```  
**Пример:**  
```bash
case $1 in  
    "start") echo "Запуск службы..." ;;  
    "stop") echo "Остановка..." ;;  
    *) echo "Неизвестная команда" ;;  
esac  
```  

---

## **3. Циклы в shell-скриптах**  
Циклы используются для многократного выполнения команд.  

### **3.1. Цикл `for`**  
Перебирает элементы списка:  
```bash
for переменная in список; do  
    команды  
done  
```  
**Пример:**  
```bash
for file in *.txt; do  
    echo "Обработка $file"  
done  
```  

### **3.2. Цикл `while`**  
Выполняется, пока условие истинно:  
```bash
while [ условие ]; do  
    команды  
done  
```  
**Пример:**  
```bash
count=1  
while [ $count -le 5 ]; do  
    echo "Итерация $count"  
    ((count++))  
done  
```  

### **3.3. Цикл `until`**  
Выполняется, пока условие ложно (антипод `while`):  
```bash
until [ условие ]; do  
    команды  
done  
```  
**Пример:**  
```bash
until ping -c1 example.com &>/dev/null; do  
    echo "Ожидание ответа от example.com..."  
    sleep 2  
done  
```  

---

## **4. Управление выполнением**  
- **`break`** — досрочный выход из цикла.  
- **`continue`** — переход к следующей итерации.  
- **`exit N`** — завершение скрипта с кодом `N` (0 — успех, 1+ — ошибка).  

**Пример:**  
```bash
for i in {1..10}; do  
    if [ $i -eq 5 ]; then  
        break  
    fi  
    echo $i  
done  
```  

---

## **5. Проверка условий**  
Условия проверяются с помощью:  
- **`[ ]`** или **`test`** — стандартный синтаксис.  
- **`[[ ]]`** — расширенный (поддерживает `&&`, `||`, регулярные выражения).  
- **`(( ))`** — для арифметических операций.  

**Операторы сравнения:**  
- **Файлы:** `-f` (существует), `-d` (директория), `-r` (доступ на чтение).  
- **Строки:** `=`, `!=`, `-z` (пустая строка).  
- **Числа:** `-eq`, `-ne`, `-lt`, `-gt`.  

**Пример:**  
```bash
if [[ "$str" == "admin" && $num -gt 10 ]]; then  
    echo "Доступ разрешен."  
fi  
```  

---

## **6. Особенности разных shell**  
- **Bash**: Поддержка массивов, арифметики `(( ))`, подстановки `{1..10}`.  
- **POSIX sh**: Ограниченный функционал (нет `[[ ]]`, массивов).  
- **zsh**: Дополнительные возможности (глобализация, проверка орфографии).  

# Выполнение лабораторной работы

Установил менеджер паролей `pass` с помощью команды `sudo dnf install pass pass-otp` (рис. [-@fig:001]).

![Установка менеджера паролей](image/001.png){#fig:001 width=70%}

Завершил установку менеджера паролей командой `sudo dnf install gopass` (рис. [-@fig:002]).

![Завершение установки менеджера паролей](image/002.png){#fig:002 width=70%}

Просмотрел список `gpg` ключей при помощи команды `gpg --list-secret-keys` (рис. [-@fig:003]).

![Просмотр списка ключей](image/003.png){#fig:003 width=70%}

Иницилизировал хранилище, написав команду `pass init <gpg-id> (рис. [-@fig:004]).

![Иницилизация хранилища](image/004.png){#fig:004 width=70%}

Создал структуру с git командой `pass git init` (рис. [-@fig:005]).

![Создание структуры](image/005.png){#fig:005 width=70%}

Синхронизировался с git командами `pass git pull`, `pass git push`

Вручную закоммитил и выложил изменения командами (рис. [-@fig:006]).

![Ручное выкладывание изменений](image/006.png){#fig:006 width=70%}

Проверил статус синхронизации командой `pass git status` (рис. [-@fig:007]).

![Проверка статуса синхронизаций](image/007.png){#fig:007 width=70%}

Добавил новый пароль командой `pass insert [OPTIONAL DIR]/[FILENAME]` (рис. [-@fig:008]).

![Добавление нового пароля](image/008.png){#fig:008 width=70%}

Отобразил пароль для указанного имени файла `pass [OPTIONAL DIR]/[FILENAME]` 

Установил дополнительное программное обеспечение (рис. [-@fig:009]).

![Установка дополнительного программного обеспечения](image/009.png){#fig:009 width=70%}

Установил дополнительно шрифты командами `sudo dnf copr enable peterwu/iosevka`, `sudo dnf search iosevka`, `sudo dnf install iosevka-fonts iosevka-aile-fonts iosevka-curly-fonts iosevka-slab-fonts iosevka-etoile-fonts iosevka-term-fonts` (рис. [-@fig:010]).

![Установка дополнительных шрифтов](image/010.png){#fig:010 width=70%}

Установил бинарный файл командой `sh -c "$(wget -qO- chezmoi.io/get)"` 

Создал собственный репозиторий при помощи утилит на основе шаблона

Подключил репозиторий к своей системе

Использовал chezmoi на нескольких машинах

Настроил новую машину с помощью одной команды

Включил функцию автоматической фиксации и отправлении изменений в репозиторий

# Выводы
  
## **Итог**  
Ветвления и циклы — **фундамент shell-программирования**, который открывает возможности для:  
✅ **Создания сложных скриптов** с минимальными усилиями.  
✅ **Эффективного администрирования** UNIX-систем.  
✅ **Построения автоматизированных рабочих процессов**.  

**Освоение этих концепций — важный шаг** к профессиональной работе с командной строкой Linux/UNIX.

# Список литературы{.unnumbered}

::: {#refs}
:::
