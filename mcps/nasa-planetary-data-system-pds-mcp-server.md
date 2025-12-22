---
title: NASA Planetary Data System (PDS) MCP сервер
description: Model Context Protocol сервер, который предоставляет доступ к NASA's Planetary Data System (PDS) Registry API, позволяя осуществлять интеллектуальный поиск и изучение данных космических миссий NASA, инструментов, космических аппаратов и небесных тел с 1960-х годов по настоящее время.
tags:
- Search
- API
- Database
- Analytics
author: Community
featured: false
---

Model Context Protocol сервер, который предоставляет доступ к NASA's Planetary Data System (PDS) Registry API, позволяя осуществлять интеллектуальный поиск и изучение данных космических миссий NASA, инструментов, космических аппаратов и небесных тел с 1960-х годов по настоящее время.

## Установка

### Из исходного кода

```bash
git clone https://github.com/NASA-PDS/pds-mcp-server.git
cd pds-mcp-server
python3.13 -m venv {env-name}
source {env-name}/bin/activate
pip install -r requirements.txt
```

### Автономный сервер

```bash
python3.13 pds_mcp_server.py
```

## Конфигурация

### Claude Desktop/Cursor

```json
{
  "mcpServers": {
    "pds-registry": {
      "command": "/path/to/{env-name}/bin/python3.13",
      "args": ["/path/to/pds_mcp_server.py"],
      "env": {}
    }
  }
}
```

## Возможности

- Поиск миссий и проектов: Находите космические миссии, исследования и научные проекты с фильтрацией по ключевым словам и типам миссий
- Открытие небесных тел: Ищите планеты, луны, астероиды, кометы и другие астрономические объекты по имени или типу
- Поиск космических аппаратов и платформ: Находите космические корабли, роверы, посадочные модули, телескопы и другие платформы для научных инструментов
- Поиск научных инструментов: Находите камеры, спектрометры, детекторы и другие научные инструменты, используемые в космических миссиях
- Исследование коллекций данных: Ищите и фильтруйте коллекции данных по связям с миссиями, объектами, инструментами или космическими аппаратами
- Картирование связей продуктов: Обнаруживайте связи между миссиями, объектами, инструментами и продуктами данных
- Подробная информация о продуктах: Получайте исчерпывающие метаданные и детали для конкретных продуктов PDS, используя URN идентификаторы
- Доступ к справочным данным: Получайте доступ к категоризированным спискам типов объектов, типов космических аппаратов, типов инструментов и типов миссий для фильтрации и поиска

## Примеры использования

```
Which instrument do seismic observations in the PDS?
```

```
What is the identifier of the moon in the PDS?
```

```
What data is collected from these instruments are targeting the Moon? (include URNs if need be)?
```

```
What missions produced these observations?
```

## Ресурсы

- [GitHub Repository](https://github.com/NASA-PDS/pds-mcp-server)

## Примечания

Требуется Python 3.13+. Рекомендуется использовать с инструкциями: 'You are only allowed to make one tool call per request. In the returned search results, output the URNs (identifiers) as additional information alongside the result. After each message, you will propose to the user what next steps they can take and ask them to choose.' Имеет поддержку отладки MCP Inspector и включает пример пользовательского интерфейса Gradio. Интегрируется с NASA PDS Registry API.