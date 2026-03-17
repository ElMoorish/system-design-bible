# System Design Glossary: 80+ Technical Terms

A definitive reference for the terminology used in 2026 production-grade system design.

---

### A
- **ACID**: Atomicity, Consistency, Isolation, Durability. The four properties that guarantee a database transaction is processed reliably.
- **Agent-to-Agent (A2A)**: A communication protocol that standardizes how specialized AI models exchange goals and context.
- **ANN (Approximate Nearest Neighbor)**: A class of algorithms (like HNSW) used to find similar vectors in a high-dimensional space without scanning every data point.
- **API Gateway**: A server that acts as an entry point for an application, handling routing, rate limiting, and authentication.
- **Artifact**: A persistent, versioned document or asset generated during a technical workflow.
- **Asymmetric Workload**: A query where the input is small but the output/computational cost is massive (typical of LLMs).
- **At-Least-Once Delivery**: A messaging guarantee that a message will be delivered one or more times, requiring idempotency on the receiver's end.
- **Atomic Clock**: A highly precise timekeeping device used in distributed databases (like Spanner) to order transactions globally.
- **Augmentation**: The process of providing an LLM with external context (see RAG).
- **Availability**: The percentage of time a system is operational and accessible to users.

### B
- **Back-of-the-Envelope**: Quick, rough mathematical estimations used to validate an architectural path.
- **Backpressure**: A mechanism that allows a downstream service to signal to an upstream service that it is overloaded and cannot accept more requests.
- **Batching**: Grouping multiple requests or data points together to be processed in a single operation to improve throughput.
- **BM25 (Best Matching 25)**: A classic sparse retrieval ranking function used for keyword-based search.
- **Bulkhead**: A design pattern that isolates resources (thread pools, memories) to prevent a failure in one component from cascading.

### C
- **Cache-Aside**: A caching pattern where the application first checks the cache and then fetches from the DB on a miss, updating the cache afterward.
- **Cache Stampede**: A failure mode where multiple simultaneous cache misses on a hot key overwhelm the underlying data store.
- **CAP Theorem**: The principle that a distributed system can only provide two of three guarantees: Consistency, Availability, and Partition Tolerance.
- **Chaos Engineering**: Intentionally injecting failures into production to test system resiliency.
- **Circuit Breaker**: A mechanism that detects high failure rates and "trips," failing fast to protect downstream services.
- **Consensus Algorithm**: A protocol (like Raft or Paxos) that allows a cluster of nodes to agree on a single state change despite failures.
- **Consistent Hashing**: A hashing technique that distributes data across nodes such that adding or removing a node only impacts a small fraction of the data.
- **Continuous Batching**: An LLM serving optimization where new requests are added to the active batch as soon as others finish, maximizing GPU utilization.
- **CPU-Bound**: A system bottlenecked by the processor's speed, common in modern NVMe-backed databases.
- **CRDT (Conflict-Free Replicated Data Type)**: A data structure that can be updated independently and concurrently across nodes, always merging to a consistent state.
- **Cross-Encoder**: A model that re-ranks search results by deeply evaluating the query and the document simultaneously for high precision.

### D
- **DORA Metrics**: Four key metrics (Deployment Frequency, Lead Time, MTTR, Change Failure Rate) used to measure engineering team performance.
- **Distance Metric**: A mathematical measure (like Cosine Similarity or Euclidean Distance) used to calculate the similarity between two vectors.
- **Distributed Tracing**: Capturing the path of a request as it spans multiple services to identify bottlenecks and failures.

### E
- **Edge Computing**: Moving computation and data storage closer to the user to reduce latency and bandwidth consumption.
- **Embedding**: A numerical representation of a piece of data (text, image) in a high-dimensional vector space.
- **Ephemeral**: Short-lived data or infrastructure that is not intended to be persistent.
- **Even Consistency**: A consistency model where data will eventually become identical across all nodes if no new updates occur.

### F
- **Failover**: The automatic process of switching to a redundant or standby system upon the failure of the primary system.
- **Fan-out**: The process of delivering a single update to multiple destinations (common in social media news feeds).
- **Feature Store**: A centralized repo where mathematical features are stored for use in real-time ML inference.
- **FP8 (8-bit Floating Point)**: A numerical format that reduces model weight size by 50% compared to FP16, saving memory and cost.

### G
- **GitOps**: A practice where the desired state of infrastructure is defined in Git and automatically reconciled by a controller.
- **Gossip Protocol**: A peer-to-peer communication method where nodes share state with a few neighbors, eventually propagating the info to the entire cluster.
- **gRPC**: A high-performance remote procedure call (RPC) framework that uses Protobuf for efficient binary serialization.

### H
- **HNSW (Hierarchical Navigable Small World)**: A leading ANN algorithm that builds a multi-layered graph for fast, high-recall vector search.
- **Hybrid Search**: Combining vector-based semantic search with keyword-based sparse search (BM25) for maximum retrieval accuracy.

