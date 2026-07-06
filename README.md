<div align="center">

# Condensate

### Memory and Governance for Autonomous AI Agents

**Condensate Core gives agents a verifiable memory substrate. Our TurboQuant-enabled Qdrant fork delivers optimized vector retrieval. Verified Agentic Development gives them a governed delivery loop.**

[![Website](https://img.shields.io/badge/condensate.io-000000?style=for-the-badge&logo=google-chrome&logoColor=white)](https://www.condensate.io)
[![GitHub](https://img.shields.io/badge/condensate--io/core-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/condensate-io/core)
[![VAD](https://img.shields.io/badge/verified--agentic--development-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/condensate-io/verified-agentic-development)
[![Qdrant](https://img.shields.io/badge/qdrant-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/condensate-io/qdrant)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/company/condensate-io/)
[![License](https://img.shields.io/badge/Apache_2.0-D22128?style=for-the-badge&logo=apache&logoColor=white)](https://github.com/condensate-io/core/blob/main/LICENSE)

[![PyPI](https://img.shields.io/pypi/v/condensate?style=flat-square&logo=python&logoColor=white&label=python)](https://pypi.org/project/condensate/)
[![npm](https://img.shields.io/npm/v/@condensate-io/sdk?style=flat-square&logo=npm&logoColor=white&label=typescript)](https://www.npmjs.com/package/@condensate-io/sdk)
[![crates.io](https://img.shields.io/crates/v/condensate?style=flat-square&logo=rust&logoColor=white&label=rust)](https://crates.io/crates/condensate)
[![npm MCP](https://img.shields.io/npm/v/@condensate-io/core?style=flat-square&logo=npm&logoColor=white&label=mcp)](https://www.npmjs.com/package/@condensate-io/core)

*Open-source infrastructure for agents that remember with provenance, retrieve with speed, and ship with proof.*

</div>

---

## The Problem

AI agents today are forced to build long-term memory on top of systems designed for document search, and to ship software through workflows that were never built for multi-agent assurance.

- Vector databases return contradictory chunks.
- Flat logs lose causality and provenance.
- Proprietary memory APIs trap cognitive data.
- Last-Write-Wins destroys nuanced multi-agent state.
- Agentic coding accelerates output without matching verification, policy evidence, or recovery.

**The result:** agents that hallucinate, forget, cannot explain why they believe what they believe, and cannot prove why a change was safe to release.

---

## The Condensate Ecosystem

Condensate is three complementary open-source projects:

| Project | Role | Repository |
|---|---|---|
| **[Condensate Core](https://github.com/condensate-io/core)** | Memory Operating System — semantic graph, provenance, consolidation | [`condensate-io/core`](https://github.com/condensate-io/core) |
| **[TurboQuant Qdrant](https://github.com/condensate-io/qdrant)** | Condensate's Qdrant fork — we integrated Google TurboQuant and built FastScan SIMD, QJL correction, and in-kernel thresholding | [`condensate-io/qdrant`](https://github.com/condensate-io/qdrant) |
| **[Verified Agentic Development (VAD)](https://github.com/condensate-io/verified-agentic-development)** | Control-system model — intent, proof, policy, orchestration, audit | [`condensate-io/verified-agentic-development`](https://github.com/condensate-io/verified-agentic-development) |

**Core** answers: *What does the agent know, and why?*  
**TurboQuant Qdrant** answers: *How fast can we retrieve and score embeddings at scale?*  
**VAD** answers: *What did the agent change, under what policy, with what proof, and who approved it?*

Together they form a stack where vector retrieval, delivery evidence, and retrospective learnings reinforce durable agent memory.

```
┌─────────────────────────────────────────────────────────────────┐
│  Agent Hosts: Cursor · Claude Code · Codex · VS Code · Windsurf │
└───────────────────────────────┬─────────────────────────────────┘
                                │
                    ┌───────────▼───────────┐
                    │  VAD Control Plane      │
                    │  intent · proof · policy│
                    │  work queue · MCP gate  │
                    │  evidence · dashboard   │
                    └───────────┬─────────────┘
                                │ events · learnings · bundles
                    ┌───────────▼───────────┐
                    │  Condensate Core        │
                    │  graph · provenance     │
                    │  consolidation · MCP    │
                    └───────────┬─────────────┘
                                │ embeddings · hybrid retrieval
                    ┌───────────▼───────────┐
                    │  TurboQuant Qdrant      │
                    │  Condensate integration │
                    │  FastScan · AVX2 · HNSW │
                    └─────────────────────────┘
```

---

## Condensate Core — The Memory Operating System

Current AI memory is built for search. Condensate Core is built for cognition.

Condensate Core shifts AI memory from *"similarity search over text"* to a *verifiable, multi-agent causal graph*:

- **Structured Memory Ontology** — condenses raw events into typed Entities, Assertions, Relations, Events, Learnings, and Policies.
- **Cryptographic Provenance** — wraps memory assertions with signed proof envelopes and input hashes.
- **Active Learning** — builds weighted semantic links and consolidates dense clusters into higher-order knowledge.
- **Deterministic Multi-Agent Concurrency** — uses CRDT-based merge semantics for safe parallel updates.
- **Vendor Independence** — works across OpenAI-compatible providers and MCP-compatible agent hosts.

### Core Architecture

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

### Get Core Running

```bash
git clone https://github.com/condensate-io/core
cd core
cp .env.example .env
./start.sh
```

```python
from condensate import CondensateClient

client = CondensateClient("http://localhost:8000", "sk-your-key")
client.store_memory(content="User prefers dark mode.", type="episodic")
result = client.retrieve("What are the user's preferences?")
print(result["answer"])
```

---

## Verified Agentic Development — The Governance Loop

VAD is a control-system model for enterprise software delivery under agentic acceleration. It treats delivery as a closed loop of **intent → proof → construction → verification → release → feedback**, with separation of duties between builder, verifier, and release guardian roles.

The current reference implementation is a **local Level 4 orchestrator**: an operator-owned control plane that coordinates multi-client agent work on localhost without requiring hosted SaaS, managed tenancy, or live credentials in default tests.

### What VAD Implements Today

- **Executable Intent Packages (EIP)** — structured intent, invariants, proof obligations, and evidence bundles.
- **Verified agentic loop** — ask assessment, proof mapping, guarded execution, MEES effort scoring, and release gates.
- **Local control-plane server** — lifecycle, readiness, SQLite event ledger, replay dashboard, and approval routing.
- **Active orchestration** — durable work items, scheduler assignment, run/task state projection, stale-client recovery with optional auto-reassignment.
- **Governed MCP gateway** — role-aware tool visibility, high-risk denial, client attribution, and redacted summaries over stdio and local HTTP JSON-RPC.
- **Multi-client packages** — local connector artifacts for Codex, Claude Code, VS Code, Cursor, Windsurf, OpenCode, Generic MCP/A2A, and Antigravity fallback.
- **Plugin operations** — review-only dry-runs, persisted inventory, local apply/uninstall/rollback writers, and event-derived dashboard status.
- **Change control** — diff proposal persistence, verifier and release-guardian approval before sandboxed apply, operator intent records.
- **Deterministic verification** — Docker test gate with 570+ passing tests and no paid model calls in default flows.

VAD remains intentionally **local and operator-owned**. It is not a cloud control plane, managed marketplace, or automatic production deployment system unless you explicitly opt in outside the default reference boundary.

### Get VAD Running

```bash
git clone https://github.com/condensate-io/verified-agentic-development
cd verified-agentic-development
docker build -t vad-test:local .
docker run --rm vad-test:local
```

Start the local control plane and dashboard:

```bash
vad control-plane serve
vad local-os demo
```

Key docs in the VAD repository:

| Doc | Description |
|---|---|
| [Quickstart](https://github.com/condensate-io/verified-agentic-development/blob/main/docs/quickstart.md) | First commands and Docker gate |
| [Control Plane](https://github.com/condensate-io/verified-agentic-development/blob/main/docs/control-plane.md) | Level 4 local architecture and API surface |
| [Evolution Plan](https://github.com/condensate-io/verified-agentic-development/blob/main/docs/evolution-plan.md) | Orchestrator OS direction and gap closure |
| [Maturity Model](https://github.com/condensate-io/verified-agentic-development/blob/main/maturity_model.md) | Level 0–4 adoption path |
| [Condensate Integration](https://github.com/condensate-io/verified-agentic-development/blob/main/docs/condensate-integration.md) | Persisting VAD evidence and retrospectives to Core |

### VAD + Core Together

VAD generates structured delivery evidence — verification events, policy decisions, EIP compliance, and retrospective learnings. Condensate Core is the natural long-term store for that evidence as typed **Events** and **Learnings**, queryable across projects and agents.

See the [Condensate Integration Guide](https://github.com/condensate-io/verified-agentic-development/blob/main/docs/condensate-integration.md) for wiring VAD's memory gateway to `CondensateClient`.

---

## TurboQuant Qdrant — Condensate's Vector Retrieval Engine

[condensate-io/qdrant](https://github.com/condensate-io/qdrant) is **Condensate engineering work**: we forked Qdrant v1.18.2 and integrated Google's **TurboQuant** extreme quantization (4-bit, 2-bit, and 1-bit modes), then built the SIMD FastScan kernels, QJL residual correction, and in-kernel threshold filtering that drive the benchmark gains below. This is not upstream Qdrant — it is our performance path for agent-scale embedding retrieval.

### What We Implemented

- **FastScan block-transposed layout** — groups vectors into 32-vector blocks for AVX2 cache locality and coalesced memory loads.
- **SIMD multi-query scoring** — parallel distance accumulation in 256-bit registers instead of scalar loops.
- **QJL residual correction** — 1-bit Quantized Johnson–Lindenstrauss projection to recover quantization accuracy.
- **SIMD thresholding and in-kernel filtering** — fuses priority-queue threshold checks into AVX2 kernels to reduce branch overhead during HNSW candidate evaluation.
- **Dynamic density fallback** — protects sparse/random batch access patterns from block-scoring overhead by falling back to point-wise scoring when block density is low.

### Benchmark Highlights

Full methodology and tables live in [docs/BENCHMARKS.md](https://github.com/condensate-io/qdrant/blob/dev/docs/BENCHMARKS.md). Summary against Qdrant v1.18.2 baseline on 10,000 vectors with 4-bit TurboQuant (`Bits4`), Criterion.rs, AVX2:

| Access pattern | Best result | Notes |
|---|---|---|
| **Dense (contiguous) batch scoring** | **1.82x speedup** at dim 128, batch 32 | Up to **1.65x** at batch 256; strong gains on plain-index / linear scan paths |
| **Sparse (random) batch scoring** | overhead without fallback | Block layout evaluates full 32-vector blocks; density heuristic recommended before FastScan |

Representative dense results (latency vs baseline):

| Dimension | Batch | Speedup |
|---|---|---|
| 128 | 32 | **1.82x** (−45% latency) |
| 128 | 1024 | **1.61x** (−38% latency) |
| 768 | 32 | **1.15x** (−13% latency) |

### Get Qdrant Running

```bash
git clone https://github.com/condensate-io/qdrant
cd qdrant
docker run -p 6333:6333 qdrant/qdrant
```

Build and benchmark locally (see [docs/DEVELOPMENT.md](https://github.com/condensate-io/qdrant/blob/dev/docs/DEVELOPMENT.md)):

```bash
cargo test -p quantization
cargo bench -p quantization --bench turboquant_bench
```

Key docs in the Qdrant fork:

| Doc | Description |
|---|---|
| [Benchmark Report](https://github.com/condensate-io/qdrant/blob/dev/docs/BENCHMARKS.md) | TurboQuant dense vs sparse scoring analysis |
| [Development Guide](https://github.com/condensate-io/qdrant/blob/dev/docs/DEVELOPMENT.md) | Build, Docker gates, and profiling conventions |
| [Implementation Tracker](https://github.com/condensate-io/qdrant/blob/dev/implementation_tracker.md) | Tranche status and recovery checkpoints |

### TurboQuant Qdrant + Core Together

Condensate Core's memory router combines graph traversal with vector search. Our TurboQuant Qdrant fork is the performance path for embedding retrieval at scale — especially when collections use TurboQuant compression and workloads include dense plain-index scans or HNSW graph traversal with in-kernel threshold filtering.

---

## SDKs (Condensate Core)

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
- **Agent Hosts (Core):** Claude Desktop, Cursor, Windsurf, Codeium
- **Agent Hosts (VAD packages):** Codex, Claude Code, VS Code, Cursor, Windsurf, OpenCode, Generic MCP/A2A, Antigravity

---

## Wiki and Documentation

### Condensate Core Wiki

| Page | Description |
|------|-------------|
| [The Problem](https://github.com/condensate-io/core/wiki/The-Problem) | Why current AI memory architectures fail |
| [Architecture](https://github.com/condensate-io/core/wiki/Architecture) | Merkle-DAGs, CRDTs, Condenser pipeline, Proof Envelopes |
| [Synapse Engine](https://github.com/condensate-io/core/wiki/Synapse-Engine) | Hebbian learning and memory consolidation |
| [SDKs and Integration](https://github.com/condensate-io/core/wiki/SDKs-and-Integration) | SDK and MCP integration reference |
| [Getting Started](https://github.com/condensate-io/core/wiki/Getting-Started) | Setup and first ingestion walkthrough |
| [Security and Threat Model](https://github.com/condensate-io/core/wiki/Security-and-Threat-Model) | Guardrails, provenance, and tenant isolation |
| [FAQ](https://github.com/condensate-io/core/wiki/FAQ) | Common questions |

### Verified Agentic Development Docs

| Page | Description |
|------|-------------|
| [README / Whitepaper](https://github.com/condensate-io/verified-agentic-development/blob/main/README.md) | VAD principles and control-system model |
| [Control Plane](https://github.com/condensate-io/verified-agentic-development/blob/main/docs/control-plane.md) | Local Level 4 orchestrator reference |
| [Level 4 Operator Guide](https://github.com/condensate-io/verified-agentic-development/blob/main/docs/level4-operator.md) | Operator workflows and recovery |
| [MCP Gateway Audit](https://github.com/condensate-io/verified-agentic-development/blob/main/docs/mcp-gateway-security-audit.md) | Tool visibility and high-risk controls |

### Qdrant (TurboQuant) Docs

| Page | Description |
|------|-------------|
| [Benchmark Report](https://github.com/condensate-io/qdrant/blob/dev/docs/BENCHMARKS.md) | FastScan dense/sparse scoring results and analysis |
| [Development Guide](https://github.com/condensate-io/qdrant/blob/dev/docs/DEVELOPMENT.md) | Build, test, and benchmark workflow |
| [Implementation Tracker](https://github.com/condensate-io/qdrant/blob/dev/implementation_tracker.md) | Tranche 1–4 status and QA gates |

---

## Links

| | |
|---|---|
| **Website** | [https://www.condensate.io](https://www.condensate.io) |
| **Condensate Core** | [https://github.com/condensate-io/core](https://github.com/condensate-io/core) |
| **Qdrant (TurboQuant fork)** | [https://github.com/condensate-io/qdrant](https://github.com/condensate-io/qdrant) |
| **Verified Agentic Development** | [https://github.com/condensate-io/verified-agentic-development](https://github.com/condensate-io/verified-agentic-development) |
| **Core Wiki** | [https://github.com/condensate-io/core/wiki](https://github.com/condensate-io/core/wiki) |
| **LinkedIn** | [https://www.linkedin.com/company/condensate-io/](https://www.linkedin.com/company/condensate-io/) |
| **License** | Apache 2.0 |

---

<div align="center">

**Standardizing the brain, the retrieval layer, and the governance loop of AI agents.**

🇦🇺 Built in Melbourne, Australia · Open source · Apache 2.0

</div>
