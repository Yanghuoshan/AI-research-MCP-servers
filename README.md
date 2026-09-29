# 🔬 AI Research MCP Servers

> A curated list of **Model Context Protocol (MCP) servers for AI research and engineering**.

**🇺🇸 English** · [🇨🇳 中文版](./README.zh-CN.md)

[![Curated](https://img.shields.io/badge/list-curated-blue)](./CATALOG.md)
[![MCP](https://img.shields.io/badge/MCP-Model%20Context%20Protocol-green)](https://modelcontextprotocol.io/)
[![Servers](https://img.shields.io/badge/servers-27-purple)](./CATALOG.md)

A practical collection of MCP servers that help AI researchers and engineers with:

**📚 Literature → 🤗 Models & Datasets → 💻 Computing → 🧪 Experiments → 📊 Evaluation → 🚀 Deployment**

This repository is **not** meant to list every MCP server on GitHub. We only keep servers that are:

* ⭐ Useful for real AI research workflows
* 📖 Easy to understand
* 🚀 Easy to get started with
* 🧩 Easy to integrate with existing AI agents
* 🔧 Actively maintained or backed by a credible project
* 🔐 Reasonable in terms of permissions and security

---

## 🗺️ Where to go next

| I want to...                          | Go to                                                            |
| ------------------------------------- | ---------------------------------------------------------------- |
| Browse every recommended MCP         | **[CATALOG.md](./CATALOG.md)** (full table + table of contents)   |
| Read detailed reviews                 | **[servers/](./servers/)** (one file per category)                |
| Submit a new MCP                      | **[CONTRIBUTING.md](./CONTRIBUTING.md)**                          |
| Understand permission risks           | **[SECURITY.md](./SECURITY.md)**                                  |
| Use the machine-readable dataset      | **[data/servers.yaml](./data/servers.yaml)**                      |

---

## ⚡ Quick Start

New to MCP? Start with these five, then add more only when you actually need them.

| MCP                         | What it does                      | Why start here                       |
| --------------------------- | --------------------------------- | ------------------------------------ |
| 🤗 **Hugging Face MCP**     | Models, datasets, papers, Spaces  | Best entry point for AI/ML resources |
| 📚 **arXiv MCP**            | Search and read papers            | Essential for literature research    |
| 📓 **Jupyter MCP**          | Execute Python / notebooks        | Actual scientific computing          |
| 🧪 **W&B MCP**              | Experiments and metrics           | Analyze training runs                |
| 🔬 **MLflow MCP**           | Experiments / models / traces     | Open-source MLOps                    |

### 1. Add a server to your MCP client

Most MCP clients read a JSON config. Remote servers use `url`, local servers use `command`:

```json
{
  "mcpServers": {
    "huggingface": {
      "url": "https://huggingface.co/mcp?login"
    },
    "my-local-mcp": {
      "command": "uvx",
      "args": ["<mcp-package-name>"]
    }
  }
}
```

> Always copy the exact config from the project's official documentation — transports and package names change.

### 2. Recommended starter stack

```text
                    AI Research Agent
                           │
          ┌────────────────┼────────────────┐
          │                │                │
          ▼                ▼                ▼
       Literature        Models            Code
          │                │                │
       arXiv/S2             HF            GitHub
          │                │                │
          └────────────────┼────────────────┘
                           │
                           ▼
                     Jupyter / Colab
                           │
                           ▼
                    Training / Analysis
                           │
                 ┌─────────┴─────────┐
                 ▼                   ▼
                W&B                MLflow
                 │                   │
                 └─────────┬─────────┘
                           ▼
                    Evaluation / Report
```

---

## 🏆 Featured Picks

A short list, not an exhaustive one. See [CATALOG.md](./CATALOG.md) for all 27.

| Category                | Pick                                                                       | One-liner                                       |
| ----------------------- | -------------------------------------------------------------------------- | ----------------------------------------------- |
| 📚 Literature           | [arXiv MCP](./servers/literature.md#-arxiv-mcp)                            | Search and retrieve research papers             |
| 📚 Literature           | [Semantic Scholar MCP](./servers/literature.md#-semantic-scholar-mcp)      | Papers + citation graph discovery               |
| 🤗 Models & Datasets    | [Hugging Face MCP](./servers/models-datasets.md#-hugging-face-mcp)         | Models, datasets, papers, Spaces, docs          |
| 🧠 Models & Datasets    | [Replicate MCP](./servers/models-datasets.md#-replicate-mcp)               | Run models through a hosted API                 |
| 🧪 Experiments          | [Weights & Biases MCP](./servers/experiments.md#-weights--biases-mcp)      | Runs, metrics, artifacts, model registry        |
| 🔬 Experiments          | [MLflow MCP](./servers/experiments.md#-mlflow-mcp)                         | Open-source experiment & model management       |
| 📊 Evaluation           | [LangSmith MCP](./servers/evaluation.md#-langsmith-mcp)                    | LLM/agent traces, datasets, evaluation          |
| 🚀 Deployment           | [HF Inference Endpoints MCP](./servers/deployment.md#-hf-inference-endpoints-mcp) | Create, scale and test inference endpoints |
| 🤖 Infrastructure       | [Jupyter MCP](./servers/infrastructure.md#-jupyter-mcp)                    | Python / notebook execution for real science    |
| 📚 Literature           | [Exa MCP](./servers/literature.md#-exa-mcp)                                | Semantic web + paper search                     |
| 🤖 Infrastructure       | [Google Colab MCP](./servers/infrastructure.md#-google-colab-mcp)          | Cloud notebooks with GPU access                 |
| 🤖 Infrastructure       | [Filesystem MCP](./servers/infrastructure.md#-filesystem-mcp)              | Read/write files in an allowed directory        |
| 🤖 Infrastructure       | [Context7 MCP](./servers/infrastructure.md#-context7-mcp)                  | Version-specific library documentation          |

---

## 📁 Repository Layout

```text
ai-research-mcp/
├── README.md                 # Project home (this file)
├── README.zh-CN.md           # 中文版首页
├── CATALOG.md                # Full MCP catalog with TOC ⭐
├── CONTRIBUTING.md           # How to submit a new MCP
├── SECURITY.md               # Permissions & safety notes
├── LICENSE
│
├── data/
│   └── servers.yaml          # Structured data (source of truth)
│
└── servers/
    ├── literature.md         # Literature & research
    ├── models-datasets.md    # Models & datasets
    ├── experiments.md        # Experiment management
    ├── evaluation.md         # Evaluation & observability
    ├── deployment.md         # Inference & deployment
    └── infrastructure.md     # Agent / compute / DevOps
```

---

## 🧭 How to Choose

Don't install everything. Pick by workflow:

| You are...                       | Stack                                          |
| -------------------------------- | ---------------------------------------------- |
| 🧑‍🎓 AI researcher                | arXiv + Semantic Scholar + Hugging Face + Jupyter |
| 🧪 Deep learning researcher      | Hugging Face + Jupyter/Colab + W&B             |
| 🤖 LLM / agent researcher        | Hugging Face + Jupyter + LangSmith + W&B Weave |
| 🚀 ML engineer                   | Hugging Face + MLflow + GitHub + HF Inference Endpoints |
| 🔬 Autonomous research agent     | Literature + HF + Jupyter/Colab + W&B/MLflow + Evaluation |

Full picker table: [CATALOG.md → Quick Picker](./CATALOG.md#quick-picker).

---

## ⭐ Recommendation Levels

| Label                | Meaning                                                     |
| -------------------- | ----------------------------------------------------------- |
| 🏆 **Recommended**   | Easy to use and valuable for most researchers               |
| ⭐ **Worth Trying**  | Useful, but more specialized                                |
| 🧪 **Experimental**  | Interesting but still immature                              |
| 🛠️ **Advanced**      | Requires infrastructure or non-trivial configuration        |
| ⚠️ **Use with Care** | Sensitive permissions or potentially destructive operations |

A project does **not** get a higher rank just because it has more GitHub stars.

---

## 🔐 Security in One Minute

MCP servers can read files, execute code, call cloud APIs and spend money. Before installing one, ask:

```text
What can it READ?        What can it WRITE?
Can it execute code?     Can it touch my filesystem?
Can it access cloud resources?  Can it spend money?  Can it delete resources?
```

Preferred escalation order: **read-only → experiment → human approval → write/deploy**.

Full guidance: [SECURITY.md](./SECURITY.md).

---

## 🤝 Contributing

Contributions are welcome. New entries must be relevant to AI research, publicly accessible, documented, installable, maintained, and honest about permissions.

Start here: [CONTRIBUTING.md](./CONTRIBUTING.md).

---

## 📌 Disclaimer

This is a **curated list**, not an official MCP ranking. Project status, APIs, pricing and maintenance activity change over time — always check the official documentation before deploying an MCP server in a production or research environment.

---

## ⭐ Star this repository

If this list helps you build a better AI research workflow, consider giving it a ⭐. Corrections and contributions are welcome.

Licensed under [MIT](./LICENSE).
