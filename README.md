# Лабораторная работа №2: Изучение систем контроля версий на примере Git

## Выполнила: Алексеева Ольга

---

## Цель работы

Изучить основные возможности системы контроля версий Git: создание репозитория, работа с файлами, ветвление, разрешение конфликтов, оформление отчётов.

---

## Часть 1. Базовые настройки и структура репозитория (Tutorial)

### 1.1. Настройка окружения

```bash
export GITHUB_USERNAME=OlgaIAK
export GITHUB_EMAIL=ovalekseeva07@mail.ru
### 1.2. Создание репозитория
mkdir -p ~/OlgaIAK/workspace/projects/lab02
cd ~/OlgaIAK/workspace/projects/lab02
git init
git remote add origin https://github.com/OlgaIAK/lab02.git
