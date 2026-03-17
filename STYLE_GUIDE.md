# Style Guide: System Design Bible

This guide defines the standards for voice, tone, and formatting. Consistency across all chapters ensures that the repository remains a premium, professional resource.

## 1. Voice and Tone
- **Senior Engineer to Peer**: Write like you are explaining a production system to a colleague. Avoid being overly academic or parental.
- **Second Person ("You")**: Address the reader directly.
- **Present Tense, Active Voice**: "The load balancer routes traffic" instead of "The traffic will be routed by the load balancer."
- **Concrete Over Abstract**: Numbers and specific constraints beat vague adjectives.

## 2. Banned Words
To maintain an objective and technical tone, the following marketing-speak and vague words are strictly banned:
- powerful, robust, leverage, utilize
- best practices, seamless, game-changing
- revolutionary, state-of-the-art, cutting-edge
- amazing, comprehensive, holistic
- significantly, considerably (without a accompanying number)

## 3. Core Trade-offs Format
Every chapter must include a decision table with exactly three columns:

| When to use this | When NOT to use this | Trade-off you accept |
|---|---|---|
| [Concrete condition] | [Concrete condition] | [Specific architectural cost] |

## 4. Failure Modes Format
Every chapter must include a failure modes table with three columns:

| Symptom you see | Root cause | Specific fix |
|---|---|---|
| [Observable metric/error] | [Technical mechanism failing] | [Actionable engineering fix] |

## 5. Diagram Rules
- **Mermaid Required**: Use Mermaid syntax for high accessibility and styling consistency.
- **Maximum 12 Nodes**: If your diagram is more complex, split it into two or simplify the abstraction.
- **Labeled Nodes**: Every box or arrow must have a technical label.
- **Orientation**: Use `flowchart TD` (Top Down) or `sequenceDiagram` depending on what best illustrates the flow.

## 6. Numbers Policy
- **2026 Ready**: Never use numbers older than 3 years.
- **NVMe Focus**: Use latency numbers that reflect SSD and modern network fabric, not magnetic disks.
- **Citations Required**: Every number must be followed by a comment citing the research brief or source.
  - `Throughput: 15k tokens/sec <!-- source: research brief, section 5 -->`

## 7. What "Maintained" Means
A resource is considered "stale" if its primarily cited source was last updated > 3 years ago and it doesn't reflect a foundational, unchanging law (like Little's Law). We actively prune links that point to dead blogs or deprecated tools.
