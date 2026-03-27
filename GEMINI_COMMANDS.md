# 🤖 Gemini CLI: Command Reference

> [!abstract] Overview
> This document serves as a high-level technical reference for **Gemini CLI (v0.34.0)**. It covers core slash commands, session management, and advanced features designed for local development and security research.

---

## ⚡ Slash Commands (`/`)
Slash commands are meta-controls used to manage the AI session, context, and environment.

### 🛠️ Session & Context
| Command | Alias | Description |
| :--- | :--- | :--- |
| `/init` | - | **Bootstrap**: Analyzes workspace and generates `GEMINI.md`. |
| `/chat` | `/resume` | **History**: Manage, save, or resume previous sessions. |
| `/memory` | - | **Context**: Manage hierarchical instructions via `GEMINI.md`. |
| `/dir` | `/directory`| **Workspace**: Add or show active project directories. |
| `/compress` | - | **Token Saver**: Summarizes current context to reduce overhead. |
| `/clear` | - | **Clean**: Clears terminal screen and visible history. |

### 🔍 State Control
| Command | Description |
| :--- | :--- |
| `/rewind` | **Time Travel**: Step backward through history to revert state/code. |
| `/restore` | **Recovery**: Restore files to a state before a specific tool call. |
| `/plan` | **Strategy**: View or copy the current execution plan in Plan Mode. |

### ⚙️ System & Config
| Command | Alias | Description |
| :--- | :--- | :--- |
| `/settings` | - | **Config**: Open interactive settings editor. |
| `/theme` | - | **Aesthetic**: Cycle or set CLI visual themes. |
| `/vim` | - | **Editor**: Toggle Vim-style navigation for the prompt. |
| `/stats` | - | **Metrics**: View token usage, tool calls, and session data. |
| `/help` | `/?` | **Docs**: Display help information. |
| `/quit` | `/exit` | **Term**: Exit the Gemini CLI session. |

---

## 🧬 Core Features & Integration

> [!tip] Pro-Tip: Context Injection
> Use `@filename` or `@directory` in your prompts to explicitly include local files while respecting `.gitignore`.

### 🥷 Offensive & Development Features
- **Agent Skills**: Specialized expertise modules (e.g., `skill-creator`) with custom toolsets.
- **Plan Mode**: A read--only "Research & Strategy" phase for complex architectural changes.
- **Shell Passthrough (`!`)**: Execute shell commands directly (e.g., `!ls -la` or `!checksec ./bin`).
- **MCP (Model Context Protocol)**: Connect to remote tools, databases, or specialized agents.
- **Headless Mode**: Pipe data directly: `cat exploit.c | gemini --prompt "Analyze for overflows"`.

### 🎹 Workflow Keys
> [!info] Interactive Modes
> - **Vim Mode**: Full `HJKL`, `i`, `a`, `dd` support in the input buffer.
> - **Shell Mode**: Dedicated environment for system interaction.
> - **Terminal Focus**: Press `Tab` to focus into interactive shell tools (e.g., `gdb`, `vim`).

---

## 📂 Hierarchical Memory (`GEMINI.md`)
The CLI uses a "Bottom-Up" context loading system:
1. **Global**: `~/.gemini/GEMINI.md` (Global preferences)
2. **Project**: `./GEMINI.md` (Project-specific rules)
3. **Local**: `./subdir/GEMINI.md` (Task-specific context)

---

## 🚀 Examples
```bash
# Start a new session in an exploit dev dir
gemini

# Analyze a binary with a specific skill
/skills activate binary-expert
@exploit.c How do I bypass NX on this?

# Revert a bad code change
/rewind 1

# Check token consumption
/stats
```

