# Contributing to System Design Bible

Thank you for your interest in improving the System Design Bible. Our goal is to maintain a definitive, production-ready reference for the AI era. To ensure the highest quality, every contribution must pass through our systematic verification process.

## What belongs in this repo
We only accept content that passes all three of these "gates":
1. **Verifiable Source**: Every architectural claim or number must be grounded in a primary source (e.g., engineering blog post, academic paper, or GitHub commit).
2. **Original Annotation**: We do not accept link dumps. Every resource must have an original, 2-sentence explanation of what it is and why it matters.
3. **2026 Ready**: Content must be accurate for the 2024–2026 technology cycle. We prioritize NVMe storage patterns and GPU-inference logic over legacy magnetic-disk paradigms.

## What does NOT belong
- **Link Dumps**: Aggregations without synthesis or original descriptions.
- **AI-Generated Drafts**: Content that hasn't been verified by a human for technical accuracy.
- **Outdated Resources**: Jeff Dean numbers from 2012, traditional CDNs-only definitions, or outdated Kafka benchmarking.
- **Marketing Fluff**: Use of banned words like "revolutionary," "seamless," or "game-changing."

## Annotation Format (Mandatory)
Every external resource added to a chapter must follow this exact format:
- **[Resource Title](URL)** — Author/Organization, Year
- **What it is**: [One sentence describing the technical depth]
- **Why it matters**: [One sentence explaining exactly what an engineer gains from reading it]

**Example**:
- **[vLLM: Easy, Fast, and Cheap LLM Serving with PagedAttention](https://arxiv.org/abs/2309.06180)** — Woosuk Kwon et al., 2023
- **What it is**: The foundational research paper introducing block-based memory management for KV caches.
- **Why it matters**: An engineer needs to understand this to explain how to maximize GPU throughput in an interview or production environment.

## How to add a resource
1. Fork the repository.
2. Identify the relevant chapter (e.g., `ai-era/08-rag-systems.md`).
3. Add the resource to the **Further Reading** section using the mandatory annotation format.
4. Ensure no banned words are used in your description.
5. Submit a Pull Request with the title: `Resource: [Topic] from [Source]`.

## How to propose a new chapter
1. Open an Issue with the tag `proposal: new-chapter`.
2. Provide a 3-bullet justification for why this chapter is needed for the 2026 cycle.
3. List at least 3 primary sources that will form the basis of the content.

## PR Checklist
Before submitting, ensure:
- [ ] No banned words ("powerful", "robust", "leverage", etc.) are present.
- [ ] All Mermaid diagrams are tested and compile correctly.
- [ ] Cross-references use relative links (e.g., `../foundations/01-scalability.md`).
- [ ] Every claim has a cited source in a comment: `<!-- source: [Source Name] -->`.
