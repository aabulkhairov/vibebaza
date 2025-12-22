---
title: QuickChart MCP сервер
description: MCP сервер, который интегрируется с QuickChart.io для генерации различных типов диаграмм и визуализаций с использованием конфигураций Chart.js.
tags:
- Analytics
- API
- Productivity
- Media
- Integration
author: GongRzhe
featured: true
---

MCP сервер, который интегрируется с QuickChart.io для генерации различных типов диаграмм и визуализаций с использованием конфигураций Chart.js.

## Установка

### NPM

```bash
npm install @gongrzhe/quickchart-mcp-server
```

### Smithery

```bash
npx -y @smithery/cli install @gongrzhe/quickchart-mcp-server --client claude
```

### Из исходного кода

```bash
npm install
npm run build
```

## Конфигурация

### Claude Desktop (Собранная версия)

```json
{
  "mcpServers": {
    "quickchart-server": {
      "command": "node",
      "args": ["/path/to/quickchart-server/build/index.js"]
    }
  }
}
```

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "quickchart-server": {
      "command": "npx",
      "args": [
        "-y",
        "@gongrzhe/quickchart-mcp-server"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `generate_chart` | Генерирует URL диаграммы через QuickChart.io с поддержкой множественных типов диаграмм и настраиваемых параметров |
| `download_chart` | Скачивает изображение диаграммы в локальный файл, принимая конфигурацию диаграммы и путь вывода в качестве параметров |

## Возможности

- Поддержка множественных типов диаграмм: bar, line, pie, doughnut, radar, polarArea, scatter, bubble, radialGauge, speedometer
- Настройка с помощью меток, наборов данных, цветов и дополнительных опций
- Возвращает URL сгенерированных диаграмм
- Скачивание изображений диаграмм в локальные файлы
- Использует формат конфигурации Chart.js
- Интеграция с URL-сервисом генерации диаграмм QuickChart.io

## Ресурсы

- [GitHub Repository](https://github.com/GongRzhe/Quickchart-MCP-Server)

## Примечания

Сервер использует формат конфигурации Chart.js и преобразует конфигурации в URL QuickChart. Типы диаграмм включают: столбчатые диаграммы для сравнения значений, линейные диаграммы для трендов, круговые диаграммы для пропорциональных данных, радарные диаграммы для многомерных данных, точечные диаграммы для распределения данных, пузырьковые диаграммы для трёхмерных данных и шкальные диаграммы для отображения одиночных значений.