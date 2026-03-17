# Case Study 04: Netflix - Chaos Engineering

## The Problem
By 2011, Netflix had migrated its entire infrastructure from a monolith to hundreds of microservices on AWS. This massive distribution introduced "cascading failures": if a low-priority service (like "Recommendations") failed and tied up thread pools or database connections, it could crash the entire streaming platform. They realized that in a complex system, failure is not a possibility—it is a certainty.

## The Solution: Chaos Engineering
Netflix pioneered the discipline of **Chaos Engineering**: the practice of intentionally injecting failures into production to verify that the system is resilient.

### Key Architectural Pillars
- **Chaos Monkey**: A tool that randomly terminates virtual machine instances in production. This forced engineers to design every service to handle the sudden loss of an underlying node.
- **Circuit Breakers (Hystrix)**: Netflix developed the Hystrix library to isolate points of access to remote systems. If a service becomes slow or fails, the circuit breaker "trips," instantly returning a fallback response and preventing the failure from spreading.
- **Failover-by-Design**: Netflix runs in multiple AWS regions. If a whole region fails (as happened in 2012), they can reroute global traffic to other regions within minutes.

## Why it matters in 2026
Netflix proved that **resiliency must be tested, not assumed**. In the AI era, where agents and LLMs introduce new non-deterministic failure modes, Chaos Engineering is the only way to ensure that a "hallucination" in one sub-agent doesn't crash the entire production orchestration engine.

---
<!-- source: research brief, section 3, Topic: Reliability -->
