# 🤗 Models & Datasets

MCP servers for **finding models and datasets**, and for **running models** without local GPU setup.

← [Catalog](../CATALOG.md) · [README](../README.md)

---

## 📑 In this file

| MCP                                          | One-liner                                    | Type     | Level           | Setup   | Run    |
| -------------------------------------------- | -------------------------------------------- | -------- | --------------- | ------- | ------ |
| [🤗 Hugging Face MCP](#-hugging-face-mcp)    | Models, datasets, papers, Spaces, docs       | Official | 🏆 Recommended  | 🟢 Easy | Remote |
| [🧠 Replicate MCP](#-replicate-mcp)          | Run hosted models (image/video/audio/multi)  | Official | ⭐ Worth Trying | 🟢 Easy | Remote |

Cross-listed: [HF Inference Endpoints MCP](./deployment.md#-hf-inference-endpoints-mcp) for deploying what you find here.

---

## 🤗 Hugging Face MCP

**Discover models, datasets, papers, Spaces and AI applications.**

* **Best for:** AI/ML resource discovery
* **Category:** models-datasets (also listed under [literature](./literature.md))
* **Type:** Official
* **Difficulty:** 🟢 Easy
* **Setup:** 🟢 Easy
* **Run:** Remote
* **Level:** 🏆 Recommended
* **Permissions:** 🟢 `read` *(if you use a token, keep it read-only)*

**Useful for**

* Model discovery
* Dataset discovery
* Papers
* Spaces
* AI demos
* Hugging Face documentation

**Why we recommend it**

The Hugging Face ecosystem is the most useful single starting point for modern AI research: models, datasets, papers and runnable demos behind one tool interface. If you only install one MCP from this repository, install this one.

**Known limitations**

* A write-enabled Hub token significantly widens the blast radius — use a fine-grained **read** token.
* Remote service; availability and login flow depend on Hugging Face.

🔗 [Documentation](https://huggingface.co/docs/hub/agents-mcp)

🔗 [GitHub](https://github.com/huggingface/hf-mcp-server)

---

## 🧠 Replicate MCP

**Search and run AI models through Replicate.**

* **Best for:** Fast model experimentation
* **Category:** models-datasets
* **Type:** Official
* **Difficulty:** 🟢 Easy
* **Setup:** 🟢 Easy
* **Run:** Remote
* **Level:** ⭐ Worth Trying
* **Permissions:** 🟢 `read` + 🔴 `billing`

**Useful for**

* Image generation
* Video
* Audio
* Multimodal models
* Model comparison
* Quick experiments

**Why it's worth trying**

It turns "let's see what this model does" into a single tool call — no weights, no environment, no GPU. Ideal for multimodal baselines and quick ablations.

**Known limitations**

* 💸 Every run costs money. Do not expose it to an unsupervised agent loop without spend limits.
* Not a substitute for reproducible local inference; results depend on a hosted service.

🔗 [Documentation](https://replicate.com/docs/reference/mcp)

---

## 🧭 Suggested combinations

| Goal                            | Stack                                   |
| ------------------------------- | --------------------------------------- |
| Find a model/dataset            | Hugging Face                            |
| Try a multimodal model quickly  | Replicate                               |
| Reproduce a paper's baseline    | Hugging Face + [Jupyter](./infrastructure.md#-jupyter-mcp) |
| Serve it afterwards             | Hugging Face + [HF Inference Endpoints](./deployment.md#-hf-inference-endpoints-mcp) |
