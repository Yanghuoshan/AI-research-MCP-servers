# 🚀 Inference & Deployment

MCP servers for **serving and operating models** after research is done.

← [Catalog](../CATALOG.md) · [README](../README.md)

---

## 📑 In this file

| MCP                                                                        | One-liner                                | Type     | Level       | Setup     | Run    |
| -------------------------------------------------------------------------- | ---------------------------------------- | -------- | ----------- | --------- | ------ |
| [☁️ HF Inference Endpoints MCP](#-hf-inference-endpoints-mcp)              | Create, deploy, scale and test endpoints | Official  | 🛠️ Advanced      | 🟡 Medium | Remote |
| [☸️ Kubernetes MCP](#-kubernetes-mcp)                                      | Run training/serving jobs on a cluster   | Community | ⚠️ Use with Care | 🔴 Advanced | Local  |

This is the smallest category in the catalog on purpose: deployment MCPs grant **billing- or cluster-level permissions**, so we keep it short and label risky entries explicitly.

---

## ☁️ HF Inference Endpoints MCP

**Manage and deploy models to Hugging Face Inference Endpoints.**

* **Best for:** Model deployment
* **Category:** deployment
* **Type:** Official
* **Difficulty:** 🟡 Medium
* **Setup:** 🟡 Medium
* **Run:** Remote
* **Level:** 🛠️ Advanced *(also ⚠️ Use with Care)*
* **Permissions:** 🟢 `read` + 🟡 `write` + 🔴 `billing`

**Useful for**

* Create endpoints
* Deploy models
* Scale endpoints
* Logs
* Metrics
* Inference testing

**Why we recommend it**

It closes the research loop: the same agent that found the model on the Hub can deploy it, smoke-test it, read the logs and then scale it down again.

**Known limitations**

* 🔴 It provisions paid GPU resources. Require human approval for create/scale operations and set billing alerts.
* Endpoint state is real infrastructure — clean up after experiments.

🔗 [Documentation](https://huggingface.co/docs/inference-endpoints/guides/mcp_server)

---

## ☸️ Kubernetes MCP

**Inspect and operate a Kubernetes cluster — jobs, pods and deployments.**

* **Best for:** Submitting training and serving jobs to a GPU cluster
* **Category:** deployment
* **Type:** Community
* **Difficulty:** 🔴 Advanced
* **Setup:** 🔴 Advanced
* **Run:** Local
* **Level:** ⚠️ Use with Care
* **Permissions:** 🟢 `read` + 🟡 `write` + 🟠 `exec`

**Useful for**

* Pod and job inspection
* Job submission
* Logs
* Resource inspection
* Deployment rollout

**Why it's worth trying**

Most serious research runs on a cluster, not a laptop. This lets the agent submit a training job, watch the pod, read the logs and clean up afterwards without you writing YAML by hand.

**Known limitations**

* ⚠️ Cluster-level blast radius. Use a **scoped service account**, restrict it to a dev namespace, and never point it at a production cluster from an agent.
* Prefer the read-only subset (inspect/logs) for analysis; enable write tools only when the agent must actually launch a job.

🔗 [GitHub](https://github.com/Flux159/mcp-server-kubernetes)

---

## 🔐 Operating rules we recommend

1. **Human-in-the-loop for money.** Any tool that creates or scales an endpoint should require confirmation.
2. **Separate credentials.** Use a dedicated Hugging Face token with only the endpoint scopes you need.
3. **Always scale down.** Add an explicit "delete/scale-to-zero" step at the end of agent workflows.
4. **Smoke-test before announcing.** Call the endpoint once through the MCP and check latency and output shape.

See [SECURITY.md](../SECURITY.md#2-permission-tiers) for the permission tier definitions.

---

## 🧭 Suggested combinations

| Goal                             | Stack                                                                                        |
| -------------------------------- | -------------------------------------------------------------------------------------------- |
| Deploy a model you just found    | [Hugging Face](./models-datasets.md#-hugging-face-mcp) + HF Inference Endpoints               |
| Serve a fine-tuned run           | [W&B/MLflow](./experiments.md) + HF Inference Endpoints                                       |
| Quick multimodal demo            | [Replicate](./models-datasets.md#-replicate-mcp) (no endpoint management needed)              |
| Train/serve on your own cluster  | Kubernetes MCP + [GitHub](./infrastructure.md#-github-mcp) (job specs in repo)                |
