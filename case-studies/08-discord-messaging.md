# Case Study 08: Discord - Scaling to Trillions of Messages

## The Problem
By 2022, Discord had trillions of messages across millions of servers. Their original storage engine, MongoDB, could not keep up with the massive write volume and complex partitioning required to serve a global user base. They were facing "latency spikes" and "node maintenance" nightmares as the size of their indexes outstripped the capacity of their disks.

## The Solution: ScyllaDB & Virtual Nodes
Discord migrated their entire message storage from MongoDB to **ScyllaDB**, a high-performance C++ rewrite of Cassandra.

### Key Architectural Pillars
- **Shard-per-Core Architecture**: ScyllaDB utilizes a shared-nothing architecture where each CPU core manages its own memory and disk I/O, eliminating lock contention and maximizing modern NVMe hardware.
- **Log-Structured Merge-Trees (LSM)**: This storage engine is optimized for high-write volume. Messages are written to an in-memory buffer and later "compacted" into immutable files on disk, ensuring that writes are always fast.
- **Bucket-based Partitioning**: Discord partitions messages by `(channel_id, bucket_id)`. This prevents any single channel from becoming a "hot partition" that could crash a database node.

## Why it matters in 2026
Discord's migration is the definitive case study on **matching storage engines to hardware**. Their use of ScyllaDB illustrates why NVMe-optimized, shared-nothing architectures are mandatory for the massive data ingestion requirements of modern AI logging and real-time messaging platforms.

---
<!-- source: research brief, section 4, Case Study 8 -->
