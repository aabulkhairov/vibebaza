---
title: Qwen_Max MCP сервер
description: Реализация сервера Model Context Protocol (MCP) для серии языковых моделей Qwen Max, обеспечивающая доступ к моделям Qwen от Alibaba Cloud (Max, Plus, Turbo) с различными характеристиками производительности и стоимости.
tags:
- AI
- API
- Integration
- Code
- Productivity
author: 66julienmartin
featured: false
---

Реализация сервера Model Context Protocol (MCP) для серии языковых моделей Qwen Max, обеспечивающая доступ к моделям Qwen от Alibaba Cloud (Max, Plus, Turbo) с различными характеристиками производительности и стоимости.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @66julienmartin/mcp-server-qwen_max --client claude
```

### Из исходного кода

```bash
git clone https://github.com/66julienmartin/mcp-server-qwen-max.git
cd Qwen_Max
npm install
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "qwen_max": {
      "command": "node",
      "args": ["/path/to/Qwen_Max/build/index.js"],
      "env": {
        "DASHSCOPE_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `qwen_max` | Генерация текста с помощью моделей Qwen с поддержкой настраиваемых параметров, таких как max_tokens и temperature |

## Возможности

- Генерация текста с помощью моделей Qwen
- Настраиваемые параметры (max_tokens, temperature)
- Обработка ошибок
- Поддержка протокола MCP
- Интеграция с Claude Desktop
- Поддержка всех коммерческих моделей Qwen (Max, Plus, Turbo)
- Обширные контекстные окна токенов

## Переменные окружения

### Обязательные
- `DASHSCOPE_API_KEY` - API ключ для доступа к моделям Qwen через Dashscope/Alibaba Cloud

## Ресурсы

- [GitHub Repository](https://github.com/66julienmartin/MCP-server-Qwen_Max)

## Примечания

Сервер поддерживает три варианта моделей Qwen: Qwen-Max (лучшая производительность, контекст 32K), Qwen-Plus (сбалансированная производительность/стоимость, контекст 131K) и Qwen-Turbo (быстрая/низкая стоимость, контекст 1M). Параметр temperature можно настроить для различных случаев использования: 0.0-0.3 для генерации кода, 0.3-0.5 для технического письма, 0.7 для общих задач и 0.8-1.0 для творческого письма. Все модели включают бесплатную квоту в 1 миллион токенов.