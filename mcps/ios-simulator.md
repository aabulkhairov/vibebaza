---
title: iOS Simulator MCP сервер
description: Сервер Model Context Protocol (MCP), который позволяет LLM взаимодействовать с симуляторами iOS через команды на естественном языке, предоставляя полный контроль над управлением симуляторами, операциями с приложениями, UI-взаимодействиями и отладкой.
tags:
- DevOps
- Code
- Integration
- Productivity
- API
author: InditexTech
featured: true
---

Сервер Model Context Protocol (MCP), который позволяет LLM взаимодействовать с симуляторами iOS через команды на естественном языке, предоставляя полный контроль над управлением симуляторами, операциями с приложениями, UI-взаимодействиями и отладкой.

## Установка

### Cline

```bash
Add this mcp to cline https://github.com/InditexTech/mcp-server-simulator-ios-idb
```

### Из исходного кода

```bash
git clone https://github.com/InditexTech/mcp-server-simulator-ios-idb.git
cd mcp-server-simulator-ios-idb
python3 -m venv venv
source venv/bin/activate
npm install
npm run build
npm start
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "ios-simulator": {
      "command": "node",
      "args": ["/path/to/mcp-server-simulator-ios-idb/dist/index.js"],
      "env": {}
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `process-instruction` | Обрабатывает инструкции на естественном языке для управления симуляторами iOS |

## Возможности

- Создание и управление сессиями симулятора
- Загрузка, выключение и мониторинг состояний симулятора
- Установка и управление iOS-приложениями
- Запуск, завершение и удаление приложений
- Выполнение действий тапа, свайпа и нажатий кнопок
- Ввод текста и последовательностей клавиш
- Доступ к элементам доступности для UI-тестирования
- Запись видео UI-взаимодействий
- Создание скриншотов и системных логов
- Отладка приложений в реальном времени

## Примеры использования

```
create a simulator session with iPhone 14
```

```
install app /path/to/my-app.ipa
```

```
launch app com.example.myapp
```

```
tap at 100, 200
```

```
take a screenshot
```

## Ресурсы

- [GitHub Repository](https://github.com/InditexTech/mcp-server-simulator-ios-idb)

## Примечания

Требует macOS с установленными XCode и симуляторами iOS. Использует facebook/idb для базового управления симулятором iOS. Может использоваться как отдельная библиотека в TypeScript-проектах. Автоматически устанавливает idb-companion через Homebrew и fb-idb через pip во время настройки.