---
title: Attestable MCP сервер
description: MCP сервер, который работает внутри доверенной среды исполнения (TEE) с использованием Intel SGX и Gramine, обеспечивая удаленную аттестацию через RA-TLS, что позволяет MCP клиентам криптографически проверить целостность кода сервера перед подключением.
tags:
- Security
- DevOps
- Integration
- API
author: kontext-dev
featured: false
---

MCP сервер, который работает внутри доверенной среды исполнения (TEE) с использованием Intel SGX и Gramine, обеспечивая удаленную аттестацию через RA-TLS, что позволяет MCP клиентам криптографически проверить целостность кода сервера перед подключением.

## Установка

### Из исходного кода с Docker и Gramine

```bash
uv sync
docker build -t attestable-mcp-server .
gramine-sgx-gen-private-key
git clone https://github.com/gramineproject/gsc docker/gsc
cd docker/gsc
uv run ./gsc build-gramine --rm --no-cache -c ../gramine_base.config.yaml gramine_base
uv run ./gsc build -c ../attestable-mcp-server.config.yaml --rm attestable-mcp-server ../attestable-mcp-server.manifest
uv run ./gsc sign-image -c ../attestable-mcp-server.config.yaml attestable-mcp-server "$HOME"/.config/gramine/enclave-key.pem
uv run ./gsc info-image gsc-attestable-mcp-server
```

### Запуск на безопасном железе

```bash
docker run -itp --device=/dev/sgx_provision:/dev/sgx/provision --device=/dev/sgx_enclave:/dev/sgx/enclave -v /var/run/aesmd/aesm.socket:/var/run/aesmd/aesm.socket -p 8000:8000 --rm gsc-attestable-mcp-server
```

### Запуск на локальной машине для разработки

```bash
docker run -p 8000:8000 --rm gsc-attestable-mcp-server
```

## Возможности

- MCP клиенты могут удаленно аттестовать код, работающий на любом MCP сервере
- MCP серверы могут опционально удаленно аттестовать MCP клиентов
- Использует протокол RA-TLS для удаленной аттестации клиент-сервер
- Встраивает SGX quote в поле расширения X.509 сертификата
- Генерирует подписанную аттестацию кода, работающего внутри TEE
- Docker образы подписаны GitHub Actions
- Возможна независимая проверка с безопасным железом или без него

## Ресурсы

- [GitHub Repository](https://github.com/co-browser/attestable-mcp-server)

## Примечания

Требует Intel SGX железо, Gramine, Python 3.13, Ubuntu 22.04, а также Intel SGX SDK & PSW. Сервер работает на GitHub Actions с self-hosted runners внутри TEE. В планах: валидация JSON Web Key (JWK) attestation claim и демонстрация MCP клиента.