---
title: "Blog 3: Amazon Threat Intelligence observes threat actors running cybercrime campaigns with ARTEX AI agents"
date: 2026-11-17
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

Artificial Intelligence (AI) is increasingly being used to automate tasks and improve productivity. However, the same technology can also be misused by cybercriminals to automate malicious activities and conduct attacks on a larger scale.

In November 2026, Amazon Threat Intelligence reported that threat actors had used ARTEX, an open-source agentic AI penetration testing framework, to organize cybercrime campaigns. Through Amazon's MadPot threat detection network, security researchers observed records from AI agents involved in credential theft and attempts to bypass identity verification systems.

**Key points to know:**

- ARTEX is an open-source agentic AI framework that can coordinate multiple AI agents to perform security-related tasks.
- Amazon MadPot uses globally distributed decoy sensors to observe suspicious activity and collect threat intelligence.
- Attackers used AI agents to search for exposed credentials and API keys that provide access to AI models and cloud services.
- Another campaign attempted to bypass Know Your Customer (KYC) verification at cryptocurrency exchanges using real-time deepfakes.
- ARTEX agents shared information through a persistent knowledge graph, allowing different agents to continue tasks performed by others.
- The campaigns demonstrate how AI can increase the speed, persistence, and scale of cyberattacks.
- Organizations should protect credentials, secure AI applications, update vulnerable software, and monitor unusual API usage and service costs.

These findings highlight an important security challenge: AI agents can make cyberattacks more automated and persistent, even when attackers rely on weaknesses that already exist in traditional systems.

#### How did Amazon Threat Intelligence detect these campaigns?

Amazon used MadPot, a globally distributed network of decoy threat sensors designed to observe suspicious activities.

These sensors presented controlled services that appeared to be popular Large Language Model (LLM) inference APIs. ARTEX agents interacted with these interfaces as part of their workflows.

The captured requests contained information such as task instructions, agent histories, and reported findings. This allowed Amazon Threat Intelligence to analyze how the campaigns were organized and what the attackers were attempting to achieve.

It is important to note that the findings were based on the agents' own records. Amazon did not directly observe every activity described in those records and could not independently verify all reported outcomes.

#### How did ARTEX AI agents organize cyberattacks?

ARTEX divided tasks among several specialized agents, including:

- **Planner agents:** Organize tasks and define the next actions.
- **Worker agents:** Perform assigned activities.
- **Verification agents:** Check and evaluate reported results.
- **Compression agents:** Summarize information to maintain shared operational context.

These agents used a persistent knowledge graph as shared memory. Each agent could read information collected by others and add new findings, allowing the operation to continue without restarting from the beginning.

Amazon identified two major campaigns.

#### Campaign 1: Large-scale theft of AI credentials

In the first campaign, threat actors used AI agents to search for exposed API keys and credentials that provided access to AI models.

The agents targeted internet-exposed AI applications, API gateways, and platforms that managed credentials for multiple AI providers.

The stolen credentials could then be used to access AI services without paying for the associated usage. Cloud credentials were also investigated because they could provide access to additional resources and sensitive information.

This campaign demonstrates the risks of:

- Exposing API keys in public code repositories.
- Using default or hardcoded credentials.
- Leaving management interfaces accessible without authentication.
- Running outdated applications with known vulnerabilities.
- Failing to protect cloud credentials and application secrets.

#### Campaign 2: Attempts to bypass identity verification using deepfakes

The second campaign targeted Know Your Customer (KYC) verification systems at two cryptocurrency exchanges.

According to the agents' records, attackers attempted to use real-time deepfake videos to pass live selfie checks and manipulated identity document images to bypass document verification.

The agents also attempted to reproduce the behavior of liveness detection systems, which are designed to confirm that a real person is physically present during identity verification.

However, AWS reported that the verification provider's server-side checks rejected every deepfake attempt recorded by the agents.

This campaign highlights the increasing security challenges associated with AI-generated media and digital identity verification.

#### What can organizations learn from these campaigns?

Amazon emphasized that the attack techniques were not entirely new. The major change was the speed, persistence, and level of automation provided by AI agents.

Organizations should strengthen fundamental security practices:

- **Protect credentials:** Avoid exposing API keys, passwords, and cloud credentials in public repositories or application files.
- **Secure AI applications:** Apply appropriate access controls to AI applications, model gateways, and inference endpoints.
- **Remove default credentials:** Replace default passwords and hardcoded secrets with secure authentication mechanisms.
- **Patch vulnerabilities:** Regularly update applications and address known security weaknesses.
- **Monitor unusual activity:** Use monitoring systems to detect unexpected API usage, suspicious access patterns, and unusual increases in AI service costs.

#### Why does this matter?

The use of ARTEX demonstrates how agentic AI can change the way cybercriminals organize their operations.

Instead of relying entirely on manual activities, attackers can coordinate multiple AI agents to perform different tasks, share information, and continue operations with limited human intervention.

For Cloud Engineers, DevOps Engineers, and Security Engineers, this highlights the importance of protecting cloud credentials, securing AI infrastructure, monitoring API usage, and maintaining strong security configurations.

As AI technology continues to develop, organizations must ensure that their security practices evolve alongside it.

#### Reference and Further Reading

- Original AWS Security Blog: https://aws.amazon.com/blogs/security/amazon-threat-intelligence-observes-threat-actors-running-cybercrime-campaigns-with-artex-ai-agents/
- AWS Security Documentation: https://docs.aws.amazon.com/security/
- AWS Security Blog: https://aws.amazon.com/blogs/security/
