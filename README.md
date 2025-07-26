# 🚀 goose-omniagent-core

**Supercharging [Goose](https://github.com/block/goose) from within: Modular, Memory-Augmented, and Multi-Tool Native Agents**

[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Python Version](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![Goose Integration](https://img.shields.io/badge/Goose-Integration-blue.svg)](https://github.com/block/goose)
[![Goose Stars](https://img.shields.io/badge/Goose-17.5k%20stars-brightgreen.svg)](https://github.com/block/goose)

> **This project is a core extension to Goose, designed to evolve Goose’s native capabilities not just as a plugin, but as a fundamental upgrade to its memory, event, and tool orchestration systems.**

---

## 🦢 Goose Grant Alignment

This project is being developed as a proposal for the [Goose Grant program](https://block.github.io/goose/grants/), with the goal of:

- **Evolving Goose’s core architecture** to natively support multi-tier memory, event streaming, and advanced tool orchestration.
- **Empowering Goose users and developers** with modular, extensible, and production-ready agentic infrastructure.
- **Demonstrating open-source-first values** and cross-framework collaboration, in line with Goose’s mission of openness, modularity, and user empowerment.

---

## 📚 Table of Contents

- [Vision & Value](#-vision--value)
- [Core Features](#-core-features)
- [Quick Start](#-quick-start)
- [Project Milestones](#-project-milestones)
- [Technical Architecture](#-technical-architecture)
- [Impact](#-impact)
- [Contributing](#-contributing)
- [Success Criteria](#-success-criteria)
- [Team & Community](#-team--community)
- [License](#-license)
- [Contact & Support](#-contact--support)

**goose-omniagent-core** integrates the full power of **OmniAgent** and **MCPOmni Connect** into the **[Goose framework](https://github.com/block/goose)**, transforming it into a memory-augmented, event-driven agent platform with advanced tool orchestration capabilities.

## 🎯 Vision & Value

### Goal
Empower the [Goose ecosystem](https://github.com/block/goose) by integrating the full capabilities of OmniAgent and MCPOmni Connect—enabling Goose users to create, orchestrate, and extend modular agents equipped with advanced memory, tool orchestration, and event-driven architecture.

### Why
- **Enhance Goose's 17.5k+ star ecosystem** with advanced memory and event capabilities
- **Showcase seamless interoperability** between Rust-based Goose and Python-based OmniAgent
- **Bring powerful African-built infrastructure (OmniAgent)** to a global developer audience
- **Extend Goose's MCP server integration** with advanced memory management and event streaming

### OmniAgent introduces unique capabilities to Goose:
- **XML-based reasoning logic** with strict tool formatting
- **Concurrent multi-tool execution** via MCP servers (complementing Goose's existing MCP support)
- **Multi-database memory support** (Redis, All SQL databases)
- **Event streaming and task coordination**
- **Real-time orchestration for multi-agent systems**
- **Advanced memory management** (working, episodic, long-term memory)

This integration will turn Goose into a launchpad for real-world, autonomous systems powered by OmniAgent.

## ✨ Core Features

### 🧠 Advanced Memory Management
- **Multi-tier memory system**: Working, episodic, and long-term memory
- **Vector database integration** with semantic search (Qdrant)
- **Flexible database support**: Redis, PostgreSQL, SQLite, MySQL
- **Intelligent memory router** with token budget management
- **Memory-aware agents** that learn from past interactions
- **Cross-session memory persistence** for continuous learning

### 🔄 Event-Driven Architecture
- **Real-time event streaming** with Redis Streams, InMemory
- **Comprehensive event types**: User messages, tool calls, errors, final answers
- **Pluggable event backends**: In-memory, Redis, SQL
- **Event-driven memory processing** and background tasks
- **Real-time monitoring and analytics**
- **Event replay and debugging capabilities**

### 🛠️ Universal Tool Orchestration
- **Enhanced MCP server integration**: Extends Goose's existing MCP capabilities
- **Local Python tool support** alongside MCP tools
- **Cross-server tool coordination** and parallel execution
- **Automatic tool discovery** and intelligent routing
- **Tool composition and chaining**
- **Tool performance monitoring and optimization**

### 🤖 Agent Intelligence
- **XML-based reasoning** with ReAct methodology
- **Mandatory memory checking** for every interaction
- **Multi-modal LLM support**: 100+ models via LiteLLM
- **Three agent modes**: ReAct, Orchestrator, and Interactive
- **Self-improving prompts** and adaptive behavior
- **Context-aware decision making**

### 🏗️ Production Infrastructure
- **Session management** with persistent chat IDs
- **Usage limits and API monitoring**
- **OAuth authentication** and secure communication
- **Robust error handling** and graceful degradation
- **Scalable architecture** for enterprise deployment
- **Performance metrics and health monitoring**

## 🚀 Quick Start

### Prerequisites
- [Goose](https://github.com/block/goose) (latest version, with support for core extensions)
- Python 3.10+
- [uv](https://github.com/astral-sh/uv) package manager (required)

### Installation

```bash
# Clone the repository
git clone https://github.com/Abiorh001/goose-omniagent-core.git
cd goose-omniagent-core

# Install all dependencies using uv (pip/requirements.txt not supported)
uv sync
```

### Basic Usage

```python
from mcpomni_connect.omni_agent import OmniAgent
from mcpomni_connect.memory_store.memory_router import MemoryRouter

# Initialize memory store
memory_store = MemoryRouter(memory_store_type="redis")  # or "postgresql", "sqlite", "mysql"

# Create OmniAgent
agent = OmniAgent(
    name="my_agent",
    system_instruction="You are a helpful assistant that can answer questions and help with tasks.",
    model_config={
        "provider": "openai",
        "model": "gpt-4o",
        "max_context_length": 50000,
    },
    mcp_tools=[
        {
            "name": "filesystem",
            "transport_type": "stdio",
            "command": "npx",
            "args": ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/directory"],
        }
    ],
    memory_store=memory_store,
)

# Run the agent
result = await agent.run("Analyze my project files and create a summary report")
print(f"Response: {result['response']}")
print(f"Session ID: {result['session_id']}")
```

### Session Management

```python
# Use session ID for conversation continuity
session_id = "user_123_conversation"
result1 = await agent.run("Hello! My name is Alice.", session_id)
result2 = await agent.run("What did I tell you my name was?", session_id)

# Get conversation history
history = await agent.get_session_history(session_id)

# Stream events in real-time
async for event in agent.stream_events(session_id):
    print(f"Event: {event.type} - {event.payload}")
```

### Current Status

**This is how OmniAgent works today** - a powerful, memory-augmented agent framework with advanced tool orchestration capabilities. The goal of **goose-omniagent-core** is to integrate these capabilities directly into the [Goose framework](https://github.com/block/goose) as a core extension, evolving Goose's native agent capabilities.

**Future Integration**: Once the Goose Grant is approved, this will become a native extension to Goose, allowing Goose users to leverage OmniAgent's memory, event streaming, and advanced tool orchestration directly within the Goose ecosystem.

## 🛠️ Integration Approach

- **goose-omniagent-core** is designed to be integrated directly into Goose’s codebase or as a first-class extension, not as a standalone plugin.
- All features (memory, events, tool orchestration) are exposed natively to Goose agents and workflows.
- The project will work closely with the Goose community to ensure seamless, maintainable, and future-proof integration.

## 📋 Project Milestones

### 🎯 Milestone 1: Plugin MVP (Month 1-2)
**Deliverable**: Goose plugin that registers OmniAgent as a tool or agent backend

**Features**:
- ✅ Goose agent sends user queries to OmniAgent via API
- ✅ Receives final answers, source traces, and tool metadata
- ✅ Basic memory integration
- ✅ Simple tool orchestration
- ✅ Integration with Goose's existing MCP server support

### 🔧 Milestone 2: Adapter Layer (Month 2-4)
**Deliverable**: Adapter to translate Goose JSON tool calls into XML-based OmniAgent prompts

**Features**:
- 🔄 Memory, event, and user session translation
- 🔄 Reusable adapter functions and response validation
- 🔄 Cross-framework data format conversion (Rust ↔ Python)
- 🔄 Error handling and fallback mechanisms
- 🔄 Performance optimization for Rust-Python bridge

### 🧠 Milestone 3: Memory & Event Streaming (Month 4-6)
**Deliverable**: Goose agents can leverage multi-database memory and stream events

**Features**:
- 📅 Episodic + vector memory integration
- 📅 Real-time logs and event chaining
- 📅 Multi-database support (Redis, PostgreSQL, SQLite, MySQL)
- 📅 Memory analytics and insights
- 📅 Cross-platform memory synchronization

### 🤖 Milestone 4: Multi-Modal & Self-Improving Agents (Month 6-9)
**Deliverable**: Support for multi-modal inputs and self-evolving agents

**Features**:
- 🎥 Camera, voice, or sketch input support
- 🔄 Prompt mutation and self-editing tools
- 🧠 Adaptive learning and behavior modification
- 📊 Performance analytics and optimization
- 🔄 Integration with Goose's multi-model configuration

### 🌍 Milestone 5: Real-World Use Cases & Community SDK (Month 9-12)
**Deliverable**: End-to-end examples and comprehensive SDK

**Features**:
- 🏠 Home automation examples
- 💰 Finance and trading agents
- 🔍 Search and research workflows
- 📚 Complete SDK and documentation
- 🎓 Developer onboarding and tutorials
- 🔧 Integration examples for Goose's desktop app and CLI

## 🏗️ Technical Architecture

### Bridge Architecture
```
Goose Framework (Rust)
    │
    ▼
goose-omniagent-core Bridge (Python)
    │
    ▼
OmniAgent Core
    ├── Memory Router (Redis/PostgreSQL/SQLite/MySQL)
    ├── Tool Orchestrator (MCP + Local Tools)
    ├── Event System (Redis Streams/InMemory)
    ├── Vector Database (Qdrant)
    └── LLM Integration (LiteLLM)
```

### Memory Flow
```
Goose User Input → Memory Check → Tool Selection → Execution → Memory Storage → Response
    │                    │              │              │              │              │
    ▼                    ▼              ▼              ▼              ▼              ▼
Goose Session → Episodic Memory → Tool Registry → MCP/Local → Vector Store → Final Answer
```

### Integration Points
- **MCP Server Extension**: Enhances Goose's existing MCP capabilities
- **Memory Bridge**: Provides persistent memory across Goose sessions
- **Event Streaming**: Real-time monitoring and debugging
- **Tool Orchestration**: Advanced tool coordination beyond basic MCP

## 🎯 Impact

### For Goose Framework
- **Enhanced Agent Capabilities**: Memory-aware agents that learn from past interactions
- **Advanced Tool Ecosystem**: Extends existing MCP support with advanced orchestration
- **Production-Ready Memory**: Multi-database persistence with vector search
- **Event-Driven Architecture**: Real-time monitoring and extensible event system
- **Universal Model Support**: Single interface for 100+ AI models
- **Cross-Platform Compatibility**: Works with both Goose CLI and desktop app

### For Goose Developers
- **Simplified Agent Creation**: XML-based reasoning with automatic memory management
- **Rich Tool Integration**: Seamless MCP server and local tool orchestration
- **Advanced Memory Features**: Multi-tier memory with semantic search
- **Event Monitoring**: Comprehensive event streaming for debugging and analytics
- **Extensible Architecture**: Plugin-based system for custom extensions
- **Rust-Python Bridge**: Efficient communication between frameworks

### For Goose Users
- **Memory-Aware Interactions**: Agents that remember past conversations and preferences
- **Intelligent Tool Usage**: Automatic tool selection and orchestration
- **Multi-Modal Support**: Access to diverse AI models and capabilities
- **Reliable Performance**: Production-ready infrastructure with error handling
- **Rich Ecosystem**: Access to 100+ MCP servers and tools
- **Seamless Experience**: Works with existing Goose workflows

## 🤝 Contributing

We welcome contributions! This project is designed to be community-driven and extensible.

### Development Setup

```bash
# Clone and setup
git clone https://github.com/Abiorh001/goose-omniagent-core.git
cd goose-omniagent-core

# Install development dependencies
uv sync

# Run tests
pytest tests/

# Run linting
flake8 src/
black src/
```

### Contributing Guidelines

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b feature/amazing-feature`
3. **Make your changes** and add tests
4. **Run the test suite**: `pytest tests/`
5. **Submit a pull request**

### Integration Testing
```bash
# Test with Goose
goose --enable-omniagent-core --test-mode

# Run integration tests
pytest tests/integration/test_goose_integration.py
```

## 🏆 Success Criteria

- ✅ **Goose agents can call OmniAgent** and receive final answers + source data
- ✅ **OmniAgent tools, memory, and events** are accessible via Goose
- ✅ **Demonstrated use cases** in automation, search, and finance
- ✅ **SDK and docs** adopted or forked by external developers
- ✅ **Community adoption** and active contributions
- ✅ **Seamless integration** with Goose's existing MCP and multi-model capabilities

## 👥 Team & Community

### Lead Developer
**Abiola Adeshina** — Creator of MCPOmni Connect and OmniAgent.

### Open Source Commitment
- **MIT License**: Code, documentation, and SDK publicly maintained
- **Community Driven**: Open to partnering with [Goose maintainers](https://github.com/block/goose) and plugin authors
- **Transparent Development**: Public roadmap and regular updates

### Collaboration
We're open to partnering with:
- [Goose maintainers](https://github.com/block/goose) and core team
- Plugin authors and ecosystem developers
- Adjacent agentic AI efforts
- Research institutions and academic partners

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📞 Contact & Support

- **GitHub Issues**: [Report a bug](https://github.com/Abiorh001/goose-omniagent-core/issues)
- **Discussions**: [Join the conversation](https://github.com/Abiorh001/goose-omniagent-core/discussions)
- **Goose Community**: [Goose Discord](https://discord.gg/goose) and [GitHub Discussions](https://github.com/block/goose/discussions)
- **Email**: abiolaadedayo1993@gmail.com

---

<p align="center">Built with ❤️ by the goose-omniagent-core Team</p>

<p align="center">
  <strong>Powered by African-built AI infrastructure — designed for the global open-source community.</strong>
</p>

<p align="center">
  <em>Enhancing the <a href="https://github.com/block/goose">Goose ecosystem</a> with advanced memory, event streaming, and tool orchestration capabilities.</em>
</p> 
