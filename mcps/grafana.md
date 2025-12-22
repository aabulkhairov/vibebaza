---
title: Grafana MCP
description: Official Grafana MCP server for dashboards, datasources, Prometheus queries,
  Loki logs, alerting, and incident management.
tags:
- Monitoring
- Observability
- Dashboards
- Prometheus
- Loki
author: Grafana
featured: true
install_command: claude mcp add grafana -e GRAFANA_URL=http://localhost:3000 -e GRAFANA_SERVICE_ACCOUNT_TOKEN=your_token
  -- mcp-grafana
connection_type: stdio
paid_api: true
---

The Grafana MCP Server provides comprehensive access to your Grafana instance and the surrounding observability ecosystem, including dashboards, datasources, alerting, and incident management.

## Installation

### Download Binary

Download from [releases](https://github.com/grafana/mcp-grafana/releases) and add to your PATH.

### Build from Source

```bash
GOBIN="$HOME/go/bin" go install github.com/grafana/mcp-grafana/cmd/mcp-grafana@latest
```

### Docker

```bash
docker pull mcp/grafana
docker run --rm -i -e GRAFANA_URL=http://localhost:3000 -e GRAFANA_SERVICE_ACCOUNT_TOKEN=<token> mcp/grafana -t stdio
```

## Configuration

### Claude Desktop

```json
{
  "mcpServers": {
    "grafana": {
      "command": "mcp-grafana",
      "args": [],
      "env": {
        "GRAFANA_URL": "http://localhost:3000",
        "GRAFANA_SERVICE_ACCOUNT_TOKEN": "<your service account token>"
      }
    }
  }
}
```

## Features

### Dashboards
- Search, get, create, and update dashboards
- Get panel queries and datasource info
- Extract specific parts using JSONPath

### Datasources
- List and fetch datasource information
- Support for Prometheus and Loki

### Prometheus
- Execute PromQL queries (instant and range)
- Query metadata, metric names, label names/values

### Loki
- Run log and metric queries using LogQL
- Query label names, values, and stream statistics

### Alerting
- List and fetch alert rules
- List contact points
- Support for Grafana-managed and datasource-managed alerts

### Incidents
- Search, create, and update incidents
- Add activities to incidents

### OnCall
- List schedules and shifts
- Get current on-call users
- List alert groups

## Available Tools

| Tool | Category | Description |
|------|----------|-------------|
| `search_dashboards` | Search | Search for dashboards |
| `get_dashboard_by_uid` | Dashboard | Get dashboard by UID |
| `query_prometheus` | Prometheus | Execute PromQL queries |
| `query_loki_logs` | Loki | Query logs using LogQL |
| `list_alert_rules` | Alerting | List alert rules |
| `list_incidents` | Incident | List incidents |
| `list_oncall_schedules` | OnCall | List on-call schedules |

## Usage Examples

```
Show me all dashboards related to API performance
```

```
Query Prometheus for CPU usage over the last hour
```

```
List all firing alerts in the production namespace
```

## Resources

- [GitHub Repository](https://github.com/grafana/mcp-grafana)
- [Grafana Documentation](https://grafana.com/docs/)
- [Docker Hub](https://hub.docker.com/r/mcp/grafana)
