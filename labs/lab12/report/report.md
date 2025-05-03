---
## Front matter
title: "Программирование в командном процессоре ОС UNIX. Командные файлы"
subtitle: "Лабораторная работа №11"
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

Цель работы "Программирование в командном процессоре ОС UNIX. Командные файлы" заключается в освоении навыков создания и выполнения командных файлов (shell-скриптов) в UNIX-подобных операционных системах.

# Задание

1. Написать скрипт, который при запуске будет делать резервную копию самого себя в другую директорию backup в моём домашнем каталоге.
2. Написать пример командного файла, обрабатывающего любое произвольное число аргументов командной строки, в том числе превышающее десять.
3. Написать командный файл — аналог команды ls (без использования самой этой команды и команды dir). Требуется, чтобы он выдавал информацию о нужном каталоге и выводил информацию о возможностях доступа к файлам этого каталога.
4. Написать командный файл, который получает в качестве аргумента командной строки формат файла (.txt, .doc, .jpg, .pdf и т.д.) и вычисляет количество таких файлов в указанной директории.

# Теоретическое введение

#### **1. Командный процессор (shell) в UNIX**  
Командный процессор (интерпретатор команд, *shell*) — это программа, обеспечивающая взаимодействие пользователя с операционной системой UNIX. Он принимает команды, выполняет их и возвращает результат.  

**Популярные shell-процессоры:**  
- **Bash (Bourne-Again SHell)** — стандартный в большинстве Linux-дистрибутивов.  
- **sh (Bourne Shell)** — более старый, но совместимый с Bash.  
- **zsh, ksh, csh** — альтернативные оболочки с дополнительными возможностями.  

#### **2. Командные файлы (shell-скрипты)**  
Командный файл — это текстовый файл, содержащий последовательность команд для выполнения в shell.  

**Особенности shell-скриптов:**  
- Исполняются интерпретатором (не требуют компиляции).  
- Могут принимать аргументы командной строки.  
- Поддерживают переменные, условия, циклы, функции.  
- Могут вызывать другие программы и скрипты.  

#### **3. Основные элементы shell-программирования**  

##### **3.1. Структура скрипта**  
```bash
#!/bin/bash  # Шебанг (указывает интерпретатор)
# Комментарии начинаются с #

echo "Hello, World!"  # Простая команда
```

##### **3.2. Переменные**  
- Объявление: `VAR=value` (без пробелов!).  
- Использование: `$VAR` или `${VAR}`.  
```bash
name="User"
echo "Hello, $name!"  # Hello, User!
```

##### **3.3. Параметры командной строки**  
- `$0` — имя скрипта.  
- `$1`, `$2`, ... — аргументы.  
- `$#` — количество аргументов.  
- `$*` или `$@` — все аргументы.  

##### **3.4. Управляющие конструкции**  
- **Условия:**  
  ```bash
  if [ "$1" -eq 10 ]; then
      echo "Аргумент равен 10"
  else
      echo "Аргумент не равен 10"
  fi
  ```
- **Циклы:**  
  ```bash
  for file in *.txt; do
      echo "Обработка $file"
  done
  ```

##### **3.5. Перенаправление ввода/вывода**  
- `>` — вывод в файл (перезапись).  
- `>>` — вывод в файл (дополнение).  
- `<` — ввод из файла.  
- `|` — конвейер (передача вывода одной команды на вход другой).  

##### **3.6. Коды возврата и обработка ошибок**  
- `$?` — код завершения последней команды (0 — успех, иначе ошибка).  
- `set -e` — завершить скрипт при ошибке.  
- `trap` — перехват сигналов.  

#### **4. Пример скрипта**  
```bash
#!/bin/bash
# Скрипт для поиска файлов и вывода информации

if [ $# -eq 0 ]; then
    echo "Использование: $0 <каталог>"
    exit 1
fi

dir=$1
echo "Файлы в каталоге $dir:"
find "$dir" -type f -exec ls -l {} \;
```

#### **5. Практическое применение**  
- Автоматизация рутинных задач (резервное копирование, логирование).  
- Обработка текстовых данных (логи, CSV).  
- Управление системными процессами.  

### **Заключение**  
Shell-скрипты — мощный инструмент для автоматизации в UNIX. Они позволяют комбинировать системные команды, обрабатывать данные и управлять ОС без написания сложных программ.  

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
  
В ходе выполнения работы были изучены ключевые аспекты создания и использования командных файлов (shell-скриптов) в UNIX-подобных системах.
 
# Список литературы{.unnumbered}

::: {#refs}
:::
