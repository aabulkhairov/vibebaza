---
title: EDA MCP сервер
description: Комплексный сервер Model Context Protocol для инструментов Electronic Design Automation, позволяющий AI-ассистентам синтезировать Verilog с помощью Yosys, симулировать проекты с Icarus Verilog, выполнять полный ASIC-поток с OpenLane и просматривать результаты с GTKWave и KLayout.
tags:
- DevOps
- Code
- Integration
- Analytics
- Productivity
author: Community
featured: false
---

Комплексный сервер Model Context Protocol для инструментов Electronic Design Automation, позволяющий AI-ассистентам синтезировать Verilog с помощью Yosys, симулировать проекты с Icarus Verilog, выполнять полный ASIC-поток с OpenLane и просматривать результаты с GTKWave и KLayout.

## Установка

### Из исходного кода

```bash
git clone https://github.com/NellyW8/mcp-EDA
cd mcp-EDA
npm install
npm run build
npx tsc
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "MCP_DOCKER": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "alpine/socat",
        "STDIO",
        "TCP:host.docker.internal:8811"
      ]
    },
    "eda-mcp": {
      "command": "node",
      "args": [
        "/absolute/path/to/your/eda-mcp-server/build/index.js"
      ],
      "env": {
        "PATH": "/usr/local/bin:/opt/homebrew/bin:/usr/bin:/bin",
        "HOME": "/your/home/directory"
      }
    }
  }
}
```

### Cursor IDE

```json
{
  "mcpServers": {
    "MCP_DOCKER": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "alpine/socat",
        "STDIO",
        "TCP:host.docker.internal:8811"
      ]
    },
    "eda-mcp": {
      "command": "node",
      "args": [
        "/absolute/path/to/your/eda-mcp-server/build/index.js"
      ],
      "env": {
        "PATH": "/usr/local/bin:/opt/homebrew/bin:/usr/bin:/bin",
        "HOME": "/your/home/directory"
      }
    }
  }
}
```

## Возможности

- Синтез Verilog: Синтезируйте код Verilog с использованием Yosys для различных целей FPGA (generic, ice40, xilinx)
- Симуляция Verilog: Симулируйте проекты с использованием Icarus Verilog с автоматическим выполнением тестбенчей
- Просмотр сигналов: Запускайте GTKWave для визуализации VCD файлов и анализа сигналов
- ASIC поток проектирования: Полный поток RTL-to-GDSII с использованием OpenLane и интеграции Docker
- Просмотр топологии: Открывайте GDSII файлы в KLayout для инспекции физического проекта
- Анализ отчетов: Читайте и анализируйте отчеты OpenLane для метрик PPA и оценки качества проекта

## Переменные окружения

### Обязательные
- `PATH` - Системный PATH для доступа к инструментам EDA
- `HOME` - Путь к домашней директории пользователя

## Примеры использования

```
Можешь синтезировать этот модуль счетчика для FPGA ice40?
```

```
Пожалуйста, симулируй этот сумматор с тестбенчем
```

```
Запусти полный ASIC-поток для этого проекта с периодом тактирования 10нс
```

```
Посмотри сигналы из симуляции с ID проекта: abc123
```

## Ресурсы

- [GitHub Repository](https://github.com/NellyW8/mcp-EDA)

## Примечания

Требует локальной установки инструментов EDA, включая Yosys, Icarus Verilog, GTKWave, Docker Desktop, OpenLane и KLayout. Сервер выступает в роли моста между AI-ассистентами и вашей локальной цепочкой инструментов EDA. Имеет таймаут 10 минут для потоков OpenLane. Реализация статьи MCP4EDA: LLM-Powered Model Context Protocol RTL-to-GDSII Automation with Backend Aware Synthesis Optimization.