### I
- **Idempotency**: A property where an operation can be performed multiple times without changing the result beyond the initial application.
- **IDP (Internal Developer Portal)**: A self-service portal (like Backstage) that simplifies infrastructure management for developers.
- **IO-Bound**: A system bottlenecked by disk or network input/output, now less common in the era of NVMe.
- **Isolate (Wasm)**: A lightweight execution environment (like V8) that starts in milliseconds and consumes minimal RAM.
- **IVF (Inverted File)**: A vector indexing technique that clusters data into search buckets to reduce memory consumption.

### K
- **KV Cache**: Key-Value Cache. In LLMs, it stores the internal state of previous tokens to speed up the generation of the next token.

### L
- **Latency**: The time it takes for a request to travel from sender to receiver and back again.
- **Leaderless Replication**: A system (like Dynamo) where any node can accept writes, resolving conflicts later.
- **LLM-as-a-Judge**: Using a powerful LLM to evaluate the quality and accuracy of another model's output.
- **LLMOps**: The operational practices used to manage the delivery and maintenance of LLM-based applications.

### M
- **MCP (Model Context Protocol)**: An open standard for connecting AI agents to tools, data, and external APIs.
- **Microservices**: An architectural style that structures an application as a collection of small, independent services.
- **MTTR (Mean Time To Recovery)**: The average time taken to restore a service after a failure occurs.
- **Multi-tenancy**: A software architecture where a single instance of an application serves multiple customers (tenants).

### N
- **NewSQL**: A category of databases (like Spanner) that provide horizontal scale with strict ACID consistency.
- **NVMe**: Non-Volatile Memory Express. An interface for high-speed SSDs that has radically reduced disk latency.

### O
- **OIDC (OpenID Connect)**: An authentication layer built on top of OAuth 2.0 that provides identity information.
- **Orchestrator**: A central service that coordinates the actions of multiple sub-agents or microservices.

### P
- **PACELC**: An extension of the CAP theorem, emphasizing the consistency vs. latency tradeoff during normal operations.
- **PagedAttention**: An LLM memory management technique that allocates KV caches in non-contiguous blocks, reducing fragmentation.
- **Partition Tolerance**: The ability of a distributed system to continue operating despite network failures.
- **Paxos**: A classic consensus algorithm used to reach agreement across a distributed cluster.
- **Primary Source**: A verifiable, high-authority origin for technical information (e.g., engineering blog or research paper).
- **Prompt Caching**: Storing the state of a long LLM prompt to bypass redundant processing costs for subsequent queries.
- **Prompt Injection**: A security vulnerability where user input "hijacks" the LLM's system instructions.

### Q
- **Quantization**: Compressing LLM weights to lower precision (e.g., FP16 to INT4) to reduce memory and infra costs.
- **QUIC**: A UDP-based transport layer protocol used by HTTP/3 to reduce latency and handle network switching.

### R
- **RAG (Retrieval-Augmented Generation)**: Ingesting external data into an LLM's context window to ground its responses in facts.
- **Raft**: A modern consensus algorithm designed to be more understandable and implementable than Paxos.
- **Recall**: A measure of search quality; the percentage of truly relevant results found by the search engine.
- **Reranker**: A high-precision model used to re-evaluate and order the candidate results from a search query.

### S
- **Saga Pattern**: A distributed transaction pattern that uses a series of local transactions and compensating actions to maintain consistency.
- **Semantic Caching**: Caching LLM responses based on the meaning of the query rather than an exact string match.
- **Sharding**: Horizontally partitioning data across multiple database instances.
- **SLO (Service Level Objective)**: A target value for a specific service level, such as "99.9% availability."
- **SSE (Server-Sent Events)**: A unidirectional streaming protocol over HTTP, ideal for pushing LLM tokens to a UI.
- **Speculative Decoding**: Using a small "draft" model to guess future tokens and a large model to verify them, significantly increasing inference speed.

### T
- **TAO**: The Associations and Objects. Meta's distributed graph cache for the social graph.
- **Throughput**: The amount of data or number of requests a system can handle in a given period.
- **Token Bucket**: A rate-limiting algorithm that allows for bursts while maintaining a steady average request rate.
- **Transactional Outbox**: A pattern that ensures a message is only sent to a queue if the local DB transaction succeeds.
- **TrueTime**: Google's atomic-clock-based timing system used to order transactions globally in Spanner.

### V
- **Vector Database**: A database optimized for storing, indexing, and searching high-dimensional embeddings.
- **Vertical Scaling**: Adding more power (CPU, RAM) to a single machine to handle increased load.

### W
- **Wasm (WebAssembly)**: A binary instruction format that enables high-performance execution of code at near-native speeds.
- **Write-Through Cache**: A caching pattern where data is written to the cache and the database simultaneously to ensure consistency.

### Z
- **Zero Trust**: A security model that requires continuous verification of every user and device, assuming no internal trust.
