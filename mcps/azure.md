---
title: Azure MCP
description: Official Microsoft Azure MCP server for comprehensive Azure service integration
  including Storage, Cosmos DB, CLI, and more.
tags:
- Azure
- Cloud
- Microsoft
- Infrastructure
- DevOps
author: Microsoft
featured: true
install_command: claude mcp add azure -- npx -y @azure/mcp@latest
connection_type: stdio
paid_api: true
---

The Azure MCP Server is Microsoft's official MCP implementation that creates a seamless connection between AI agents and Azure services. It provides comprehensive tools for managing Azure resources through natural language.

## Installation

### VS Code Extension (Recommended)

Install the Azure MCP Server extension from VS Code Marketplace.

### NPX

```bash
npx -y @azure/mcp@latest
```

### Docker

```bash
docker pull mcr.microsoft.com/azure-mcp
```

## Configuration

```json
{
  "mcpServers": {
    "azure": {
      "command": "npx",
      "args": ["-y", "@azure/mcp@latest"]
    }
  }
}
```

## Available Services

### Storage
- Blob storage operations
- Container management
- File uploads and downloads

### Cosmos DB
- Database queries
- Document management
- Collection operations

### Azure CLI
- Execute Azure CLI commands
- Resource management
- Subscription operations

### Resource Management
- Create and manage resources
- Deploy ARM templates
- Monitor resource status

## Microsoft MCP Ecosystem

Microsoft provides several specialized MCP servers:

| Server | Description |
|--------|-------------|
| Azure MCP | Core Azure services |
| Azure DevOps | CI/CD and work items |
| Microsoft Fabric | Data analytics platform |
| Playwright | Browser automation |
| Microsoft Learn | Documentation access |

## Features

- **Multi-Service Support** - Access to key Azure services
- **Native Authentication** - Uses Azure credential chain
- **VS Code Integration** - Works with GitHub Copilot for Azure
- **Docker Support** - Official Docker images available

## Usage Examples

```
Create a new storage account in East US
```

```
List all Cosmos DB databases in my subscription
```

```
Deploy my ARM template to the production resource group
```

## Environment Variables

| Variable | Description |
|----------|-------------|
| `AZURE_SUBSCRIPTION_ID` | Default subscription |
| `AZURE_TENANT_ID` | Azure AD tenant |
| `AZURE_CLIENT_ID` | Service principal ID |
| `AZURE_CLIENT_SECRET` | Service principal secret |

## Resources

- [Azure MCP Documentation](https://learn.microsoft.com/azure/developer/azure-mcp-server/)
- [GitHub Repository](https://github.com/microsoft/mcp)
- [Azure Documentation](https://docs.microsoft.com/azure/)
