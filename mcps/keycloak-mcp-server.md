---
title: Keycloak MCP сервер
description: Сервер Model Context Protocol, который предоставляет программный доступ к функциям администрирования Keycloak, позволяя AI-ассистентам и инструментам разработки взаимодействовать с Keycloak для управления пользователями, конфигурации realm-ов, администрирования клиентов и управления потоками аутентификации.
tags:
- Security
- DevOps
- API
- Integration
- Cloud
author: sshaaf
featured: false
---

Сервер Model Context Protocol, который предоставляет программный доступ к функциям администрирования Keycloak, позволяя AI-ассистентам и инструментам разработки взаимодействовать с Keycloak для управления пользователями, конфигурации realm-ов, администрирования клиентов и управления потоками аутентификации.

## Установка

### Docker

```bash
docker run -d \
  --name keycloak-mcp-server \
  -p 8080:8080 \
  -e KC_URL=https://keycloak.example.com \
  -e KC_REALM=master \
  -e OIDC_CLIENT_ID=mcp-server \
  quay.io/sshaaf/keycloak-mcp-server:latest
```

### Docker Pull

```bash
docker pull quay.io/sshaaf/keycloak-mcp-server:latest
```

### JAR

```bash
mvn clean package
java -jar target/quarkus-app/quarkus-run.jar
```

### Native Image

```bash
mvn clean package -Pnative
./target/keycloak-mcp-server-runner
```

### Container Image

```bash
mvn clean package -Dquarkus.container-image.build=true
```

## Конфигурация

### Конфигурация Cursor MCP

```json
{
  "mcpServers": {
    "keycloak": {
      "transport": "sse",
      "url": "https://mcp-server.example.com/mcp/sse",
      "headers": {
        "Authorization": "Bearer <your-jwt-token>"
      }
    }
  }
}
```

## Возможности

- Аутентификация через JWT токены пользователей
- Полный набор операций Keycloak (пользователи, realm-ы, клиенты, роли, группы и т.д.)
- SSE транспорт для HTTP-коммуникации
- Готовое к продакшену развертывание на OpenShift/Kubernetes
- Мультиархитектурные образы контейнеров
- Поддержка нативных образов GraalVM

## Переменные окружения

### Обязательные
- `KC_URL` - URL сервера Keycloak
- `KC_REALM` - Realm Keycloak для подключения
- `OIDC_CLIENT_ID` - OIDC client ID для аутентификации

## Ресурсы

- [GitHub Repository](https://github.com/sshaaf/keycloak-mcp-server)

## Примечания

Для аутентификации пользователям необходимо получить собственные JWT токены из Keycloak, используя предоставленный скрипт. Полная документация доступна в директории docs, включая руководство по началу работы, гид по аутентификации и инструкции по развертыванию на OpenShift. Построен на Quarkus для облачного развертывания и поддерживает более 40 инструментов, покрывающих пользователей, realm-ы, клиентов, роли, группы, IDP и аутентификацию.