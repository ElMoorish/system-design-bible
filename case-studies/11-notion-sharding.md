# Case Study 11: Notion - Sharding & The Analytical Split

## The Problem
By 2021, Notion was suffering from "Shard-Panic." Their core Postgres database, which stores every block of text, checkbox, and page, was reaching the physical limits of single-node hardware. A simple query for a user's workspace would take seconds instead of milliseconds. They needed to move from a single monolithic instance to a horizontally sharded architecture without taking the service offline.

## The Solution: Manual Sharding & S3 Data Lake
Notion undertook a massive engineering effort to manually shard their database and separate analytical traffic from operational traffic.

### Key Architectural Pillars
- **480 Logical Shards**: They partitioned their data across 480 shards, which they distributed across 96 physical Postgres instances. This allowed them to scale writes indefinitely by simply adding more nodes.
- **The Analytical Split**: They realized that long-form "Workspace Analytics" queries were crashing their production database. They moved this historical data to an **S3-backed Data Lake** (using Snowflake/Snowpipe), keeping the primary DB fast for user actions.
- **Block-based Schema**: Their data is stored as "Blocks," allowing for extreme nesting and reuse, a schema design that prioritizes flexibility but requires massive sharding to handle the resulting join complexity.

## Why it matters in 2026
Notion's migration is a masterclass in **Operational Survival**. In 2026, their "Transactional-Analytical Split" is the standard for any data-intensive AI application that needs to perform RAG over massive historical datasets without impacting real-time user performance.

---
<!-- source: research brief, section 4, Case Study 6 -->
