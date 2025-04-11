# 2.2  Identify AI System Trustworthy threats

## Expanding Threat Modeling Beyond Security

Modern AI systems are not only susceptible to technical security threats like prompt injection or data poisoning, but also to **ethical, social, and governance risks** that affect **trustworthiness**, **fairness**, and **compliance**.

Threat Modeling performed in the previous paragraph is not enought, we need to expand the approach.

Before we review it, let's briefly revisit key Trustworthy AI concepts defined by NIST and European Commission guidelines:

- Explainability & Transparency: AI outputs must be understandable to users.
- Fairness & Non-discrimination: AI must avoid bias and discriminatory outcomes.
- Robustness & Security: AI must withstand unintended use and adversarial attacks.
- Privacy & Data Governance: Personal data must be respected and protected.
- Human Agency & Oversight: AI systems should not undermine human autonomy or create excessive agency.
- Accountability: Clear responsibility mechanisms must exist for AI decisions.
- Based on these concepts, we carefully revise your previous identification of threats:

Back to the AI System Architecure, we need to perform a more deeply TM. Here is the result:



<p align="center">
  <img src="/Document/images/RT-Threats.png" alt="Description" width="800"/>
</p>



### Responsible AI / Trustworthy AI Additions Only

#### 🟦 AI Application (4 additions):
1. Hallucinations  
2. Toxic Content Generation  
3. Automation Bias  
4. Lack of Explainability
5. Lack of Accountability in Agent/Plugin Actions 

#### 🟪 AI Model (3 additions):
6. Bias and Discrimination  
7. Overfitting and Generalization  
8. Misalignment with Human Intent

#### 🟩 AI Infrastructure (2 additions):
9. Lack of Traceability & Auditability of Infrastructure Processes

#### 🟨 AI Data (3 additions):
10. Non-representative Training Data  
11. Toxic or Harmful Training Data  
12. Data Privacy Violations


---


The following tables provide a structured overview, facilitating clear visibility for identifying, managing, and mitigating critical Responsible AI and Trustworthy AI (RT) threats across your entire AI system architecture.

## 🟦 AI Application RT Threats 

| # | Component                       | Responsible & Trustworthy AI Threats                          |
|---|---------------------------------|----------------------------------------------------------------|
| 1 | Application & User Interaction  | Hallucinations, Toxic Content Generation, Automation Bias, Lack of Explainability |
| 2 | Agent/Plugin                    | Lack of Accountability in Agent/Plugin Actions                 |

---

## 🟪 AI Model RT Threats 

| # | Component                       | Responsible & Trustworthy AI Threats                          |
|---|---------------------------------|----------------------------------------------------------------|
| 3 | Model (Inference & Training)    | Bias and Discrimination, Overfitting and Generalization, Misalignment with Human Intent |

---

## 🟩 AI Infrastructure RT Threats 

| # | Component                                         | Responsible & Trustworthy AI Threats                          |
|---|---------------------------------------------------|----------------------------------------------------------------|
| 4 | Infrastructure (Storage, Serving, Frameworks, Training & Evaluation) | Lack of Traceability & Auditability of Infrastructure Processes |

---

## 🟨 AI Data RT Threats 

| # | Component                                | Responsible & Trustworthy AI Threats                          |
|---|------------------------------------------|----------------------------------------------------------------|
| 5 | Data (Sources, Processing, Storage)      | Non-representative Training Data, Toxic or Harmful Training Data, Data Privacy Violations |

---



## Four Pillars of AI Testing

### 1. **AI Application Testing**
- **Scope**: Front-end UX, APIs, agents/plugins, user-AI interactions
- **Threats**:
  - Prompt injection (LLM01)
  - Output handling (LLM05)
  - Excessive agency (LLM06)
  - Misinformation (LLM09)
  - Automation bias
  - Hallucinations
  - Toxic content
  - Explainability gaps
- **Testing Focus**:
  - Behavior consistency
  - Ethical content validation
  - User interface abuse (e.g., phishing via AI)
  - Interpretability & transparency evaluation

---

### 2. **AI Model Testing**
- **Scope**: Model training, fine-tuning, inference behavior
- **Threats**:
  - Model & data poisoning (LLM04)
  - Inversion/inference attacks
  - Bias/discrimination
  - Model exfiltration
  - Overfitting / generalization issues
  - Explainability & fairness gaps
- **Testing Focus**:
  - Adversarial robustness
  - Fairness auditing
  - Membership inference testing
  - Alignment and behavior under edge cases

---

