---
title: Depyler MCP сервер
description: Транспайлер из Python в Rust с семантической верификацией и анализом безопасности памяти, который переводит аннотированный Python код в идиоматичный Rust, сохраняя семантику программы и обеспечивая гарантии безопасности на этапе компиляции.
tags:
- Code
- AI
- Productivity
- DevOps
- Analytics
author: paiml
featured: true
---

Транспайлер из Python в Rust с семантической верификацией и анализом безопасности памяти, который переводит аннотированный Python код в идиоматичный Rust, сохраняя семантику программы и обеспечивая гарантии безопасности на этапе компиляции.

## Установка

### Cargo Install

```bash
cargo install depyler
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "depyler": {
      "command": "depyler",
      "args": ["agent", "start", "--foreground", "--port", "3000"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `transpile_python` | Конвертация Python кода в Rust |
| `analyze_migration_complexity` | Анализ сложности миграции |
| `verify_transpilation` | Верификация семантической эквивалентности |
| `pmat_quality_check` | Анализ качества кода |

## Возможности

- Компиляция одной командой из Python в standalone нативные бинарники
- Транспиляция, управляемая типами, с использованием Python аннотаций типов
- Анализ безопасности памяти с выводом паттернов владения и заимствования
- Семантическая верификация через property-based тестирование
- Поддержка 27 модулей Python stdlib со 100% валидацией
- Кастомные Rust атрибуты через @rust.attr() декораторы
- Поддержка ArgumentParser с clap derive макросами
- Поддержка generator выражений и функций
- Обработка исключений, сопоставленная с Result<T, E>
- Кроссплатформенная компиляция (Windows, Linux, macOS)

## Примеры использования

```
Compile Python script to binary: depyler compile script.py
```

```
Transpile Python file to Rust: depyler transpile example.py
```

```
Analyze migration complexity: depyler analyze example.py
```

```
Verify transpilation with semantic checking: depyler transpile example.py --verify
```

## Ресурсы

- [GitHub Repository](https://github.com/paiml/depyler)

## Примечания

Требует Rust 1.83.0 или выше и Python 3.8+ для валидации тестов. Готов к продакшену со 100% валидацией stdlib (27 модулей, 151 тест прошел). Текущая версия v3.20.0 с основной функциональностью compile команды.