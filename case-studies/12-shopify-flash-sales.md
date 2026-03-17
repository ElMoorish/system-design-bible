# Case Study 12: Shopify - Flash Sales at the Edge

## The Problem
Shopify powers over 1 million merchants. Their biggest challenge is the "Flash Sale"—a celebrity like Kylie Jenner or a massive brand like MrBeast drops a product, and millions of users hit the "Buy" button at the exact same second. A naive architecture would crash under this "Thundering Herd" of checkouts, leading to lost revenue and merchant distrust.

## The Solution: Scriptable Load Balancing & Queuing
Shopify rearchitected their checkout to protect the core commerce engine using edge logic and chronological queuing.

### Key Architectural Pillars
- **Lua-scripted Nginx**: They use custom Lua scripts inside their Nginx load balancers to perform "First-line Defense." If incoming traffic exceeds a certain threshold, the load balancer instantly moves users into a "Virtual Waiting Room."
- **Chronological Queuing**: Instead of crashing the DB with millions of writes, the system places users in a fair, order-preserving queue. Only a fixed number of users are allowed to enter the "Checkout" flow at a time.
- **Pod-based Isolation**: Merchants are grouped into "Pods." If one merchant's flash sale goes viral, its traffic is isolated to its specific pod, ensuring that other merchants on the platform are unaffected.

## Why it matters in 2026
Shopify's strategy is the definitive guide to **handling bursty, non-deterministic traffic**. Their use of edge-based "Waiting Rooms" and pod isolation is essential for building AI applications that might experience viral growth or sudden spikes in expensive inference demand.

---
<!-- source: research brief, section 4, Case Study 12 -->
