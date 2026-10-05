# Paper 1: [Enterprise-Grade Security for the Model Context Protocol](https://arxiv.org/html/2504.08623v2)

- three components of MCP
  - **Host:** ai applications like claude, cursor
  - **Client:** intermediary between host and server
  - **Server:** gateway to allow client to interact with external services.
    1. Tools
    2. Resources
    3. Prompts

- **MAESTRO framework** to examine ai system vulnerabilities
  - basically 7 levels/layers to examine them.
  - They categorize the threats as server, client, host, tool, prompt related threats.

- **Dedicated MCP Security Zones:** Isolate MCP servers and critical components within dedicated network segments
- **Service Mesh Implementation**
- **Application-Layer Filtering Gateways**
- **End-to-End Encryption**(?? I thought this was basic)
- **Robust Tool Vetting and Onboarding**
- **Just-In-Time (JIT) Access Provisioning**

- this paper was really just about what to do instead of how to do.
- They were really on the surface the whole time but they do give **future research directions**

# Paper 2: [Studying the Security and Maintainability of MCP Servers (1899 servers)](https://arxiv.org/html/2506.13538v5)

- nearly 1/3rd of this paper was just references lol.
- **FM = foundational models** (like GPT4, llama)
- MCP’s AI-driven, non-deterministic control flow introduces new risks to sustainability, security, and maintainability, warranting closer examination. Need for MCP-specific vulnerability detection techniques.

- a universal, client-server protocol standardizing how AI applications expose tools to FMs.

- a compromised MCP server can bypass conventional security controls and leak sensitive data at scale.

- they raise three questions
  1. how frequent is the MCP ecosystem maintained.
  2. how different are the vulnerabilities from already existing ecosystems.
  3. maintainability issues.

- **5.5% MCP servers suffer from tool poisoning.**
- MCP servers also suffer with code smell just like traditional software engineering domain.
- **IaC = Infrastructure as Code**

- An MCP Server wraps the functionalities of one or more external services or data sources and exposes those in a standardized manner via the MCP protocol. It handles input validation, tool execution, and response formatting.

- An MCP Client manages the communication between the FM and one or more MCP servers.

- this paper goes very technical into how they did this study (not really relevant to us). They even use something called **LLM Jury** which I didn't really want to understand to the core. Just know that it is a method to assess unbiased.

- As MCP adoption accelerates, researchers, practitioners, and registry maintainers must invest in domain-specific security tooling, automated auditing, longitudinal tracking of vulnerability patches, and robust governance to ensure the safe and reliable evolution of FM-based software systems.
