# Local Ollama Pipelines & OpenClaw Configuration

## Ollama Models

| Name | ID | Size | Modified |
|------|-----|------|----------|
| minimax-m2.7:cloud | 06daa293c105 | - | 2 days ago |

**Note:** Only local model available is `minimax-m2.7:cloud`. Other cloud models (kimi-k2.5:cloud, glm-5.1:cloud) are configured but not pulled locally.

## OpenClaw Configuration

Location: `~/.openclaw/openclaw.json`

```json
{
  "agents": {
    "defaults": {
      "model": {
        "primary": "ollama/deepseek-coder:6.7b"
      },
      "workspace": "/home/mlt/.openclaw/workspace"
    }
  },
  "gateway": {
    "auth": {
      "mode": "token",
      "token": "***masked***"
    },
    "bind": "loopback",
    "mode": "local",
    "port": 18789,
    "tailscale": {
      "mode": "off",
      "resetOnExit": false
    }
  },
  "plugins": {
    "allow": ["openclaw-web-search", "ollama"],
    "entries": {
      "ollama": {"enabled": true},
      "openclaw-web-search": {"enabled": true}
    }
  },
  "session": {
    "dmScope": "per-channel-peer"
  },
  "tools": {
    "profile": "coding",
    "web": {
      "fetch": {"enabled": false},
      "search": {"enabled": false}
    }
  }
}
```

## Pi Coding Agent Models Configuration

Location: `~/.pi/agent/models.json`

```json
{
  "providers": {
    "ollama": {
      "api": "openai-completions",
      "apiKey": "ollama",
      "baseUrl": "http://127.0.0.1:11434/v1",
      "models": [
        {"_launch": true, "contextWindow": 262144, "id": "minimax-m2.7:cloud", "input": ["text", "image"], "reasoning": true},
        {"_launch": true, "contextWindow": 262144, "id": "kimi-k2.5:cloud", "input": ["text", "image"], "reasoning": true},
        {"_launch": true, "contextWindow": 202752, "id": "glm-5.1:cloud", "input": ["text"], "reasoning": true}
      ]
    }
  }
}
```

## Pi Settings

Location: `~/.pi/agent/settings.json`

```json
{
  "defaultModel": "minimax-m2.7:cloud",
  "defaultProvider": "ollama",
  "lastChangelogVersion": "0.66.1",
  "packages": [
    "npm:@ollama/pi-web-search",
    "npm:@ogulcancelik/pi-session-recall",
    "https://github.com/davebcn87/pi-autoresearch",
    "npm:pi-qmd"
  ]
}
```

## Projects

| Project | Path | Description |
|---------|------|-------------|
| dgm | ~/projects/dgm | Darwin Gödel Machine - Self-Improving AI Agent |
| mlt-autoresearch | ~/projects/mlt-autoresearch | Rust/Go hybrid build system |
| ollama-ref | ~/projects/ollama-ref | Ollama reference implementation |

## Security Notes

- Sudo password NOT stored or requested
- Gateway token is masked in this document
- Configurations read from user-level files only
- No system-wide privileged access required
