---
## Front matter
lang: ru-RU
title: Создание образа виртуальной машины
subtitle: Презентация по лабораторной работе №1
author: Козомазов Владимир Романович
supervisor:
  - Кулябов Д. С. 
    * д.ф.-м.н., профессор
    * профессор кафедры прикладной информатики и теории вероятностей
    * Российский университет дружбы народов
    * [kulyabov-ds@rudn.ru](mailto:kulyabov-ds@rudn.ru)
    * <https://yamadharma.github.io/ru/>
institute: Российский университет дружбы народов, Москва, Россия
date: 06 марта 2025

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
---

# Информация

## Докладчик

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

  * Козомазов Владимир Романович
  * студент факультета ФМЕН
  * Российский университет дружбы народов
  * [1132246812@pfur.com](mailto:1132246812@pfur.com)

:::
::: {.column width="30%"}

![]()

:::
::::::::::::::

# Вводная часть

## Актуальность

Актуальность виртуализации обусловлена её способностью решать ключевые задачи современного ИТ-мира: оптимизация ресурсов, снижение затрат, повышение гибкости и безопасности. Она стала неотъемлемой частью облачных вычислений, DevOps, корпоративных инфраструктур и даже домашнего использования. С развитием технологий виртуализация продолжает оставаться важным инструментом для инноваций и эффективного управления ИТ-ресурсами.

## Объект и предмет исследования

Объектом и предсетом исследования является виртуализция в современных операционных системах

## Цели и задачи

- Развитие практических навыков, которые необходимы для работы в современной ИТ-индустрии
- Получение теоретических знаний

## Материалы и методы

- Работа выполнялась на базе операционной системе Windows и виртуальной машины VirtualBox
- Устанавливалась операционная система Fedora Linux Sway 41

# Выполнение работы

## Настройка виртуальной машины 

- Создание пользователя с помощью команды `liveinst`
- Установка обновлений командой `dnf update`
- Установка tmux и mc

## Установка автообновлений

- Установка автообновлений с помощью команды `dnf install dnf-automatic`
- В файлее automatic.conf пишем следующиее команды: `[commands]`,`download_updates = yes`,`apply_updates = no`,`upgrade_type = default`
- Используем команду `systemctl enable --now dnf-automatic.timer`

## Установка драйверов для виртуальной машины

- С помощью команды `dnf -y install dkms` подгоняем модуль под текущее ядро
- Командой `mount /dev/sr0 /mqdia/` подмонтируем
- Подключаем диск
- Устанавлием и запускаем драйвера с помощью команды `./VBoxLinuxAdditions run`
- Перезапускаем виртуальную машину командой `reboot`

## Изменение имени хоста

- Меняем имя хоста на vkozomazov с помощью команды `hostnamectl set-hostname vkozomazov`
- Проверяем, что замена прошла успешно командой `hostnamectk`

## Установка pandoc и texlive

- Установим все необходимые пакеты для дальнейшей пвботы с помощью команды `dnf -y install pandoc`
- Установим texlive командой `dnf -y install texlive texlive\*`
- Проверим после установки, что все пакеты были установлены, в частности `lualatex`, `pdflatex`, `xelatex`

# Результаты

## Итоги

В ходе выполнения лабораторной работы №1 были получены навыки по созданию и настраиванию виртуальной машины для дальнейшей работы с ней.


