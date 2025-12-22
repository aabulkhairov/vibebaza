---
title: ToolHive MCP сервер
description: Комплексная платформа, которая упрощает развертывание и управление серверами Model Context Protocol (MCP) с функциями безопасности, контейнеризации и корпоративного уровня для десктопных, CLI и Kubernetes окружений.
tags:
- DevOps
- Security
- API
- Integration
- Productivity
author: stacklok
featured: true
---

Комплексная платформа, которая упрощает развертывание и управление серверами Model Context Protocol (MCP) с функциями безопасности, контейнеризации и корпоративного уровня для десктопных, CLI и Kubernetes окружений.

## Возможности

- Мгновенное развертывание MCP серверов одним кликом или командой с использованием Docker или Kubernetes
- Безопасность по умолчанию с изолированными контейнерами и правильным управлением разрешениями
- Кроссплатформенная поддержка с десктопным приложением, CLI, веб-приложением и Kubernetes оператором
- Автоконфигурация для популярных клиентов как GitHub Copilot, Cursor и VS Code
- Gateway для оркестрации нескольких инструментов в виртуальный MCP с движком workflow
- Registry Server для курирования каталогов доверенных MCP серверов
- Runtime для безопасного развертывания и управления с мониторингом
- Portal с кроссплатформенным UI для упрощенного внедрения MCP
- Корпоративная безопасность с OIDC/OAuth SSO и журналированием аудита
- Интеграция с OpenTelemetry и Prometheus для наблюдаемости

## Ресурсы

- [GitHub Repository](https://github.com/StacklokLabs/toolhive)

## Примечания

ToolHive — это полноценная платформа управления MCP, а не отдельный сервер. Она включает несколько компонентов: Gateway, Registry Server, Runtime и Portal. У проекта есть отдельные репозитории для различных компонентов, включая десктопный UI (toolhive-studio), облачный UI (toolhive-cloud-ui) и registry server. Загрузки доступны по адресу https://toolhive.dev/download/ с подробной документацией на https://docs.stacklok.com/toolhive/.