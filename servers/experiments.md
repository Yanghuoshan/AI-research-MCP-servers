# 🧪 Experiment Management

MCP servers for **tracking, inspecting and comparing experiments** — runs, metrics, artifacts and model registries.

← [Catalog](../CATALOG.md) · [README](../README.md)

---

## 📑 In this file

| MCP                                                      | One-liner                             | Type     | Level           | Setup     | Run   |
| -------------------------------------------------------- | ------------------------------------- | -------- | --------------- | --------- | ----- |
| [📊 Weights & Biases MCP](#-weights--biases-mcp)         | Runs, metrics, artifacts, registry    | Official | 🏆 Recommended  | 🟢 Easy   | Local |
| [🔬 MLflow MCP](#-mlflow-mcp)                            | Experiments, traces, model management | Official | ⭐ Worth Trying | 🟡 Medium | Local |

---

## 📊 Weights & Biases MCP

**Let AI agents inspect and analyze W&B experiments.**

* **Best for:** Deep learning experiments
* **Category:** experiments
* **Type:** Official
* **Difficulty:** 🟢 Easy
* **Setup:** 🟢 Easy–Medium
* **Run:** Local / Remote (check the official docs for the current hosted option)
* **Level:** 🏆 Recommended
* **Permissions:** 🟢 `read` + 🟡 `write`

**Useful for**

* Runs
* Metrics
* Experiments
* Traces
* Reports
* Artifacts
* Model registry

**Why we recommend it**

If you already use W&B, this is the highest-value MCP in the whole workflow: the agent can answer "which run was best and why" directly from your real metrics instead of you copy-pasting dashboards.

**Known limitations**

* Default credential scope can cover the whole organization — use a project/team-scoped service account.
* Large sweeps need prompt-level filtering; don't ask the agent to "load everything".

🔗 [Official MCP](https://wandb.ai/site/mcp/)

🔗 [GitHub](https://github.com/wandb/wandb-mcp-server)

---

## 🔬 MLflow MCP

**Connect AI agents to MLflow experiments, traces and model management.**

* **Best for:** Open-source MLOps
* **Category:** experiments
* **Type:** Official
* **Difficulty:** 🟡 Medium
* **Setup:** 🟡 Medium
* **Run:** Local
* **Level:** ⭐ Worth Trying
* **Permissions:** 🟢 `read` + 🟡 `write`

**Useful for**

* Experiments
* Runs
* Model registry
* Traces
* Evaluation
* Model management

**Why it's worth trying**

The right choice when your stack is self-hosted or when you need GenAI traces alongside classic experiment tracking. No vendor lock-in.

**Known limitations**

* Requires a reachable MLflow tracking server plus matching auth configuration — more setup than a hosted remote MCP.
* Registry write operations can transition model stages; point it at a dev server, not production.

🔗 [Documentation](https://mlflow.org/docs/latest/genai/mcp/)

---

## 🧭 Suggested combinations

| Goal                              | Stack                                                          |
| --------------------------------- | -------------------------------------------------------------- |
| Analyze last night's sweeps       | W&B + [Jupyter](./infrastructure.md#-jupyter-mcp)               |
| Self-hosted / on-prem tracking    | MLflow                                                          |
| LLM app tracing + experiments     | MLflow or [LangSmith](./evaluation.md#-langsmith-mcp)  |
| From experiment to deployment     | W&B/MLflow + [HF Inference Endpoints](./deployment.md#-hf-inference-endpoints-mcp) |
