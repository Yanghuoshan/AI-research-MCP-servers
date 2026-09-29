# 📊 Evaluation & Observability

MCP servers for **evaluating LLMs and agents**, inspecting traces, and turning failures into datasets.

← [Catalog](../CATALOG.md) · [README](../README.md)

---

## 📑 In this file

| MCP                                          | One-liner                            | Type     | Level           | Setup   | Run             |
| -------------------------------------------- | ------------------------------------ | -------- | --------------- | ------- | --------------- |
| [🔭 LangSmith MCP](#-langsmith-mcp)          | LLM/agent traces, datasets, evals    | Official | 🏆 Recommended  | 🟢 Easy | Local           |
| [📊 W&B Weave](#-wb-weave)                   | LLM/agent observability & evaluation | Official | ⭐ Worth Trying | 🟢 Easy | Local / Remote  |
| [🔮 Arize Phoenix MCP](#-arize-phoenix-mcp) | Self-hosted LLM/RAG traces and evals | Official | ⭐ Worth Trying | 🟡 Medium | Local           |

Related: [MLflow MCP](./experiments.md#-mlflow-mcp) also exposes GenAI traces and evaluation.

---

## 🔭 LangSmith MCP

**Inspect LLM and agent traces, datasets and experiments.**

* **Best for:** LLM / Agent research
* **Category:** evaluation
* **Type:** Official
* **Difficulty:** 🟢 Easy
* **Setup:** 🟢 Easy
* **Run:** Local
* **Level:** 🏆 Recommended
* **Permissions:** 🟢 `read` + 🟡 `write`

**Useful for**

* LLM traces
* Agent traces
* Datasets
* Evaluation
* Debugging
* Prompt experiments

**Why we recommend it**

The fastest way to close the loop on agent research: pull the failing traces, turn them into a dataset, re-run the eval, compare. Without this, agent iteration is guesswork.

**Known limitations**

* Traces contain prompts and possibly user content — scope to a single workspace and scrub PII.
* Budget-aware: tracing at high volume generates a lot of data.

🔗 [GitHub](https://github.com/langchain-ai/langsmith-mcp-server)

---

## 📊 W&B Weave

**Evaluate and analyze LLM and agent workflows.**

* **Best for:** LLM observability and evaluation
* **Category:** evaluation
* **Type:** Official
* **Difficulty:** 🟢 Easy–Medium
* **Setup:** 🟢 Easy–Medium
* **Run:** Local / Remote
* **Level:** ⭐ Worth Trying
* **Permissions:** 🟢 `read` + 🟡 `write`

**Useful for**

* LLM calls
* Agent traces
* Evaluation
* Latency
* Failures

**Why it's worth trying**

A good fit if your team already lives in W&B: evaluation sits next to your training metrics instead of in a separate tool.

**Known limitations**

* Overlaps with the W&B MCP — enable one, not both, or the agent gets duplicate tools.
* Same data-sensitivity caveats as any trace store.

🔗 [W&B MCP](https://wandb.ai/site/mcp/)

---

## 🔮 Arize Phoenix MCP

**Open-source LLM observability, traces and evaluations.**

* **Best for:** Self-hosted LLM / RAG evaluation
* **Category:** evaluation
* **Type:** Official
* **Difficulty:** 🟡 Medium
* **Setup:** 🟡 Medium
* **Run:** Local
* **Level:** ⭐ Worth Trying
* **Permissions:** 🟢 `read` + 🟡 `write`

**Useful for**

* Traces
* Datasets
* Experiments
* RAG evaluation
* Prompt experiments

**Why it's worth trying**

The open-source option in this category: Phoenix runs on your own infrastructure (OpenTelemetry-based), so trace data never has to leave your lab. Good default when data residency or cost rules out a hosted eval platform.

**Known limitations**

* Requires a running Phoenix server — more setup than a hosted remote MCP.
* Evals consume model calls; a large eval suite is a real bill.

🔗 [GitHub](https://github.com/Arize-ai/phoenix)

---

## 🧭 Suggested combinations

| Goal                              | Stack                                                            |
| --------------------------------- | ---------------------------------------------------------------- |
| Debug a failing agent             | LangSmith + [Jupyter](./infrastructure.md#-jupyter-mcp)          |
| Build a regression eval set       | LangSmith                                                        |
| LLM evals next to training metrics| W&B Weave + [W&B MCP](./experiments.md#-weights--biases-mcp)     |
| Reproduce the failing run         | LangSmith + [GitHub](./infrastructure.md#-github-mcp)            |
