---
title: mcp-guardian MCP сервер
description: MCP Guardian управляет доступом вашего LLM-помощника к MCP серверам, обеспечивая контроль активности вашего LLM в реальном времени с логированием сообщений, подтверждениями и автоматическими проверками безопасности.
tags:
- Security
- Monitoring
- Productivity
- AI
author: eqtylab
featured: true
---

MCP Guardian управляет доступом вашего LLM-помощника к MCP серверам, обеспечивая контроль активности вашего LLM в реальном времени с логированием сообщений, подтверждениями и автоматическими проверками безопасности.

## Установка

### Из исходного кода - Linux/macOS с Nix

```bash
# Install nix
# Enable nix flakes
sudo sh -c 'echo "experimental-features = nix-command flakes" >> /etc/nix/nix.conf'
# Enter dev shell
nix develop
# Build project
just build-release
```

### Из исходного кода - Windows

```bash
# Install git with symlink support
# Install rustup
# Install nodejs
# Install yarn
npm install --global yarn
# Install just
cargo install just
# Build project (in git-bash)
just build-release
```

## Возможности

- Логирование сообщений - Просматривайте трейсы всей активности LLM на MCP серверах
- Подтверждение сообщений - Одобряйте или отклоняйте отдельные вызовы инструментов в реальном времени
- Автоматическое сканирование сообщений - Автоматические проверки безопасности, конфиденциальности и т.д. в реальном времени (скоро появится)
- Простое управление множественными конфигурациями MCP серверов
- Быстрое переключение между коллекциями серверов без ручного управления файлами конфигурации

## Ресурсы

- [GitHub Repository](https://github.com/eqtylab/mcp-guardian)

## Примечания

MCP Guardian включает как `mcp-guardian`, так и `mcp-guardian-proxy` исполняемые файлы. Проект использует nix для управления средой разработки на Linux и macOS. Собранные исполняемые файлы размещаются в директории `_build/bin/`. Больше информации доступно на https://mcp-guardian.org