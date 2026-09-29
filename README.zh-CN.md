# 🔬 AI Research MCP Servers

> 面向 **AI 科研与工程** 的 Model Context Protocol (MCP) Server 精选清单。

[🇨🇳 中文](#-ai-research-mcp-servers) · [🇺🇸 English](./README.md)

[![Curated](https://img.shields.io/badge/清单-精选-blue)](./CATALOG.md)
[![MCP](https://img.shields.io/badge/MCP-Model%20Context%20Protocol-green)](https://modelcontextprotocol.io/)
[![Servers](https://img.shields.io/badge/收录-27-purple)](./CATALOG.md)

本仓库收录能帮助 AI 研究者与工程师完成如下链路的 MCP Server：

**📚 文献 → 🤗 模型与数据集 → 💻 算力 → 🧪 实验 → 📊 评测 → 🚀 部署**

我们**不追求收录 GitHub 上所有 MCP**，只保留满足以下条件的项目：

* ⭐ 对真实的 AI 科研流程确实有用
* 📖 容易理解
* 🚀 容易上手
* 🧩 容易接入已有的 AI Agent
* 🔧 维护活跃，或来自可信团队
* 🔐 权限与安全边界合理

---

## 🗺️ 下一步去哪

| 我想...                    | 前往                                                     |
| -------------------------- | -------------------------------------------------------- |
| 浏览全部推荐 MCP           | **[CATALOG.md](./CATALOG.md)**（完整表格 + 目录）         |
| 看详细介绍                 | **[servers/](./servers/)**（每个分类一个文件）            |
| 提交新的 MCP               | **[CONTRIBUTING.md](./CONTRIBUTING.md)**                 |
| 了解权限与风险             | **[SECURITY.md](./SECURITY.md)**                         |
| 使用结构化数据             | **[data/servers.yaml](./data/servers.yaml)**              |

---

## ⚡ 快速开始

刚接触 MCP？先用这五个，其它等真的需要时再加。

| MCP                       | 能力                              | 为什么先装它                       |
| ------------------------- | --------------------------------- | ---------------------------------- |
| 🤗 **Hugging Face MCP**   | 模型、数据集、论文、Spaces         | AI/ML 资源的最佳入口               |
| 📚 **arXiv MCP**          | 检索与读取论文                     | 文献调研必备                       |
| 📓 **Jupyter MCP**        | 执行 Python / Notebook             | 真正的科学计算能力                 |
| 🧪 **W&B MCP**            | 实验与指标                         | 分析训练任务                       |
| 🔬 **MLflow MCP**         | 实验 / 模型 / Trace                | 开源 MLOps                         |

### 1. 把 Server 加到你的 MCP 客户端

大多数 MCP 客户端读取一份 JSON 配置：远程服务用 `url`，本地服务用 `command`：

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

> 请始终从项目官方文档复制确切配置 —— 传输方式与包名会随版本变化。

### 2. 推荐起步架构

```text
                    AI Research Agent
                           │
          ┌────────────────┼────────────────┐
          │                │                │
          ▼                ▼                ▼
         文献             模型              代码
          │                │                │
       arXiv/S2             HF            GitHub
          │                │                │
          └────────────────┼────────────────┘
                           │
                           ▼
                     Jupyter / Colab
                           │
                           ▼
                      训练 / 分析
                           │
                 ┌─────────┴─────────┐
                 ▼                   ▼
                W&B                MLflow
                 │                   │
                 └─────────┬─────────┘
                           ▼
                      评测 / 报告
```

---

## 🏆 精选推荐

这里只放精选，完整 27 个见 [CATALOG.md](./CATALOG.md)。

| 分类              | 推荐项目                                                                           | 一句话说明                              |
| ----------------- | ---------------------------------------------------------------------------------- | --------------------------------------- |
| 📚 文献           | [arXiv MCP](./servers/literature.md#-arxiv-mcp)                                    | 检索与获取研究论文                      |
| 📚 文献           | [Semantic Scholar MCP](./servers/literature.md#-semantic-scholar-mcp)              | 论文检索 + 引用关系发现                 |
| 🤗 模型与数据集   | [Hugging Face MCP](./servers/models-datasets.md#-hugging-face-mcp)                 | 模型、数据集、论文、Spaces、文档        |
| 🧠 模型与数据集   | [Replicate MCP](./servers/models-datasets.md#-replicate-mcp)                       | 通过托管 API 直接跑模型                 |
| 🧪 实验           | [Weights & Biases MCP](./servers/experiments.md#-weights--biases-mcp)              | 实验、指标、Artifact、模型仓库          |
| 🔬 实验           | [MLflow MCP](./servers/experiments.md#-mlflow-mcp)                                 | 开源实验与模型管理                      |
| 📊 评测           | [LangSmith MCP](./servers/evaluation.md#-langsmith-mcp)                            | LLM/Agent Trace、数据集、评测           |
| 🚀 部署           | [HF Inference Endpoints MCP](./servers/deployment.md#-hf-inference-endpoints-mcp)  | 创建、扩缩容与测试推理端点              |
| 🤖 基础设施       | [Jupyter MCP](./servers/infrastructure.md#-jupyter-mcp)                            | 真正能跑科学的 Python / Notebook 环境   |
| 📚 文献           | [Exa MCP](./servers/literature.md#-exa-mcp)                                        | 语义化网络与论文检索                    |
| 🤖 基础设施       | [Google Colab MCP](./servers/infrastructure.md#-google-colab-mcp)                  | 带 GPU 的云端 Notebook                  |
| 🤖 基础设施       | [Filesystem MCP](./servers/infrastructure.md#-filesystem-mcp)                      | 在授权目录内读写文件                    |
| 🤖 基础设施       | [Context7 MCP](./servers/infrastructure.md#-context7-mcp)                          | 版本匹配的库文档                        |

---

## 📁 仓库结构

```text
ai-research-mcp/
├── README.md                 # 项目首页（英文）
├── README.zh-CN.md           # 项目首页（中文，本文件）
├── CATALOG.md                # 完整 MCP 推荐表（带目录）⭐
├── CONTRIBUTING.md           # 如何提交新的 MCP
├── SECURITY.md               # 权限与安全说明
├── LICENSE
│
├── data/
│   └── servers.yaml          # 结构化数据（唯一数据源）
│
└── servers/
    ├── literature.md         # 文献科研
    ├── models-datasets.md    # 模型 / 数据集
    ├── experiments.md        # 实验管理
    ├── evaluation.md         # 评测与可观测
    ├── deployment.md         # 推理 / 部署
    └── infrastructure.md     # Agent / 算力 / DevOps
```

---

## 🧭 如何选择

不要一次装完，按你的工作流挑选：

| 你的角色                  | 推荐组合                                                     |
| ------------------------- | ------------------------------------------------------------ |
| 🧑‍🎓 AI 研究者              | arXiv + Semantic Scholar + Hugging Face + Jupyter             |
| 🧪 深度学习研究者          | Hugging Face + Jupyter/Colab + W&B                            |
| 🤖 LLM / Agent 研究者      | Hugging Face + Jupyter + LangSmith + W&B Weave                |
| 🚀 ML 工程师               | Hugging Face + MLflow + GitHub + HF Inference Endpoints       |
| 🔬 自主科研 Agent          | 文献 + HF + Jupyter/Colab + W&B/MLflow + 评测                 |

完整速查表见 [CATALOG.md → Quick Picker](./CATALOG.md#quick-picker)。

---

## ⭐ 推荐等级

| 标签                    | 含义                                     |
| ----------------------- | ---------------------------------------- |
| 🏆 **Recommended**      | 好用，且对大多数研究者有价值             |
| ⭐ **Worth Trying**     | 有用，但更偏向特定场景                   |
| 🧪 **Experimental**     | 有意思，但还不够成熟                     |
| 🛠️ **Advanced**         | 需要基础设施或较复杂的配置               |
| ⚠️ **Use with Care**    | 权限敏感，或包含可能造成破坏的操作       |

项目**不会**因为 GitHub star 多就获得更高等级。

---

## 🔐 一分钟安全须知

MCP Server 可能读取文件、执行代码、调用云 API 甚至花钱。安装前先问：

```text
它能 READ 什么？       它能 WRITE 什么？
它能执行代码吗？       它能访问我的文件系统吗？
它能访问云资源吗？     它会花钱吗？     它能删除资源吗？
```

建议的权限升级顺序：**只读 → 实验 → 人工确认 → 写入/部署**。

完整说明见 [SECURITY.md](./SECURITY.md)。

---

## 🤝 参与贡献

欢迎提交。新条目必须与 AI 科研相关、公开可访问、有文档、可安装、在维护，并且如实说明所需权限。

请从 [CONTRIBUTING.md](./CONTRIBUTING.md) 开始。

---

## 📌 免责声明

这是一份**精选清单**，不是官方 MCP 排名。项目状态、API、价格与维护活跃度都会随时间变化 —— 在研究或生产环境部署 MCP Server 前，请务必查阅官方文档。

---

## ⭐ 给仓库点个星

如果这份清单帮你搭建了更好的 AI 科研工作流，欢迎点个 ⭐。纠错与投稿同样欢迎。

许可证：[MIT](./LICENSE)。
