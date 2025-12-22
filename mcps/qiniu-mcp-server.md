---
title: Qiniu MCP сервер
description: MCP сервер на базе продуктов Qiniu Cloud, который позволяет AI моделям получать доступ к облачному хранилищу Qiniu, интеллектуальным мультимедийным сервисам, стриминговым возможностям и CDN.
tags:
- Cloud
- Storage
- Media
- CDN
- Integration
author: qiniu
featured: false
---

MCP сервер на базе продуктов Qiniu Cloud, который позволяет AI моделям получать доступ к облачному хранилищу Qiniu, интеллектуальным мультимедийным сервисам, стриминговым возможностям и CDN.

## Установка

### UV Package Manager

```bash
# Install uv first
brew install uv  # Mac
# or
curl -LsSf https://astral.sh/uv/install.sh | sh  # Linux & Mac
# or
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"  # Windows

# Run with uvx
uvx qiniu-mcp-server
```

### Из исходного кода

```bash
git clone git@github.com:qiniu/qiniu-mcp-server.git
cd qiniu-mcp-server
uv venv
source .venv/bin/activate  # Linux/macOS
# or .venv\Scripts\activate  # Windows
uv pip install -e .
```

## Конфигурация

### Cline/Claude Desktop - полный функционал

```json
{
  "mcpServers": {
    "qiniu": {
      "command": "uvx",
      "args": [
        "qiniu-mcp-server"
      ],
      "env": {
        "QINIU_ACCESS_KEY": "YOUR_ACCESS_KEY",
        "QINIU_SECRET_KEY": "YOUR_SECRET_KEY",
        "QINIU_REGION_NAME": "YOUR_REGION_NAME",
        "QINIU_ENDPOINT_URL": "YOUR_ENDPOINT_URL",
        "QINIU_BUCKETS": "YOUR_BUCKET_A,YOUR_BUCKET_B"
      },
      "disabled": false
    }
  }
}
```

### Live стриминг - аутентификация через Access/Secret ключи

```json
{
  "mcpServers": {
    "qiniu": {
      "command": "uvx",
      "args": [
        "qiniu-mcp-server"
      ],
      "env": {
        "QINIU_ACCESS_KEY": "YOUR_ACCESS_KEY",
        "QINIU_SECRET_KEY": "YOUR_SECRET_KEY"
      },
      "disabled": false
    }
  }
}
```

### Live стриминг - аутентификация через API ключ

```json
{
  "mcpServers": {
    "qiniu": {
      "command": "uvx",
      "args": [
        "qiniu-mcp-server"
      ],
      "env": {
        "QINIU_LIVE_API_KEY": "YOUR_LIVE_API_KEY"
      },
      "disabled": false
    }
  }
}
```

## Возможности

- Получение списка Bucket
- Получение списка файлов в Bucket
- Загрузка локальных файлов и загрузка с содержимым файлов
- Чтение содержимого файлов
- Получение ссылок для скачивания файлов
- Масштабирование изображений
- Скругление углов изображений
- Обновление файлов CDN по URL
- Предварительная загрузка файлов CDN по URL
- Создание bucket для live стримингового пространства

## Переменные окружения

### Обязательные
- `QINIU_ACCESS_KEY` - Ключ доступа Qiniu Cloud для аутентификации
- `QINIU_SECRET_KEY` - Секретный ключ Qiniu Cloud для аутентификации
- `QINIU_REGION_NAME` - Название региона Qiniu Cloud
- `QINIU_ENDPOINT_URL` - URL эндпоинта Qiniu Cloud (например, https://s3.your_region.qiniucs.com)
- `QINIU_BUCKETS` - Список названий bucket через запятую (рекомендуется максимум 20 bucket)

### Опциональные
- `QINIU_LIVE_API_KEY` - API ключ Qiniu Live для аутентификации live стриминга (альтернатива access/secret ключам)

## Примеры использования

```
列举 qiniu 的资源信息
```

```
列举 qiniu 中所有的 Bucket
```

```
列举 qiniu 中 xxx Bucket 的文件
```

```
读取 qiniu xxx Bucket 中 yyy 的文件内容
```

```
对 qiniu xxx Bucket 中 yyy 的图片切个宽200像素的圆角
```

## Ресурсы

- [GitHub Repository](https://github.com/qiniu/qiniu-mcp-server)

## Примечания

Требует Python 3.12 или выше и пакетный менеджер uv. Для пользователей Claude, которые сталкиваются с ошибкой 'spawn uvx ENOENT', используйте абсолютный путь к uvx в поле команды (например, /usr/local/bin/uvx). Можно протестировать с помощью Model Control Protocol Inspector командой: npx @modelcontextprotocol/inspector uv --directory . run qiniu-mcp-server