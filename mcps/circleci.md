---
title: CircleCI MCP
description: Enable AI agents to interact with CircleCI for build logs, pipeline status,
  flaky tests, and CI/CD operations.
tags:
- CI/CD
- DevOps
- Builds
- Testing
- Automation
author: CircleCI
featured: true
install_command: claude mcp add circleci-mcp-server -e CIRCLECI_TOKEN=your_token --
  npx -y @circleci/mcp-server-circleci@latest
connection_type: sse
paid_api: true
---

The CircleCI MCP server integrates with CircleCI's development workflow, enabling AI-powered access to build failures, pipeline status, flaky tests, and more. Use natural language to accomplish CI/CD tasks directly from your IDE.

## Installation

```bash
npm install -g @circleci/mcp-server-circleci
```

## Configuration

```json
{
  "mcpServers": {
    "circleci-mcp-server": {
      "command": "npx",
      "args": ["-y", "@circleci/mcp-server-circleci@latest"],
      "env": {
        "CIRCLECI_TOKEN": "your-circleci-token",
        "CIRCLECI_BASE_URL": "https://circleci.com"
      }
    }
  }
}
```

### Docker Installation

```json
{
  "mcpServers": {
    "circleci-mcp-server": {
      "command": "docker",
      "args": [
        "run", "--rm", "-i",
        "-e", "CIRCLECI_TOKEN",
        "-e", "CIRCLECI_BASE_URL",
        "circleci:mcp-server-circleci"
      ],
      "env": {
        "CIRCLECI_TOKEN": "your-circleci-token"
      }
    }
  }
}
```

## Available Tools

### Build & Pipeline Tools
- `get_build_failure_logs` - Retrieve detailed failure logs from builds
- `get_latest_pipeline_status` - Get status of latest pipeline for a branch
- `run_pipeline` - Trigger a pipeline to run
- `rerun_workflow` - Rerun a workflow from start or failed job

### Testing Tools
- `find_flaky_tests` - Identify flaky tests in your project
- `get_job_test_results` - Retrieve test metadata for jobs

### Configuration Tools
- `config_helper` - Validate CircleCI configuration
- `analyze_diff` - Analyze git diffs against cursor rules

### Project Tools
- `list_followed_projects` - List all followed CircleCI projects
- `list_component_versions` - List versions for a component

### Prompt Engineering Tools
- `create_prompt_template` - Generate structured prompt templates
- `recommend_prompt_template_tests` - Generate test cases for prompts

### Advanced Tools
- `run_rollback_pipeline` - Trigger a rollback for a project
- `download_usage_api_data` - Download CircleCI usage data
- `find_underused_resource_classes` - Find jobs with low resource utilization

## Features

- Natural language interaction with CI/CD
- Support for multiple workflows (Project Slug, URL, Local Context)
- Detailed failure log extraction
- Flaky test detection and analysis
- Configuration validation
- Pipeline triggering and monitoring

## Usage Examples

```
Find the latest failed pipeline on my branch and get logs
```

```
List my CircleCI projects and show the status of the main branch
```

```
Find flaky tests in my current project
```

## Getting an API Token

Generate a Personal API Token from [CircleCI User Settings](https://app.circleci.com/settings/user/tokens).

## Resources

- [CircleCI Documentation](https://circleci.com/docs/)
- [MCP Server Wiki](https://github.com/CircleCI-Public/mcp-server-circleci/wiki)
