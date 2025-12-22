---
title: Bluetooth MCP сервер
description: MCP сервер, который позволяет AI-ассистентам сканировать и взаимодействовать с Bluetooth устройствами, предоставляя возможности обнаружения устройств, фильтрации и автоматического распознавания на различных платформах.
tags:
- Integration
- API
- DevOps
- Monitoring
author: Hypijump31
featured: false
---

MCP сервер, который позволяет AI-ассистентам сканировать и взаимодействовать с Bluetooth устройствами, предоставляя возможности обнаружения устройств, фильтрации и автоматического распознавания на различных платформах.

## Установка

### Из исходного кода

```bash
# Clone the repository
git clone https://github.com/yourusername/bluetooth-mcp-server.git
cd bluetooth-mcp-server

# Create and activate virtual environment
python -m venv venv

# On Windows
venv\Scripts\activate
# On macOS/Linux
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Configure environment variables
cp .env.example .env
# Edit the .env file as needed
```

### Запуск сервера

```bash
# Start the Bluetooth API server
python run.py

# In another terminal, start the MCP server
python bluetooth_mcp_server.py
```

### Интеграция с Claude

```bash
# Expose server using ngrok
ngrok http 8000

# Configure Claude
npx @anthropic-ai/sdk install-model-context-protocol <YOUR_SERVER_URL>
```

## Возможности

- Мультипротокольное сканирование: обнаружение как BLE, так и классических Bluetooth устройств
- Гибкая фильтрация: фильтрация устройств по имени, типу или другим атрибутам
- Автоматическое распознавание устройств: идентификация и категоризация распространённых устройств (например, Freebox, телевизоры и т.д.)
- Расширенная информация об устройствах: получение информации о производителе, типе устройства и детальных характеристиках
- Кроссплатформенная поддержка: работает на Windows, macOS и Linux
- Платформо-специфичные оптимизации: улучшенные возможности обнаружения на Windows
- MCP интеграция: бесшовная интеграция с Claude и совместимыми AI-ассистентами

## Примеры использования

```
Could you scan for nearby Bluetooth devices?
```

## Ресурсы

- [GitHub Repository](https://github.com/Hypijump31/bluetooth-mcp-server)

## Примечания

Требует Python 3.7+, Bluetooth адаптер, права администратора/sudo для некоторых операций и интернет-соединение. Построен с использованием подхода Test-Driven Development на основе фреймворка FastAPI. Поддерживает комплексное тестирование с pytest.