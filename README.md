# MLT Agency

MLT Agency is a self-improving AI system that integrates local Ollama pipelines with OpenClaw configuration management.

## Overview

This repository contains:
- **Local Ollama Configuration** - Documentation of local AI models and pipelines
- **OpenClaw Configuration** - Agent configuration and workspace settings
- **PI Coding Agent Setup** - Model configuration for the PI coding agent

## Local AI Stack

### Ollama Models
| Model | ID | Context Window | Features |
|-------|-----|----------------|----------|
| minimax-m2.7:cloud | 06daa293c105 | 262K | text, image, reasoning |

### OpenClaw
- Gateway Port: 18789
- Auth Mode: token-based
- Plugins: web-search, ollama

### PI Coding Agent
- Default Model: minimax-m2.7:cloud
- Base URL: http://127.0.0.1:11434/v1

## Projects

| Project | Description |
|---------|-------------|
| [DGM](./dgm/) | Darwin Gödel Machine - Self-improve |
| [mlt-autoresearch](./mlt-autoresearch/) | Rust/Go hybrid build |
| [ollama-ref](./ollama-ref/) | Ollama reference |

## Documentation

- [Local Ollama & OpenClaw Config](./docs/LOCAL_OLLAMA_OPENCLAW_CONFIG.md)

## Repository

https://github.com/tanmenglock/mlt-agency

## Generated

2026-04-14

## Agentic Self-Improving (ASI)

The DGM project has been moved to: https://github.com/tanmenglock/asi

Path: `~/projects/asi/`

Key features:
- Local Ollama-only operation (no API keys)
- Self-modifying code agent
- PI coding agent integration
