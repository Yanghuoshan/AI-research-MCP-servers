# 📇 MCP Catalog

> The complete, scannable index of **27 MCP servers** in this repository.
> Home: [README.md](./README.md) · [中文首页](./README.zh-CN.md) · Detail pages: [`servers/`](./servers/)

**What this file is:** a *catalog* — compact tables you can skim in 30 seconds.
**What it is not:** a long-form review. Per-server details live in [`servers/*.md`](./servers/).

---

## 📑 Table of Contents

* [1. How to read this catalog](#1-how-to-read-this-catalog)
* [2. Master index (all 27 servers)](#2-master-index-all-27-servers)
* [3. Quick picker: "I want to..."](#3-quick-picker-i-want-to)
* [4. By category](#4-by-category)
  * [4.1 Literature & Research](#41--literature--research) — 6 servers + 1 cross-listed
  * [4.2 Models & Datasets](#42--models--datasets) — 2 servers
  * [4.3 Experiment Management](#43--experiment-management) — 2 servers
  * [4.4 Evaluation & Observability](#44--evaluation--observability) — 3 servers
  * [4.5 Inference & Deployment](#45--inference--deployment) — 2 servers
  * [4.6 Agent / Compute / DevOps](#46--agent--compute--devops) — 12 servers
* [5. Recommendation levels](#5-recommendation-levels)
* [6. Fields & legend](#6-fields--legend)
* [7. Maintenance](#7-maintenance)

---

## 1. How to read this catalog

Each row is one MCP server. Columns are deliberately short so the table stays readable:

| Column       | Meaning                                                          |
| ------------ | ---------------------------------------------------------------- |
| **MCP**      | Link to the detailed entry in `servers/`                          |
| **One-liner**| What it actually does, in one sentence                            |
| **Type**     | `Official` (from the vendor) or `Community`                        |
| **Level**    | Our recommendation label — see [§5](#5-recommendation-levels)      |
| **Setup**    | 🟢 Easy / 🟡 Medium / 🔴 Advanced                                   |
| **Run**      | Remote (hosted URL) / Local (`npx`/`uvx`/`pip`) / Docker           |
| **Risk**     | Main permission concern — see [SECURITY.md](./SECURITY.md)         |
| **Links**    | Official docs / repository *(shown in the category tables, §4)*    |

---

## 2. Master index (all 27 servers)

| #  | Category            | MCP                                                                            | One-liner                                            | Type      | Level            | Setup     | Run              | Risk              |
| -- | ------------------- | ------------------------------------------------------------------------------ | ---------------------------------------------------- | --------- | ---------------- | --------- | ---------------- | ----------------- |
| 1  | 🤗 Models/Datasets  | [🤗 Hugging Face MCP](./servers/models-datasets.md#-hugging-face-mcp)          | Models, datasets, papers, Spaces and docs             | Official  | 🏆 Recommended   | 🟢 Easy   | Remote           | Read + API token  |
| 2  | 🤗 Models/Datasets  | [🧠 Replicate MCP](./servers/models-datasets.md#-replicate-mcp)                 | Run hosted models (image/video/audio/multimodal)      | Official  | ⭐ Worth Trying  | 🟢 Easy   | Remote           | 💸 Spends money   |
| 3  | 📚 Literature       | [📄 arXiv MCP](./servers/literature.md#-arxiv-mcp)                              | Search and retrieve arXiv papers                      | Community | 🏆 Recommended   | 🟢 Easy   | Local            | Read-only         |
| 4  | 📚 Literature       | [🔎 Semantic Scholar MCP](./servers/literature.md#-semantic-scholar-mcp)       | Paper search + citation graph                         | Community | 🏆 Recommended   | 🟢 Easy   | Local            | Read-only         |
| 5  | 📚 Literature       | [🌐 OpenAlex MCP](./servers/literature.md#-openalex-mcp)                        | Large-scale research-landscape analysis               | Community | ⭐ Worth Trying  | 🟢 Easy   | Local            | Read-only         |
| 6  | 📚 Literature       | [🔍 Exa MCP](./servers/literature.md#-exa-mcp)                                  | Semantic web + research-paper search                  | Official  | 🏆 Recommended   | 🟢 Easy   | Remote           | Read + API key    |
| 7  | 📚 Literature       | [🔥 Firecrawl MCP](./servers/literature.md#-firecrawl-mcp)                      | Search, scrape and crawl the web                      | Official  | 🏆 Recommended   | 🟢 Easy   | Remote           | 💸 Spends money   |
| 8  | 📚 Literature       | [🧬 PubMed MCP](./servers/literature.md#-pubmed-mcp)                            | Biomedical literature search                          | Community | ⭐ Worth Trying  | 🟢 Easy   | Local            | Read-only         |
| 9  | 🧪 Experiments      | [📊 Weights & Biases MCP](./servers/experiments.md#-weights--biases-mcp)       | Runs, metrics, artifacts, model registry              | Official  | 🏆 Recommended   | 🟢 Easy   | Local / Remote   | Org data          |
| 10 | 🧪 Experiments      | [🔬 MLflow MCP](./servers/experiments.md#-mlflow-mcp)                           | Experiments, traces, model registry                   | Official  | ⭐ Worth Trying  | 🟡 Medium | Local            | Write-capable     |
| 11 | 📊 Evaluation       | [🔭 LangSmith MCP](./servers/evaluation.md#-langsmith-mcp)                      | LLM/agent traces, datasets, evaluation                | Official  | 🏆 Recommended   | 🟢 Easy   | Local            | Trace data        |
| 12 | 📊 Evaluation       | [📊 W&B Weave](./servers/evaluation.md#-wb-weave)                               | LLM/agent observability and evaluation                | Official  | ⭐ Worth Trying  | 🟢 Easy   | Local / Remote   | Trace data        |
| 13 | 📊 Evaluation       | [🔮 Arize Phoenix MCP](./servers/evaluation.md#-arize-phoenix-mcp)              | Self-hosted LLM/RAG traces and evals                  | Official  | ⭐ Worth Trying  | 🟡 Medium | Local            | Trace data        |
| 14 | 🚀 Deployment       | [☁️ HF Inference Endpoints MCP](./servers/deployment.md#-hf-inference-endpoints-mcp) | Create, scale, test inference endpoints          | Official  | 🛠️ Advanced      | 🟡 Medium | Remote           | 💸 Spends money   |
| 15 | 🚀 Deployment       | [☸️ Kubernetes MCP](./servers/deployment.md#-kubernetes-mcp)                    | Run training/serving jobs on a cluster                | Community | ⚠️ Use with Care | 🔴 Advanced | Local         | ⚠️ Cluster access |
| 16 | 🤖 Infrastructure   | [📁 Filesystem MCP](./servers/infrastructure.md#-filesystem-mcp)                | Read/write files in an allowed directory              | Official  | 🏆 Recommended   | 🟢 Easy   | Local            | ⚠️ Local writes   |
| 17 | 🤖 Infrastructure   | [🌿 Git MCP](./servers/infrastructure.md#-git-mcp)                              | Read, search and manipulate a repo                    | Official  | 🏆 Recommended   | 🟢 Easy   | Local            | ⚠️ Local writes   |
| 18 | 🤖 Infrastructure   | [🐙 GitHub MCP](./servers/infrastructure.md#-github-mcp)                        | Repos, issues, PRs, code search                       | Official  | 🏆 Recommended   | 🟡 Medium | Remote / Docker  | ⚠️ Write-capable  |
| 19 | 🤖 Infrastructure   | [📓 Jupyter MCP](./servers/infrastructure.md#-jupyter-mcp)                      | Python / notebook execution                           | Community | 🏆 Recommended   | 🟡 Medium | Local / Docker   | ⚠️ Code execution |
| 20 | 🤖 Infrastructure   | [☁️ Google Colab MCP](./servers/infrastructure.md#-google-colab-mcp)            | Cloud notebooks with GPU                              | Official  | ⭐ Worth Trying  | 🟢 Easy   | Remote           | ⚠️ Code execution |
| 21 | 🤖 Infrastructure   | [🗄️ SQLite MCP](./servers/infrastructure.md#-sqlite-mcp)                        | Query a local SQLite database                         | Official  | 🏆 Recommended   | 🟢 Easy   | Local            | ⚠️ Local writes   |
| 22 | 🤖 Infrastructure   | [🐘 PostgreSQL MCP](./servers/infrastructure.md#-postgresql-mcp)                | Query and inspect PostgreSQL schemas                  | Official  | ⭐ Worth Trying  | 🟡 Medium | Local            | ⚠️ Arbitrary SQL  |
| 23 | 🤖 Infrastructure   | [🌈 Chroma MCP](./servers/infrastructure.md#-chroma-mcp)                        | Vector store for RAG experiments                      | Official  | ⭐ Worth Trying  | 🟡 Medium | Local            | Write-capable     |
| 24 | 🤖 Infrastructure   | [🐳 Docker MCP Gateway](./servers/infrastructure.md#-docker-mcp-gateway)        | Run MCP servers in containers                         | Official  | ⭐ Worth Trying  | 🟡 Medium | Docker           | ⚠️ Container exec |
| 25 | 🤖 Infrastructure   | [🎭 Playwright MCP](./servers/infrastructure.md#-playwright-mcp)                | Browser automation for the agent                      | Official  | ⭐ Worth Trying  | 🟢 Easy   | Local            | ⚠️ Browser session |
| 26 | 🤖 Infrastructure   | [📚 Context7 MCP](./servers/infrastructure.md#-context7-mcp)                    | Version-specific library documentation                | Official  | 🏆 Recommended   | 🟢 Easy   | Remote           | Read-only         |
| 27 | 🤖 Infrastructure   | [🧩 NVIDIA NeMo Agent Toolkit](./servers/infrastructure.md#-nvidia-nemo-agent-toolkit) | Build and expose agent workflows over MCP       | Official  | 🛠️ Advanced      | 🟡 Medium | Local            | Config-heavy      |

---

## 3. Quick picker: "I want to..."

| I want to...                            | Start with                               |
| --------------------------------------- | ---------------------------------------- |
| Find recent AI papers                   | arXiv                                    |
| Explore citation networks               | Semantic Scholar                         |
| Analyze research trends                 | OpenAlex                                 |
| Search the web / grey literature        | Exa                                      |
| Scrape or crawl a website               | Firecrawl                                |
| Find biomedical papers                  | PubMed                                   |
| Find AI models                          | Hugging Face                             |
| Find datasets                           | Hugging Face                             |
| Find AI demos                           | Hugging Face Spaces                      |
| Run a model quickly                     | Replicate                                |
| Run Python                              | Jupyter                                  |
| Get a GPU notebook                      | Google Colab                             |
| Submit a job to the GPU cluster         | Kubernetes MCP                           |
| Track experiments                       | W&B                                      |
| Manage ML experiments                   | MLflow                                   |
| Query results with SQL                  | SQLite MCP                               |
| Read the shared results database        | PostgreSQL MCP                           |
| Debug LLM agents                        | LangSmith                                |
| Evaluate agents                         | LangSmith / W&B Weave                    |
| Self-host LLM/RAG evaluation            | Arize Phoenix                            |
| Deploy a model                          | HF Inference Endpoints                   |
| Build a retrieval/RAG pipeline          | Chroma MCP                               |
| Let the agent work with my files        | Filesystem MCP                           |
| Inspect repo history                    | Git MCP                                  |
| Work with code & repos                  | GitHub MCP                               |
| Avoid outdated APIs in generated code   | Context7 MCP                             |
| Automate a site that has no API         | Playwright MCP                           |
| Sandbox third-party MCP servers         | Docker MCP Gateway                       |
| Build MCP-enabled agents                | NVIDIA NeMo Agent Toolkit                |

---

## 4. By category

### 4.1 📚 Literature & Research

Detail page: [`servers/literature.md`](./servers/literature.md)

| MCP                                                                      | One-liner                                | Type      | Level           | Setup   | Run    | Links                                                                                              |
| ------------------------------------------------------------------------ | ---------------------------------------- | --------- | --------------- | ------- | ------ | -------------------------------------------------------------------------------------------------- |
| [📄 arXiv MCP](./servers/literature.md#-arxiv-mcp)                        | Search and retrieve research papers      | Community | 🏆 Recommended  | 🟢 Easy | Local  | [GitHub](https://github.com/Tejas242/arxiv-mcp)                                                    |
| [🔎 Semantic Scholar MCP](./servers/literature.md#-semantic-scholar-mcp) | Papers, authors, citations               | Community | 🏆 Recommended  | 🟢 Easy | Local  | [GitHub](https://github.com/yogsoth-ai/semantic-scholar-mcp)                                       |
| [🌐 OpenAlex MCP](./servers/literature.md#-openalex-mcp)                  | Global research landscape analysis       | Community | ⭐ Worth Trying | 🟢 Easy | Local  | [GitHub](https://github.com/oksure/openalex-research-mcp)                                          |
| [🔍 Exa MCP](./servers/literature.md#-exa-mcp)                            | Semantic web + paper search              | Official  | 🏆 Recommended  | 🟢 Easy | Remote | [Docs](https://exa.ai/docs/get-started/exa-mcp) · [GitHub](https://github.com/exa-labs/exa-mcp-server) |
| [🔥 Firecrawl MCP](./servers/literature.md#-firecrawl-mcp)                | Search, scrape, crawl to markdown        | Official  | 🏆 Recommended  | 🟢 Easy | Remote | [GitHub](https://github.com/firecrawl/firecrawl-mcp-server)                                        |
| [🧬 PubMed MCP](./servers/literature.md#-pubmed-mcp)                      | Biomedical literature search             | Community | ⭐ Worth Trying | 🟢 Easy | Local  | [GitHub](https://github.com/JackKuo666/PubMed-MCP-Server)                                          |
| [🤗 Hugging Face MCP](./servers/models-datasets.md#-hugging-face-mcp)    | Papers on the HF Hub *(cross-listed)*    | Official  | 🏆 Recommended  | 🟢 Easy | Remote | [Docs](https://huggingface.co/docs/hub/agents-mcp)                                                 |

---

### 4.2 🤗 Models & Datasets

Detail page: [`servers/models-datasets.md`](./servers/models-datasets.md)

| MCP                                                                   | One-liner                                       | Type     | Level           | Setup   | Run    | Links                                                        |
| --------------------------------------------------------------------- | ----------------------------------------------- | -------- | --------------- | ------- | ------ | ------------------------------------------------------------ |
| [🤗 Hugging Face MCP](./servers/models-datasets.md#-hugging-face-mcp) | Models, datasets, papers, Spaces, docs          | Official | 🏆 Recommended  | 🟢 Easy | Remote | [Docs](https://huggingface.co/docs/hub/agents-mcp) · [GitHub](https://github.com/huggingface/hf-mcp-server) |
| [🧠 Replicate MCP](./servers/models-datasets.md#-replicate-mcp)       | Run hosted models for fast experimentation      | Official | ⭐ Worth Trying | 🟢 Easy | Remote | [Docs](https://replicate.com/docs/reference/mcp)             |

---

### 4.3 🧪 Experiment Management

Detail page: [`servers/experiments.md`](./servers/experiments.md)

| MCP                                                                        | One-liner                               | Type     | Level           | Setup     | Run             | Links                                                                   |
| -------------------------------------------------------------------------- | --------------------------------------- | -------- | --------------- | --------- | --------------- | ----------------------------------------------------------------------- |
| [📊 Weights & Biases MCP](./servers/experiments.md#-weights--biases-mcp)   | Runs, metrics, artifacts, registry      | Official | 🏆 Recommended  | 🟢 Easy   | Local / Remote  | [Official](https://wandb.ai/site/mcp/) · [GitHub](https://github.com/wandb/wandb-mcp-server) |
| [🔬 MLflow MCP](./servers/experiments.md#-mlflow-mcp)                      | Experiments, traces, model management   | Official | ⭐ Worth Trying | 🟡 Medium | Local           | [Docs](https://mlflow.org/docs/latest/genai/mcp/)                       |

---

### 4.4 📊 Evaluation & Observability

Detail page: [`servers/evaluation.md`](./servers/evaluation.md)

| MCP                                                       | One-liner                             | Type     | Level           | Setup     | Run             | Links                                                          |
| --------------------------------------------------------- | ------------------------------------- | -------- | --------------- | --------- | --------------- | -------------------------------------------------------------- |
| [🔭 LangSmith MCP](./servers/evaluation.md#-langsmith-mcp) | LLM/agent traces, datasets, evals     | Official | 🏆 Recommended  | 🟢 Easy   | Local           | [GitHub](https://github.com/langchain-ai/langsmith-mcp-server) |
| [📊 W&B Weave](./servers/evaluation.md#-wb-weave)          | LLM/agent observability & evaluation  | Official | ⭐ Worth Trying | 🟢 Easy   | Local / Remote  | [W&B MCP](https://wandb.ai/site/mcp/)                          |
| [🔮 Arize Phoenix MCP](./servers/evaluation.md#-arize-phoenix-mcp) | Self-hosted LLM/RAG traces and evals | Official | ⭐ Worth Trying | 🟡 Medium | Local      | [GitHub](https://github.com/Arize-ai/phoenix)                  |

---

### 4.5 🚀 Inference & Deployment

Detail page: [`servers/deployment.md`](./servers/deployment.md)

| MCP                                                                                            | One-liner                                    | Type      | Level            | Setup      | Run    | Links                                                                                   |
| ---------------------------------------------------------------------------------------------- | -------------------------------------------- | --------- | ---------------- | ---------- | ------ | --------------------------------------------------------------------------------------- |
| [☁️ HF Inference Endpoints MCP](./servers/deployment.md#-hf-inference-endpoints-mcp)           | Create, deploy, scale and test endpoints     | Official  | 🛠️ Advanced      | 🟡 Medium  | Remote | [Docs](https://huggingface.co/docs/inference-endpoints/guides/mcp_server)               |
| [☸️ Kubernetes MCP](./servers/deployment.md#-kubernetes-mcp)                                   | Run training/serving jobs on a cluster       | Community | ⚠️ Use with Care | 🔴 Advanced | Local | [GitHub](https://github.com/Flux159/mcp-server-kubernetes)                              |

---

### 4.6 🤖 Agent / Compute / DevOps

Detail page: [`servers/infrastructure.md`](./servers/infrastructure.md)

| MCP                                                                                                    | One-liner                              | Type      | Level           | Setup     | Run             | Links                                                                                              |
| ------------------------------------------------------------------------------------------------------ | -------------------------------------- | --------- | --------------- | --------- | --------------- | -------------------------------------------------------------------------------------------------- |
| [📁 Filesystem MCP](./servers/infrastructure.md#-filesystem-mcp)                                        | Read/write files in an allowed dir     | Official  | 🏆 Recommended  | 🟢 Easy   | Local           | [GitHub](https://github.com/modelcontextprotocol/servers)                                           |
| [🌿 Git MCP](./servers/infrastructure.md#-git-mcp)                                                      | Read, search and manipulate a repo     | Official  | 🏆 Recommended  | 🟢 Easy   | Local           | [GitHub](https://github.com/modelcontextprotocol/servers)                                           |
| [🐙 GitHub MCP](./servers/infrastructure.md#-github-mcp)                                                | Repos, issues, PRs, code search        | Official  | 🏆 Recommended  | 🟡 Medium | Remote / Docker | [GitHub](https://github.com/github/github-mcp-server)                                               |
| [📓 Jupyter MCP](./servers/infrastructure.md#-jupyter-mcp)                                              | Python / notebook execution            | Community | 🏆 Recommended  | 🟡 Medium | Local / Docker  | [GitHub](https://github.com/datalayer/jupyter-mcp-server)                                           |
| [☁️ Google Colab MCP](./servers/infrastructure.md#-google-colab-mcp)                                    | Cloud notebooks, GPU access            | Official  | ⭐ Worth Trying | 🟢 Easy   | Remote          | [Announcement](https://developers.googleblog.com/announcing-the-colab-mcp-server-connect-any-ai-agent-to-google-colab/) |
| [🗄️ SQLite MCP](./servers/infrastructure.md#-sqlite-mcp)                                                | Query a local SQLite database          | Official  | 🏆 Recommended  | 🟢 Easy   | Local           | [GitHub](https://github.com/modelcontextprotocol/servers)                                           |
| [🐘 PostgreSQL MCP](./servers/infrastructure.md#-postgresql-mcp)                                        | Query and inspect PostgreSQL schemas   | Official  | ⭐ Worth Trying | 🟡 Medium | Local           | [GitHub](https://github.com/modelcontextprotocol/servers)                                           |
| [🌈 Chroma MCP](./servers/infrastructure.md#-chroma-mcp)                                                | Vector store for RAG experiments       | Official  | ⭐ Worth Trying | 🟡 Medium | Local           | [GitHub](https://github.com/chroma-core/chroma-mcp)                                                |
| [🐳 Docker MCP Gateway](./servers/infrastructure.md#-docker-mcp-gateway)                                | Run MCP servers in containers          | Official  | ⭐ Worth Trying | 🟡 Medium | Docker          | [GitHub](https://github.com/docker/mcp-gateway) · [Docs](https://docs.docker.com/ai/mcp-catalog-and-toolkit/) |
| [🎭 Playwright MCP](./servers/infrastructure.md#-playwright-mcp)                                        | Browser automation for the agent       | Official  | ⭐ Worth Trying | 🟢 Easy   | Local           | [GitHub](https://github.com/microsoft/playwright-mcp)                                               |
| [📚 Context7 MCP](./servers/infrastructure.md#-context7-mcp)                                            | Version-specific library documentation | Official  | 🏆 Recommended  | 🟢 Easy   | Remote          | [GitHub](https://github.com/upstash/context7)                                                        |
| [🧩 NVIDIA NeMo Agent Toolkit](./servers/infrastructure.md#-nvidia-nemo-agent-toolkit)                  | Build & expose agent workflows via MCP | Official  | 🛠️ Advanced     | 🟡 Medium | Local           | [GitHub](https://github.com/NVIDIA/NeMo-Agent-Toolkit)                                              |

---

## 5. Recommendation levels

| Label                | Meaning                                                     |
| -------------------- | ----------------------------------------------------------- |
| 🏆 **Recommended**   | Easy to use and valuable for most researchers               |
| ⭐ **Worth Trying**  | Useful, but more specialized                                |
| 🧪 **Experimental**  | Interesting but still immature                              |
| 🛠️ **Advanced**      | Requires infrastructure or non-trivial configuration        |
| ⚠️ **Use with Care** | Sensitive permissions or potentially destructive operations |

> ⚠️ Emoji collision: 🧪 is also the icon of the **Experiments** category. As a *level*, 🧪 Experimental means "still immature" — no server in this catalog currently carries that level.

Ranking is **not** based on GitHub stars. Every entry is scored on five dimensions:

1. **Usefulness** — does it solve a real AI research problem?
2. **Ease of use** — can a researcher start without becoming an MCP expert?
3. **Documentation** — install, config, auth, tools, examples, troubleshooting.
4. **Maintenance** — recent commits, issue activity, clear ownership, releases.
5. **Security** — file access, code execution, cloud resources, destructive ops, credentials.

---

## 6. Fields & legend

| Field      | Values                                                        |
| ---------- | ------------------------------------------------------------- |
| `Type`     | `Official` (vendor-maintained) · `Community`                   |
| `Setup`    | 🟢 Easy · 🟡 Medium · 🔴 Advanced                                |
| `Run`      | `Remote` (hosted URL) · `Local` (`npx`/`uvx`/`pip`) · `Docker` |
| `Risk`     | Read-only · Write-capable · ⚠️ Code execution · ⚠️ Local writes · ⚠️ Cluster access · 💸 Spends money · Config-heavy |

Typical installation paths, in order of preference:

```text
Remote URL  →  zero install, best for hosted services
npx         →  JS/TS MCPs, quick local testing
uvx         →  Python MCPs, local research environments
Docker      →  reproducibility, teams, heavy dependencies
```

---

## 7. Maintenance

* `data/servers.yaml` is the **structured source of truth** (27 records).
* `CATALOG.md` and `servers/*.md` are the human-readable views derived from it.
* Changing a server means updating **all three** — see [CONTRIBUTING.md](./CONTRIBUTING.md).

Last catalog review: **2026-09-29**.
