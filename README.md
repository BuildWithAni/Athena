# Athena ⚡

**Permission-gated CLI coding assistant powered by local LLMs (Ollama).**

Athena is an elite terminal-based software engineering assistant that runs entirely on your machine via Ollama. It features a rich REPL interface, autonomous agentic mode, conversation memory, file system tools, and a safe permission-gated execution model.

![Version](https://img.shields.io/badge/version-3.2.0-blue)
[![GitHub](https://img.shields.io/badge/Created%20by-CodeWithAni-181717?logo=github)](https://github.com/CodeWithAni)

---

## Features

- **Permission-gated execution** — Athena asks before running any command, especially destructive ones
- **Local & private** — All inference runs through Ollama using models on your own machine
- **Rich REPL** — Tab completion, syntax highlighting, streaming responses, splash screen
- **Conversation management** — Save, load, search, and tag conversations
- **Persistent memory** — Facts, preferences, and learned corrections survive across sessions
- **Autonomous agent mode** — Divide & Conquer orchestration for complex multi-step tasks
- **Built-in file tools** — `/tree`, `/grep`, `/cat`, `/head`, `/tail`, `/write`, `/replace`, `/undo`, and more
- **Code execution** — Run Python, shell, and other code blocks with safety confirmation
- **Persona system** — Switch between different assistant personas
- **Cross-platform** — Works on Windows, macOS, and Linux

---

## Requirements

- **Python 3.10+**
- **[Ollama](https://ollama.com)** — Local LLM runtime
- An Ollama model pulled (default: `llama3.2`)

### Python Dependencies

```
rich
prompt_toolkit
pygments
ollama
```

Install with:

```bash
pip install rich prompt_toolkit pygments ollama
```

---

## Quick Start

1. **Install Ollama** and pull a model:

   ```bash
   ollama pull llama3.2
   ```

2. **Install Python dependencies**:

   ```bash
   pip install rich prompt_toolkit pygments ollama
   ```

3. **Run Athena**:

   ```bash
   python athena.py
   ```

   You'll see the splash screen and land in the interactive REPL.

---

## Usage

### REPL Commands

| Command | Description |
|---------|-------------|
| `/help` | Show all commands |
| `/new` | Start a new conversation |
| `/model <name>` | Switch Ollama model |
| `/save` | Save current conversation |
| `/load <id>` | Load a saved conversation |
| `/history` | List saved conversations |
| `/memory` | Show stored facts & preferences |
| `/persona <name>` | Switch assistant persona |
| `/run [n]` | Execute a code block |
| `/tree` | Display directory tree |
| `/grep <pattern>` | Search files by content |
| `/undo` | Restore the last file backup |
| `/write <path>` | Write content to a file |
| `/config` | Show current configuration |
| `/set <key> <value>` | Change a config setting |
| `/quit` | Exit Athena |

Type any question or request directly — Athena treats free-form input as a chat message and will respond, write code, or execute commands as needed (always asking for confirmation first).

### Safe by Default

Athena's default configuration (`confirm_all: true`, `auto_execute: false`) means it will **always ask for your permission** before executing any code or shell command. Destructive operations are highlighted in red.

You can adjust these settings with `/set`:

```bash
/set confirm_all false    # Skip confirm prompts
/set auto_execute true    # Run without asking (not recommended)
```

---

## Files

| File | Description |
|------|-------------|
| `athena.py` | Modular bundle — the recommended entry point |
| `athena_standalone.py` | Self-contained standalone bundle |
| `athena_monolith.py` | Original single-file monolith (v3.0) |

All three are fully functional. Run any of them with `python <filename>`.

---

## Configuration

Athena stores its configuration at `~/.athena/config.json`. Key settings:

| Setting | Default | Description |
|---------|---------|-------------|
| `model` | `llama3.2` | Ollama model to use |
| `temperature` | `0.1` | LLM temperature (0.0–1.0) |
| `max_tokens` | `8192` | Max tokens per response |
| `stream` | `true` | Stream responses word-by-word |
| `confirm_all` | `true` | Always ask before executing |
| `auto_execute` | `false` | Auto-run code without confirmation |
| `context_window` | `40` | Number of messages to keep |

---

## Architecture

Athena is organized as a Python package with these modules:

- **`prompts`** — System prompts, personas, and templates
- **`runtime`** — Runtime discovery, health checks, and diagnostics
- **`config`** — Global configuration, paths, color palette, console
- **`memory`** — Persistent memory (facts, preferences, corrections)
- **`ui`** — Splash screen, environment context, stats display
- **`detection`** — Code/language detection, dangerous-command patterns
- **`files`** — File reading, extension detection, auto-injection
- **`tools`** — Backup/undo system, CLI tools (tree, grep, replace)
- **`execution`** — Code execution engine with safety checks
- **`streaming`** — LLM streaming, deep thinking, clarification
- **`conversation`** — Conversation manager, save/load/search
- **`completer`** — Tab completion for the CLI
- **`rendering`** — Rich-formatted response rendering
- **`commands`** — Command definitions, help, export
- **`agents`** — Agentic execution and Divide & Conquer orchestrator

---

## License

MIT

---

<p align="center">
  Created with ❤️ by <a href="https://github.com/CodeWithAni"><b>CodeWithAni</b></a>
  <br>
  <a href="https://github.com/CodeWithAni">github.com/CodeWithAni</a>
</p>
