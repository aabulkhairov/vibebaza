---
title: Unity3d Game Engine MCP сервер
description: MCP сервер, который позволяет AI-ассистентам взаимодействовать с Unity Editor,
  обеспечивая манипуляции с Unity проектами, сценами, GameObjects и доступ к инструментам Unity
  таким как Test Runner и Package Manager.
tags:
- Code
- DevOps
- Integration
- Productivity
- API
author: Community
featured: false
---

MCP сервер, который позволяет AI-ассистентам взаимодействовать с Unity Editor, обеспечивая манипуляции с Unity проектами, сценами, GameObjects и доступ к инструментам Unity таким как Test Runner и Package Manager.

## Установка

### Unity Package Manager

```bash
1. Open Unity Package Manager (Window > Package Manager)
2. Click "+" button
3. Select "Add package from git URL..."
4. Enter: https://github.com/CoderGamester/mcp-unity.git
5. Click "Add"
```

### Ручная сборка

```bash
cd ABSOLUTE/PATH/TO/mcp-unity/Server~
npm install
npm run build
node build/index.js
```

## Конфигурация

### Обычный MCP клиент

```json
{
   "mcpServers": {
       "mcp-unity": {
          "command": "node",
          "args": [
             "ABSOLUTE/PATH/TO/mcp-unity/Server~/build/index.js"
          ]
       }
   }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `execute_menu_item` | Выполняет элементы меню Unity (функции с атрибутом MenuItem) |
| `select_gameobject` | Выбирает игровые объекты в иерархии Unity по пути или ID экземпляра |
| `update_gameobject` | Обновляет основные свойства GameObject (имя, тег, слой, активное/статическое состояние) или создает Ga... |
| `update_component` | Обновляет поля компонентов на GameObject или добавляет его к GameObject, если он не содержит... |
| `add_package` | Устанавливает новые пакеты в Unity Package Manager |
| `run_tests` | Запускает тесты с помощью Unity Test Runner |
| `send_console_log` | Отправляет лог консоли в Unity |
| `add_asset_to_scene` | Добавляет ассет из AssetDatabase в сцену Unity |
| `create_prefab` | Создает префаб с опциональным MonoBehaviour скриптом и значениями сериализованных полей |
| `recompile_scripts` | Перекомпилирует все скрипты в Unity проекте |

## Возможности

- Интеграция с IDE с доступом к кэшу пакетов для лучшего анализа кода
- Автоматическая настройка рабочего пространства для IDE типа VSCode
- Манипуляции со сценами Unity и GameObjects
- Интеграция с Unity Package Manager
- Доступ к Unity Test Runner
- Управление логами консоли
- Интеграция с Asset Database
- WebSocket-коммуникация
- Настраиваемые порт и таймаут
- Поддержка удаленных соединений

## Переменные окружения

### Опциональные
- `UNITY_PORT` - WebSocket порт для подключения к Unity Editor (по умолчанию: 8090)
- `UNITY_REQUEST_TIMEOUT` - Таймаут в секундах для запросов MCP сервера (по умолчанию: 10)
- `UNITY_HOST` - IP адрес хоста для удаленных bridge соединений
- `LOGGING` - Включить логирование в консоль для отладки
- `LOGGING_FILE` - Включить логирование в файл для отладки

## Примеры использования

```
Execute the menu item 'GameObject/Create Empty' to create a new empty GameObject
```

```
Select the Main Camera object in my scene
```

```
Set the Player object's tag to 'Enemy' and make it inactive
```

```
Add a Rigidbody component to the Player object and set its mass to 5
```

```
Add the TextMeshPro package to my project
```

## Ресурсы

- [GitHub Repository](https://github.com/CoderGamester/mcp-unity)

## Примечания

Требует Unity 2022.3 или выше и Node.js 18 или выше. Путь к проекту не должен содержать пробелов, иначе MCP клиент не сможет подключиться. Сервер предоставляет как инструменты для манипуляций с Unity объектами, так и ресурсы для запроса состояния Unity. Включает поддержку многоязычной документации (английский, китайский, японский).