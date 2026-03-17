# Case Study 09: Slack - Real-time Messaging & WebSockets

## The Problem
Slack's value proposition is "Instant Collaboration." When you type a message, your teammate across the world must see it in under 100ms. In the early days, they struggled with the "Thundering Herd" problem: when a major news event happened or a large company arrived at work at 9:00 AM, millions of clients would simultaneously attempt to reconnect and fetch their state, crashing the Slack backend.

## The Solution: The Gateway Architecture
Slack developed a dedicated **Gateway** layer to manage millions of persistent user connections.

### Key Architectural Pillars
- **Edge WebSockets**: Clients maintain a long-lived WebSocket connection to a regional Gateway server. This avoids the overhead of repeated HTTP handshakes for every single message.
- **State Compression**: To handle 9:00 AM reconnection spikes, Slack doesn't send the entire world's state at once. Instead, they send a "Delta" of what changed since the user was last online.
- **Pub/Sub Routing**: When a message is posted to a channel, the backend publishes it to a regional message bus. The Gateway servers in each region "subscribe" to the channels their connected users care about and "push" the message down the WebSocket.

## Why it matters in 2026
Slack's Gateway pattern is the foundation for **AI Streaming UI**. Just as Slack pushes messages via WebSockets, modern AI apps push LLM tokens via **Server-Sent Events (SSE)**. Slack's lessons in managing persistent connections and "Lazy Loading" state are vital for building responsive, agent-driven work environments.

---
<!-- source: research brief, section 4, Case Study 9 -->
