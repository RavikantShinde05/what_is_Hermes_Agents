# what_is_Hermes_Agents
This repo is for introduction to a popular AI agent known as Hermes Agent

**Hermes Agent** is an autonomous artificial intelligence platform developed by **Nous Research** that operates independently from local laptops across cloud infrastructures, virtual private servers, and serverless environments. Unlike traditional chatbots or IDE-tethered copilots, the system features a **built-in learning loop** enabling it to autonomously create, refine, and reuse procedural skills while maintaining persistent cross-session memory. Users can interact with the software through more than twenty **messaging platforms** such as Telegram, Discord, and Slack, or via a command-line interface and desktop application. The architecture supports advanced capabilities including **Bot Mode** for specialized multi-agent teams, scheduled automations, voice interactions, and integrations with standard developer tools and model providers. Furthermore, it offers extensive flexibility through **open standard skills** and model context protocol compatibility, making it adaptable for both everyday productivity tasks and complex research workflows.

## Key Concepts & Architecture:

### 1. Closed Learning Loop & Memory System

Hermes Agent's core differentiator is its **closed learning loop**:

* **Persistent Memory**: Uses **SQLite FTS5 full-text search** paired with periodic LLM summarization to maintain long-term memory across chat sessions.
* **Autonomous Skill Creation**: Automatically codifies past experience into procedural skills, which it reuses and refines during execution. Skills adhere to the removed]** open standard and can be shared via the Skills Hub.
* **User Modeling**: Integrates **Honcho dialectic user modeling** to construct an evolving model of user preferences and style over time.
* **Memory Nudges**: Periodically prompts itself to persist key facts and learnings.

#### 2. Runtime Backends & Execution Environments

The agent decouples reasoning from compute by offering ** terminal execution backends**:

* **Compute Environments**: Local host, Docker, SSH, Daytona, Singularity, Modal, and Vercel Sandbox.
* **Serverless Cost Efficiency**: When deployed on serverless platforms such as Daytona or Modal, the execution environment hibernates when idle, maintaining persistent state while minimizing compute costs.

#### 3. Subagent Parallelism &amp; Programmatic Tool Calling

* **Subagent Delegation**: Spawns isolated subagents to execute parallel subtasks.
* **Programmatic Tool Execution**: Uses an `execute_code` mechanism to collapse multi-step tool call pipelines into single inference calls.
* **MCP Integration**: Fully supports the **Model Context Protocol (MCP)**, allowing connection to external MCP servers with tool filtering and safety controls.

#### 4. Multi-Channel Messaging Gateway

Hermes can be deployed across **20+ messaging platforms** through a unified gateway:

* **Supported Channels**: CLI, Telegram, Discord, Slack, WhatsApp, Signal, Matrix, Microsoft Teams, Google Chat, Email, SMS, Home Assistant, and more.
* **Bot Mode**: Allows you to run teams of specialist Bots-each with its own LLM model, memory, skills, automated routines, and group chat handling.

#### 5. Persona, Voice, and Security

* **Personality**: Configured globally using a file.
* **Project Context**: Incorporates local `.md` context files to guide task execution.
* **Voice Support**: Features real-time voice mode across CLI, Telegram, Discord, and Discord VC.
* **Security Layer**: Includes command approval workflows, authorization, and container-level isolation.

---

## Installation &amp; Quickstart

### 1. One-Line Installers

* **Linux / macOS / WSL2**:

```
curl -fsSL https://hermes-agent.nousresearch.com/install.sh | bash
``` [4]

```

* **Windows (PowerShell)**:

```
iex (irm https://hermes-agent.nousresearch.com/install.ps1)
``` [4]

```

#### 2. Initial Setup

The fastest path to get the agent running is:

```
hermes setup --portal
```
This connects Hermes via OAuth to **Nous Portal**, providing model access alongside the **Tool Gateway** (which supplies web search, web browsing/extraction, image generation, and text-to-speech tools out of the box). You can also configure standard LLM providers such as OpenRouter, OpenAI, or any OpenAI-compatible API endpoint.

---

### Typical Usage Patterns for Developers

1. **Remote Cloud Agent**: Run Hermes on a \$5 VPS, Docker container, or serverless backend (Modal/Daytona). Control and monitor its work streams remotely via Telegram or Discord without needing to SSH in .
2. **Specialized Bot Clusters**: Deploy distinct bots in **Bot Mode** into team group chats (e.g., Code Reviewer Bot, SRE Bot).
3. **Machine-Readable Agent Docs**: If you want to feed Hermes documentation into another AI tool or LLM context, Nous Research exposes pre-built files:
   * `/llms.txt`: Curated index (~17 KB) .
   * `/llms-full.txt`: Full concatenated documentation (~1.8 MB).

🤖 Would you like to explore setting up a specific execution backend (such as Docker or Daytona) or configuring Bot Mode for team workflows?
```
