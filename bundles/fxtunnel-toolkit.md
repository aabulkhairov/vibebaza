---
title: "fxTunnel Toolkit"
description: "Полный набор навыков для работы с fxTunnel — реверс-туннелирование, инспекция HTTP-трафика, отладка, replay запросов и мониторинг в реальном времени"
tags:
  - fxtunnel
  - tunneling
  - reverse-proxy
  - http
  - debugging
  - traffic-analysis
  - devtools
author: "@mephistofox"
featured: true
category: "development"
---

## What's Included

Complete skill set for fxTunnel — self-hosted reverse tunneling solution (fxtun.dev). Expose local services to the internet via HTTP subdomains, TCP/UDP ports. Includes traffic inspection, debugging, replay, and real-time monitoring.

### Skills

| Skill | Description |
|-------|-------------|
| Setup | Install, authenticate, create first tunnel |
| Configure | YAML config, CLI flags, environment variables |
| Status | Health checks, active tunnels, traffic summary |
| Inspect | HTTP traffic filtering, exchange details |
| Watch | Real-time SSE traffic monitoring |
| Debug | Systematic error investigation workflow |
| Replay | Re-send captured requests with modifications |
| Diff | Compare two HTTP exchanges |
| Export | Save traffic as JSON, cURL commands, test fixtures |
| Security Scan | Traffic analysis for prompt injection and anomalies |
| Secure OpenClaw | Hardening guide for AI agent deployments |

---

## Setup

Set up fxTunnel for your project.

### Install

```bash
# Linux amd64
curl -Lo fxtunnel https://fxtun.dev/downloads/fxtunnel-linux-amd64 && chmod +x fxtunnel && sudo mv fxtunnel /usr/local/bin/

# macOS arm64
curl -Lo fxtunnel https://fxtun.dev/downloads/fxtunnel-darwin-arm64 && chmod +x fxtunnel && sudo mv fxtunnel /usr/local/bin/
```

### Authenticate

```bash
fxtunnel login
# or
fxtunnel login -t sk_your_api_token
```

### Create Config

Create `fxtunnel.yaml` in your project root:

```yaml
server:
  address: mfdev.ru:4443

tunnels:
  - name: web
    type: http
    local_port: 3000

inspect:
  enabled: true
```

### Start

```bash
fxtunnel             # from config
fxtunnel http 3000   # quick one-off
```

### Verify

```bash
curl -s http://127.0.0.1:4040/api/status | jq
curl -s http://127.0.0.1:4040/api/tunnels | jq
```

---

## Configure

### Config File Locations

1. `fxtunnel.yaml` in current directory
2. `client.yaml` in current directory
3. `configs/client.yaml`
4. `~/.fxtunnel/client.yaml`

### Full Config Example

```yaml
server:
  address: mfdev.ru:4443
  token: sk_your_token_here
  compression: true

tunnels:
  - name: web
    type: http
    local_port: 3000
    subdomain: myapp
  - name: ssh
    type: tcp
    local_port: 22

inspect:
  enabled: true
  addr: "127.0.0.1:4040"
  max_body_size: 262144
  max_entries: 1000

reconnect:
  enabled: true
  interval: 5s
  max_attempts: 0
```

### CLI Flags

```bash
fxtunnel http 3000 --domain myapp
fxtunnel tcp 22 --remote-port 2222
fxtunnel http 3000 --no-inspect
fxtunnel http 3000 --inspect-addr 0.0.0.0:5050
```

### Environment Variables

All config overridden via `FXTUNNEL_` prefix:

```bash
FXTUNNEL_SERVER_ADDRESS=mfdev.ru:4443
FXTUNNEL_SERVER_TOKEN=sk_xxx
FXTUNNEL_INSPECT_ENABLED=true
```

---

## Status

### Quick Health Check

```bash
echo "=== Inspector ===" && \
curl -s http://127.0.0.1:4040/api/status | jq '{version, uptime_seconds, total_exchanges}' && \
echo "=== Tunnels ===" && \
curl -s http://127.0.0.1:4040/api/tunnels | jq '.tunnels[] | {name, type, url, local_port}' && \
echo "=== Traffic ===" && \
curl -s http://127.0.0.1:4040/api/requests/http/summary | jq '{total, error_rate, avg_duration_ms}'
```

---

## Inspect

### List Requests

```bash
curl -s 'http://127.0.0.1:4040/api/requests/http?limit=20' | jq
```

### Filtering

