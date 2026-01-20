Why Java + Python Split?

The system is intentionally split between Java and Python to reflect real-world production architecture. Java is used for the API gateway and service orchestration because it provides strong typing, mature resilience libraries, and operational reliability for backend systems. Python is used for the AI engine because the AI ecosystem—LLMs, embeddings, vector databases, and parsing libraries—is significantly more mature and flexible in Python. This separation allows each language to be used where it is strongest while keeping AI logic isolated from core service infrastructure.

Why Static Analysis Before LLM?

Static analysis refers to examining source code without executing it to detect structural and semantic issues such as concurrency risks, exception handling problems, or performance anti-patterns. Running static analysis before invoking an LLM reduces noise, narrows the LLM’s focus to high-impact areas, and prevents the model from hallucinating issues that do not exist. The LLM is used for reasoning and recommendation, not discovery, which improves accuracy, consistency, and explainability.

Why RAG Instead of a Long Prompt?

Retrieval-Augmented Generation (RAG) is used to ground the LLM’s reasoning in explicit coding standards, architectural rules, and known anti-patterns rather than relying on general model knowledge. Instead of passing a large static prompt, relevant rules are dynamically retrieved based on the detected issues and code context. This approach reduces hallucinations, improves relevance, and allows the system’s knowledge base to evolve independently of the model.

Why Local Open-Source LLM?

A local open-source LLM is used to ensure the system is fully reproducible, cost-free, and independent of third-party APIs. This avoids rate limits, data privacy concerns, and vendor lock-in while allowing full control over inference behavior and latency. Using a local model also mirrors enterprise scenarios where sensitive code cannot be sent to external services.

Why a Deterministic Agent Instead of an Autonomous Agent?

The agent is designed as a deterministic state machine rather than an autonomous loop to maintain predictability, debuggability, and bounded execution. Each step—static analysis, retrieval, reasoning, and confidence evaluation—has explicit inputs, outputs, and stop conditions. This prevents runaway behavior, uncontrolled costs, and non-reproducible results, which are unacceptable in production backend systems.