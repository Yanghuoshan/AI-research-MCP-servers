# 🤝 Contributing

Thanks for helping improve this list. This document explains **how to submit a new MCP server** and how to keep the repository consistent.

Home: [README.md](./README.md) · [中文首页](./README.zh-CN.md) · [Catalog](./CATALOG.md)

---

## 📑 Table of Contents

* [1. Before you submit](#1-before-you-submit)
* [2. Acceptance checklist](#2-acceptance-checklist)
* [3. Where to make changes](#3-where-to-make-changes)
* [4. Step-by-step: add a new server](#4-step-by-step-add-a-new-server)
* [5. Entry format](#5-entry-format)
* [6. YAML schema](#6-yaml-schema)
* [7. Other kinds of contributions](#7-other-kinds-of-contributions)
* [8. Style rules](#8-style-rules)

---

## 1. Before you submit

* Search [CATALOG.md](./CATALOG.md) and the open issues — avoid duplicates.
* Use the server yourself at least once. We do not list things we have not read the docs of.
* Be honest about limitations. A short "known limitations" note is more valuable than marketing copy.
* This repository is **not** a place for every MCP server; it is a curated list for **AI research workflows**.

---

## 2. Acceptance checklist

A submission should satisfy **all** of the following:

* [ ] Relevant to AI research or AI engineering
* [ ] Publicly accessible (docs and/or repository)
* [ ] Has clear documentation (install, config, auth, tools, examples)
* [ ] Has a working installation method (remote URL, `npx`, `uvx`, `pip` or Docker)
* [ ] Has at least one usable example
* [ ] Maintained or updated recently
* [ ] Does not intentionally bypass authentication or access controls
* [ ] Clearly documents the permissions it requires
* [ ] MCP functionality is more than a thin wrapper (`not just "one REST call"`)
* [ ] No fabricated benchmarks, star counts, or capabilities

Entries that fail the security bar go on the list with a `⚠️ Use with Care` label, or are rejected — see [SECURITY.md](./SECURITY.md).

---

## 3. Where to make changes

One logical change touches **three** places. Keep them in sync:

| File                                     | What to update                                              |
| ---------------------------------------- | ----------------------------------------------------------- |
| `data/servers.yaml`                      | Add/update the structured record (source of truth)           |
| `servers/<category>.md`                  | Add/update the detailed entry + the index table at the top    |
| `CATALOG.md`                             | Add the row to the master index and the category table        |

If a new category is genuinely needed, add a new file under `servers/` and link it from `README.md`, `CATALOG.md` and the other category pages. Prefer fitting into the existing six categories.

Categories:

| File                          | Scope                                                    |
| ----------------------------- | -------------------------------------------------------- |
| `servers/literature.md`       | Papers, citations, web search/scraping, research discovery |
| `servers/models-datasets.md`  | Model hubs, dataset hubs, hosted model execution          |
| `servers/experiments.md`      | Experiment tracking, run management, model registry       |
| `servers/evaluation.md`       | LLM/agent evaluation, traces, observability, benchmarks   |
| `servers/deployment.md`       | Inference endpoints, serving, deployment                  |
| `servers/infrastructure.md`   | Agent frameworks, compute/notebooks, DevOps & code hosts  |

---

## 4. Step-by-step: add a new server

1. **Fork** the repository and create a branch: `git checkout -b add/<server-id>`.
2. **Pick an `id`**: lowercase, hyphenated, stable (e.g. `semantic-scholar`). Never rename it later.
3. **Add the record** to `data/servers.yaml` (see [§6](#6-yaml-schema)).
4. **Add the detailed entry** to the matching `servers/*.md`, following [§5](#5-entry-format).
5. **Add the index rows** in `servers/*.md`, in `CATALOG.md` master index + category table, and (if it is a standout) the featured table in `README.md` / `README.zh-CN.md`.
6. **Run the sync check**: every `id` in `servers.yaml` must appear exactly once in the **master index** of `CATALOG.md`. A cross-listed server may appear a second time in its extra category table, but never twice in the master index.
7. **Open a PR** with:
   * what the server does, in one sentence;
   * how you verified it (client used, version, date);
   * the permission surface (read / write / exec / billing).

---

## 5. Entry format

Copy this block into the right `servers/*.md` file:

```markdown
## 🧩 Project Name

**One-sentence description of what it does.**

- **Best for:** ...
- **Category:** literature | models-datasets | experiments | evaluation | deployment | infrastructure
- **Type:** Official | Community
- **Difficulty:** 🟢 Easy | 🟡 Medium | 🔴 Advanced
- **Setup:** 🟢 Easy | 🟡 Medium | 🔴 Advanced
- **Run:** Remote | Local (`npx` / `uvx` / `pip`) | Docker | Local / Remote | Remote / Docker | Local / Docker
- **Level:** 🏆 Recommended | ⭐ Worth Trying | 🧪 Experimental | 🛠️ Advanced | ⚠️ Use with Care
- **Permissions:** read-only | write | code execution | cloud billing

**Useful for**

- ...
- ...
- ...

**Known limitations**

- ...

🔗 [Documentation](...)
🔗 [GitHub](...)
```

Rules for the write-up:

* Describe **what the researcher accomplishes**, not the implementation technology.
* Do not paste marketing language from the project's landing page.
* Do not include raw star counts — they go stale and are not a ranking signal.
* Always include at least one official link (docs or repository).

---

## 6. YAML schema

`data/servers.yaml` mirrors the Markdown so the tables can be generated or audited. Minimal record:

```yaml
- id: semantic-scholar          # required, stable, lowercase-hyphen
  name: Semantic Scholar MCP
  emoji: "🔎"
  category: literature          # must match a servers/*.md file stem
  also_in: []                   # optional: extra categories where it is cross-listed
  tagline: Paper search + citation graph
  type: community               # official | community
  difficulty: easy              # easy | medium | advanced
  setup: easy                   # easy | medium | advanced
  run: [local, remote]          # remote | local | docker — use a list when several work
  level: recommended            # recommended | worth-trying | experimental | advanced | use-with-care
  permissions: [read]           # read | write | exec | billing
  best_for: Literature discovery
  useful_for:
    - Paper search
    - Citations
  limitations:
    - Rate limits on the public API
  links:
    docs: https://...
    github: https://...
  tags: [papers, citations]
  added: 2026-09-29
  last_reviewed: 2026-09-29
```

Keep keys sorted as above; keep `added` immutable once merged.

---

## 7. Other kinds of contributions

| Kind                | How                                                                        |
| ------------------- | -------------------------------------------------------------------------- |
| 🐛 Fix stale info   | PR with the corrected field + a link to the upstream evidence               |
| 🗑️ Remove a server  | PR explaining why (abandoned, broken, security issue); keep a note in the PR body |
| 🔁 Move a server    | PR that updates `category`, both Markdown files, and leaves the `id` unchanged |
| 🌏 Translation      | Keep `README.zh-CN.md` in sync with `README.md` section by section          |
| 💡 Suggestion only  | Open an issue with the `suggestion` label instead of a PR                    |

---

## 8. Style rules

* One sentence per line in lists; no walls of text.
* Use the emoji/icons already present in the repo (`📚 🤗 🧪 📊 🚀 🤖`) — don't invent new category icons without need.
* Tables over prose for anything scannable.
* No absolute claims ("the best", "the fastest"). Use "best for ...".
* Write in English for `CATALOG.md`, `servers/*.md`, `CONTRIBUTING.md` and `SECURITY.md`; `README.md` (EN) and `README.zh-CN.md` (中文) are kept as parallel versions.

---

## 📌 Final note

Maintainers may edit submissions for consistency. If an entry is declined, we will say why — usually relevance, maintenance, or permissions. Feel free to resubmit when the situation changes.