| Parameter | Example | Description |
|-----------|---------|-------------|
| `method` | `POST` | HTTP method |
| `status` | `5xx` or `404` | Status range or exact code |
| `path` | `/api/*` | Glob pattern |
| `search` | `error` | Search in bodies |
| `since` | `5m` | Time window |
| `include_body` | `true` | Include base64 bodies |
| `limit` | `50` | Max results |

### Exchange Detail

```bash
curl -s http://127.0.0.1:4040/api/requests/http/{id} | jq
```

---

## Watch

### Live SSE Stream

```bash
curl -s -N http://127.0.0.1:4040/api/requests/http/stream
```

### Watch Only Errors

```bash
curl -s -N http://127.0.0.1:4040/api/requests/http/stream | \
  grep --line-buffered '^data:' | sed 's/^data: //' | \
  jq --unbuffered 'select(.status_code >= 400) | {method, path, status_code}'
```

### Watch Specific Path

```bash
curl -s -N http://127.0.0.1:4040/api/requests/http/stream | \
  grep --line-buffered '^data:' | sed 's/^data: //' | \
  jq --unbuffered 'select(.path | startswith("/api/")) | {method, path, status_code}'
```

---

## Debug

### Systematic Workflow

1. **Assess** — get traffic summary:

```bash
curl -s http://127.0.0.1:4040/api/requests/http/summary | jq
```

2. **Find errors** — 5xx and 4xx:

```bash
curl -s 'http://127.0.0.1:4040/api/requests/http?status=5xx&limit=10' | jq '.requests[] | {id, method, path, status_code, duration_ms}'
```

3. **Inspect details** — full exchange by ID:

```bash
curl -s http://127.0.0.1:4040/api/requests/http/{id} | jq
```

4. **Find slow requests** — duration > 1s:

```bash
curl -s 'http://127.0.0.1:4040/api/requests/http?limit=50' | jq '[.requests[] | select(.duration_ms > 1000)] | sort_by(-.duration_ms) | .[] | {id, method, path, duration_ms}'
```

5. **Replay and verify** — re-send after fix.

### Common Patterns

- **Auth issues:** filter 401/403, check Authorization headers
- **Payload issues:** get exchange with body, validate JSON
- **Timeout issues:** check duration_ms near timeout limit
- **CORS issues:** look for OPTIONS preflights, check response headers

---

## Replay

### Basic Replay

```bash
curl -s -X POST http://127.0.0.1:4040/api/requests/http \
  -H 'Content-Type: application/json' \
  -d '{"id":"EXCHANGE_ID"}' | jq
```

### Modified Replay

```bash
curl -s -X POST http://127.0.0.1:4040/api/requests/http \
  -H 'Content-Type: application/json' \
  -d '{
    "id": "EXCHANGE_ID",
    "method": "PUT",
    "path": "/api/v2/webhook",
    "headers": {"Authorization": "Bearer new-token"},
    "body": "BASE64_ENCODED_BODY"
  }' | jq
```

---

## Diff

### Compare Two Exchanges

```bash
A=$(curl -s http://127.0.0.1:4040/api/requests/http/EXCHANGE_ID_A)
B=$(curl -s http://127.0.0.1:4040/api/requests/http/EXCHANGE_ID_B)

echo "=== Request Diff ==="
diff <(echo "$A" | jq '{method, path, host, request_headers}') \
     <(echo "$B" | jq '{method, path, host, request_headers}')

echo "=== Response Diff ==="
diff <(echo "$A" | jq '{status_code, response_headers}') \
     <(echo "$B" | jq '{status_code, response_headers}')

echo "=== Body Diff ==="
diff <(echo "$A" | jq -r '.request_body | @base64d' 2>/dev/null) \
     <(echo "$B" | jq -r '.request_body | @base64d' 2>/dev/null)
```

---

## Export

### All Traffic to JSON

```bash
curl -s 'http://127.0.0.1:4040/api/requests/http?limit=100&include_body=true' | jq > traffic_export.json
```

### Errors Only

```bash
curl -s 'http://127.0.0.1:4040/api/requests/http?status=5xx&include_body=true&limit=100' | jq > errors.json
```

### Test Fixtures

```bash
ID="EXCHANGE_ID"
curl -s "http://127.0.0.1:4040/api/requests/http/$ID" | jq '{
  request: {method, path, host, request_headers, request_body: (.request_body | @base64d | fromjson?)},
  response: {status_code, response_headers, response_body: (.response_body | @base64d | fromjson?)}
}' > fixture.json
```

---

## Security Scan

AI-powered analysis of HTTP traffic to detect prompt injection, data exfiltration, and anomalous patterns targeting AI agents.

### Quick Scan

