Aug 28 '26 
Look into JetStream : https://jetstream.security

Jetstream has an idea very similar our idea: 
It has 5 pillars: 
- AI Visibility — discovering shadow AI across the org
- AI Design Control — documenting how agentic systems are assembled, before approval
- Agentic Identity — binding every AI agent/tool-call/key to a responsible human owner (ABAC, least privilege)
- Runtime Governance — comparing live agent behavior against approved "blueprints" in real time, flagging drift
- AI FinOps Accountability — tracking spend by model/agent/workflow/owner

Specifically on MCP, they have a Verified MCP Catalog™ — they ingest, scan, harden, and cryptographically attest MCP servers before an agent is allowed to call them, plus tool-level filtering (e.g., allow a read tool, block a destructive one from the same server) rather than all-or-nothing server access.

Their MCP governance is about vetting before use (attestation, hardening, curated catalog) — it's a gatekeeping model. It says less about behavioral drift detection for approved servers that go bad after deployment, or about unvetted/long-tail MCP servers that will never make it into any curated catalog (which, realistically, is most of them — small internal tools, experimental servers, things individual teams stand up).
Their "Runtime Governance" pillar mentions comparing behavior against approved blueprints — but there's no public detail on the actual detection mechanism, false-positive rates, latency overhead, or evaluation methodology. That absence is your opening: a capstone can contribute a rigorous, published evaluation methodology for exactly this kind of runtime enforcement, which a commercial vendor has no incentive to publish (it's not in their interest to show you their false-positive rate).
Everything they show is enterprise/security-buyer-framed marketing — there's no visible academic-style benchmark, dataset, or reproducible methodology. That's a legitimate, citable gap: "existing commercial systems (JetStream) claim runtime governance and MCP hardening capabilities, but no public, reproducible evaluation exists for detection accuracy or performance overhead of agent action-level enforcement."

that a $34M-funded team with security veterans considers this problem serious and real — it validates the space.

