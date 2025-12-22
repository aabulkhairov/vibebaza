---
title: Mikrotik MCP сервер
description: Mikrotik MCP предоставляет мост между AI-ассистентами и устройствами MikroTik RouterOS, позволяя взаимодействовать с роутерами на естественном языке для управления VLAN, правилами файрвола, настройками DNS и другими сетевыми операциями.
tags:
- DevOps
- Monitoring
- Security
- Integration
- API
author: Community
featured: false
---

Mikrotik MCP предоставляет мост между AI-ассистентами и устройствами MikroTik RouterOS, позволяя взаимодействовать с роутерами на естественном языке для управления VLAN, правилами файрвола, настройками DNS и другими сетевыми операциями.

## Установка

### Ручная установка

```bash
# Clone the repository
git clone https://github.com/jeff-nasseri/mikrotik-mcp/tree/master
cd mcp-mikrotik

# Create virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install -e .

# Run the server
mcp-server-mikrotik
```

### Docker

```bash
git clone https://github.com/jeff-nasseri/mikrotik-mcp.git
cd mikrotik-mcp
docker build -t mikrotik-mcp .
```

## Конфигурация

### Cursor IDE

```json
{
  "mcpServers": {
    "mikrotik-mcp-server": {
      "command": "docker",
      "args": [
        "run",
        "--rm",
        "-i",
        "-e", "MIKROTIK_HOST=192.168.88.1",
        "-e", "MIKROTIK_USERNAME=sshuser",
        "-e", "MIKROTIK_PASSWORD=your_password",
        "-e", "MIKROTIK_PORT=22",
        "mikrotik-mcp"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `mikrotik_create_vlan_interface` | Создает VLAN интерфейс на устройстве MikroTik |
| `mikrotik_list_vlan_interfaces` | Выводит список VLAN интерфейсов на устройстве MikroTik |
| `mikrotik_get_vlan_interface` | Получает детальную информацию о конкретном VLAN интерфейсе |
| `mikrotik_update_vlan_interface` | Обновляет существующий VLAN интерфейс |
| `mikrotik_remove_vlan_interface` | Удаляет VLAN интерфейс с устройства MikroTik |
| `mikrotik_add_ip_address` | Добавляет IP адрес к интерфейсу |
| `mikrotik_list_ip_addresses` | Выводит список IP адресов на устройстве MikroTik |
| `mikrotik_get_ip_address` | Получает детальную информацию о конкретном IP адресе |
| `mikrotik_remove_ip_address` | Удаляет IP адрес с устройства MikroTik |
| `mikrotik_create_dhcp_server` | Создает DHCP сервер на устройстве MikroTik |
| `mikrotik_list_dhcp_servers` | Выводит список DHCP серверов на устройстве MikroTik |
| `mikrotik_get_dhcp_server` | Получает детальную информацию о конкретном DHCP сервере |
| `mikrotik_create_dhcp_network` | Создает конфигурацию DHCP сети |
| `mikrotik_create_dhcp_pool` | Создает пул адресов DHCP |
| `mikrotik_remove_dhcp_server` | Удаляет DHCP сервер с устройства MikroTik |

## Возможности

- Управление VLAN интерфейсами (создание, просмотр, обновление, удаление)
- Управление IP адресами на интерфейсах
- Конфигурация и управление DHCP серверами
- Создание и управление NAT правилами
- Управление и мониторинг IP пулов
- Резервное копирование системы и экспорт конфигурации
- Интеграционное тестирование с pytest и Docker
- Интерфейс на естественном языке для операций с роутером

## Переменные окружения

### Обязательные
- `MIKROTIK_HOST` - IP адрес или имя хоста устройства MikroTik
- `MIKROTIK_USERNAME` - SSH имя пользователя для устройства MikroTik
- `MIKROTIK_PASSWORD` - SSH пароль для устройства MikroTik

### Опциональные
- `MIKROTIK_PORT` - SSH порт для устройства MikroTik (по умолчанию: 22)

## Ресурсы

- [GitHub Repository](https://github.com/jeff-nasseri/mikrotik-mcp)

## Примечания

Требует Python 3.8+ и устройство MikroTik RouterOS с включенным доступом к API. Включает интеграционные тесты, которые запускают временный контейнер MikroTik RouterOS для тестирования. Имеет значок оценки безопасности от MseeP.ai.