```bash
echo "=== Prompt Injection ===" && \
curl -s 'http://127.0.0.1:4040/api/requests/http?search=ignore+previous&limit=5' | jq '.total' && \
curl -s 'http://127.0.0.1:4040/api/requests/http?search=system+prompt&limit=5' | jq '.total' && \
echo "=== Key Leaks ===" && \
curl -s 'http://127.0.0.1:4040/api/requests/http?search=sk-&limit=5' | jq '.total' && \
curl -s 'http://127.0.0.1:4040/api/requests/http?search=PRIVATE+KEY&limit=5' | jq '.total' && \
echo "=== Path Traversal ===" && \
curl -s 'http://127.0.0.1:4040/api/requests/http?search=..%2F&limit=5' | jq '.total' && \
echo "=== Error Spike ===" && \
curl -s 'http://127.0.0.1:4040/api/requests/http/summary' | jq '{error_rate, total, by_status}'
```

### Threat Categories

**Prompt Injection** — patterns in request bodies:
- Direct: `ignore previous`, `disregard instructions`, `you are now`, `system prompt`
- Role hijacking: `pretend you are`, `act as`, `override`
- Delimiter attacks: `###`, `---`, `<|endoftext|>`, `[INST]`, `<<SYS>>`
- Encoded payloads: base64 strings containing injection patterns

**Data Exfiltration** — in response bodies:
- API keys: `sk-`, `sk_`, `Bearer `, `AKIA` (AWS)
- Private keys: `-----BEGIN`, `PRIVATE KEY`
- Credentials: `password`, `secret`, `credential`
- File paths: `/etc/passwd`, `.ssh/`, `.env`, `id_rsa`
- Unusually large response bodies

**Anomalous Patterns:**
- Path traversal: `../`, `..%2F`, `%2e%2e`
- Command injection in headers
- Rapid request bursts
- Unexpected content types
- WebSocket upgrade to unexpected paths

### Severity Levels

| Severity | Criteria |
|----------|----------|
| CRITICAL | Active prompt injection with success, confirmed key leak |
| HIGH | Injection attempt, path traversal, potential exfiltration |
| MEDIUM | Anomalous patterns, unusual methods, suspicious payloads |
| LOW | Minor anomalies, information disclosure |

---

## Secure OpenClaw

Step-by-step hardening for OpenClaw AI agent deployments. Based on SecurityScorecard STRIKE research (135K+ exposed instances, 3 CVEs with public exploits).

### Pre-flight

```bash
ss -tlnp | grep 18789
# 0.0.0.0:18789 = EXPOSED RIGHT NOW
# 127.0.0.1:18789 = good
```

### Step 1: Bind to localhost

```json
{
  "gateway": {
    "bind": "127.0.0.1",
    "port": 18789,
    "auth": {
      "mode": "token",
      "token": "RANDOM-TOKEN-MIN-32-CHARS"
    }
  }
}
```

### Step 2: Firewall

```bash
# Ubuntu/Debian
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22/tcp
sudo ufw limit 22/tcp
sudo ufw deny 18789/tcp
sudo ufw enable
```

### Step 3: fxTunnel tunnel

```bash
curl -fsSL https://fxtun.dev/install.sh | sh
fxtunnel auth login
fxtunnel http 18789 --subdomain my-ai-agent
# Accessible at: https://my-ai-agent.fxtun.dev
# Port 18789 stays CLOSED
```

### Step 4: Docker isolation

```yaml
services:
  openclaw:
    image: openclaw/agent:latest
    security_opt:
      - no-new-privileges:true
    read_only: true
    user: "1000:1000"
    cap_drop:
      - ALL
    ports:
      - "127.0.0.1:18789:18789"
```

### 10-Minute Checklist

1. `gateway.bind = "127.0.0.1"`
2. Auth token set (min 32 chars)
3. Firewall: `ufw deny 18789/tcp`
4. fxTunnel installed and running
5. IP allowlist in fxTun.dev panel
6. Docker: `cap_drop: ALL`, `no-new-privileges`
7. Update OpenClaw to v2026.2.1+
8. Rotate all API keys
9. Fail2Ban for SSH
10. Verify: `ss -tlnp | grep 18789` → 127.0.0.1 only

### CVE Reference

- **CVE-2026-25253** (CVSS 8.8) — 1-click RCE via gatewayUrl, token leak via CSWSH
- **CVE-2026-25157** (CVSS 7.8) — Command injection via SSH on macOS
- **CVE-2026-24763** (CVSS 8.8) — Docker sandbox escape via PATH manipulation
