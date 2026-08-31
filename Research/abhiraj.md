`1. MCP Security Design Considerations
NSA / CISA joint cybersecurity advisory, 2026`

### Problem ###
MCP enables AI agents to dynamically access tools, data, and other services, but its rapid adoption has outpaced its security design. Many critical controls are optional or implementation-dependent, creating opportunities for prompt/tool injection, privilege escalation, data leakage, unauthorized tool execution, session hijacking, and malicious tool behavior.

### Method ###
The NSA studied how MCP works and looked at different security problems and real-world vulnerabilities. They suggested security measures such as checking tool inputs and outputs, limiting permissions, using sandboxing, and keeping proper logs.

### Result ###
The main finding was that MCP does not provide enough security by itself. Many security protections have to be added by the developers (individuals) using MCP.
secure-by-default behavior must be enforced through implementation rigor, proper coding practices, clearer protocol specifications, and robust validation tools. 

### Limitation / Gap ###
Existing MCP security guidance identifies numerous attack surfaces and recommends defense-in-depth controls, but it does not provide an integrated, automated mechanism for detecting and preventing malicious tool behavior, poisoned outputs, prompt injection, and unauthorized actions across an MCP agent pipeline.
Security is still handled separately through different methods like authentication, permissions, monitoring, and sandboxing.

### How it relates to us ###

It supports our idea because it confirms that MCP has important security problems. We can use their suggested techniques—especially checking tool inputs/outputs, controlling permissions, detecting malicious instructions, and logging activity—in our system.

`2. Model Context Protocol (MCP): Landscape, Security Threats, and Future Research Directions
Hou, Zhao, Wang & Wang — arXiv:2503.23278, 2025`

### Problem ###
MCP makes it easy for AI to discover and use external tools, but this also creates security risks because the AI may interact with untrusted or malicious tools. Attackers can manipulate tool descriptions, inject malicious instructions, steal credentials, abuse permissions, or use multiple tools together to perform an attack.

### Method ###
The authors performed a systematic security analysis of MCP and studied its complete lifecycle: creation, deployment, operation and maintenance. They divided the lifecycle into 16 activities, identified 16 security threats from four types of attackers, and used case studies/proof-of-concept examples to demonstrate how these attacks can occur.

### Result ###
16 different MCP security threat scenarios were identified across the MCP lifecycle. The study showed that MCP has important weaknesses in authentication, authorization, monitoring, version management, tool trust and multi-step tool interactions.

### Limitation / Gap ###
The paper mainly identifies and analyzes the threats rather than providing one complete automated system that detects and prevents them. The authors highlight the need for better authentication, monitoring, trust boundaries, automated vulnerability detection, and security for multi-step tool chains.

### How it relates to us ###

Strongly supports our idea. The paper gives us the security problems and attack types that our system can target. We can build an automated security layer that monitors MCP tools, checks permissions and inputs/outputs, detects suspicious behavior, and logs or blocks malicious tool activity.