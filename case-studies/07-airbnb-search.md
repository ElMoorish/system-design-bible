# Case Study 07: Airbnb - Search & Discovery

## The Problem
Airbnb's core product is search. Unlike Google, which can serve slightly stale results, Airbnb must ensure that when a user searches for a home in Paris, they only see homes that are actually available for their specific dates. This requires merging static listing data (photos, descriptions) with highly dynamic availability and pricing data across millions of homes globally.

## The Solution: Search Infrastructure
Airbnb built a multi-tier search architecture that separates the heavy "Indexing" of listings from the real-time "Filtering" of availability.

### Key Architectural Pillars
- **Distributed Indexing (Elasticsearch)**: Listings are stored in Elasticsearch clusters, optimized for complex geographic and attribute-based queries.
- **Availability Service**: A dedicated, high-performance in-memory service tracks every single reservation. When a search query hits the backend, it simultaneously queries the availability service to filter out booked homes before the user sees them.
- **Machine Learning Ranking**: Every search result is ranked in real-time by a model that considers past user preferences, listing quality, and pricing.

## Why it matters in 2026
Airbnb's work on **Hybrid Search**—merging structured data with high-speed dynamic filters—is the blueprint for production **RAG systems**. Just as Airbnb filters homes by availability, a production RAG system filters document chunks by user permissions and factual relevance, ensuring the LLM only "sees" what it is authorized to use.

---
<!-- source: research brief, section 4, Case Study 7 -->
