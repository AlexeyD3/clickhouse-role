ansible-clickhouse
=========
![GitHub tag (latest by date)](https://img.shields.io/badge/tag-1.0.0-blue)
[![Ansible Galaxy Clickhouse](https://img.shields.io/badge/role-AlexeyD3.clickhouse-blue.svg)](https://galaxy.ansible.com/AlexeyD3/clickhouse/)
[![Ansible Galaxy Vector](https://img.shields.io/badge/role-AlexeyD3.vector-yellow.svg)](https://galaxy.ansible.com/AlexeyD3/vector/)
[![Ansible Galaxy Lighthouse](https://img.shields.io/badge/role-AlexeyD3.lighthouse-yellow.svg)](https://galaxy.ansible.com/AlexeyD3/lighthouse/)

Роль для установки clickhouse.
- Установка:
  - clickhouse-client
  - clickhouse-server
  - clickhouse-common-static
- Создаётся БД
- Создаётся таблица для логов
- Создаётся пользователь для записи в БД
- Конфигурируется clickhouse-server для работы внешних подключений

Requirements
------------

Role Variables
--------------
Переменные для установки
default/main.yml:
```yaml
clickhouse_user: netology
clickhouse_password: netology
```

Переменные для установки необходимых пакетов и конфигурационных файлов clickhouse
vars/main.yml
```yaml
clickhouse_version: "22.3.3.44"
clickhouse_packages:
  - clickhouse-client
  - clickhouse-server
  - clickhouse-common-static
clickhouse_config_path: /etc/clickhouse-server/config.xml
clickhouse_users_path: /etc/clickhouse-server/users.xml
```

Переменные для имён БД и таблицы:
vars/main.yml
```yaml
dbname: logs
tablename: vector_internal_logs
#table propertes: (message String) ENGINE = MergeTree() ORDER BY tuple()
```

Dependencies
------------


Example Playbook
----------------
```yaml
hosts: clickhouse
roles:
  - role: clickhouse-role
```

Author Information
------------------
Alexey Dubrovin
