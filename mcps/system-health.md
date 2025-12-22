---
title: System Health MCP сервер
description: Надежная система мониторинга удаленных Linux серверов в реальном времени, которая предоставляет комплексные метрики состояния и производительности, включая CPU, память, диск, сеть и статистику безопасности через SSH соединения.
tags:
- Monitoring
- DevOps
- Security
- Analytics
- Integration
author: Community
featured: false
---

Надежная система мониторинга удаленных Linux серверов в реальном времени, которая предоставляет комплексные метрики состояния и производительности, включая CPU, память, диск, сеть и статистику безопасности через SSH соединения.

## Установка

### Из исходного кода

```bash
git clone https://github.com/yourusername/mcp-system-health.git
cd mcp-system-health
python -m venv venv
# On macOS/Linux:
source venv/bin/activate
# On Windows:
venv\Scripts\activate
pip install -r requirements.txt
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "system-health": {
      "command": "/path/to/your/venv/bin/python3",
      "args": [
        "/path/to/your/system-health-mcp-server/src/mcp_launcher.py", 
        "--username=your_ssh_username", 
        "--password=your_ssh_password",
        "--key-path=~/.ssh/id_rsa",
        "--servers=server1.example.com,server2.example.com", 
        "--log-level=debug"
      ],
      "description": "System Health MCP Server for monitoring remote servers"
    }
  }
}
```

### Конфигурация сервера

```json
{
  "hostname": "server1",
  "ip": "192.168.1.100",
  "ssh_port": 22,
  "username": "admin",
  "key_path": "~/.ssh/id_rsa"
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `system_status` | Общая информация о состоянии системы |
| `cpu_metrics` | Детальные метрики CPU |
| `memory_metrics` | Статистика использования памяти и swap |
| `disk_metrics` | Использование дисков для всех или конкретных точек монтирования |
| `network_metrics` | Статистика сетевых интерфейсов |
| `security_metrics` | Метрики, связанные с безопасностью |
| `process_list` | Список процессов, потребляющих больше всего CPU |
| `system_alerts` | Текущие предупреждения на основе нарушения пороговых значений |
| `health_summary` | Комплексная сводка состояния здоровья системы |

## Возможности

- Комплексный сбор метрик CPU, памяти, диска, сети и безопасности
- Мониторинг в реальном времени с проверкой статуса системы
- Поддержка нескольких серверов для мониторинга множества серверов из одного экземпляра
- Предупреждения на основе пороговых значений для автоматического обнаружения критических состояний
- Управление SSH соединениями с эффективным пулингом и переиспользованием
- Мониторинг безопасности для отслеживания неудачных попыток входа и подозрительных процессов
- Готовая интеграция с MCP для взаимодействия с AI ассистентами

## Ресурсы

- [GitHub Repository](https://github.com/thanhtung0201/mcp-remote-system-health)

## Примечания

Требует Python 3.10+, SSH доступ к целевым серверам и в настоящее время поддерживает только Linux серверы. Пороговые значения предупреждений предустановлены для CPU (критический ≥90%, предупреждение ≥80%), памяти (критический ≥95%, предупреждение ≥85%), диска (критический ≥95%, предупреждение ≥85%) и метрик безопасности. Рекомендуется использовать аутентификацию на основе ключей вместо паролей для обеспечения безопасности.