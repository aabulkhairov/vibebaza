---
title: Solver MCP сервер
description: Model Context Protocol сервер, который предоставляет языковым моделям возможности решения ограничений, SAT, SMT и ASP задач, позволяя AI моделям интерактивно создавать, редактировать и решать модели ограничений в MiniZinc, PySAT, Z3 и Clingo.
tags:
- AI
- Analytics
- Code
- Integration
author: Community
featured: false
---

Model Context Protocol сервер, который предоставляет языковым моделям возможности решения ограничений, SAT, SMT и ASP задач, позволяя AI моделям интерактивно создавать, редактировать и решать модели ограничений в MiniZinc, PySAT, Z3 и Clingo.

## Установка

### Из исходного кода

```bash
git clone https://github.com/szeider/mcp-solver.git
cd mcp-solver
uv venv
source .venv/bin/activate
uv pip install -e ".[all]"  # Install all solvers
```

### Режим MiniZinc

```bash
uv pip install -e ".[mzn]"
mcp-solver-mzn
```

### Режим PySAT

```bash
uv pip install -e ".[pysat]"
mcp-solver-pysat
```

### Режим MaxSAT

```bash
uv pip install -e ".[pysat]"
mcp-solver-maxsat
```

### Режим Z3

```bash
uv pip install -e ".[z3]"
mcp-solver-z3
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `clear_model` | Удалить все элементы из модели |
| `add_item` | Добавить новый элемент по определенному индексу |
| `delete_item` | Удалить элемент по индексу |
| `replace_item` | Заменить элемент по индексу |
| `get_model` | Получить текущее содержимое модели с пронумерованными элементами |
| `solve_model` | Решить модель (с параметром таймаута) |

## Возможности

- Модели ограничений в MiniZinc с богатыми выражениями ограничений и глобальными ограничениями
- SAT модели в PySAT с моделированием пропозициональных ограничений через CNF
- Задачи оптимизации MaxSAT с поддержкой взвешенного CNF
- SMT формулы в Z3 Python с богатой системой типов (логические, целые, вещественные числа, битовые векторы, массивы)
- Answer Set программы в Clingo для декларативного решения задач с логическими программами
- Интеграция с множественными бэкендами решателей (Chuffed, Glucose3/4, Lingeling, RC2, Z3, Clingo)
- Возможности оптимизации во всех режимах
- Интерактивное создание, редактирование и решение моделей
- MCP тестовый клиент с фреймворком ReAct агента для разработки и экспериментов

## Переменные окружения

### Опциональные
- `ANTHROPIC_API_KEY` - API ключ для Claude Sonnet 3.7 (LLM по умолчанию для тестового клиента)

## Примеры использования

```
Suppose that a theatrical director feels obligated to cast either his ingenue, Actress Alvarez, or his nephew, Actor Cohen, in a production. But Miss Alvarez won't be in a play with Mr. Cohen (her former lover), and she demands that the cast include her new flame, Actor Davenport. The producer, with her own favors to repay, insists that Actor Branislavsky have a part. But Mr. Branislavsky won't be in any play with Miss Alvarez or Mr. Davenport. Can the director cast the play?
```

```
Check whether you can place n Queens on an nxn chessboard. Try n=10,20,30,40 and compare the solving times
```

```
A saleswoman based in Vienna needs to plan her upcoming tour through Austria, visiting each province capital once. Help find the shortest route.
```

## Ресурсы

- [GitHub Repository](https://github.com/szeider/mcp-solver)

## Примечания

Требует Python 3.11+, пакетный менеджер uv и зависимости для конкретных решателей. Доступен на macOS, Windows и Linux. Это проект на стадии прототипа - используйте с осторожностью в критически важных средах. Включает ссылку на исследовательскую работу: Stefan Szeider, 'Bridging Language Models and Symbolic Solvers via the Model Context Protocol', SAT 2025.