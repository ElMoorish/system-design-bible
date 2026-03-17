# Case Study 02: Amazon - The Dynamo Architecture

## The Problem
In the early 2000s, Amazon realized that traditional relational databases could not scale to meet the reliability requirements of their global e-commerce platform. Even a few seconds of downtime on the "Shopping Cart" or "Checkout" service resulted in millions of dollars in lost revenue. They needed a data store that was "Always On," even if it meant sacrificing some consistency (the AP in the CAP theorem).

## The Solution: Dynamo
Amazon published the **Dynamo** paper in 2007, defining a highly available, decentralized key-value store. This architecture avoided any single point of failure by using a completely peer-to-peer design.

### Key Architectural Pillars
- **Consistent Hashing**: Data is distributed across a ring of nodes. Virtual nodes ensure that load remains balanced even when physical nodes are added or removed.
- **Sloppy Quorum & Hinted Handoff**: To ensure high availability, Dynamo allows writes to be accepted even if the primary nodes are unavailable. The data is temporarily stored on a secondary node and handed back when the primary returns.
- **Varying Consistency (W+R > N)**: Developers can tune the system. For a shopping cart, they might set N=3, W=1, R=1 for maximum availability, resolving conflicts (like "last write wins") at the application layer.

## Why it matters in 2026
Dynamo birthed the NoSQL movement. Modern databases like **Cassandra** and **ScyllaDB** (used by Discord) are direct descendants of this architecture. In the AI era, Dynamo's peer-to-peer scaling principles are essential for managing the massive, distributed metadata indexes used by global agent networks.

---
<!-- source: research brief, section 4, Case Study 2 -->
