

# 2. Threat Modeling for AI Systems

## What is Threat Modeling?

Threat modeling is a structured process for identifying, quantifying, and addressing security threats to a system. It allows developers, architects, and security professionals to proactively assess how their system could be attacked and to design appropriate defenses early in the development lifecycle.

In the context of AI systems, threat modeling helps uncover novel and evolving risks—ranging from prompt injection to model extraction—that stem from the unique properties of machine learning and generative AI technologies.

---

## Objectives

- Understand the **attack surface** of AI/ML systems
- Apply systematic methodologies to identify the threats. The following methodologies are applied to perfom the threat modeling on the AI System Architecture.

*Threat Modeling: Designing for Security*  
**Author:** Adam Shostack  
**URL:** [https://www.shostack.org/ThreatModeling](https://www.shostack.org/ThreatModeling)  
**Publisher:** Wiley, 2014  
**ISBN:** 978-1118809990  

> One of the most widely referenced books on structured threat modeling methodologies, especially in software and system design.

---

*Risk Centric Threat Modeling: Process for Attack Simulation and Threat Analysis*  
**Authors:** Tony UcedaVélez and Marco M. Morana  
**URL:** [https://www.wiley.com/en-us/Risk+Centric+Threat+Modeling%3A+Process+for+Attack+Simulation+and+Threat+Analysis-p-9781118810040](https://www.wiley.com/en-us/Risk+Centric+Threat+Modeling%3A+Process+for+Attack+Simulation+and+Threat+Analysis-p-9781118810040)  
**Publisher:** Wiley, 2015  
**ISBN:** 978-1118810040  

> This book introduces the **PASTA** (Process for Attack Simulation and Threat Analysis) methodology, which is risk-driven and highly applicable to modern AI systems and application environments.

## AI System Architecture

We base our analysis on the Google Secure AI Framework (SAIF), a public model for securing AI systems at scale.

🔗 [Google Secure AI Framework (SAIF) Architecture Map](https://saif.google/secure-ai-framework/saif-map)



<p align="center">
  <img src="/Document/images/AISystemArchitecture.png" alt="Description" width="800"/>
</p>



## AI System Architecture Threat Modeling

This threat model analyzes the provided AI System Architecture. We've structured our approach around the Adam Shostack threat modeling methodology, using his approach as basis, contestualizing for our scope:

1. **What are we building?** (Architectural Decomposition)
2. **What can go wrong?** (Threat Identification)
3. **What are we doing about it?** (Mitigations, not in scope)
4. **Did we do a good job?** (Validation and Review)

---

## Architectural Decomposition

Based on the provided AI system architecture, we identify these key components:


<p align="center">
  <img src="/Document/images/AI-System-Architecture-TM.png" alt="Description" width="800"/>
</p>



### **Application Layer**
(1) User input
(2) User output
(3) User Interface and interaction (Application)
(4) Agents/Plugins (Autonomous decision-making entities)
(5) External sources for Agents interactions

### **Model Layer**
(6) Input Handling
(7) Output Handling
(8) Model Usage (inference)

### **Infrastructure Layer**
(9) Model Storage Infrastructure
(10) Model Serving Infrastructure
(11) Model Evaluation
(12) Model Training & Tuning
(13) Model Frameworks and Code
(14) Data Storage Infrastructure

### **Data Layer**
(15) Training Data
(16) Data Filtering and Processing
(17) Data Sources
(18) External Data Sources (third-party providers)


---

# Comprehensive AI System Threat Model

The AI system architecture provided has been decomposed into components and communication channels (trusted boundaries). The threats to each are carefully identified according to the CIA (Confidentiality, Integrity, Availability) triad.

## Threat Analysis (CIA)
We did analyze each component of the architecture from a CIA point of view.

- **Confidentiality:**
  - MITM attacks on all communications
  - Unauthorized data interception across input/output, external sources
  - Exposure of sensitive or proprietary model communications

- **Integrity:**
  - Data injection, modification, and replay attacks on communication channels
  - Spoofing attacks against APIs and plugin communications
  - Injection of adversarial inputs or malicious payloads through communication channels

- **Availability:**
  - Resource exhaustion attacks on endpoints, infrastructure overload via communication flooding
  - Downtime and disruption caused by external dependency failures
  - Latency attacks, slow-loris style DoS on model serving endpoints
 
  The following are the identified threats.

---

## Identified CIA Threats 

Here are the four threat tables aligned with our AI system architecture. Each table represents one of your defined layers, displaying each component with their corresponding threats identified during the threat modeling exercise. 

---

## 🟦 Application Layer Threats

| # | Component | Threats (CIA) |
|---|-----------|---------------|
| 1 | **User Input** | Prompt Injection (Integrity), Sensitive data disclosure (Confidentiality), Input-based DoS (Availability) |
| 2 | **User Output** | Unauthorized data exposure (Confidentiality), Output manipulation (Integrity), Output flooding (Availability) |
| 3 | **User Interface and Interaction** | Credential leakage (Confidentiality), UI Spoofing, Parameter tampering (Integrity), UI DoS (Availability) |
| 4 | **Agents/Plugins** | Privilege escalation (Confidentiality), Plugin instruction tampering (Integrity), Automation loops (Availability) |
| 5 | **External Sources for Agent Interactions** | MITM interception (Confidentiality), Replay attacks, Data tampering (Integrity), External downtime, API DoS (Availability) |

---

## 🟪 Model Layer Threats

| # | Component | Threats (CIA) |
|---|-----------|---------------|
| 6 | **Input Handling** | Input mishandling leaks (Confidentiality), Evasion attacks, input validation flaws (Integrity), Resource exhaustion (Availability) |
| 7 | **Output Handling** | Leakage of inference results (Confidentiality), Unsafe or biased output generation (Integrity), Excessive latency (Availability) |
| 8 | **Model Usage (Inference)** | Inference interception (Confidentiality), MITM inference manipulation (Integrity), Endpoint flooding, slow-loris attacks (Availability) |

---

## 🟩 Infrastructure Layer Threats

| # | Component | Threats (CIA) |
|---|-----------|---------------|
| 9 | **Model Storage Infrastructure** | Unauthorized model access (Confidentiality), Unauthorized modification (Integrity), Data loss, ransomware (Availability) |
| 10 | **Model Serving Infrastructure** | Inference result interception (Confidentiality), Malicious inference code injection (Integrity), DoS, server overload (Availability) |
| 11 | **Model Evaluation Infrastructure** | Evaluation data exposure (Confidentiality), Manipulated evaluation results (Integrity), Resource starvation (Availability) |
| 12 | **Model Training & Tuning Infrastructure** | Training data leakage, intellectual property exposure (Confidentiality), Model poisoning, backdoors (Integrity), Training disruption (Availability) |
| 13 | **Model Frameworks and Code** | Vulnerable code exploitation (Confidentiality), Supply chain attacks, dependency confusion (Integrity), Infrastructure crashes (Availability) |
| 14 | **Data Storage Infrastructure** | Unauthorized data access, breaches (Confidentiality), Data modification or deletion (Integrity), Disk flooding, ransomware attacks (Availability) |

---

## 🟨 Data Layer Threats

| # | Component | Threats (CIA) |
|---|-----------|---------------|
| 15 | **Training Data** | Data breaches, unauthorized access (Confidentiality), Data poisoning, corruption (Integrity), Data destruction, excessive processing (Availability) |
| 16 | **Data Filtering and Processing** | Sensitive data leaks during processing (Confidentiality), Filter bypass, malicious data insertion (Integrity), Resource-heavy filtering causing DoS (Availability) |
| 17 | **Data Sources** | MITM interception during transfer (Confidentiality), Data tampering in transit (Integrity), Data source downtime or throttling (Availability) |
| 18 | **External Data Sources** | Third-party breaches (Confidentiality), External data manipulation (Integrity), Downtime, rate-limiting (Availability) |

These threats list include some controls we are not able to cover in this guide, that  **does not attempt to replace or duplicate** existing foundational security testing methodologies. Instead, it complements them by focusing on **AI-specific threats**. For general system and application security, we recommend the following best-in-class references:

- **Network Security**  
  🔗 *NIST SP 800-115: Technical Guide to Information Security Testing and Assessment*  
  [https://csrc.nist.gov/publications/detail/sp/800-115/final](https://csrc.nist.gov/publications/detail/sp/800-115/final)

- **Infrastructure Security**  
  🔗 *OSSTMM – Open Source Security Testing Methodology Manual*  
  [https://www.isecom.org/OSSTMM.3.pdf](https://www.isecom.org/OSSTMM.3.pdf)

- **Web Application Security**  
  🔗 *OWASP Web Security Testing Guide (WSTG)*  
  [https://owasp.org/www-project-web-security-testing-guide/](https://owasp.org/www-project-web-security-testing-guide/)

---

In the next sections we will analyze:
- the OWASP Threats coming from OWASP AI Exchange and OWASP GenAI projects in order to review our approach adding possible new security threats
- the AI System architecture from a Trustworthy and Responsible AI point of view in order to add specific AI developement threats not security related.

## References

- **OWASP Top 10 for LLM Applications**  
  [https://genai.owasp.org/llmrisk/](https://genai.owasp.org/llmrisk/)
  
- **OWASP AI Exchange Threats Through Use**  
  [https://owaspai.org/docs/2_threats_through_use/](https://owaspai.org/docs/2_threats_through_use/)

- **"Threat Modeling: Designing for Security"**  
  Adam Shostack  
  [https://www.shostack.org/ThreatModeling](https://www.shostack.org/ThreatModeling)

- **“Risk-Centric Threat Modeling” (PASTA Methodology)**  
  Tony UcedaVélez, Marco Morana  
  [https://www.wiley.com/en-us/Risk+Centric+Threat+Modeling](https://www.wiley.com/en-us/Risk+Centric+Threat+Modeling%3A+Process+for+Attack+Simulation+and+Threat+Analysis-p-9781118810040)



---
NEXT:
2.1 [Identify AI Security Threats](2.1IdentifyAIThreats.md)

[Table of Contents](/Document/README.md)
