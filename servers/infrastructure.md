# 🤖 Agent / Compute / DevOps

MCP servers that provide **compute, code, storage and agent infrastructure** — the layer under everything else.

← [Catalog](../CATALOG.md) · [README](../README.md)

---

## 📑 In this file

### 🗂️ Files & repositories

| MCP                                     | One-liner                              | Type     | Level           | Setup     | Run             |
| --------------------------------------- | -------------------------------------- | -------- | --------------- | --------- | --------------- |
| [📁 Filesystem MCP](#-filesystem-mcp)    | Read/write files in an allowed dir     | Official | 🏆 Recommended  | 🟢 Easy   | Local           |
| [🌿 Git MCP](#-git-mcp)                  | Read, search and manipulate a repo     | Official | 🏆 Recommended  | 🟢 Easy   | Local           |
| [🐙 GitHub MCP](#-github-mcp)            | Repos, issues, PRs, code search        | Official | 🏆 Recommended  | 🟡 Medium | Remote / Docker |

### 🖥️ Compute & notebooks

| MCP                                     | One-liner                              | Type      | Level           | Setup     | Run             |
| --------------------------------------- | -------------------------------------- | --------- | --------------- | --------- | --------------- |
| [📓 Jupyter MCP](#-jupyter-mcp)          | Python / notebook execution            | Community | 🏆 Recommended  | 🟡 Medium | Local / Docker  |
| [☁️ Google Colab MCP](#-google-colab-mcp)| Cloud notebooks with GPU               | Official  | ⭐ Worth Trying | 🟢 Easy   | Remote          |

### 🗄️ Storage & retrieval

| MCP                                     | One-liner                              | Type     | Level           | Setup     | Run    |
| --------------------------------------- | -------------------------------------- | -------- | --------------- | --------- | ------ |
| [🗄️ SQLite MCP](#-sqlite-mcp)            | Query a local SQLite database          | Official | 🏆 Recommended  | 🟢 Easy   | Local  |
| [🐘 PostgreSQL MCP](#-postgresql-mcp)    | Query and inspect PostgreSQL schemas   | Official | ⭐ Worth Trying | 🟡 Medium | Local  |
| [🌈 Chroma MCP](#-chroma-mcp)            | Vector store for RAG experiments       | Official | ⭐ Worth Trying | 🟡 Medium | Local  |

### 🛠️ Tooling, browser & docs

| MCP                                                      | One-liner                              | Type     | Level           | Setup     | Run    |
| -------------------------------------------------------- | -------------------------------------- | -------- | --------------- | --------- | ------ |
| [🐳 Docker MCP Gateway](#-docker-mcp-gateway)             | Run MCP servers in containers          | Official | ⭐ Worth Trying | 🟡 Medium | Docker |
| [🎭 Playwright MCP](#-playwright-mcp)                    | Browser automation for the agent       | Official | ⭐ Worth Trying | 🟢 Easy   | Local  |
| [📚 Context7 MCP](#-context7-mcp)                        | Version-specific library documentation | Official | 🏆 Recommended  | 🟢 Easy   | Remote |
| [🧩 NVIDIA NeMo Agent Toolkit](#-nvidia-nemo-agent-toolkit) | Build & expose agent workflows      | Official | 🛠️ Advanced     | 🟡 Medium | Local  |

Cross-listed: [☸️ Kubernetes MCP](./deployment.md#-kubernetes-mcp) for cluster job submission.

---

**🗂️ Files & repositories**

## 📁 Filesystem MCP

**Read, write and search files inside an allow-listed directory.**

* **Best for:** Giving the agent a working directory for a project
* **Category:** infrastructure
* **Type:** Official (reference implementation)
* **Difficulty:** 🟢 Easy
* **Setup:** 🟢 Easy
* **Run:** Local
* **Level:** 🏆 Recommended
* **Permissions:** 🟢 `read` + 🟡 `write`

**Useful for**

* Reading notes and drafts
* Writing result files
* Directory search
* File diffing

**Why we recommend it**

Every research agent needs somewhere to put things: drafts, extracted tables, generated figures, run logs. This is the canonical reference server for that job, and its allow-list model is the safety pattern other servers should copy.

**Known limitations**

* ⚠️ Grant only the project directory — never `$HOME`, `~/.ssh` or `~/.aws`.
* The reference implementation enables write tools by default; disable them when you only need reading.

🔗 [GitHub](https://github.com/modelcontextprotocol/servers)

---

## 🌿 Git MCP

**Read, search and manipulate a local Git repository.**

* **Best for:** Versioning the actual research repo
* **Category:** infrastructure
* **Type:** Official (reference implementation)
* **Difficulty:** 🟢 Easy
* **Setup:** 🟢 Easy
* **Run:** Local
* **Level:** 🏆 Recommended
* **Permissions:** 🟢 `read` + 🟡 `write`

**Useful for**

* Repo status and diff
* Commit history search
* Branch inspection
* Creating commits

**Why we recommend it**

"Which commit changed the data loader?" and "what did I try last Tuesday?" are real research questions. Git history is often the only record of why an experiment went a certain way.

**Known limitations**

* Can create commits — keep your tree clean so the agent's changes stay reviewable.
* Works on a local clone; for PRs and issues use [GitHub MCP](#-github-mcp).

🔗 [GitHub](https://github.com/modelcontextprotocol/servers)

---

## 🐙 GitHub MCP

**Repositories, issues, pull requests and code search.**

* **Best for:** Code, issues and pull requests
* **Category:** infrastructure
* **Type:** Official
* **Difficulty:** 🟡 Medium
* **Setup:** 🟡 Medium
* **Run:** Remote / Docker
* **Level:** 🏆 Recommended *(⚠️ write-capable)*
* **Permissions:** 🟢 `read` + 🟡 `write`

**Useful for**

* Repository search
* Code search
* Issues
* Pull requests
* Code review workflows

**Why we recommend it**

Research is code. This lets the agent find reference implementations, read the actual source of a method, and turn an experiment into a PR.

**Known limitations**

* ⚠️ Can push branches and open PRs. Prefer read-only toolsets by default; use a fine-grained token scoped to specific repositories.
* Private repositories become visible to the agent — decide deliberately.

🔗 [GitHub](https://github.com/github/github-mcp-server)

---

**🖥️ Compute & notebooks**

## 📓 Jupyter MCP

**Give your AI agent access to Jupyter notebooks and Python execution.**

* **Best for:** Scientific computing
* **Category:** infrastructure
* **Type:** Community
* **Difficulty:** 🟡 Medium
* **Setup:** 🟡 Medium
* **Run:** Local / Docker
* **Level:** 🏆 Recommended *(⚠️ code execution)*
* **Permissions:** 🟢 `read` + 🟡 `write` + 🟠 `exec`

**Useful for**

* Python
* Data analysis
* Visualization
* Model experiments
* Notebook workflows

**Why we recommend it**

This is what turns an LLM from "talks about research" into "does research": real execution, real dataframes, real plots, reproducible notebook cells.

**Known limitations**

* ⚠️ Arbitrary code execution. Run it in a container, and never mount directories with credentials or private research data.
* Long-running cells can block the agent loop; keep kernels scoped to one experiment.

🔗 [GitHub](https://github.com/datalayer/jupyter-mcp-server)

---

## ☁️ Google Colab MCP

**Connect AI agents to Google Colab environments.**

* **Best for:** Cloud-based AI experiments
* **Category:** infrastructure
* **Type:** Official
* **Difficulty:** 🟢 Easy
* **Setup:** 🟢 Easy
* **Run:** Remote
* **Level:** ⭐ Worth Trying *(⚠️ code execution)*
* **Permissions:** 🟢 `read` + 🟡 `write` + 🟠 `exec`

**Useful for**

* Python
* GPU experiments
* Notebook execution
* ML experiments

**Why it's worth trying**

The easiest path to a GPU without touching your laptop or your cluster. Good for short training runs and quick reproduction attempts.

**Known limitations**

* ⚠️ Code runs in a Google account context with drive access — use a **separate account** for agent work.
* Sessions are ephemeral; not suitable for long training jobs or persistent state.

🔗 [Announcement](https://developers.googleblog.com/announcing-the-colab-mcp-server-connect-any-ai-agent-to-google-colab/)

---

**🗄️ Storage & retrieval**

## 🗄️ SQLite MCP

**Query a local SQLite database with SQL.**

* **Best for:** Storing and re-querying experiment results
* **Category:** infrastructure
* **Type:** Official (reference implementation)
* **Difficulty:** 🟢 Easy
* **Setup:** 🟢 Easy
* **Run:** Local
* **Level:** 🏆 Recommended
* **Permissions:** 🟢 `read` + 🟡 `write`

**Useful for**

* Ad-hoc SQL analysis
* Result tables
* Schema inspection
* Local reproducible datasets

**Why we recommend it**

The cheapest way to make results *queryable* instead of *scrollable*: dump every run's metrics into one SQLite file and let the agent do the aggregation. No server, no credentials, one file you can commit or share.

**Known limitations**

* The reference server exposes write and DDL tools — point it at a copy if the data matters.
* Single-writer; not a substitute for a real results database on a team.

🔗 [GitHub](https://github.com/modelcontextprotocol/servers)

---

## 🐘 PostgreSQL MCP

**Query and inspect PostgreSQL schemas.**

* **Best for:** Reading the lab's shared results database
* **Category:** infrastructure
* **Type:** Official (reference implementation)
* **Difficulty:** 🟡 Medium
* **Setup:** 🟡 Medium
* **Run:** Local
* **Level:** ⭐ Worth Trying
* **Permissions:** 🟢 `read` + 🟡 `write`

**Useful for**

* Schema inspection
* Read-only analytics queries
* Result aggregation

**Why it's worth trying**

When results already live in Postgres, this beats exporting CSVs: the agent inspects the schema and writes the query itself.

**Known limitations**

* Executes arbitrary SQL — connect with a **read-only role** unless writes are required.
* Broad schemas produce huge tool output; scope the connection to one database.

🔗 [GitHub](https://github.com/modelcontextprotocol/servers)

---

## 🌈 Chroma MCP

**Vector store for retrieval and RAG experiments.**

* **Best for:** Building and inspecting retrieval pipelines
* **Category:** infrastructure
* **Type:** Official
* **Difficulty:** 🟡 Medium
* **Setup:** 🟡 Medium
* **Run:** Local
* **Level:** ⭐ Worth Trying
* **Permissions:** 🟢 `read` + 🟡 `write`

**Useful for**

* Collection management
* Embedding ingestion
* Similarity search
* Metadata filtering

**Why it's worth trying**

Retrieval is a research variable, not a constant. Having the vector store as a tool lets the agent build a collection, query it, and show you exactly what your RAG pipeline retrieved — which is how you debug retrieval quality.

**Known limitations**

* Requires an embedding model to be configured, and results depend entirely on that choice.
* It is a store, not a benchmark harness — evaluate retrieval quality yourself.

🔗 [GitHub](https://github.com/chroma-core/chroma-mcp)

---

**🛠️ Tooling, browser & docs**

## 🐳 Docker MCP Gateway

**Run and manage containerised MCP servers from the Docker catalog.**

* **Best for:** Reproducible, sandboxed MCP setups
* **Category:** infrastructure
* **Type:** Official
* **Difficulty:** 🟡 Medium
* **Setup:** 🟡 Medium
* **Run:** Docker
* **Level:** ⭐ Worth Trying
* **Permissions:** 🟢 `read` + 🟡 `write` + 🟠 `exec`

**Useful for**

* Running MCP servers in containers
* Credential management via the Docker MCP Toolkit
* Catalog discovery
* Per-client enable/disable

**Why it's worth trying**

The container boundary is the cleanest sandbox we have for third-party MCP servers: no host Python/Node pollution, and credentials handled in one place instead of scattered across client configs.

**Known limitations**

* Requires Docker Desktop with the MCP Toolkit.
* Containerisation is not a security boundary by itself — check what each image mounts before enabling it.

🔗 [GitHub](https://github.com/docker/mcp-gateway)

🔗 [Documentation](https://docs.docker.com/ai/mcp-catalog-and-toolkit/)

---

## 🎭 Playwright MCP

**Browser automation driven by the agent.**

* **Best for:** Pages that have no API (dashboards, forms, repositories)
* **Category:** infrastructure
* **Type:** Official
* **Difficulty:** 🟡 Medium
* **Setup:** 🟢 Easy
* **Run:** Local
* **Level:** ⭐ Worth Trying
* **Permissions:** 🟢 `read` + 🟡 `write` + 🟠 `exec`

**Useful for**

* Navigating websites
* Downloading files
* Filling forms
* Screenshots
* Scraping content that sits behind interactions

**Why it's worth trying**

Some research material is only reachable by clicking: supplementary material behind a journal UI, W&B dashboards, dataset download wizards, leaderboards. This is the escape hatch when no API exists.

**Known limitations**

* ⚠️ Full browser context — any logged-in session is in scope. Use a dedicated browser profile with no saved credentials.
* Slower and more brittle than an API; prefer [Firecrawl](../servers/literature.md#-firecrawl-mcp) for plain content extraction.

🔗 [GitHub](https://github.com/microsoft/playwright-mcp)

---

## 📚 Context7 MCP

**Up-to-date, version-specific library documentation.**

* **Best for:** Avoiding hallucinated APIs in generated research code
* **Category:** infrastructure
* **Type:** Official
* **Difficulty:** 🟢 Easy
* **Setup:** 🟢 Easy
* **Run:** Remote
* **Level:** 🏆 Recommended
* **Permissions:** 🟢 `read`

**Useful for**

* Library documentation lookup
* Version-specific examples
* Framework API reference

**Why we recommend it**

The single most common failure of research code generation is an API that changed two releases ago. Context7 pulls the current, version-matched docs and examples into the agent's context before it writes code.

**Known limitations**

* Coverage depends on what has been indexed; niche research libraries may be missing.
* It does not replace reading the source when the exact behaviour matters for your results.

🔗 [GitHub](https://github.com/upstash/context7)

🔗 [Documentation](https://context7.com)

---

## 🧩 NVIDIA NeMo Agent Toolkit

**Build and expose AI workflows using MCP.**

* **Best for:** Agent research and multi-agent systems
* **Category:** infrastructure
* **Type:** Official
* **Difficulty:** 🟡 Medium
* **Setup:** 🟡 Medium
* **Run:** Local
* **Level:** 🛠️ Advanced
* **Permissions:** 🟢 `read` + 🟡 `write`

**Useful for**

* Agent workflows
* MCP clients
* MCP servers
* Multi-agent systems
* NVIDIA AI infrastructure

**Why it's worth trying**

The right tool when your research object *is* the agent: it gives you a framework to build workflows and then expose them as MCP servers or consume others as a client.

**Known limitations**

* Configuration-heavy; expect real setup work.
* Review the generated tool schemas before publishing a server — you are defining another agent's capability surface.

🔗 [GitHub](https://github.com/NVIDIA/NeMo-Agent-Toolkit)

---

## 🧭 Suggested combinations

| Goal                          | Stack                                                            |
| ----------------------------- | ---------------------------------------------------------------- |
| Do actual data analysis       | Jupyter + Filesystem + SQLite                                    |
| Keep the repo tidy            | Git + GitHub + [Context7](#-context7-mcp)                         |
| Need a GPU, no cluster        | Google Colab                                                     |
| Reproduce a paper's code      | GitHub + [Context7](#-context7-mcp) + Jupyter                    |
| Build a retrieval baseline    | Chroma + Jupyter                                                 |
| Sandbox third-party MCPs      | Docker MCP Gateway                                               |
| Research on agents themselves | NeMo Agent Toolkit + [LangSmith](./evaluation.md#-langsmith-mcp) |
