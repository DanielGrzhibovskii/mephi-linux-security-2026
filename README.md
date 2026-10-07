# ДЗ №1. Изучение средств защиты ОС GNU/Linux

Окружение: Rocky Linux 9, все действия выполнены в командной строке с правами root.
Настройки сохраняются после перезагрузки (файлы `/etc/passwd`, `/etc/shadow`, `/etc/group`, `/etc/sudoers`, бит set-UID, расширенные атрибуты файловой системы).

## Проверка результатов

- Без set-UID `cat /etc/shadow` от `user1` даёт `Permission denied`, а `/home/user1/cat_suid /etc/shadow` выводит содержимое файла.
- Обычный `chown root ~/testfile` от `user1` завершается отказом, а `~/chown_cap root ~/testfile` проходит успешно.
- Команда `sudo date -s ...` от `user1` меняет время, без `sudo` это невозможно.

## Состав репозитория

| Файл | Содержимое |
|---|---|
| `mephi-screenshot.png` | Скриншот терминала с уникальным номером |
| `history.out` | История команд root |
| `history_user1.out` | История команд пользователя `user1` |
| `stat.out` | `stat` домашнего каталога и обеих утилит |
| `getcap.out` | Привилегии утилиты из раздела 4 |
| `passwd`, `shadow`, `group`, `sudoers` | Копии системных файлов |
| `suid_files.out` | Файлы с битом set-UID |
| `proc_monitor.out` | Процессы с EUID=0 и обычным RUID |
