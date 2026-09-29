# 🔐 Security & Permissions

MCP servers are **not passive data sources** — they are capabilities you hand to an AI agent. This document explains the risks in this catalog and how to evaluate a new server before installing it.

Home: [README.md](./README.md) · [中文首页](./README.zh-CN.md) · [Catalog](./CATALOG.md)

---

## 📑 Table of Contents

* [1. The seven questions](#1-the-seven-questions)
* [2. Permission tiers](#2-permission-tiers)
* [3. Risk matrix for this catalog](#3-risk-matrix-for-this-catalog)
* [4. Recommended escalation order](#4-recommended-escalation-order)
* [5. Credential handling](#5-credential-handling)
* [6. Red flags when reviewing a server](#6-red-flags-when-reviewing-a-server)
* [7. Reporting a security issue](#7-reporting-a-security-issue)

---

## 1. The seven questions

Before installing any MCP server, answer these:

```text
What can it READ?
What can it WRITE?
Can it execute code?
Can it access my filesystem?
Can it access cloud resources?
Can it spend money?
Can it delete resources?
```

If you cannot answer all seven from the project's documentation, treat that as a **finding**, not a detail — undocumented capability is unbounded capability.

---

## 2. Permission tiers

Used in the `permissions` field of `data/servers.yaml` and in the `Risk` column of [CATALOG.md](./CATALOG.md).

| Tier                | Meaning                                                     | Typical examples                     |
| ------------------- | ----------------------------------------------------------- | ------------------------------------ |
| 🟢 `read`           | Reads public or already-authorized data; no side effects    | Paper search, dataset metadata       |
| 🟡 `write`          | Creates or mutates state (runs, issues, files, registries)  | Experiment logging, PR creation      |
| 🟠 `exec`           | Executes arbitrary code or shell commands                   | Notebooks, local Python, dev servers |
| 🔴 `billing`        | Provisions paid cloud resources                             | Inference endpoints, hosted GPU runs |

Tiers are cumulative in practice: a server with `write` usually also has `read`.

---

## 3. Risk matrix for this catalog

| MCP                             | Tier     | Main concern                                              | Mitigation                                              |
| ------------------------------- | -------- | --------------------------------------------------------- | ------------------------------------------------------- |
| arXiv MCP                       | 🟢 read  | None significant                                          | —                                                       |
| Semantic Scholar MCP            | 🟢 read  | API key may be required for higher limits                  | Use a dedicated key; never reuse a production key       |
| OpenAlex MCP                    | 🟢 read  | None significant                                          | —                                                       |
| Hugging Face MCP                | 🟢 read  | Token can carry write scope on the Hub                     | Use a **fine-grained read token**; disable write scope  |
| Replicate MCP                   | 🔴 billing | Every model run costs money                              | Set spend limits; never expose in an unsupervised loop  |
| Weights & Biases MCP            | 🟡 write | Can read/log runs across the whole org                     | Scope to one project/team; use a service account        |
| MLflow MCP                      | 🟡 write | Can register/transition model versions                    | Point at a dev tracking server, not production           |
| LangSmith MCP                   | 🟡 write | Trace data may contain prompts and user content           | Scrub PII; scope to a single workspace                  |
| W&B Weave                       | 🟡 write | Same as above                                             | Same as above                                           |
| HF Inference Endpoints MCP      | 🔴 billing | Creates and scales paid GPU endpoints                    | Budget alerts; require human approval for scale-up      |
| Jupyter MCP                     | 🟠 exec  | Arbitrary Python on your machine                          | Run in a container; no host mounts of private data      |
| Google Colab MCP                | 🟠 exec  | Arbitrary Python + drive/credential access                | Use a separate Google account for agent work            |
| GitHub MCP                      | 🟡 write | Can open PRs, push branches, read private repos           | Use a fine-grained PAT; prefer read-only toolsets       |
| NVIDIA NeMo Agent Toolkit       | 🟡 write | Exposes your own workflows as tools to others             | Review exposed tool schemas before publishing           |
| Exa MCP                         | 🟢 read  | Metered API key; queries leave your network               | Dedicated key with a spend cap                          |
| Firecrawl MCP                   | 🔴 billing | Per-page/per-crawl charges can scale without bound     | Cap crawl depth; set usage alerts                        |
| PubMed MCP                      | 🟢 read  | Community implementation; provenance unverified          | Review the code before granting it network access        |
| Arize Phoenix MCP               | 🟡 write | Trace data + eval runs consume model calls               | Point at a self-hosted Phoenix; scope datasets           |
| Kubernetes MCP                  | 🟠 exec  | Cluster-level blast radius (delete, scale, exec)          | Scoped service account, dev namespace, never production  |
| Filesystem MCP                  | 🟡 write | Writes and deletes files in the granted tree             | Allow-list one project dir; disable write tools by default |
| Git MCP                         | 🟡 write | Can create commits and modify the working tree           | Keep a clean tree; review diffs before merging           |
| SQLite MCP                      | 🟡 write | DDL and write statements on the database file            | Use a copy of the results DB, not the original           |
| PostgreSQL MCP                  | 🟡 write | Executes arbitrary SQL, including destructive queries    | Connect with a read-only role; scope to one database     |
| Chroma MCP                      | 🟡 write | Ingests and deletes collection data                      | Isolated collection per experiment                       |
| Docker MCP Gateway              | 🟠 exec  | Runs containers that may mount host paths                | Inspect each image's mounts before enabling              |
| Playwright MCP                  | 🟠 exec  | Full browser session, including logged-in cookies        | Dedicated browser profile with no saved credentials      |
| Context7 MCP                    | 🟢 read  | Sends library/version context to a third party           | No credentials required; avoid private package names     |

---

## 4. Recommended escalation order

For research environments, grant permissions in this order and stop as early as possible:

```text
Read-only
    ↓
Experiment (sandboxed writes)
    ↓
Human approval (agent proposes, you confirm)
    ↓
Write / Deploy
```

Avoid giving an AI agent unrestricted access to:

```text
sudo
+
production credentials
+
cloud billing
+
GPU clusters
+
private research data
```

unless you fully understand the implications.

Practical rules:

1. **Sandbox execution.** Code-execution MCPs (Jupyter, Colab) belong in a container or a throwaway account.
2. **Separate credentials.** Never reuse your primary cloud/HF/W&B key for an agent.
3. **Least scope.** Prefer read-only toolsets; enable write tools only for the task at hand.
4. **Human-in-the-loop for money.** Anything that provisions GPUs or endpoints should require confirmation.
5. **Log everything.** Keep the MCP client's tool-call log; it is your audit trail when something unexpected happens.

---

## 5. Credential handling

* Store tokens in environment variables or your client's secret store — **never** commit them to this repository or paste them into a shared config.
* Prefer fine-grained / scoped tokens (read-only Hub token, per-repo GitHub PAT, project-scoped W&B key).
* Rotate agent credentials on a schedule and on every suspected exposure.
* If a server asks for credentials it does not explain, do not install it.

---

## 6. Red flags when reviewing a server

Reject or label `⚠️ Use with Care` when a project:

* Requests broad OAuth scopes without documenting why.
* Sends file contents or environment variables to a third-party endpoint without disclosure.
* Has no license, no maintainer, or no way to report issues.
* Silently writes outside its stated working directory.
* Provides delete/scale/provision tools with no confirmation step.
* Claims to bypass paywalls, rate limits, or access controls.

---

## 7. Reporting a security issue

If a server **listed in this catalog** has a security problem:

1. Open an issue **without** exploit details: state the server, the affected version, and the class of problem.
2. Tell us whether it is already disclosed upstream; prefer reporting to the upstream maintainer first.
3. We will add a `⚠️ Use with Care` label or remove the entry while the issue is open.

For security problems in **this repository** (e.g. a malicious link or a credential committed by accident), open an issue immediately and mention `@maintainers`.

---

## 📌 Disclaimer

This document is guidance for researchers, not a security audit. Every deployment is different — evaluate each MCP server against your own threat model.
