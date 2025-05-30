---
## Front matter
lang: ru-RU
title: Менеджер паролей pass
subtitle: Лабораторная работа №8
author: Козомазов Владимир Романович
institute: Российский университет дружбы народов, Москва, Россия
date: 5 апреля 2025

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
  * Студент факультета ФМЕН
  * Российский университет дружбы народов
:::
::: {.column width="30%"}

![](./image/001.jpg)

:::
::::::::::::::

# Вводная часть

## Актуальность

Pass остается актуальным инструментом благодаря своей простоте, безопасности и интеграции с Unix-экосистемой. Он идеально подходит для пользователей, которые ценят локальное хранение данных, открытый исходный код и гибкость в управлении паролями. В условиях растущих угроз кибербезопасности pass предоставляет надежное решение для защиты учетных данных.

## Объект и предмет исследования

Объект исследования 
- Менеджер паролей pass как инструмент для управления паролями

Предмет исследования 
- Принципы работы 
- Функциональные возможности 
- Безопасность 
- Практическое применение

Четкое определение объекта и предмета исследования позволяет сосредоточиться на ключевых аспектах темы и провести глубокий анализ менеджера паролей pass.

## Цели и задачи

Цель установки менеджера паролей — обеспечить безопасное, удобное и эффективное управление учетными данными. Менеджер паролей помогает:
- Создавать и использовать сложные уникальные пароли.
- Защищать данные от утечек и атак.
- Упрощать процесс входа на сайты и в приложения.
- Организовывать и синхронизировать пароли между устройствами.

## Установка менеджера паролей pass

- Установка менеджера паролей `sudo dnf install pass pass-otp`, `sudo dnf install gopass`

## Настройка

- Инициализация хранилища, командой `pass init <gpg-id>`
- Создание структуры git `pass git init`
- Синхронизация `pass git pull`, `pass git push`
- Проверка статуса синхронизации `pass git status`

## Сохранение пароля

- Добавил новый пароль `pass insert [OPTIONAL DIR]/[FILENAME]`
- Отобразил пароль для указанного имени файла `pass [OPTIONAL DIR]/[FILENAME]`
- Заменил существующий пароль `pass generate --in-place FILENAME`

## Дополнительное программное обеспечение

Установил дополнительное программное обеспечение:
sudo dnf -y install \
         dunst \
         fontawesome-fonts \
         powerline-fonts \
         light \
         fuzzel \
         swaylock \
         kitty \
         waybar swaybg \
         wl-clipboard \
         mpv \
         grim \
         slurp

## Дополнительное программное обеспечение

Установил шрифты:
  `sudo dnf copr enable peterwu/iosevka`
  `sudo dnf search iosevka`
  `sudo dnf install iosevka-fonts iosevka-aile-fonts iosevka-curly-fonts iosevka-slab-fonts iosevka-etoile-fonts iosevka-term-fonts`

## Установка

- Установка бинарного файла `sh -c "$(wget -qO- chezmoi.io/get)"`

## Создание собственного репозитория с помощью утилит

Создал репозиторий на основе шаблона 

## Подключение репозитория к своей системе

- Инициализировал chezmoi с моим репозиторием `chezmoi init git@github.com:<username>/dotfiles.git`
- Проверил внесённые изменения `chezmoi diff`

## Ежедневные операции c chezmoi

- Включил функцию автоматической фиксации и отправке изменений в репозиторий:
  [git]
    autoCommit = true
    autoPush = true

# Результаты

**pass** — это мощный и гибкий менеджер паролей, который сочетает в себе простоту использования, высокий уровень безопасности и интеграцию с Unix-экосистемой. Он идеально подходит для пользователей, которые предпочитают консольные инструменты и хотят иметь полный контроль над своими данными. Благодаря использованию GPG и Git, **pass** обеспечивает надежное шифрование и удобную синхронизацию паролей между устройствами.