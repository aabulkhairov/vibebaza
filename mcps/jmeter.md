---
title: JMeter MCP сервер
description: MCP сервер, который позволяет выполнять нагрузочные тесты Apache JMeter и анализировать результаты тестирования через совместимые с MCP клиенты.
tags:
- DevOps
- Monitoring
- Analytics
- API
author: QAInsights
featured: false
---

MCP сервер, который позволяет выполнять нагрузочные тесты Apache JMeter и анализировать результаты тестирования через совместимые с MCP клиенты.

## Установка

### Локальная установка

```bash
pip install numpy matplotlib
chmod +x /path/to/jmeter/bin/jmeter
```

## Конфигурация

### MCP клиент

```json
{
    "mcpServers": {
      "jmeter": {
        "command": "/path/to/uv",
        "args": [
          "--directory",
          "/path/to/jmeter-mcp-server",
          "run",
          "jmeter_server.py"
        ]
      }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `execute_jmeter_test` | Запускает JMeter в GUI режиме, но не выполняет тест в соответствии с дизайном JMeter |
| `execute_jmeter_test_non_gui` | Выполняет тест JMeter в режиме без GUI (режим по умолчанию для лучшей производительности) |
| `analyze_jmeter_results` | Анализирует результаты тестов JMeter и предоставляет сводку ключевых метрик и аналитики |
| `identify_performance_bottlenecks` | Выявляет узкие места производительности в результатах тестов JMeter |
| `get_performance_insights` | Получает аналитику и рекомендации для улучшения производительности |
| `generate_visualization` | Генерирует визуализации результатов тестов JMeter |

## Возможности

- Выполнение тестов JMeter в режиме без GUI
- Запуск JMeter в GUI режиме
- Захват и возврат результатов выполнения
- Генерация дашборда отчетов JMeter
- Парсинг и анализ результатов тестов JMeter (JTL файлы)
- Расчет комплексных метрик производительности
- Автоматическое выявление узких мест производительности
- Генерация практических аналитических данных и рекомендаций
- Создание визуализаций результатов тестов
- Генерация HTML отчетов с результатами анализа

## Переменные окружения

### Обязательные
- `JMETER_HOME` - Путь к директории установки Apache JMeter
- `JMETER_BIN` - Путь к исполняемому файлу JMeter

### Опциональные
- `JMETER_JAVA_OPTS` - Java опции для выполнения JMeter (например, настройки памяти)

## Примеры использования

```
Run JMeter test /path/to/test.jmx
```

```
Run JMeter test sample_test.jmx in non-GUI mode and save results to results.jtl
```

```
Analyze the JMeter test results in results.jtl and provide detailed insights
```

```
What are the performance bottlenecks in the results.jtl file?
```

```
What recommendations do you have for improving performance based on results.jtl?
```

## Ресурсы

- [GitHub Repository](https://github.com/QAInsights/jmeter-mcp-server)

## Примечания

Требует установки Apache JMeter и доступности через командную строку. Сервер валидирует существование файлов тестов, проверяет расширения .jmx, валидирует форматы JTL файлов и обеспечивает комплексную обработку ошибок. Поддерживает потоковые парсеры для больших файлов и включает анализ узких мест с приоритизированными рекомендациями.