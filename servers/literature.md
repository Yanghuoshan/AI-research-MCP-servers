# 📚 Literature & Research

MCP servers for **finding, reading and connecting research papers**.

← [Catalog](../CATALOG.md) · [README](../README.md)

---

## 📑 In this file

| MCP                                            | One-liner                                | Type      | Level           | Setup   | Run   |
| ---------------------------------------------- | ---------------------------------------- | --------- | --------------- | ------- | ----- |
| [📄 arXiv MCP](#-arxiv-mcp)                     | Search and retrieve arXiv papers         | Community | 🏆 Recommended  | 🟢 Easy | Local |
| [🔎 Semantic Scholar MCP](#-semantic-scholar-mcp) | Paper search + citation graph          | Community | 🏆 Recommended  | 🟢 Easy | Local |
| [🌐 OpenAlex MCP](#-openalex-mcp)               | Global research-landscape analysis       | Community | ⭐ Worth Trying | 🟢 Easy | Local |
| [🤗 Hugging Face MCP](../servers/models-datasets.md#-hugging-face-mcp) *(cross-listed)* | Papers & daily AI papers on the Hub | Official  | 🏆 Recommended  | 🟢 Easy | Remote |
| [🔍 Exa MCP](#-exa-mcp)                         | Semantic web + research-paper search   | Official  | 🏆 Recommended  | 🟢 Easy | Remote |
| [🔥 Firecrawl MCP](#-firecrawl-mcp)             | Search, scrape and crawl the web       | Official  | 🏆 Recommended  | 🟢 Easy | Remote |
| [🧬 PubMed MCP](#-pubmed-mcp)                   | Biomedical literature search           | Community | ⭐ Worth Trying | 🟢 Easy | Local  |

Also relevant: [🐙 GitHub MCP](./infrastructure.md#-github-mcp) for finding reference implementations.

---

## 📄 arXiv MCP

**Search and retrieve research papers from arXiv.**

* **Best for:** Literature search
* **Category:** literature
* **Type:** Community
* **Difficulty:** 🟢 Easy
* **Setup:** 🟢 Easy
* **Run:** Local (`uvx` / `pip` — check the repo for the exact command)
* **Level:** 🏆 Recommended
* **Permissions:** 🟢 `read`

**Useful for**

* Paper search
* Paper metadata
* Abstracts
* PDF retrieval
* Literature review

**Why we recommend it**

arXiv is still one of the most important sources for current AI research. This is the lowest-effort way to give an agent real literature access.

**Known limitations**

* Community-maintained — verify client compatibility and pinned versions.
* No built-in citation graph; pair with Semantic Scholar for that.

🔗 [GitHub](https://github.com/Tejas242/arxiv-mcp)

---

## 🔎 Semantic Scholar MCP

**Search academic papers and explore citation relationships.**

* **Best for:** Literature discovery
* **Category:** literature
* **Type:** Community
* **Difficulty:** 🟢 Easy
* **Setup:** 🟢 Easy
* **Run:** Local
* **Level:** 🏆 Recommended
* **Permissions:** 🟢 `read`

**Useful for**

* Paper search
* Authors
* Citations
* Related papers
* Research discovery

**Why we recommend it**

Better discovery than keyword search: the citation graph lets an agent walk forward and backward from a seed paper, which is exactly how literature reviews are done.

**Known limitations**

* Public API rate limits; an API key may be required for higher throughput.
* Coverage outside CS/medicine can be uneven.

🔗 [GitHub](https://github.com/yogsoth-ai/semantic-scholar-mcp)

---

## 🌐 OpenAlex MCP

**Search and analyze the global research landscape.**

* **Best for:** Large-scale literature analysis
* **Category:** literature
* **Type:** Community
* **Difficulty:** 🟢 Easy
* **Setup:** 🟢 Easy
* **Run:** Local
* **Level:** ⭐ Worth Trying
* **Permissions:** 🟢 `read`

**Useful for**

* Papers
* Authors
* Institutions
* Citations
* Research trends
* Collaboration networks

**Why it's worth trying**

OpenAlex is the best free source when you need bibliometrics at scale — trends by institution, country or field — rather than a single paper lookup.

**Known limitations**

* Metadata quality varies by discipline; deduplication is sometimes needed.
* More specialized than arXiv/S2 — install it when you actually need landscape analysis.

🔗 [GitHub](https://github.com/oksure/openalex-research-mcp)

---

## 🤗 Hugging Face MCP *(cross-listed)*

The Hugging Face MCP also exposes **papers and daily trending papers** on the Hub, which makes it a useful literature companion.

* **Category:** models-datasets (primary)
* **Level:** 🏆 Recommended

→ Full entry: [Hugging Face MCP](../servers/models-datasets.md#-hugging-face-mcp)

---

## 🔍 Exa MCP

**Semantic web and research-paper search.**

* **Best for:** Discovery beyond arXiv (preprints, blogs, lab pages, grey literature)
* **Category:** literature
* **Type:** Official
* **Difficulty:** 🟢 Easy
* **Setup:** 🟢 Easy
* **Run:** Remote
* **Level:** 🏆 Recommended
* **Permissions:** 🟢 `read`

**Useful for**

* Semantic web search
* Research paper search
* Similar-paper lookup
* Company / topic research
* Crawling a result page

**Why we recommend it**

arXiv and Semantic Scholar only cover what is indexed. Exa fills the gap: blog posts, lab pages, technical reports and preprints that never made it into a bibliographic database — which is where a lot of current AI practice actually lives.

**Known limitations**

* Requires an API key and is metered.
* Ranking comes from a proprietary model, not citation counts — treat it as discovery, not evidence.

🔗 [Documentation](https://exa.ai/docs/get-started/exa-mcp)

🔗 [GitHub](https://github.com/exa-labs/exa-mcp-server)

---

## 🔥 Firecrawl MCP

**Search, scrape and crawl the web into clean markdown.**

* **Best for:** Turning any web page into LLM-ready content
* **Category:** literature
* **Type:** Official
* **Difficulty:** 🟢 Easy
* **Setup:** 🟢 Easy
* **Run:** Remote
* **Level:** 🏆 Recommended
* **Permissions:** 🟢 `read` + 🔴 `billing`

**Useful for**

* Web search
* Page scraping
* Site crawling
* Structured extraction
* Documentation ingestion

**Why we recommend it**

The practical counterpart to Exa: once you know *where* the information is, Firecrawl gets the *content* into the agent's context as markdown instead of raw HTML. Also the easiest way to ingest documentation sites as a research corpus.

**Known limitations**

* 💸 Usage-based billing — a "crawl this docs site" instruction can burn a lot of credits.
* Respect `robots.txt` and the site's terms of use.

🔗 [GitHub](https://github.com/firecrawl/firecrawl-mcp-server)

🔗 [Documentation](https://docs.firecrawl.dev/mcp-server)

---

## 🧬 PubMed MCP

**Search and retrieve biomedical literature from PubMed.**

* **Best for:** Biomedical and life-science AI research
* **Category:** literature
* **Type:** Community
* **Difficulty:** 🟢 Easy
* **Setup:** 🟢 Easy
* **Run:** Local
* **Level:** ⭐ Worth Trying
* **Permissions:** 🟢 `read`

**Useful for**

* Article search
* Abstracts
* MeSH terms
* Citation metadata

**Why it's worth trying**

If your research touches biology, medicine or health, arXiv is the wrong corpus. This is the minimum viable bridge from an agent to PubMed/MEDLINE.

**Known limitations**

* Several competing community implementations exist and none is canonical — evaluate the one you pick before depending on it.
* No full-text access: you get abstracts and metadata, PDFs usually sit behind publisher access.

🔗 [GitHub](https://github.com/JackKuo666/PubMed-MCP-Server)

---

## 🧭 Suggested combinations

| Goal                         | Stack                                        |
| ---------------------------- | -------------------------------------------- |
| Fast "what's new" scan       | arXiv + Hugging Face (daily papers)          |
| Systematic literature review | arXiv + Semantic Scholar                     |
| Field/landscape analysis     | OpenAlex + Semantic Scholar                  |
| Find code for a paper        | Semantic Scholar + [GitHub MCP](./infrastructure.md#-github-mcp) |
| Grey literature / blog posts | Exa + Firecrawl                              |
| Biomedical research          | PubMed + Semantic Scholar                    |
