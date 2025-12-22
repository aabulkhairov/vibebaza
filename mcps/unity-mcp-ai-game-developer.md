---
title: Unity MCP (AI Game Developer) MCP сервер
description: Unity MCP — это ассистент для разработки игр на базе искусственного интеллекта, который работает как мост между MCP Client и Unity, позволяя общаться с ИИ на естественном языке для написания кода, отладки и создания игр.
tags:
- Code
- AI
- DevOps
- Integration
- Productivity
author: Community
featured: false
---

Unity MCP — это ассистент для разработки игр на базе искусственного интеллекта, который работает как мост между MCP Client и Unity, позволяя общаться с ИИ на естественном языке для написания кода, отладки и создания игр.

## Установка

### Unity Package Installer

```bash
Download AI-Game-Dev-Installer.unitypackage from releases and import into Unity project
```

### OpenUPM-CLI

```bash
openupm add com.ivanmurzak.unity.mcp
```

### Docker HTTP

```bash
docker run -p 3001:3001 ivanmurzakdev/unity-mcp-server:latest port=3001 client-transport=http
```

### Docker STDIO

```bash
docker run ivanmurzakdev/unity-mcp-server:latest port=3001 client-transport=stdio
```

## Конфигурация

### Автоматическая конфигурация

```json
Open Unity project → Window/AI Game Developer (Unity-MCP) → Click Configure at your MCP client
```

### Конфигурация через командную строку

```json
"<unityProjectPath>/Library/mcp-server/win-x64/unity-mcp-server.exe" port=<port> client-transport=stdio
```

## Возможности

- Естественное общение - Общайтесь с ИИ как с живым человеком
- Помощь с кодом - Просите ИИ писать код и запускать тесты
- Поддержка отладки - Просите ИИ получать логи и исправлять ошибки
- Множество LLM провайдеров - Используйте агентов от Anthropic, OpenAI, Microsoft или любого другого провайдера
- Гибкое развертывание - Работает локально (stdio) и удаленно (http)
- Богатый набор инструментов - Широкий спектр стандартных MCP инструментов
- Расширяемость - Создавайте кастомные MCP инструменты в коде вашего проекта
- Мгновенная компиляция - Компиляция и выполнение C# кода с использованием Roslyn
- Полный доступ к ассетам - Доступ на чтение/запись к ассетам и C# скриптам
- Ссылки на объекты - Предоставляйте ссылки на существующие объекты для мгновенного C# кода

## Переменные окружения

### Обязательные
- `port` - Номер порта для MCP сервера
- `client-transport` - Метод транспорта (stdio или http)

## Примеры использования

```
Explain my scene hierarchy
```

```
Create 3 cubes in a circle with radius 2
```

```
Create metallic golden material and attach it to a sphere gameObject
```

## Ресурсы

- [GitHub Repository](https://github.com/IvanMurzak/Unity-MCP)

## Примечания

Поддерживает версии Unity 2022.3.61f1, 2023.2.20f1 и 6000.2.3f1. Путь к проекту не может содержать пробелы. Требует интеграции с Unity Editor и поддерживает использование как в Editor, так и в Runtime. Включает тестирование стабильности в различных версиях Unity и режимах развертывания.