# Лабораторная работа: Настройка CI (Travis CI и AppVeyor)

## 📋 Описание

Во второй лабораторной работе в рамках стажировки в "Formatter Inc." нужно было настроить системы непрерывной интеграции (CI) для автоматической сборки C++-проектов на разных платформах.

Цель — проверить, что проект корректно собирается и работает как на Linux (gcc/clang), так и на Windows (MSVC), без ручной сборки и тестирования.

---

## 🧰 Инструменты CI/CD

- Travis CI — автоматическая сборка под Linux (gcc, clang)
- AppVeyor — автоматическая сборка под Windows (Visual Studio)

---

## 📄 Файлы конфигурации

### .travis.yml — Travis CI (Linux)
```yaml
language: cpp
compiler:
  - gcc
  - clang

script:
  - mkdir build            # Создаёт папку для сборки
  - cd build               # Переходит в неё
  - cmake ..               # Генерирует файлы сборки
  - make                   # Выполняет сборку
git clone <url>                # Клонирование репозитория
git checkout -b ci-setup      # Создание новой ветки для конфигурации CI
nano .travis.yml              # Редактирование файла для Travis CI
nano appveyor.yml             # Редактирование файла для AppVeyor
git add .                     # Добавление всех файлов (в т.ч. конфигов)
git commit -m "Настройка Travis и AppVeyor CI"
git push origin ci-setup      # Отправка новой ветки на GitHub
