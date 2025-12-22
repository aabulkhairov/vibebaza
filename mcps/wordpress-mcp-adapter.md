---
title: WordPress MCP Adapter MCP сервер
description: WordPress адаптер, который связывает WordPress Abilities API с Model Context Protocol, позволяя AI агентам взаимодействовать с функциональностью WordPress через стандартизированные MCP инструменты, ресурсы и промпты.
tags:
- Integration
- API
- CRM
- Code
- Productivity
author: WordPress
featured: true
---

WordPress адаптер, который связывает WordPress Abilities API с Model Context Protocol, позволяя AI агентам взаимодействовать с функциональностью WordPress через стандартизированные MCP инструменты, ресурсы и промпты.

## Установка

### Composer

```bash
composer require wordpress/abilities-api wordpress/mcp-adapter
```

### С Jetpack Autoloader

```bash
composer require automattic/jetpack-autoloader
# Затем загрузите в файле плагина:
require_once plugin_dir_path( __FILE__ ) . 'vendor/autoload_packages.php';
```

### Git Clone

```bash
git clone https://github.com/WordPress/mcp-adapter.git wp-content/plugins/mcp-adapter
cd wp-content/plugins/mcp-adapter
composer install
```

### WP-Env

```bash
{
  "plugins": [
    "WordPress/abilities-api",
    "WordPress/mcp-adapter"
  ]
}
```

## Возможности

- Автоматически конвертирует WordPress abilities в MCP инструменты, ресурсы и промпты
- Управление несколькими серверами с уникальными конфигурациями
- Поддержка HTTP и STDIO транспорта согласно спецификации MCP 2025-06-18
- Расширяемый транспортный слой с поддержкой кастомных транспортов
- Встроенная обработка ошибок с поддержкой кастомных обработчиков ошибок
- Наблюдаемость с отслеживанием метрик и кастомными обработчиками
- Контроль разрешений с детальной проверкой прав доступа
- Обнаружение серверов и автоматическая регистрация
- Интеграция с CLI через WP-CLI команды
- Встроенные abilities для интроспекции системы и управления abilities

## Примеры использования

```
Создавайте WordPress abilities, которые автоматически становятся доступными через MCP
```

```
Получайте доступ к abilities через HTTP по адресу /wp-json/mcp/mcp-adapter-default-server
```

```
Получайте доступ к abilities через STDIO используя wp mcp-adapter serve --server=mcp-adapter-default-server
```

## Ресурсы

- [GitHub Repository](https://github.com/WordPress/mcp-adapter)

## Примечания

Часть инициативы AI Building Blocks для WordPress. Требует PHP >= 7.4 и WordPress Abilities API. Адаптер создает сервер по умолчанию, который автоматически предоставляет все зарегистрированные WordPress abilities без ручной конфигурации.