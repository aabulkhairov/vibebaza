---
title: it-tools-mcp MCP сервер
description: Комплексный MCP сервер, предоставляющий доступ к более чем 121 IT инструменту и утилитам для кодирования/декодирования, работы с текстом, хеширования, сетевых утилит и других распространенных задач разработки и IT.
tags:
- DevOps
- Productivity
- Code
- Security
- API
author: wrenchpilot
featured: false
---

Комплексный MCP сервер, предоставляющий доступ к более чем 121 IT инструменту и утилитам для кодирования/декодирования, работы с текстом, хеширования, сетевых утилит и других распространенных задач разработки и IT.

## Установка

### NPX

```bash
npx it-tools-mcp
```

### Docker

```bash
docker run -i --rm --init --security-opt no-new-privileges:true --cap-drop ALL --read-only --user 1001:1001 --memory=256m --cpus=0.5 --name it-tools-mcp wrenchpilot/it-tools-mcp:latest
```

### Docker Interactive

```bash
docker run -it --rm wrenchpilot/it-tools-mcp:latest
```

## Конфигурация

### VS Code Node

```json
{
  "mcp": {
    "servers": {
      "it-tools": {
        "command": "npx",
        "args": ["it-tools-mcp"],
        "env": {}
      }
    }
  }
}
```

### VS Code Docker

```json
{
  "mcp": {
    "servers": {
      "it-tools": {
        "command": "docker",
        "args": [
          "run",
          "-i",
          "--rm",
          "--init",
          "--security-opt", "no-new-privileges:true",
          "--cap-drop", "ALL",
          "--read-only",
          "--user", "1001:1001",
          "--memory=256m",
          "--cpus=0.5",
          "--name", "it-tools-mcp",
          "wrenchpilot/it-tools-mcp:latest"
        ]
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `parse_ansible_inventory` | Парсинг Ansible inventory |
| `generate_ansible_inventory` | Генерация Ansible inventory |
| `validate_ansible_playbook` | Валидация YAML playbook для Ansible |
| `show_ansible_reference` | Справочник по синтаксису и модулям Ansible |
| `decrypt_ansible_vault` | Расшифровка данных Ansible Vault |
| `encrypt_ansible_vault` | Шифрование данных с помощью Ansible Vault |
| `convert_hex_to_rgb` | Конвертация HEX в RGB |
| `convert_rgb_to_hex` | Конвертация RGB в HEX |
| `convert_html_to_markdown` | Конвертация HTML в Markdown |
| `compare_json` | Сравнение JSON объектов |
| `format_json` | Форматирование и валидация JSON |
| `minify_json` | Минификация JSON |
| `convert_json_to_csv` | Конвертация JSON в CSV |
| `logging_setLevel` | Изменение минимального уровня логирования в рантайме |
| `logging_status` | Просмотр текущей конфигурации логирования и доступных уровней |

## Возможности

- Более 121 IT инструмента в 14 категориях
- Полное соответствие спецификации MCP 2025-06-18
- Полная поддержка логирования с 8 различными уровнями логов
- Отслеживание прогресса для длительных операций
- Поддержка отмены запросов
- Проверка состояния с помощью ping утилиты
- Поддержка семплинга для интеграции с LLM
- Поддержка Docker с усиленной безопасностью
- Поведение, зависящее от окружения (dev/prod режимы)
- Инструменты Ansible для шифрования vault и валидации playbook

## Примеры использования

```
Сгенерировать UUID
```

```
Закодировать текст в Base64
```

```
Безопасно хешировать пароль
```

```
Создать ASCII art из текста
```

```
Конвертировать HEX цвета в RGB
```

## Ресурсы

- [GitHub Repository](https://github.com/wrenchpilot/it-tools-mcp)

## Примечания

Сервер включает в себя комплексные возможности логирования, поддерживает режимы разработки и продакшена, а также предоставляет Docker образы для множества платформ (linux/amd64, linux/arm64). Реализует продвинутые функции MCP, такие как отслеживание прогресса, отмена запросов и поддержка семплинга для AI-powered рабочих процессов.