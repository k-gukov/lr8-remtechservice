# Лабораторная работа №8

Вариант 7. Выездное обслуживание.

Для проверки выбранной среды используется PostgreSQL 17 и тестовая база данных `remtechservice_lr8`.

## Структура репозитория

- `db/smoke_test.sql` — SQL-запрос для проверки подключения к базе данных;
- `scripts/check-postgres.ps1` — скрипт запуска проверки;
- `evidence/smoke-test.txt` — результат выполненного теста.

## Подготовка среды

1. Установить PostgreSQL 17.
2. Убедиться, что утилита `psql` доступна из командной строки.
3. Создать базу данных:

```sql
CREATE DATABASE remtechservice_lr8;
```

4. Открыть PowerShell в корневой папке проекта.

5. Задать параметры подключения:

```powershell
$env:PGHOST="localhost"
$env:PGPORT="5432"
$env:PGDATABASE="remtechservice_lr8"
$env:PGUSER="postgres"
$env:PGPASSWORD="пароль_пользователя_postgres"
```

## Проверка подключения

Запустить:

```powershell
.\scripts\check-postgres.ps1
```

Скрипт выполняет файл `db/smoke_test.sql`, проверяет подключение к PostgreSQL, создаёт тестовую схему и таблицу, записывает контрольную строку и считывает её обратно.

При успешной проверке в выводе должна присутствовать строка:

```text
LR8 connection OK
```

Результат выполнения сохраняется в:

```text
evidence/smoke-test.txt
```

## Фактическая проверка

Проверка выполнена на PostgreSQL 17.7 x86_64-windows.

Использована база данных:

```text
remtechservice_lr8
```

Подключение и тестовый запрос выполнены успешно. Контрольная запись `LR8 connection OK` создана и прочитана из базы данных.
