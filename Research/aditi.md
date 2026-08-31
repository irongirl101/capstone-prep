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

Aug 31 '26 
AI Trust OS 

- Shadow AI describes the proliferation of LLM integrations, experimental RAG pipelines, and model-backed features deployed by engineering teams without formal security or compliance review
- Surveys consistently suggest that a significant proportion of AI systems running in enterprise production environments are unknown to the security and compliance functions nominally responsible for governing them
- The central thesis is that effective AI governance in the enterprise requires abandoning the attestation-based compliance model — in which trust is asserted by humans filling out forms, in favor of a telemetry-based governance model in which trust is demonstrated by machines collecting, validating, and continuously maintaining evidence of control effectiveness (telemetry - automated way of collecting measurements) 
- discover AI systems through observability rather than declaration, validate controls through automated probes rather than manual evidence collection [22], maintain compliance posture continuously rather than periodically [30], and synthesize trust artifacts from machine-verified assertions rather than consultant-assembled documents.



The following are the main contributions of this research.

1.
A novel telemetry-first AI governance framework that replaces manual, attestation-based compliance workflows with continuous, machine-collected control assertions mapped in real time to emerging regulatory standards, including ISO 42001 and the EU AI Act.
2.
An autonomous Shadow AI discovery mechanism that detects undocumented AI systems through live observability telemetry, shifting the epistemological basis of enterprise AI governance from organizational self-declaration to empirical machine evidence.
3.
A zero-trust telemetry boundary model for AI infrastructure auditing, in which ephemeral read-only probes validate structural configuration metadata without ingressing source code, prompt content, or payload-level personally identifiable information.
4.
An LLM-assisted documentation synthesis pipeline in which passed control assertions — never raw infrastructure payloads — are transformed into board-grade compliance narratives, operationalizing AI as both the subject of governance and an instrument of it.


Zero-Trust Security Architecture
The zero-trust security model, originally articulated by Kindervag [33] and subsequently formalized in NIST Special Publication 800-207 [43], holds that no system, user, or process should be trusted by default regardless of whether it operates inside or outside an organizational network perimeter. Trust must be continuously verified rather than assumed, and access must be scoped to the minimum privilege required for a given operation. The model emerged in response to the obsolescence of perimeter-based security architectures in cloud and mobile computing environments, where the concept of a trusted internal network no longer maps to the actual distribution of systems and data.

look into PII Scrubbing in detail -- https://mostly.ai/blog/data-scrubbing-pii-scrubbing

Shadow AI describes the organisational phenomenon in which AI systems are deployed into production environments without the knowledge or formal approval of the security, compliance, or governance functions nominally responsible for overseeing them. 


### READ MORE IN DETAIL FOR THE BELOW 
ISO 42001 establishes an AI management system standard, published in 2023, that is directly analogous to ISO 27001 for information security management [31]. It requires organisations to establish, implement, maintain, and continually improve an AI management system that covers AI system inventory, risk assessment, control implementation, objective setting, and performance evaluation. ISO 42001 is certification-eligible, meaning organisations can obtain third-party certification of their AI management system, making it an increasingly significant signal in enterprise procurement and supply chain risk assessment.

The EU AI Act [28], adopted in 2024, introduces a risk-tier classification framework for AI systems operating in or affecting the European Union. Systems are classified as unacceptable risk, high risk, limited risk, or minimal risk, with high-risk systems — including applications in hiring, credit assessment, biometric identification, and critical infrastructure management — subject to mandatory conformity assessment, technical documentation requirements, human oversight obligations, and post-market monitoring. The Act creates a direct regulatory requirement for the kind of structured AI system inventory, risk classification, and continuous monitoring that AI Trust OS is designed to automate.

SOC 2, while not AI-specific, remains the dominant trust standard in North American enterprise software procurement [4]. Its Trust Services Criteria cover availability, security, processing integrity, confidentiality, and privacy in ways that apply to AI infrastructure when interpreted by a knowledgeable auditor. The absence of AI-specific SOC 2 criteria creates both an interpretive challenge and a governance opportunity for platforms that can map AI control evidence to existing criteria in a principled and auditable way.

GDPR [27] and HIPAA [51] impose data protection obligations that become substantially more complex in the presence of AI systems. The introduction of an LLM into a data processing chain raises questions of lawful basis for processing, automated decision-making transparency under GDPR Article 22, data minimisation obligations when inputs are logged by third-party observability platforms, and cross-border transfer mechanisms when model inference occurs outside the data subject’s jurisdiction. Traditional data protection management tools were not designed for the multi-vendor, multi-hop data flows characteristic of AI inference pipelines, creating a compliance gap that AI Trust OS addresses through its Records of Processing Activities mapping architecture.


Wheres our novelty? 
MCP 
A2A/OpenClaw like 
Probably Agentic Identification 


Agentic Identification -- the idea is that AI agents themselevs can call on resources, we need to see which agent is calling what

FIn. 


