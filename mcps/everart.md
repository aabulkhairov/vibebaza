---
title: EverArt MCP
description: AI image generation using various models including FLUX, Stable Diffusion,
  and Recraft.
tags:
- Images
- AI
- Generation
- Art
author: EverArt
featured: true
install_command: claude mcp add everart -e EVERART_API_KEY=your_api_key -- npx -y
  @modelcontextprotocol/server-everart
connection_type: stdio
paid_api: true
---

The EverArt MCP server enables AI image generation using EverArt's API, supporting multiple state-of-the-art image generation models.

## Installation

```bash
npm install -g @modelcontextprotocol/server-everart
```

## Configuration

Add to your Claude Code settings:

```json
{
  "mcpServers": {
    "everart": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-everart"],
      "env": {
        "EVERART_API_KEY": "your_key_here"
      }
    }
  }
}
```

## Available Tools

### generate_image
Generates images with multiple model options. Opens result in browser and returns URL.

```typescript
generate_image(
  prompt: string,
  model?: string,
  image_count?: number
): GenerationResult
```

**Parameters:**
- `prompt` - Image description
- `model` - Model ID (optional, default: "207910310772879360")
- `image_count` - Number of images to generate (default: 1)

## Supported Models

| Model ID | Name | Description |
|----------|------|-------------|
| 5000 | FLUX1.1 | Standard FLUX model |
| 9000 | FLUX1.1-ultra | High-quality FLUX |
| 6000 | SD3.5 | Stable Diffusion 3.5 |
| 7000 | Recraft-Real | Realistic style |
| 8000 | Recraft-Vector | Vector art style |

All images are generated at 1024x1024 resolution.

## Getting an API Key

Sign up at [EverArt](https://everart.ai/) to obtain an API key.

## Usage Example

```
Claude, generate an image of a futuristic city at sunset
using the FLUX1.1-ultra model.
```

## Response Format

```
Image generated successfully!
The image has been opened in your default browser.

Generation details:
- Model: 7000
- Prompt: "A cat sitting elegantly"
- Image URL: https://storage.googleapis.com/...
```
