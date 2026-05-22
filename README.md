<div align="center">

# Condensate

### The Memory Operating System for AI Agents

**Current AI Memory is Built for Search. Condensate is Built for Cognition.**

[![Website](https://img.shields.io/badge/condensate.io-000000?style=for-the-badge&logo=google-chrome&logoColor=white)](https://www.condensate.io)
[![GitHub](https://img.shields.io/badge/condensate--io/core-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/condensate-io/core)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/company/condensate-io/)
[![License](https://img.shields.io/badge/Apache_2.0-D22128?style=for-the-badge&logo=apache&logoColor=white)](https://github.com/condensate-io/core/blob/main/LICENSE)

[![PyPI](https://img.shields.io/pypi/v/condensate?style=flat-square&logo=python&logoColor=white&label=python)](https://pypi.org/project/condensate/)
[![npm](https://img.shields.io/npm/v/@condensate-io/sdk?style=flat-square&logo=npm&logoColor=white&label=typescript)](https://www.npmjs.com/package/@condensate-io/sdk)
[![crates.io](https://img.shields.io/crates/v/condensate?style=flat-square&logo=rust&logoColor=white&label=rust)](https://crates.io/crates/condensate)
[![npm MCP](https://img.shields.io/npm/v/@condensate-io/core?style=flat-square&logo=npm&logoColor=white&label=mcp)](https://www.npmjs.com/package/@condensate-io/core)

*Open-source Memory Operating System — the canonical, cross-vendor memory substrate for autonomous AI agents.*

</div>

---

## The Problem

AI agents today are forced to build long-term memory on top of systems designed for document search.

- Vector databases return contradictory chunks.
- Flat logs lose causality and provenance.
- Proprietary memory APIs trap cognitive data.
- Last-Write-Wins destroys nuanced multi-agent state.

**The result:** agents that hallucinate, forget, and cannot explain why they believe what they believe.

---

## What Condensate Changes

Condensate shifts AI memory from *"similarity search over text"* to a *verifiable, multi-agent causal graph*:

- **Structured Memory Ontology** — condenses raw events into typed Entities, Assertions, Relations, Events, Learnings, and Policies.
- **Cryptographic Provenance** — wraps memory assertions with signed proof envelopes and input hashes.
- **Active Learning** — builds weighted semantic links and consolidates dense clusters into higher-order knowledge.
- **Deterministic Multi-Agent Concurrency** — uses CRDT-based merge semantics for safe parallel updates.
- **Vendor Independence** — works across OpenAI-compatible providers and MCP-compatible agent hosts.

---

## Architecture at a Glance

```
Raw Input (Chat / Docs / API)
        │
        ▼
   [Ingress Agent]  ──── stores EpisodicItem + vector embedding
        │
        ▼
   [Condenser]      ──── NER → LLM Extraction → Entity Canonicalization
        │                → Assertion Consolidation → Edge Synthesis
        ▼
   [Synapse Engine] ──── Multi-Signal Scoring → Cluster Detection
        │                → LLM High-Fidelity Consolidation
        ▼
   [Knowledge Graph] ─── Entities, Assertions, Relations (Postgres)
        │
        ▼
   [Memory Router]  ──── Vector search + Graph traversal + Hebbian updates
        │
        ▼
   [MCP / API]      ──── Agents, SDKs, Admin Dashboard
```

---

## Get Started in 60 Seconds

```bash
git clone https://github.com/condensate-io/core
cd core
cp .env.example .env
./start.sh
```

Then connect with the Python SDK:

```python
from condensate import CondensateClient

client = CondensateClient("http://localhost:8000", "sk-your-key")
client.store_memory(content="User prefers dark mode.", type="episodic")
result = client.retrieve("What are the user's preferences?")
print(result["answer"])
```

---

## SDKs

| SDK | Install | Docs |
|---|---|---|
| Python | `pip install condensate` | [sdks/python](https://github.com/condensate-io/core/tree/main/sdks/python) |
| TypeScript | `npm install @condensate-io/sdk` | [sdks/ts](https://github.com/condensate-io/core/tree/main/sdks/ts) |
| MCP Bridge | `npx -y @condensate-io/core` | [sdks/mcp-bridge](https://github.com/condensate-io/core/tree/main/sdks/mcp-bridge) |
| Rust | `cargo add condensate` | [sdks/rust](https://github.com/condensate-io/core/tree/main/sdks/rust) |
| Go | `go get github.com/condensate/condensate-go-sdk` | [sdks/go](https://github.com/condensate-io/core/tree/main/sdks/go) |

---

## Ecosystem Compatibility

- **Model Providers:** OpenAI, Anthropic, Azure OpenAI, Google Gemini, Mistral
- **Local Inference:** Ollama, LM Studio, LocalAI
- **Agent Frameworks:** LangChain, LlamaIndex, AutoGen, CrewAI
- **Agent Hosts:** Claude Desktop, Cursor, Windsurf, Codeium

---

## Wiki Navigation

| Page | Description |
|------|-------------|
| [The Problem](https://github.com/condensate-io/core/wiki/The-Problem) | Why current AI memory architectures fail |
| [Architecture](https://github.com/condensate-io/core/wiki/Architecture) | Merkle-DAGs, CRDTs, Condenser pipeline, Proof Envelopes |
| [Synapse Engine](https://github.com/condensate-io/core/wiki/Synapse-Engine) | Hebbian learning and memory consolidation |
| [SDKs and Integration](https://github.com/condensate-io/core/wiki/SDKs-and-Integration) | SDK and MCP integration reference |
| [Getting Started](https://github.com/condensate-io/core/wiki/Getting-Started) | Setup and first ingestion walkthrough |
| [Security and Threat Model](https://github.com/condensate-io/core/wiki/Security-and-Threat-Model) | Guardrails, provenance, and tenant isolation |
| [FAQ](https://github.com/condensate-io/core/wiki/FAQ) | Common questions |

---

## Links

| | |
|---|---|
| **Website** | [https://www.condensate.io](https://www.condensate.io) |
| **Core Repository** | [https://github.com/condensate-io/core](https://github.com/condensate-io/core) |
| **Core Wiki** | [https://github.com/condensate-io/core/wiki](https://github.com/condensate-io/core/wiki) |
| **LinkedIn** | [https://www.linkedin.com/company/condensate-io/](https://www.linkedin.com/company/condensate-io/) |
| **License** | Apache 2.0 |

---

<div align="center">

**Standardizing the brain of AI agents.**

🇦🇺 Built in Melbourne, Australia · Open source · Apache 2.0

</div>
