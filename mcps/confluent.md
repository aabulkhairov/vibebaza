---
title: Confluent MCP
description: Official Confluent MCP server for managing Apache Kafka topics, connectors,
  Flink SQL, and Tableflow through natural language.
tags:
- Kafka
- Streaming
- Data Platform
- Flink
- Messaging
author: Confluent
featured: true
install_command: claude mcp add confluent -e API_TOKEN=your_token -- npx -y @confluentinc/mcp-confluent
  -e /path/to/.env
connection_type: sse
paid_api: true
---

The Confluent MCP Server enables AI assistants to interact with Confluent Cloud REST APIs, allowing management of Kafka topics, connectors, Flink SQL statements, and Tableflow through natural language interactions.

## Installation

```bash
npx -y @confluentinc/mcp-confluent -e /path/to/.env
```

## Configuration

### Claude Desktop

```json
{
  "mcpServers": {
    "confluent": {
      "command": "npx",
      "args": [
        "-y",
        "@confluentinc/mcp-confluent",
        "-e",
        "/path/to/.env"
      ]
    }
  }
}
```

### Environment Variables

Create a `.env` file with your Confluent Cloud credentials:

```bash
BOOTSTRAP_SERVERS="your-cluster.confluent.cloud:9092"
KAFKA_API_KEY="..."
KAFKA_API_SECRET="..."
KAFKA_REST_ENDPOINT="https://your-cluster.confluent.cloud:443"
KAFKA_CLUSTER_ID=""
KAFKA_ENV_ID="env-..."
FLINK_API_KEY=""
FLINK_API_SECRET=""
FLINK_COMPUTE_POOL_ID="lfcp-..."
CONFLUENT_CLOUD_API_KEY=""
CONFLUENT_CLOUD_API_SECRET=""
SCHEMA_REGISTRY_API_KEY="..."
SCHEMA_REGISTRY_API_SECRET="..."
```

## Available Tools

### Kafka Topics
- `list-topics` - List all topics in the cluster
- `create-topics` - Create new Kafka topics
- `delete-topics` - Delete topics
- `produce-message` - Produce records to topics
- `consume-messages` - Consume messages from topics

### Flink SQL
- `list-flink-statements` - List Flink SQL statements
- `create-flink-statement` - Create new statements
- `read-flink-statement` - Read statement results
- `delete-flink-statements` - Delete statements

### Connectors
- `list-connectors` - List active connectors
- `create-connector` - Create new connectors
- `read-connector` - Get connector details
- `delete-connector` - Delete connectors

### Tableflow
- `create-tableflow-topic` - Create Tableflow topics
- `list-tableflow-topics` - List Tableflow topics
- `create-tableflow-catalog-integration` - Create catalog integrations

## Features

- **Natural Language Kafka** - Manage topics and messages conversationally
- **Flink SQL Integration** - Execute and manage Flink SQL statements
- **Connector Management** - Create and manage data connectors
- **Schema Registry** - Work with data schemas
- **Tableflow** - Manage Tableflow configurations

## Transport Options

```bash
# Enable HTTP and SSE transports
npx @confluentinc/mcp-confluent -e .env --transport http,sse,stdio
```

## Usage Examples

```
List all Kafka topics in my cluster
```

```
Create a new topic called user-events with 6 partitions
```

```
Show me the latest messages from the orders topic
```

## Resources

- [GitHub Repository](https://github.com/confluentinc/mcp-confluent)
- [Confluent Documentation](https://docs.confluent.io/)
- [NPM Package](https://www.npmjs.com/package/@confluentinc/mcp-confluent)
