<div align="center">

# Orchestrator

[![GitHub Repo](https://img.shields.io/badge/GitHub-Repo-black.svg?logo=github)](https://github.com/0xtrou/snapfzz-orchestrator)
[![PyPI](https://img.shields.io/pypi/v/qwenpaw?color=3775A9&label=PyPI&logo=pypi)](https://pypi.org/project/qwenpaw/)
[![Python Version](https://img.shields.io/badge/python-3.10%20~%20%3C3.14-blue.svg?logo=python&label=Python)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-Apache%202.0-red.svg?logo=apache&label=License)](LICENSE)
[![Discord](https://img.shields.io/badge/Discord-Join_Us-blueviolet.svg?logo=discord)](https://discord.gg/eYMpfnkG8h)

<p align="center"><b>International multi-agent orchestration framework.</b></p>

</div>

Orchestrator is a self-hosted multi-agent AI framework — deploy locally or in the cloud, connect across channels, extend with custom skills.

> **Core capabilities:**
>
> **Under your control** — Memory and personalization fully under your control. Deploy locally (data stays on your machine) or in the cloud (your chosen server). No third-party hosting, no data upload.
>
> **Skills extension** — Built-in scheduling, PDF/Office processing, news digest, and more; custom skills auto-loaded, no lock-in. Skills determine what Orchestrator can do.
>
> **Multi-agent collaboration** — Create multiple independent agents, each with their own role; enable collaboration skills for inter-agent communication to tackle complex tasks together.
>
> **Multi-layer security** — Tool guard, file access control, skill security scanning to ensure safe operation.
>
> **Every channel** — Discord, Telegram, WeChat, and more. One Orchestrator, connect as needed.

---

## News

[2026-04-17] We've released **v1.1.2**! See the full [v1.1.2 Release Notes](https://qwenpaw.agentscope.io/release-notes).

- **[v1.1.2] Added**: Mission Mode (`/mission`) for autonomous, multi-phase task execution; ACP protocol for external agent delegation; `qwenpaw doctor` diagnostic command; `qwenpaw agents create` CLI agent creation; scheduled memory consolidation (Dream); new Debug page.
- **[v1.1.2] Changed**: Agent communication tools split into synchronous/asynchronous modes; provider list sorted by availability.
- **[v1.1.2] New Contributors**: @FrankJingHao, @ployts, @cqhtyi, @leesf, @flystar32.

[2026-04-14] We've released v1.1.1! See the full [v1.1.1 Release Notes](https://qwenpaw.agentscope.io/release-notes).

[2026-04-12] **CoPaw is Officially Rebranding to Orchestrator**: This rebranding marks an important step forward into our next phase of open-source development.

The new name better reflects the open ecosystem we are building and the broader direction we are continuing to pursue:

*Qwen* — represents a deeper integration with the Qwen open-source ecosystem and a sharper focus on the model layer, including local models for agents and smart collaboration between small and large models.

*Paw* — carries forward our original mission to accompany users and become a personal assistant users can truly trust.

This rebranding does not change our vision and goals in the open-source community:
- To build a more practical, secure, and personalized AI assistant;
- To stay committed to open-source collaboration and move forward together with the community.

Thank you all for your support along the way.
From today on, Orchestrator will stay and grow with you!

---

## Table of Contents

> **Recommended reading:**
>
> - **🚀 I'm new and want to try quickly**: [Quick Start](#quick-start) → three commands to run → [Configure model](#api-key) → chat in Console
> - **💬 I want to use in DingTalk/Feishu/WeChat**: Complete Quick Start → [Configure model](#api-key) → [Channel setup](https://qwenpaw.agentscope.io/docs/channels)
> - **🐍 I don't want to install Python**: [Desktop app](#option-6-desktop-application-beta) or [Script install](#option-2-script-install) or [ModelScope Studio](https://modelscope.cn/studios/fork?target=AgentScope/Orchestrator)
> - **💻 I want to use local models (no API key needed)**: [Local Models](#local-models) → download model → start using
> - **🛠️ I want to contribute code or develop new features**: [Install from source](#install-from-source) → [Contributing](#contributing)
- [News](#news)
- [Quick Start](#quick-start)
- [API Key](#api-key)
- [Local Models](#local-models)
- [Documentation](#documentation)
- [Security Features](#security-features)
- [FAQ](#faq)
- [Staying ahead](#staying-ahead)
- [Roadmap](#roadmap)
- [Install from source](#install-from-source)
- [Contributing](#contributing)
- [Why Orchestrator?](#why-qwenpaw)
- [Built by](#built-by)
- [License](#license)

---

## Quick Start

### Option 1: pip install

If you prefer managing Python yourself:

```bash
pip install qwenpaw
qwenpaw init --defaults
qwenpaw app
```

Then open the Console in your browser at **http://127.0.0.1:8088/** to configure your model. To chat in DingTalk, Feishu, WeChat, etc., see the [Channel setup](https://qwenpaw.agentscope.io/docs/channels) documentation.

![Console](https://img.alicdn.com/imgextra/i2/O1CN01EP1ra01iOAcBvF0TC_!!6000000004402-2-tps-3822-2070.png)

---

### Option 2: Script install

No Python setup required, one command installs everything. The script will automatically download uv (Python package manager), create a virtual environment, and install Orchestrator with all dependencies (including Node.js and frontend assets). Note: May not work in restricted network environments or corporate firewalls.

**macOS / Linux:**

```bash
curl -fsSL https://qwenpaw.agentscope.io/install.sh | bash
```

**Windows (CMD):**

```CMD
curl -fsSL https://qwenpaw.agentscope.io/install.bat -o install.bat && install.bat
```

**Windows (PowerShell):**

```powershell
irm https://qwenpaw.agentscope.io/install.ps1 | iex
```

> **Note**: The installer will automatically check the status of uv. If it is not installed, it will attempt to download and configure it automatically. If the automatic installation fails, please follow the on-screen prompts or execute `python -m pip install -U uv`, then rerun the installer.

> **⚠️ Special Notice for Windows Enterprise LTSC Users**
>
> If you are using Windows LTSC or an enterprise environment governed by strict security policies, PowerShell may run in **Constrained Language Mode**, potentially causing the following issue:
> 1. **If using CMD (.bat): Script executes successfully but fails to write to `Path`**
>
>    The script completes file installation. Due to **Constrained Language Mode**, it cannot automatically update environment variables. Manually configure as follows:
>    - **Locate the installation directory**:
>      - Check if `uv` is available: Enter `uv --version` in CMD. If a version number appears, **only configure the Orchestrator path**. If you receive the prompt `'uv' is not recognized as an internal or external command, operable program or batch file,` configure both paths.
>      - uv path (choose one based on installation location; use if `uv` fails): Typically `%USERPROFILE%\.local\bin`, `%USERPROFILE%\AppData\Local\uv`, or the `Scripts` folder within your Python installation directory
>      - Orchestrator path: Typically located at `%USERPROFILE%\.qwenpaw\bin`.
>    - **Manually add to the system's Path environment variable**:
>      - Press `Win + R`, type `sysdm.cpl` and press Enter to open System Properties.
>      - Click “Advanced” -> “Environment Variables”.
>      - Under “System variables”, locate and select `Path`, then click “Edit”.
>      - Click “New”, enter both directory paths sequentially, then click OK to save.
> 2. **If using PowerShell (.ps1): Script execution interrupted**
>
>   Due to **Constrained Language Mode**, the script may fail to automatically download `uv`.
>   - **Manually install uv**: Refer to the [GitHub Release](https://github.com/astral-sh/uv/releases) to download `uv.exe` and place it in `%USERPROFILE%\.local\bin` or `%USERPROFILE%\AppData\Local\uv`; or ensure Python is installed and run `python -m pip install -U uv`.
>   - **Configure `uv` environment variables**: Add the `uv` directory and `%USERPROFILE%\.qwenpaw\bin` to your system's `Path` variable.
>   - **Re-run the installation**: Open a new terminal and execute the installation script again to complete the `Orchestrator` installation.
>   - **Configure the `Orchestrator` environment variable**: Add `%USERPROFILE%\.qwenpaw\bin` to your system's `Path` variable.

Once installed, open a new terminal and run:

```bash
qwenpaw init --defaults   # or: qwenpaw init (interactive)
qwenpaw app
```

<details>
<summary><b>Install options</b></summary>

**macOS / Linux:**

```bash
# Install a specific version
curl -fsSL ... | bash -s -- --version 1.1.0

# Install from source (dev/testing)
curl -fsSL ... | bash -s -- --from-source

# Upgrade — just re-run the installer
curl -fsSL ... | bash

# Uninstall
qwenpaw uninstall          # keeps config and data
qwenpaw uninstall --purge  # removes everything
```

**Windows (PowerShell):**

```powershell
# Install a specific version
irm ... | iex; .\install.ps1 -Version 0.0.2

# Install from source (dev/testing)
.\install.ps1 -FromSource

# Upgrade — just re-run the installer
irm ... | iex

# Uninstall
qwenpaw uninstall          # keeps config and data
qwenpaw uninstall --purge  # removes everything
```

</details>


---

### Option 3: Docker

Images are on **Docker Hub** (`agentscope/qwenpaw`). Image tags: `latest` (stable); `pre` (PyPI pre-release).

```bash
docker pull agentscope/qwenpaw:latest
docker run -p 127.0.0.1:8088:8088 \
  -v qwenpaw-data:/app/working \
  -v qwenpaw-secrets:/app/working.secret \
  -v qwenpaw-backups:/app/working.backups \
  agentscope/qwenpaw:latest
```

Also available on Alibaba Cloud Container Registry (ACR) for users in China: `agentscope-registry.ap-southeast-1.cr.aliyuncs.com/agentscope/qwenpaw` (same tags).

Then open **http://127.0.0.1:8088/** for the Console. Config, memory, and skills are stored in the `qwenpaw-data` volume; model provider settings and API keys are in the `qwenpaw-secrets` volume; backup archives are stored in the `qwenpaw-backups` volume. To pass API keys (e.g. `DASHSCOPE_API_KEY`), add `-e VAR=value` or `--env-file .env` to `docker run`.

> **Connecting to Ollama or other services on the host machine**
>
> Inside a Docker container, `localhost` refers to the container itself, not your host machine. If you run Ollama (or other model services) on the host and want Orchestrator in Docker to reach them, use one of these approaches:
>
> **Option A** — Explicit host binding (all platforms):
> ```bash
> docker run -p 127.0.0.1:8088:8088 \
>   --add-host=host.docker.internal:host-gateway \
>   -v qwenpaw-data:/app/working \
>   -v qwenpaw-secrets:/app/working.secret \
>   -v qwenpaw-backups:/app/working.backups \
>   agentscope/qwenpaw:latest
> ```
> Then in Orchestrator **Settings → Models**, change the Base URL to `http://host.docker.internal:<port>` — for example, `http://host.docker.internal:11434` for Ollama, or `http://host.docker.internal:1234/v1` for LM Studio.
>
> **Option B** — Host networking (Linux only):
> ```bash
> docker run --network=host \
>   -v qwenpaw-data:/app/working \
>   -v qwenpaw-secrets:/app/working.secret \
>   -v qwenpaw-backups:/app/working.backups \
>   agentscope/qwenpaw:latest
> ```
> No port mapping (`-p`) is needed; the container shares the host network directly. Note that all container ports are exposed on the host, which may cause conflicts if the port is already in use.
>
> **Note:** If you only mount `/app/working` without a separate volume for `/app/working.secret`, the entrypoint will automatically redirect secrets into `/app/working/.secret` so they persist on the same volume.

The image is built from scratch. To build the image yourself, please refer to the [Build Docker image](scripts/README.md#build-docker-image) section in `scripts/README.md`, and then push to your registry.

---

### Option 4: Deploy on Alibaba Cloud ECS

To run Orchestrator on Alibaba Cloud (ECS), use the one-click deployment: open the [Orchestrator on Alibaba Cloud (ECS) deployment link](https://computenest.console.aliyun.com/service/instance/create/cn-hangzhou?type=user&ServiceId=service-1ed84201799f40879884) and follow the prompts. For step-by-step instructions, see [Alibaba Cloud Developer: Deploy your AI assistant in 3 minutes](https://developer.aliyun.com/article/1713682).

---

### Option 5: Using ModelScope

**No local install?** [ModelScope Studio](https://modelscope.cn/studios/fork?target=AgentScope/Orchestrator) one-click cloud setup. Set your Studio to **non-public** so others cannot control your Orchestrator.

---

### Option 6: Desktop Application (Beta)

> **Beta Notice**: The desktop application is currently in Beta testing phase with the following known limitations:
> - **Incomplete compatibility testing**: Not fully tested across all system versions and hardware configurations
> - **Potential performance issues**: Startup time, memory usage, and other performance aspects may need further optimization
> - **Features under development**: Some features may be unstable or missing

If you're not comfortable with command-line tools, you can download and use Orchestrator's desktop application without manually configuring Python environments or running commands.

#### Download

Download the desktop app from [GitHub Releases](https://github.com/agentscope-ai/Orchestrator/releases):
- **Windows**: `Orchestrator-Setup-<version>.exe`
- **macOS**: `Orchestrator-<version>-macOS.zip` (Apple Silicon recommended)

#### Features

- ✅ **Zero configuration**: Download and double-click to run, no need to install Python or configure environment variables
- ✅ **Cross-platform**: Supports Windows 10+ and macOS 14+
- ✅ **Visual interface**: Automatically opens browser interface, no need to manually enter addresses
- ⚠️ **Beta stage**: Features are continuously being improved, feedback welcome

#### First Launch

**Important**: The first launch may take 10-60 seconds (depending on your system configuration). The application needs to initialize the Python environment and load dependencies. Please wait patiently for the browser window to open automatically.

#### macOS: Bypass System Security Restrictions

When you download the Orchestrator macOS app from Releases, macOS may show: *"Apple cannot verify that 'Orchestrator' contains no malicious software"*. This happens because the app is not notarized. You can still open it as follows:

- **Right-click to open (recommended)**
  Right-click (or Control+click) the Orchestrator app → **Open** → in the dialog click **Open** again. This tells Gatekeeper you trust the app; after that you can double-click to launch as usual.

- **Allow in System Settings**
  If it is still blocked, go to **System Settings → Privacy & Security**, scroll to the message like *"Orchestrator was blocked because it is from an unidentified developer"*, and click **Open Anyway** or **Allow**.

- **Remove quarantine attribute (not recommended for most users)**
  In Terminal run:
  `xattr -cr /Applications/Orchestrator.app`
  (or use the path to the `.app` after unzipping). This clears the "downloaded from the internet" quarantine flag so the warning usually does not appear, but is less safe and controllable than using **Right-click → Open**.

For detailed usage instructions, troubleshooting, and common issues, see the [Desktop Application Guide](https://qwenpaw.agentscope.io/docs/desktop).

---

## API Key

If you use a **cloud LLM API** (e.g., Qianwen, Gemini, OpenAI), you must configure an API key before chatting. Orchestrator will not work until a valid key is set. See the [official docs](https://qwenpaw.agentscope.io/docs/models) for details.

**How to configure:**

1. **Console (recommended)** — After running `qwenpaw app`, open **http://127.0.0.1:8088/** → **Settings** → **Models**. Choose a provider, enter the **API Key**, and enable that provider and model.
2. **`qwenpaw init`** — When you run `qwenpaw init`, it will guide you through configuring the LLM provider and API key. Follow the prompts to choose a provider and enter your key.
3. **Environment variable** — For DashScope you can set `DASHSCOPE_API_KEY` in your shell or in a `.env` file in the working directory.

Tools that need extra keys (e.g. `TAVILY_API_KEY` for web search) can be set in Console **Settings → Environment variables**, see [Config](https://qwenpaw.agentscope.io/docs/config) for details.

> **Using local models only?** If you use [Local Models](#local-models) (llama.cpp / Ollama / LM Studio), you do **not** need any API key.

## Local Models

Orchestrator can run LLMs entirely on your machine — no API keys or cloud services required. See the [official docs](https://qwenpaw.agentscope.io/docs/models) for details.

| Backend       | Best for                                 | Install                                                              |
| ------------- | ---------------------------------------- | -------------------------------------------------------------------- |
| **llama.cpp** | Cross-platform (macOS / Linux / Windows) | No extra installation required; click "Download Llama.cpp" in the web UI. |
| **Ollama**    | Cross-platform (requires Ollama service) | Install and start the Ollama app in advance. |
| **LM Studio** | Cross-platform (requires LM Studio service) | Install and start the LM Studio app in advance. |

---

## Documentation

| Topic                                                                 | Description                                      |
| --------------------------------------------------------------------- | ------------------------------------------------ |
| [Introduction](https://qwenpaw.agentscope.io/docs/intro)                | What Orchestrator is and how to use it                  |
| [Quick start](https://qwenpaw.agentscope.io/docs/quickstart)            | Install and run (local or ModelScope Studio)    |
| [Console](https://qwenpaw.agentscope.io/docs/console)                   | Web UI: chat and agent configuration            |
| [Models](https://qwenpaw.agentscope.io/docs/models)                     | Configure cloud, local, and custom providers    |
| [Channels](https://qwenpaw.agentscope.io/docs/channels)                  | DingTalk, Feishu, QQ, Discord, iMessage, and more |
| [Skills](https://qwenpaw.agentscope.io/docs/skills)                      | Extend and customize capabilities               |
| [MCP](https://qwenpaw.agentscope.io/docs/mcp)                            | Manage MCP clients                               |
| [Memory](https://qwenpaw.agentscope.io/docs/memory)                     | Long-term memory                     |
| [Context](https://qwenpaw.agentscope.io/docs/context)                   | Context management mechanism                     |
| [Magic commands](https://qwenpaw.agentscope.io/docs/commands)           | Control conversation state without waiting for the AI |
| [Heartbeat](https://qwenpaw.agentscope.io/docs/heartbeat)                | Scheduled check-in and digest                    |
| [Multi-Agent](https://qwenpaw.agentscope.io/docs/multi-agent)           | Create multiple agents and enable collaboration  |
| [Config & working dir](https://qwenpaw.agentscope.io/docs/config) | Working directory and config file                |
| [CLI](https://qwenpaw.agentscope.io/docs/cli)                            | Init, cron jobs, skills, clean                   |
| [FAQ](https://qwenpaw.agentscope.io/docs/faq)                           | Common questions and troubleshooting             |

Full docs in this repo: [website/public/docs/](website/public/docs/).

---

## Security Features

Orchestrator includes multi-layer security mechanisms to protect your data and system:

- **Tool guard** — Automatically intercepts dangerous shell commands (e.g., `rm -rf /`, fork bombs, reverse shells, etc.)
- **File access guard** — Restricts agent access to sensitive paths (e.g., `~/.ssh`, key files, system directories, etc.)
- **Skill security scanning** — Automatically scans before installing skills, detecting risks like prompt injection, command injection, hardcoded keys, data exfiltration, etc.
- **Local deployment** — All data and memory stored locally, no third-party upload (when using cloud LLM APIs, conversation content is sent to the corresponding API provider)
- **Web Authentication** — Optional login protection for the Console. Disabled by default; set `QWENPAW_AUTH_ENABLED=true` to enable. See [Web Authentication](https://qwenpaw.agentscope.io/docs/security#Web-Authentication) for details.

See [Security documentation](https://qwenpaw.agentscope.io/docs/security) for details.

---

## FAQ

For common questions, troubleshooting tips, and known issues, please visit the **[FAQ page](https://qwenpaw.agentscope.io/docs/faq)**.

---

## Staying ahead

<a href="https://github.com/agentscope-ai/Orchestrator">
  <img src="https://img.alicdn.com/imgextra/i1/O1CN01V8HYv61By0HYcIDaq_!!6000000000013-1-tps-1698-954.gif" width="600" alt="Star Orchestrator" />
</a>

Star Orchestrator on GitHub and be instantly notified of new releases.

---

## Roadmap

| Area                                  | Item                                                                                                                                             | Status               |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------- |
| **Horizontal Expansion**              | More channels, models, skills, MCPs — **community contributions welcome**                                                                        | Seeking Contributors |
| **Existing Feature Extension**        | Display optimization, download hints, Windows path compatibility, etc. — **community contributions welcome**                                     | Seeking Contributors |
| **Multi-agent**                       | HiClaw integration: multi-tenant, cross-domain collaboration                                                                                     | In Progress          |
|                                       | Agent Swarm / Team                                                                                                                               | Planned              |
| **Small + Large Model Collaboration** | Intelligent switching between on-device and cloud models                                                                                         | In Progress          |
| **Orchestrator Custom Models**             | Multimodal model support                                                                                                                           | Planned              |
| **Memory System**                     | Context-aware proactive delivery                                                                                                                   | In Progress          |
| **Context Management**                | Abstract design                                                                                                                                  | In Progress          |
|                                       | Intelligent context compression                                                                                                                  | Planned              |
|                                       | User-selectable compression (fine-grained control)                                                                                                 | Planned              |
| **Versioning & Migration**            | One-click packaging; multi-version / multi-device migration                                                                                        | In Progress          |
|                                       | Agent protocol: Orchestrator → Orchestrator                                                                                                                | In Progress          |
|                                       | Agent protocol: OpenClaw → Orchestrator                                                                                                               | Planned              |
|                                       | File area / chat rollback                                                                                                                        | In Progress          |
| **Reliability & Self-operations**     | Self-update                                                                                                                                      | Planned              |
|                                       | Failure rollback                                                                                                                                 | Planned              |
| **Security**                          | Fine-grained security controls (rule-based)                                                                                                      | In Progress          |
|                                       | LLM-based security controls                                                                                                                        | In Progress          |


_Status:_ **In Progress** — actively being worked on; **Planned** — queued or under design, also welcome contributions; **Seeking Contributors** — we strongly encourage community contributions.

## Install from source

```bash
git clone https://github.com/agentscope-ai/Orchestrator.git
cd Orchestrator

# Build console frontend first (required for web UI)
cd console && npm ci && npm run build
cd ..

# Copy console build output to package directory
mkdir -p src/qwenpaw/console
cp -R console/dist/. src/qwenpaw/console/

# Install Python package
pip install -e .
```

- **Dev** (tests, formatting): `pip install -e ".[dev,full]"`
- **Then**: Run `qwenpaw init --defaults`, then `qwenpaw app`.

> **Note for updates:** When updating to a new major version after `git pull`, please also rebuild the frontend, reinstall the package (`pip install -e .`), restart `qwenpaw app`, and clear your browser cache with `Ctrl+Shift+R` (or `Cmd+Shift+R` on macOS).

---

## Contributing

Orchestrator evolves through open collaboration, and we welcome all forms of contribution! Check the [Roadmap](#roadmap) above (especially items marked **Seeking Contributors**) to find areas that interest you, and read [CONTRIBUTING](https://github.com/agentscope-ai/Orchestrator/blob/main/CONTRIBUTING.md) to get started. We particularly welcome:

- **Horizontal expansion** — new channels, model providers, skills, MCPs.
- **Existing feature extension & refinement** — display and interaction improvements, download hints, Windows path compatibility, etc.

Join [GitHub Discussions](https://github.com/agentscope-ai/Orchestrator/discussions) to discuss ideas or pick up tasks.

---

## Why Orchestrator?

Orchestrator stands for Qwen Personal Agent Workstation, and also embodies the wisdom of Qwen and the warmth of a Paw.
We hope it is not a cold tool, but an intelligent and warm "little paw" always ready to help—a most intuitive partner in your digital life.

---

## Built by

[AgentScope team](https://github.com/agentscope-ai) · [AgentScope](https://github.com/agentscope-ai/agentscope) · [AgentScope Runtime](https://github.com/agentscope-ai/agentscope-runtime) · [ReMe](https://github.com/agentscope-ai/ReMe)

---

## Contact us

| [Discord](https://discord.gg/eYMpfnkG8h)                     | [X (Twitter)](https://x.com/agentscope_ai)                   | [DingTalk](https://qr.dingtalk.com/action/joingroup?code=v1,k1,OmDlBXpjW+I2vWjKDsjvI9dhcXjGZi3bQiojOq3dlDw=&_dt_no_comment=1&origin=11) | [RedNote](https://www.xiaohongshu.com/user/profile/691c18db0000000037032be9) |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [<img src="https://gw.alicdn.com/imgextra/i1/O1CN01hhD1mu1Dd3BWVUvxN_!!6000000000238-2-tps-400-400.png" width="80" height="80" alt="Discord">](https://discord.gg/eYMpfnkG8h) | [<img src="https://img.shields.io/badge/X-black.svg?logo=x&logoColor=white" width="80" height="80" alt="X">](https://x.com/agentscope_ai) | [<img src="https://img.alicdn.com/imgextra/i2/O1CN01vCWI8a1skHtLGXEMQ_!!6000000005804-2-tps-458-460.png" width="80" height="80" alt="DingTalk">](https://qr.dingtalk.com/action/joingroup?code=v1,k1,OmDlBXpjW+I2vWjKDsjvI9dhcXjGZi3bQiojOq3dlDw=&_dt_no_comment=1&origin=11) | [<img src="https://img.alicdn.com/imgextra/i3/O1CN016BoEPS1l33CE9mHb9_!!6000000004762-0-tps-160-160.jpg" width="80" height="80" alt="RedNote">](https://www.xiaohongshu.com/user/profile/691c18db0000000037032be9) |

---

## Telemetry

Orchestrator collects **anonymous** usage data during `qwenpaw init` to help us understand our user base and prioritize improvements. Data is sent **once per version** — when you upgrade Orchestrator, telemetry is re-collected so we can track version adoption.

**What we collect:**

- Orchestrator version (e.g., 0.0.7)
- Install method (pip, Docker, or desktop app)
- OS and version (e.g., macOS 14.0, Ubuntu 22.04)
- Python version (e.g., 3.13)
- CPU architecture (e.g., x86_64, arm64)
- GPU availability (yes/no)

**What we do NOT collect:** No personal data, no files, no credentials, no IP addresses, no identifiable information.

When running `qwenpaw init` interactively, you will be asked whether to opt in. If you choose `--defaults`, telemetry is accepted automatically. The prompt appears once per version and never affects Orchestrator's functionality.

---

## License

Orchestrator is released under the [Apache License 2.0](LICENSE).

---

## Contributors

All thanks to our contributors:

<a href="https://github.com/agentscope-ai/Orchestrator/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=agentscope-ai/Orchestrator" alt="Contributors" />
</a>
