---
title: Thales CDSP CAKM MCP сервер
description: MCP сервер для операций Database EKM/TDE (Transparent Data Encryption) с использованием CipherTrust Application Key Management (CAKM) для SQL Server и Oracle баз данных.
tags:
- Database
- Security
- API
- DevOps
- Cloud
author: sanyambassi
featured: false
---

MCP сервер для операций Database EKM/TDE (Transparent Data Encryption) с использованием CipherTrust Application Key Management (CAKM) для SQL Server и Oracle баз данных.

## Установка

### Из исходного кода

```bash
git clone https://github.com/sanyambassi/thales-cdsp-cakm-mcp-server.git
cd thales-cdsp-cakm-mcp-server
uv venv && source .venv/bin/activate
uv pip install -e .
uv run python -m database_tde_server
```

### Установка uv (Windows)

```bash
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
```

### Установка uv (Linux/macOS)

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "database-tde": {
      "command": "uv",
      "args": ["run", "python", "-m", "database_tde_server"],
      "cwd": "/path/to/cakm-mcp-server-sql-oracle",
      "env": {
        "DB_TDE_SERVER_NAME": "database-tde-mcp",
        "DB_TDE_LOG_LEVEL": "INFO",
        "DB_TDE_DATABASE_CONNECTIONS": "[{\"name\":\"prod_sql\",\"db_type\":\"sqlserver\",\"host\":\"sql-prod.company.com\",\"port\":1433,\"username\":\"tde_admin\",\"password\":\"secure_password\"},{\"name\":\"oracle_cdb1\",\"db_type\":\"oracle\",\"host\":\"oracle-prod.company.com\",\"port\":1521,\"username\":\"sys\",\"password\":\"oracle_password\",\"oracle_config\":{\"oracle_home\":\"/u01/app/oracle/product/21.0.0/dbhome_1\",\"oracle_sid\":\"cdb1\",\"service_name\":\"orcl\",\"mode\":\"SYSDBA\",\"wallet_root\":\"/opt/oracle/wallet\"},\"ssh_config\":{\"host\":\"oracle-prod.company.com\",\"username\":\"oracle\",\"private_key_path\":\"/path/to/private-key.pem\",\"port\":22,\"timeout\":30}}]"
      }
    }
  }
}
```

### Cursor AI

```json
{
  "mcpServers": {
    "database-tde": {
      "command": "uv",
      "args": ["run", "python", "-m", "database_tde_server"],
      "cwd": "/path/to/cakm-mcp-server-sql-oracle",
      "env": {
        "DB_TDE_SERVER_NAME": "database-tde-mcp",
        "DB_TDE_LOG_LEVEL": "INFO",
        "DB_TDE_DATABASE_CONNECTIONS": "[{\"name\":\"prod_sql\",\"db_type\":\"sqlserver\",\"host\":\"sql-prod.company.com\",\"port\":1433,\"username\":\"tde_admin\",\"password\":\"secure_password\"},{\"name\":\"oracle_cdb1\",\"db_type\":\"oracle\",\"host\":\"oracle-prod.company.com\",\"port\":1521,\"username\":\"sys\",\"password\":\"oracle_password\",\"oracle_config\":{\"oracle_home\":\"/u01/app/oracle/product/21.0.0/dbhome_1\",\"oracle_sid\":\"cdb1\",\"service_name\":\"orcl\",\"mode\":\"SYSDBA\",\"wallet_root\":\"/opt/oracle/wallet\"},\"ssh_config\":{\"host\":\"oracle-prod.company.com\",\"username\":\"oracle\",\"private_key_path\":\"/path/to/private-key.pem\",\"port\":22,\"timeout\":30}}]"
      }
    }
  }
}
```

### Gemini CLI

```json
{
  "mcpServers": {
    "database-tde": {
      "command": "uv",
      "args": ["run", "python", "-m", "database_tde_server"],
      "cwd": "/path/to/cakm-mcp-server-sql-oracle",
      "env": {
        "DB_TDE_SERVER_NAME": "database-tde-mcp",
        "DB_TDE_LOG_LEVEL": "INFO",
        "DB_TDE_DATABASE_CONNECTIONS": "[{\"name\":\"prod_sql\",\"db_type\":\"sqlserver\",\"host\":\"sql-prod.company.com\",\"port\":1433,\"username\":\"tde_admin\",\"password\":\"secure_password\"},{\"name\":\"oracle_cdb1\",\"db_type\":\"oracle\",\"host\":\"oracle-prod.company.com\",\"port\":1521,\"username\":\"sys\",\"password\":\"oracle_password\",\"oracle_config\":{\"oracle_home\":\"/u01/app/oracle/product/21.0.0/dbhome_1\",\"oracle_sid\":\"cdb1\",\"service_name\":\"orcl\",\"mode\":\"SYSDBA\",\"wallet_root\":\"/opt/oracle/wallet\"},\"ssh_config\":{\"host\":\"oracle-prod.company.com\",\"username\":\"oracle\",\"private_key_path\":\"/path/to/private-key.pem\",\"port\":22,\"timeout\":30}}]"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_database_connections` | Выводит список всех настроенных подключений к базам данных |
| `status_tde_ekm` | Предоставляет унифицированный интерфейс для мониторинга состояния, конфигурации и соответствия требованиям TDE для SQL Server... |
| `manage_sql_ekm_objects` | Управляет провайдерами EKM, учетными данными и связанными с ними логинами сервера для SQL Server |
| `manage_sql_keys` | Управляет жизненным циклом криптографических ключей (Asymmetric Master Keys и DEKs), включая создание, вывод списка... |
| `manage_sql_encryption` | Шифрует или расшифровывает одну или несколько баз данных SQL Server |
| `manage_oracle_tde_deployment` | Обрабатывает высокоуровневые рабочие процессы развертывания TDE, такие как начальная настройка или миграция на/с HSM |
| `manage_oracle_configuration` | Управляет параметрами базы данных, связанными с TDE, для Oracle |
| `manage_oracle_wallet` | Выполняет все действия, связанные с кошельком (открытие, закрытие, резервное копирование, управление авто-логином) |
| `manage_oracle_keys` | Управляет жизненным циклом Master Encryption Keys (MEKs), включая ротацию и вывод списка |
| `manage_oracle_tablespace_encryption` | Управляет шифрованием и расшифровкой конкретных табличных пространств |

## Возможности

- Управление на основе ресурсов: Инструменты организованы по объектам базы данных, которыми они управляют
- Операционная группировка: Каждый инструмент предоставляет множество операций для комплексного управления жизненным циклом
- Продвинутое обнаружение Oracle TDE: Интеллектуальное обнаружение конфигураций Oracle TDE, включая HSM-only, HSM с Auto-login, FILE wallet TDE
- Распознавание статуса миграции: Автоматически определяет состояния прямой/обратной миграции на основе порядка и типов кошельков
- Операции Database TDE: Шифрование, расшифровка и управление TDE для нескольких типов баз данных
- Интеграция с CipherTrust: Бесшовная интеграция с CipherTrust Manager через CAKM EKM
- Поддержка множества баз данных: SQL Server и Oracle Database
- Ротация ключей: Автоматизированная ротация ключей шифрования с управлением ключами в Thales CipherTrust Manager
- SSH аутентификация: Подключения Oracle поддерживают аутентификацию как по приватному ключу, так и по паролю
- Автоматические перезапуски базы данных: MCP инструменты могут автоматически перезапускать базы данных Oracle в рамках операций TDE

## Переменные окружения

### Обязательные
- `DB_TDE_DATABASE_CONNECTIONS` - JSON массив конфигураций подключений к базам данных, включая SQL Server и Oracle базы данных

### Опциональные
- `DB_TDE_SERVER_NAME` - Имя database TDE MCP сервера
- `DB_TDE_LOG_LEVEL` - Уровень логирования для сервера

## Примеры использования

```
Покажи мне статус TDE всех моих баз данных
```

```
Для моего подключения 'prod_sql' выведи все асимметричные ключи используя инструмент 'manage_sql_keys'
```

```
Ротируй мастер-ключ на базе данных 'Db05' используя подключение 'prod_sql'
```

```
Зашифруй базу данных 'SalesDB' на моем сервере 'prod_sql'
```

```
Какой статус кошелька для моего подключения 'oracle_cdb2'?
```

## Ресурсы

- [GitHub Repository](https://github.com/sanyambassi/thales-cdsp-cakm-mcp-server)

## Примечания

Архитектура: MCP сервер ↔ Сервер базы данных ↔ CAKM провайдер/библиотека ↔ CipherTrust Manager. Этот MCP сервер взаимодействует только с серверами баз данных. CAKM провайдеры, установленные на серверах баз данных, обрабатывают всю коммуникацию с CipherTrust Manager. Включает комплексную логику включения Oracle TDE с поддержкой различных конфигураций кошельков и сценариев миграции.