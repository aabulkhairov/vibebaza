---
title: OPNSense MCP сервер
description: Model Context Protocol сервер для комплексного управления фаерволом OPNsense, который позволяет AI ассистентам напрямую управлять конфигурациями фаервола, диагностировать сетевые проблемы и автоматизировать сложные сетевые задачи.
tags:
- Security
- DevOps
- API
- Monitoring
- Integration
author: vespo92
featured: false
---

Model Context Protocol сервер для комплексного управления фаерволом OPNsense, который позволяет AI ассистентам напрямую управлять конфигурациями фаервола, диагностировать сетевые проблемы и автоматизировать сложные сетевые задачи.

## Установка

### Глобальная установка через NPM

```bash
npm install -g opnsense-mcp-server
```

### Из исходников

```bash
git clone https://github.com/vespo92/OPNSenseMCP.git
cd OPNSenseMCP
npm install
npm run build
```

### NPX

```bash
opnsense-mcp-server
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "opnsense": {
      "command": "npx",
      "args": ["opnsense-mcp-server"],
      "env": {
        "OPNSENSE_HOST": "https://your-opnsense:port",
        "OPNSENSE_API_KEY": "your-key",
        "OPNSENSE_API_SECRET": "your-secret",
        "OPNSENSE_VERIFY_SSL": "false"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `firewall_list_rules` | Список всех правил фаервола |
| `firewall_create_rule` | Создать новое правило |
| `firewall_update_rule` | Обновить существующее правило |
| `firewall_delete_rule` | Удалить правило |
| `firewall_apply_changes` | Применить ожидающие изменения |
| `nat_list_outbound` | Список исходящих NAT правил |
| `nat_set_mode` | Установить режим NAT |
| `nat_create_outbound_rule` | Создать NAT правило |
| `nat_fix_dmz` | Исправить проблемы DMZ NAT |
| `nat_analyze_config` | Анализ конфигурации NAT |
| `arp_list` | Список записей ARP таблицы |
| `routing_diagnostics` | Диагностика проблем маршрутизации |
| `routing_fix_all` | Автоисправление проблем маршрутизации |
| `interface_list` | Список сетевых интерфейсов |
| `vlan_create` | Создать VLAN |

## Возможности

- Полные CRUD операции для правил фаервола
- Правильная обработка правил автоматизации, созданных через API
- Конфигурация маршрутизации между VLAN
- Пакетное создание и управление правилами
- Улучшенная устойчивость с несколькими резервными методами
- Управление исходящими NAT правилами
- Контроль режима NAT (автоматический/гибридный/ручной/отключен)
- Правила исключения No-NAT для трафика между VLAN
- Автоматическое решение проблем DMZ NAT
- Прямая манипуляция XML конфигурацией

## Переменные окружения

### Обязательные
- `OPNSENSE_HOST` - URL хоста OPNsense с протоколом и портом
- `OPNSENSE_API_KEY` - API ключ для аутентификации
- `OPNSENSE_API_SECRET` - API секрет для аутентификации
- `OPNSENSE_VERIFY_SSL` - Проверять ли SSL сертификаты

### Опциональные
- `OPNSENSE_SSH_HOST` - SSH хост для расширенных возможностей
- `OPNSENSE_SSH_USERNAME` - SSH имя пользователя
- `OPNSENSE_SSH_PASSWORD` - SSH пароль
- `OPNSENSE_SSH_KEY_PATH` - Путь к файлу приватного SSH ключа

## Примеры использования

```
Автоматическое исправление проблем маршрутизации между DMZ и LAN
```

```
Разрешение NFS трафика от DMZ к NAS через создание правил фаервола
```

```
Запуск комплексной диагностики маршрутизации между сетями
```

```
Выполнение команд OPNsense CLI, таких как pfctl для проверки состояний
```

```
Создание и управление конфигурациями VLAN
```

## Ресурсы

- [GitHub Repository](https://github.com/vespo92/OPNSenseMCP)

## Примечания

Требует Node.js 18+ и OPNsense v24.7+. SSH доступ опционален, но включает расширенные NAT возможности и выполнение CLI команд. Сервер предоставляет более 50 MCP инструментов для комплексного управления фаерволом. Включает комплексные утилиты тестирования и обширную документацию.