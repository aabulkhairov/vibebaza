---
title: Deepseek_R1 MCP сервер
description: Реализация сервера Model Context Protocol (MCP), который предоставляет доступ к языковым моделям DeepSeek R1 и V3. Модель R1 оптимизирована для задач рассуждения и поддерживает контекстное окно в 8192 токена.
tags:
- AI
- API
- Productivity
- Integration
author: 66julienmartin
featured: false
---

Реализация сервера Model Context Protocol (MCP), который предоставляет доступ к языковым моделям DeepSeek R1 и V3. Модель R1 оптимизирована для задач рассуждения и поддерживает контекстное окно в 8192 токена.

## Установка

### Из исходного кода

```bash
# Clone and install
git clone https://github.com/66julienmartin/MCP-server-Deepseek_R1.git
cd deepseek-r1-mcp
npm install

# Set up environment
cp .env.example .env  # Then add your API key

# Build and run
npm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "deepseek_r1": {
      "command": "node",
      "args": ["/path/to/deepseek-r1-mcp/build/index.js"],
      "env": {
        "DEEPSEEK_API_KEY": "your-api-key"
      }
    }
  }
}
```

## Возможности

- Продвинутая генерация текста с Deepseek R1 (контекстное окно 8192 токена)
- Настраиваемые параметры (max_tokens, temperature)
- Надежная обработка ошибок с подробными сообщениями
- Полная поддержка протокола MCP
- Интеграция с Claude Desktop
- Поддержка моделей DeepSeek-R1 и DeepSeek-V3

## Переменные окружения

### Обязательные
- `DEEPSEEK_API_KEY` - API ключ для доступа к языковым моделям DeepSeek

## Примеры использования

```
Генерируйте код или решайте математические задачи с temperature 0.0
```

```
Выполняйте задачи по обработке данных с temperature 1.0
```

```
Ведите обычные беседы с temperature 1.3
```

```
Переводите языки с temperature 1.3
```

```
Создавайте истории или поэзию с temperature 1.5
```

## Ресурсы

- [GitHub Repository](https://github.com/66julienmartin/MCP-server-Deepseek_R1)

## Примечания

Сервер по умолчанию использует модель deepseek-R1, но может быть настроен на использование DeepSeek-V3 путем изменения параметра модели в src/index.ts. Настройки temperature рекомендуются в зависимости от случая использования: 0.0 для программирования/математики, 1.0 для анализа данных, 1.3 для беседы/перевода и 1.5 для творческого письма.