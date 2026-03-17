# Case Study 05: Stripe - Payment Reliability

## The Problem
Stripe handles hundreds of billions of dollars in payments. For a payment gateway, the margin for error is zero. A simple database timeout or a temporary network partition could lead to "ghost charges" (charging the user but not recording it) or lost transactions. They needed an architecture that guaranteed **at-least-once** delivery of payment intents and extreme technical reliability.

## The Solution: The Transactional Outbox
Stripe's reliability is built on a "Retry-First" architecture that uses the **Transactional Outbox** pattern.

### Key Architectural Pillars
- **Idempotency Keys**: Every API call includes a unique key. If a user retries a "Charge" request because of a timeout, Stripe's backend recognizes the key and ensures the user is only charged once.
- **Transactional Outbox**: When a payment is processed, the record is written to the primary database and a corresponding "Job" is written to an "Outbox" table in the same atomic transaction. 
- **Reliable Retries**: A background worker continuously reads the Outbox and sends the payment notifications to downstream bank APIs. If a bank is down, the worker retries with exponential backoff, ensuring the notification is eventually delivered.

## Why it matters in 2026
Stripe's success demonstrates that **atomic consistency at the edge of the system** is mandatory for trust. In 2026, their patterns are the gold standard for any developer building financial AI agents or automated billing systems where transactional integrity is non-negotiable.

---
<!-- source: research brief, section 4, Case Study 5 -->
