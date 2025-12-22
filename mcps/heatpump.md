---
title: HeatPump MCP сервер
description: MCP сервер для расчета размеров жилых тепловых насосов, оценки стоимости и проверки производительности в холодном климате с встроенными данными для 81 модели тепловых насосов без необходимости в API ключах.
tags:
- Analytics
- API
- Finance
author: Community
featured: false
---

MCP сервер для расчета размеров жилых тепловых насосов, оценки стоимости и проверки производительности в холодном климате с встроенными данными для 81 модели тепловых насосов без необходимости в API ключах.

## Установка

### UVX (Рекомендуется)

```bash
uvx --refresh --from git+https://github.com/subspace-lab/heatpump-mcp-server.git heatpump-mcp-server
```

### Из исходного кода

```bash
git clone https://github.com/subspace-lab/heatpump-mcp-server.git
cd heatpump-mcp-server
uv pip install -e .
```

### Локальная установка

```bash
uv pip install git+https://github.com/subspace-lab/heatpump-mcp-server.git
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "heatpump-calculator": {
      "command": "uvx",
      "args": ["--refresh", "--from", "git+https://github.com/subspace-lab/heatpump-mcp-server.git", "heatpump-mcp-server"]
    }
  }
}
```

### Claude Code

```json
{
  "mcpServers": {
    "heatpump-calculator": {
      "command": "uvx",
      "args": ["--refresh", "--from", "git+https://github.com/subspace-lab/heatpump-mcp-server.git", "heatpump-mcp-server"]
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "heatpump-calculator": {
      "command": "uvx",
      "args": ["--refresh", "--from", "git+https://github.com/subspace-lab/heatpump-mcp-server.git", "heatpump-mcp-server"]
    }
  }
}
```

### С EIA API ключом

```json
{
  "mcpServers": {
    "heatpump-calculator": {
      "command": "uvx",
      "args": ["--refresh", "--from", "git+https://github.com/subspace-lab/heatpump-mcp-server.git", "heatpump-mcp-server"],
      "env": {
        "EIA_API_KEY": "your_eia_api_key_here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `calculate_heat_pump_sizing` | Расчет BTU для одной зоны с учетом влажности |
| `calculate_multi_zone_sizing` | Расчет нагрузки по этажам для сложных домов |
| `estimate_energy_costs` | Сравнение счетов и анализ окупаемости за 10 лет |
| `check_cold_climate_performance` | Проверка мощности при расчетной температуре |
| `get_electricity_rate` | Получение текущих тарифов на электричество по ZIP коду |
| `list_heat_pump_models` | Просмотр 81 модели тепловых насосов со спецификациями |

## Возможности

- 81 модель тепловых насосов от ведущих производителей
- Средние тарифы на электричество по штатам США на 2024 год
- Данные метеостанций TMY3 для климатических зон
- Расчет BTU для одной и нескольких зон
- Анализ окупаемости за 10 лет и сравнение стоимости
- Проверка производительности в холодном климате
- Пошаговое руководство по расчету размеров с подсказками
- Не требует API ключей для базового функционала

## Переменные окружения

### Опциональные
- `EIA_API_KEY` - Опциональный API ключ EIA для получения актуальных данных о тарифах на электричество вместо использования средних значений по штатам за 2024 год

## Примеры использования

```
Мне нужна помощь в подборе теплового насоса для моего дома площадью 2000 кв. футов, построенного в 1995 году в ZIP 02138
```

```
Сколько будет стоить эксплуатация Mitsubishi MXZ-3C30NA по сравнению с моей газовой печью?
```

```
Будет ли Fujitsu AOU24RLXFZ работать в Миннеаполисе?
```

## Ресурсы

- [GitHub Repository](https://github.com/jiweiqi/heatpump-mcp-server)

## Примечания

Работает из коробки со встроенными данными - API ключи не требуются. Построен на фреймворке FastMCP. Включает ресурсы для расчетных температур, базу данных моделей тепловых насосов и климатические зоны. Предоставляет управляемые рабочие процессы с подсказками для расчета размеров, анализа стоимости и проверки в холодном климате.