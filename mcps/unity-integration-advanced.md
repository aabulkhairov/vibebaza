---
title: Unity Integration (Advanced) MCP сервер
description: Продвинутый MCP сервер для Unity3D Game Engine, который позволяет AI-ассистентам взаимодействовать с Unity Editor в реальном времени, поддерживая выполнение кода, манипуляции с файлами проекта, доступ к иерархии сцены и комплексный мониторинг состояния проекта.
tags:
- Code
- Integration
- DevOps
- Productivity
- API
author: Community
featured: false
---

Продвинутый MCP сервер для Unity3D Game Engine, который позволяет AI-ассистентам взаимодействовать с Unity Editor в реальном времени, поддерживая выполнение кода, манипуляции с файлами проекта, доступ к иерархии сцены и комплексный мониторинг состояния проекта.

## Установка

### Unity Package Manager (Git URL)

```bash
1. Open Unity Package Manager (Window > Package Manager)
2. Click + button and select 'Add package from git URL...'
3. Enter: https://github.com/quazaai/UnityMCPIntegration.git
4. Click Add
```

### Unity Custom Package

```bash
1. Clone repository or download as unityPackage
2. In Unity: Assets > Import Package > Custom Package
3. Select UnityMCPIntegration.unitypackage
```

### MCP Server Direct Run

```bash
cd mcpServer
npm install
node build/index.js
```

### Smithery Installation

```bash
npx -y @smithery/cli install @quazaai/unitymcpintegration --client claude
```

## Конфигурация

### MCP Host Configuration

```json
{
  "mcpServers": {
    "unity-mcp-server": {
      "command": "node",
      "args": [
        "path-to-project>\\Library\\PackageCache\\com.quaza.unitymcp@d2b8f1260bca\\mcpServer\\mcpServer\\build\\index.js"
      ],
      "env": {
        "MCP_WEBSOCKET_PORT": "5010"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_editor_state` | Получить исчерпывающую информацию о проекте Unity и состоянии редактора |
| `get_current_scene_info` | Получить подробную информацию о текущей сцене |
| `get_game_objects_info` | Получить информацию о конкретных GameObject в сцене |
| `execute_editor_command` | Выполнить C# код напрямую в Unity Editor |
| `get_logs` | Получить и отфильтровать логи консоли Unity |
| `verify_connection` | Проверить наличие активного подключения к Unity Editor |
| `read_file` | Прочитать содержимое файла в вашем Unity проекте |
| `read_multiple_files` | Прочитать несколько файлов одновременно |
| `write_file` | Создать или перезаписать файл с новым содержимым |
| `edit_file` | Внести точечные изменения в существующие файлы с предпросмотром diff |
| `list_directory` | Получить список файлов и папок в директории |
| `directory_tree` | Получить иерархическое представление директорий и файлов |
| `search_files` | Найти файлы, соответствующие шаблону поиска |
| `get_file_info` | Получить метаданные о конкретном файле или директории |
| `find_assets_by_type` | Найти все ассеты определенного типа (например, Material, Prefab) |

## Возможности

- Просмотр и манипуляция файлами проекта напрямую
- Доступ к информации о вашем Unity проекте в реальном времени
- Понимание иерархии сцены и игровых объектов
- Выполнение C# кода напрямую в Unity Editor
- Мониторинг логов и ошибок
- Управление режимом воспроизведения Editor
- Ожидание выполнения кода
- WebSocket-коммуникация между Unity и MCP сервером
- Доступ к файловой системе ограничен директорией Unity проекта для безопасности
- Поддержка как абсолютных, так и относительных путей к файлам

## Переменные окружения

### Опциональные
- `MCP_WEBSOCKET_PORT` - WebSocket порт для коммуникации Unity MCP сервера

## Примеры использования

```
Get a directory listing: list_directory(path: "Scenes")
```

```
Read a script file: read_file(path: "Scripts/Player.cs")
```

```
Edit a configuration file: edit_file(path: "Resources/config.json", edits: [{oldText: "value: 10", newText: "value: 20"}], dryRun: true)
```

```
Find all materials: find_assets_by_type(assetType: "Material")
```

## Ресурсы

- [GitHub Repository](https://github.com/quazaai/UnityMCPIntegration)

## Примечания

Требует Unity 2021.3+ и Node.js 18+. Коммуникация между Unity плагином и MCP сервером происходит через WebSocket. Система включает в себя комплексное MCP Debug окно, доступное через Window > MCP Debug для мониторинга подключений и тестирования возможностей. Операции с файлами обрабатываются интеллектуально с путями, разрешенными относительно папки Assets проекта.