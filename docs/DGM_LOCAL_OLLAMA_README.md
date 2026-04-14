# DGM with Ollama PI - Local Self-Improving Agent

A modified version of Darwin Gödel Machine (DGM) configured to run exclusively with local Ollama models via the PI coding agent. No external API keys required.

## Overview

This repository enables DGM's self-improvement loop using local Ollama pipelines:
- **Local Only** - No OpenAI/Anthropic API keys needed
- **PI Integration** - Uses `ollama/minimax-m2.7:cloud` model
- **Self-Modification** - Agent can read/modify its own code
- **Local Evaluation** - Testing against coding challenges

## Setup (Local Ollama Only)

```bash
# 1. Install Ollama
curl -fsSL https://ollama.com/install.sh | sh

# 2. Start Ollama service
ollama serve

# 3. Pull the PI model
ollama pull minimax-m2.7:cloud

# 4. Verify Ollama is running
ollama list
# Should show: minimax-m2.7:cloud

# 5. Install Python dependencies
pip install -r requirements.txt

# Note: No API keys required - everything runs locally
```

## Running DGM

```bash
# Run with local Ollama model
python DGM_outer.py --model ollama/minimax-m2.7:cloud

# Or set environment and run
export OLLAMA_MODEL=minimax-m2.7:cloud
python DGM_outer.py
```

## File Structure

```
.
├── coding_agent.py      # Main coding agent implementation
├── coding_agent_polyglot.py  # Polyglot variant
├── DGM_outer.py         # DGM outer loop entry point
├── self_improve_step.py # Self-improvement logic
├── llm.py               # LLM client (Ollama support added)
├── llm_withtools.py     # Tool-augmented LLM (Ollama support added)
├── tools/              # Available tools for the agent
│   ├── edit.py         # File editing tool
│   └── bash.py         # Bash execution tool
├── prompts/            # Prompts for self-improvement
├── swe_bench/           # SWE-bench evaluation (optional)
└── docs/               # Documentation
```

## Ollama Model Configuration

Models are accessed via `ollama/` prefix:

| Model | Configured As | Context Window |
|-------|---------------|----------------|
| minimax-m2.7:cloud | `ollama/minimax-m2.7:cloud` | 262K |

## Key Differences from Original DGM

1. **LLM Support** - Added Ollama provider in `llm.py` and `llm_withtools.py`
2. **No API Keys** - Uses local Ollama instead of OpenAI/Anthropic
3. **Simplified Setup** - No SWE-bench/Polyglot external dependencies
4. **PI Integration** - Works with PI coding agent framework

## Documentation

- [Local Ollama & OpenClaw Config](./docs/LOCAL_OLLAMA_OPENCLAW_CONFIG.md)

## Safety Consideration

> [!WARNING]  
> This repository involves executing untrusted, model-generated code. We strongly advise users to be aware of the associated safety risks.

## Acknowledgements

Based on [Darwin Gödel Machine](https://github.com/jennyzzt/dgm) by Zhang et al.
Evaluation framework based on [SWE-bench](https://github.com/swe-bench/SWE-bench).

## Citation

```bibtex
@article{zhang2025darwin,
  title={Darwin Godel Machine: Open-Ended Evolution of Self-Improving Agents},
  author={Zhang, Jenny and Hu, Shengran and Lu, Cong and Lange, Robert and Clune, Jeff},
  journal={arXiv preprint arXiv:2505.22954},
  year={2025}
}
```