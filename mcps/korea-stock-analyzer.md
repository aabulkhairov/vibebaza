---
title: Korea Stock Analyzer MCP сервер
description: Комплексный инструмент для анализа корейского фондового рынка, который анализирует акции KOSPI/KOSDAQ, используя инвестиционные стратегии 6 легендарных инвесторов, включая Уоррена Баффета, Питера Линча, Бенджамина Грэма, Джоэла Гринблата, Филипа Фишера и Джона Темплтона.
tags:
- Finance
- Analytics
- API
- AI
author: Mrbaeksang
featured: false
install_command: claude mcp add korea-stock -- npx -y @mrbaeksang/korea-stock-analyzer-mcp
---

Комплексный инструмент для анализа корейского фондового рынка, который анализирует акции KOSPI/KOSDAQ, используя инвестиционные стратегии 6 легендарных инвесторов, включая Уоррена Баффета, Питера Линча, Бенджамина Грэма, Джоэла Гринблата, Филипа Фишера и Джона Темплтона.

## Установка

### NPX

```bash
npx @mrbaeksang/korea-stock-analyzer-mcp
```

### NPM Global

```bash
npm install -g @mrbaeksang/korea-stock-analyzer-mcp
korea-stock-analyzer
```

### Smithery

```bash
npx -y @smithery/cli install korea-stock-analyzer --client claude
```

### Из исходного кода

```bash
git clone https://github.com/Mrbaeksang/korea-stock-analyzer-mcp.git
cd korea-stock-analyzer-mcp
npm install
npm run build
npm start
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "korea-stock-analyzer": {
      "command": "npx",
      "args": ["-y", "@mrbaeksang/korea-stock-analyzer-mcp"]
    }
  }
}
```

### Remote MCP (Serverless)

```json
{
  "mcpServers": {
    "korea-stock-analyzer": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://korea-stock-analyzer-mcp.vercel.app/api/mcp"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_financial_data` | Анализ PER, PBR, EPS, ROE, дивидендной доходности |
| `get_technical_indicators` | Технический анализ MA, RSI, MACD, 52-недельный максимум/минимум |
| `calculate_dcf` | Расчет внутренней стоимости с использованием модели DCF |
| `search_news` | Последние новости и анализ настроений |
| `get_supply_demand` | Анализ потоков институциональных/зарубежных инвесторов |
| `compare_peers` | Анализ сравнения с конкурентами в отрасли |
| `analyze_equity` | Полный анализ со всеми инвестиционными стратегиями |

## Возможности

- Анализ акций и финансов в реальном времени - PER, PBR, ROE, EPS
- Технические индикаторы - RSI, MACD, полосы Боллинджера, скользящие средние
- DCF оценка - расчет справедливой стоимости
- Анализ новостей и настроений - мониторинг последних новостей
- Потоки институциональных/зарубежных инвесторов - отслеживание умных денег
- Сравнение с конкурентами - анализ конкурентов в отрасли
- 6 стратегий инвестиционных мастеров - проверенные инвестиционные методологии
- Данные KOSPI/KOSDAQ в реальном времени через pykrx
- Возможность serverless деплоя на Vercel
- Доступен в KakaoTalk через PlayMCP

## Примеры использования

```
Analyze Samsung Electronics stock
```

```
Calculate DCF for SK Hynix
```

```
Compare NAVER with Kakao
```

```
삼성전자 주식 분석해줘
```

```
SK하이닉스 DCF 계산해줘
```

## Ресурсы

- [GitHub Repository](https://github.com/Mrbaeksang/korea-stock-analyzer-mcp)

## Примечания

Требует Node.js 18+ и Python 3.9+. Автоматически устанавливает зависимости Python (pykrx, pandas, numpy). Доступен как в виде локального MCP сервера, так и в качестве HTTP API endpoint. Поддерживает двуязычный интерфейс (английский/корейский). Доступен напрямую в KakaoTalk через PlayMCP. Только для образовательных/исследовательских целей - не является инвестиционным советом.