### 3. **AI Infrastructure Testing**
- **Scope**: Hosting, serving, orchestration, APIs, plugin permissions
- **Threats**:
  - System prompt leakage (LLM07)
  - Resource abuse (LLM10)
  - Supply chain poisoning (LLM03)
  - Unauthorized API control
  - Insecure agent capabilities
- **Testing Focus**:
  - Least privilege enforcement
  - Resource sandboxing
  - Plugin/agent boundary testing
  - Environment security (CI/CD, containers)

---

### 4. **AI Data Testing**
- **Scope**: Data collection, curation, storage, labeling, filtering
- **Threats**:
  - Data poisoning (LLM04)
  - Training data leaks
  - Toxic/unrepresentative data
  - Bias introduced during preprocessing
  - Mislabeling or filtering inconsistencies
- **Testing Focus**:
  - Dataset integrity & labeling accuracy
  - Bias and diversity analysis
  - Data provenance validation
  - Filtering robustness (toxicity, duplication)

---

## 📋 Updated Threat Table (Grouped by Testing Domain)

The following is the updated version of the four domain-specific tables with test IDs.

## 🟦 AI Application Testing

| Test ID       | Threat Name                       | Source                  | Link                                                                                      | Test Name                         |
|---------------|-----------------------------------|-------------------------|-------------------------------------------------------------------------------------------|----------------------------------------------|
| AITG-APP-01   | Prompt Injection                  | OWASP Top 10 LLM 2025   | [LLM01](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)                         | Testing for Prompt Injection                |
| AITG-APP-02   | Indirect Prompt Injection         | OWASP Top 10 LLM 2025   | [LLM01](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)                         | Testing for Indirect Prompt Injection        |
| AITG-APP-03   | Sensitive Information Disclosure          | OWASP Top 10 LLM 2025   | [LLM02](https://genai.owasp.org/llmrisk/llm02-sensitive-information-disclosure/)         | Testing for Sensitive Data Leak             |
| AITG-APP-04   | Leak Sensitive Input Data         | OWASP Top 10 LLM 2025   | [LLM02](https://genai.owasp.org/llmrisk/llm02-sensitive-information-disclosure/)         | Testing for Input Leakage                   |
| AITG-APP-05   | Improper Output Handling          | OWASP Top 10 LLM 2025   | [LLM05](https://genai.owasp.org/llmrisk/llm05-improper-output-handling/)                 | Testing for Unsafe Outputs                  |
| AITG-APP-06   | Excessive Agency                  | OWASP Top 10 LLM 2025   | [LLM06](https://genai.owasp.org/llmrisk/llm06-excessive-agency/)                         | Testing for Agentic Behavior Limits         |
| AITG-APP-07   | System Prompt Leakage             | OWASP Top 10 LLM 2025   | [LLM07](https://genai.owasp.org/llmrisk/llm07-system-prompt-leakage/)                    | Testing for Prompt Disclosure               |
| AITG-APP-08   | Vector & Embedding Weaknesses     | OWASP Top 10 LLM 2025   | [LLM08](https://genai.owasp.org/llmrisk/llm08-vector-and-embedding-weaknesses/)          | Testing for Embedding Manipulation          |
| AITG-APP-09 | Model Theft Through Use | OWASP AI Exchange | [link](https://owaspai.org/docs/2_threats_through_use/#23-model-reversal) | Testing for Model Extraction |
| AITG-APP-10   | Misinformation                    | OWASP Top 10 LLM 2025 - Responsible AI   | [LLM09](https://genai.owasp.org/llmrisk/llm09-misinformation/)                           | Testing for Harmful Content Bias            |
| AITG-APP-11   | Hallucinations                    | Trustworthy AI          | —                                                                                         | Testing for Hallucinations                  |
| AITG-APP-12   | Toxic Content Generation          | Responsible AI          | —                                                                                         | Testing for Toxic Output                    |
| AITG-APP-13   | Automation Bias                   | Responsible AI          | —                                                                                         | Testing for Over-Reliance on AI             |
| AITG-APP-14   | Lack of Explainability            | Responsible AI          | —                                                                                         | Testing for Explainability and Interpretability |


---

## 🟪 AI Model Testing

| Test ID       | Threat Name                       | Source                  | Link                                                                                      | Test Name                         |
|---------------|-----------------------------------|-------------------------|-------------------------------------------------------------------------------------------|----------------------------------------------|
| AITG-MOD-01   | Adversarial Input (Evasion)       | OWASP AI Exchange       | [Threat 2.1](https://owaspai.org/docs/2_threats_through_use/#21-adversarial-input-evasion) | Testing for Evasion Attacks                 |
| AITG-MOD-02   | Runtime Model Poisoning           | OWASP Top 10 LLM 2025   | [LLM04](https://genai.owasp.org/llmrisk/llm04-data-and-model-poisoning/)                 | Testing for Runtime Model Poisoning         |
| AITG-MOD-03   | Model Poisoning                   | OWASP Top 10 LLM 2025   | [LLM04](https://genai.owasp.org/llmrisk/llm04-data-and-model-poisoning/)                 | Testing for Poisoned Training Sets          |
| AITG-MOD-04   | Fine-tuning Poisoning             | OWASP Top 10 LLM 2025   | [LLM04](https://genai.owasp.org/llmrisk/llm04-data-and-model-poisoning/)                 | Testing for Fine-tuning Poisoning           |
| AITG-MOD-05   | Membership Inference              | OWASP AI Exchange       | [Threat 2.4](https://owaspai.org/docs/2_threats_through_use/#24-training-set-membership-inference) | Testing for Membership Inference            |
| AITG-MOD-06   | Model Inversion                   | OWASP AI Exchange       | [Threat 2.4](https://owaspai.org/docs/2_threats_through_use/#24-training-set-membership-inference) | Testing for Inversion Attacks               |
| AITG-MOD-07   | Overfitting / Generalization      | Trustworthy AI          | —                                                                                         | Testing for Robustness to New Data          |
| AITG-MOD-08   | Misalignment with Human Intent    | Trustworthy AI          | —                                                                                         | Testing for Goal Alignment                  |

---

## 🟩 AI Infrastructure Testing

| Test ID       | Threat Name                       | Source                  | Link                                                                                      | Test Name                         |
|---------------|-----------------------------------|-------------------------|-------------------------------------------------------------------------------------------|----------------------------------------------|
| AITG-INF-01   | Supply Chain Model Poisoning      | OWASP Top 10 LLM 2025   | [LLM03](https://genai.owasp.org/llmrisk/llm03-supply-chain/)                              | Testing for Supply Chain Tampering           |
| AITG-INF-02   | Denial of Service (Unbounded)     | OWASP Top 10 LLM 2025   | [LLM10](https://genai.owasp.org/llmrisk/llm10-unbounded-consumption/)                     | Testing for Resource Exhaustion              |
| AITG-INF-03   | Insecure Plugin/Agent Integration | Trustworthy AI          | —                                                                                         | Testing for Plugin Boundary Violations       |
| AITG-INF-04   | Privilege Escalation via Agentic Systems | Responsible AI    | —                                                                                         | Testing for Capability Misuse                |
| AITG-INF-05 | Data Poisoning during Fine-tuning | OWASP Top 10 LLM 2025 | [LLM04](https://genai.owasp.org/llmrisk/llm042025-data-and-model-poisoning/) | Testing for Fine-tuning Poisoning |
| AITG-INF-06   | Dev-Time Model Theft              | OWASP AI Exchange       | [Threat 2.2](https://owaspai.org/docs/2_threats_through_use/#22-model-exfiltration)       | Testing for Dev-Time Model Theft             |
---

## 🟨 AI Data Testing

| Test ID       | Threat Name                       | Source                  | Link                                                                                      | Test Name                         |
|---------------|-----------------------------------|-------------------------|-------------------------------------------------------------------------------------------|----------------------------------------------|
| AITG-DAT-01   | Training Data Leakage             | OWASP AI Exchange       | [Threat 2.5](https://owaspai.org/docs/2_threats_through_use/#25-training-data-leakage)    | Testing for Training Data Exposure           |
| AITG-DAT-02   | Runtime Model Theft               | OWASP AI Exchange       | [Threat 2.2](https://owaspai.org/docs/2_threats_through_use/#22-model-exfiltration)       | Testing for Runtime Exfiltration             |
| AITG-DAT-03   | Non-representative Data           | Responsible AI          | —                                                                                         | Testing for Dataset Diversity & Coverage     |
| AITG-DAT-04   | Toxic Training Data               | Responsible AI          | —                                                                                         | Testing for Harmful Content in Training Data |
| AITG-DAT-05   | Data Privacy Violations           | Trustworthy AI          | —                                                                                         | Testing for Data Minimization & Consent      |

---
NEXT:
---
NEXT:
3. [AI Testing Guide Framework](3.AITG-Framework.md)

[Table of Contents](/Document/README.md)
