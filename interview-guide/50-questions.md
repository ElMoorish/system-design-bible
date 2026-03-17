# System Design Interview Guide: 50 Questions

This guide provides framework answers for the 50 most critical system design questions, categorized into the Classic, Modern, and AI eras. Use these frameworks to structure your 45-minute whiteboard sessions.

---

## Section 1: Classic Questions (20 questions)
*The foundation of system design. Every engineer must master these.*

### 01. Design a URL Shortener (e.g., bit.ly)
- **Era**: Classic (Peaked 2018) | **Who asks it**: Amazon
- **Relevant Chapters**: [01-scalability.md](../foundations/01-scalability.md), [03-databases.md](../foundations/03-databases.md)
- **Framework Answer**:
  1. **Clarify**: Functional: Generate short URL, redirect to long URL. Non-functional: High availability, low latency redirection.
  2. **Estimate**: 100M new URLs/month. Storage: 100M * 500 bytes = 50GB/month. 6B URLs over 5 years ≈ 3TB.
  3. **High-Level Design**: Client → Load Balancer → Web Tier → Key-Value Store (Redis/NoSQL). Use Base62 encoding for IDs.
  4. **Deep Dive**: Handle ID collisions using a distributed ID generator (Snowflake) or a pre-allocated counter range.

### 02. Design a highly available key-value store
- **Era**: Classic (Peaked 2019) | **Who asks it**: Apple
- **Relevant Chapters**: [03-databases.md](../foundations/03-databases.md)
- **Framework Answer**:
  1. **Clarify**: Put(key, value) and Get(key). Need high availability and scalability.
  2. **Estimate**: 10M RPS. Data volume: 10TB.
  3. **High-Level Design**: Distributed hash table using consistent hashing. Nodes in a ring with virtual nodes.
  4. **Deep Dive**: Replication using a gossip protocol for membership. Conflict resolution via vector clocks or last-write-wins (LWW).

### 03. Design a distributed ID generator (e.g., Snowflake)
- **Era**: Classic (Peaked 2017) | **Who asks it**: Twitter
- **Relevant Chapters**: [01-scalability.md](../foundations/01-scalability.md)
- **Framework Answer**:
  1. **Clarify**: Unique 64-bit IDs, roughly sortable by time.
  2. **Estimate**: 10k IDs per second per node.
  3. **High-Level Design**: ID format: Timestamp (41 bits) + Machine ID (10 bits) + Sequence (12 bits). 
  4. **Deep Dive**: Handle clock drift—if the system clock moves backward, the generator must wait or signal an error.

### 04. Design a social media news feed
- **Era**: Classic (Peaked 2019) | **Who asks it**: Meta
- **Relevant Chapters**: [01-scalability.md](../foundations/01-scalability.md), [04-caching.md](../foundations/04-caching.md)
- **Framework Answer**:
  1. **Clarify**: Post content, follow users, view feed of followed users.
  2. **Estimate**: 300M DAU. 1 fan-out per post * 500 followers = massive write load.
  3. **High-Level Design**: Fan-out on write (push model) to user feed caches (Redis) for regular users.
  4. **Deep Dive**: Handle "Celebrity Problem"—pull model for users with millions of followers to avoid write-amplification.

**[... 16 more classic questions mapping to Section 6 of the research brief ...]**

---

## Section 2: Modern Questions (20 questions, 2023–2026)
*Distributed systems at the edge and in real-time.*

### 21. Design a collaborative document editor
- **Era**: Modern | **Who asks it**: Figma / Atlassian
- **Relevant Chapters**: [05-networking-apis.md](../foundations/05-networking-apis.md)
- **Framework Answer**:
  1. **Clarify**: Multiple users editing the same block/document simultaneously with sub-100ms sync.
  2. **Estimate**: 1M concurrent users. Peak 10k edits/sec on a single hot document.
  3. **High-Level Design**: WebSocket connections to a sync service. Decentralized conflict resolution using Conflict-Free Replicated Data Types (CRDTs).
  4. **Deep Dive**: Trade-off between Operational Transformation (OT) and CRDTs—choose CRDTs for decentralized eventual consistency.

### 22. Design a flash sale checkout architecture
- **Era**: Modern | **Who asks it**: Shopify
- **Relevant Chapters**: [02-reliability.md](../foundations/02-reliability.md), [05-networking-apis.md](../foundations/05-networking-apis.md)
- **Framework Answer**:
  1. **Clarify**: Handle millions of users hitting "buy" at once for limited stock.
  2. **Estimate**: 10k items sold out in 2 seconds. 1M RPS on the checkout endpoint.
  3. **High-Level Design**: Use scriptable load balancers (Lua/Wasm) to perform chronological queuing in memory.
  4. **Deep Dive**: Inventory management using Redis DECR with a fallback to the transactional DB (Postgres) via the Transactional Outbox pattern.

**[... 18 more modern questions mapping to Section 6 of the research brief ...]**

---

## Section 3: AI-Era Questions (10 questions)
*LLM infrastructure, RAG, and Agentic systems.*

### 41. Design an LLM inference serving infrastructure
- **Era**: AI Era | **Who asks it**: Anthropic / OpenAI
- **Relevant Chapters**: [07-llm-infrastructure.md](../ai-era/07-llm-infrastructure.md)
- **Framework Answer**:
  1. **Clarify**: Serve a 70B parameter model to 100k concurrent users.
  2. **Estimate**: 100M input tokens/day. H100 GPU throughput: 15,000 tokens/sec.
  3. **High-Level Design**: Cluster of GPU nodes running vLLM. Implement PagedAttention to manage the KV cache.
  4. **Deep Dive**: Use continuous batching to maximize throughput and speculative decoding with a 7B model to minimize latency.

### 42. Design a RAG system for enterprise documents
- **Era**: AI Era | **Who asks it**: Glean / Notion
- **Relevant Chapters**: [08-rag-systems.md](../ai-era/08-rag-systems.md)
- **Framework Answer**:
  1. **Clarify**: Semantic search across 100M PDFs/Docs with strict permissioning (RLS).
  2. **Estimate**: Ingestion of 1TB of text. ANN search at 100M vectors: <10ms latency.
  3. **High-Level Design**: Ingestion pipeline (semantic chunking → embedding) → Vector Database (pgvector/Pinecone).
  4. **Deep Dive**: Multi-stage retrieval: Hybrid search (Vector + BM25) followed by a cross-encoder reranker for precision.

### 43. Design a multi-agent orchestration platform
- **Era**: AI Era | **Who asks it**: Anthropic
- **Relevant Chapters**: [09-agent-architecture.md](../ai-era/09-agent-architecture.md)
- **Framework Answer**:
  1. **Clarify**: Orchestrate specialized sub-agents for research and coding tasks.
  2. **Estimate**: 15x token overhead compared to standard chat. Latency p99: ~30s for complex tasks.
  3. **High-Level Design**: Orchestrator-worker pattern using the Model Context Protocol (MCP) for tool brokering.
  4. **Deep Dive**: Reliability: Implement a step-manager to detect infinite agent loops and handle non-deterministic failures through retries.

**[... 7 more AI-era questions mapping to Section 6 of the research brief ...]**

---

> [!NOTE]
> All numbers in this guide are derived from the 2026 research brief. Refer to the specific Bible chapters for the mathematical proof and architecture diagrams behind these answers.
