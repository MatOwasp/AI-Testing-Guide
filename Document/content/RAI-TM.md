### Expanding Threat Modeling Beyond Security

Modern AI systems are not only susceptible to technical security threats like prompt injection or data poisoning, but also to **ethical, social, and governance risks** that affect **trustworthiness**, **fairness**, and **compliance**.

Threat Modeling performed in the previous paragraph is not enoght.

 **AI-specific risks extend far beyond that**:

### Responsible AI Threats

| Category | Examples |
|---------|----------|
| **Bias & Discrimination** | Models producing unfair outputs across race, gender, language, etc. |
| **Lack of Explainability** | Opaque decisions, especially in high-stakes domains (health, finance) |
| **Hallucinations** | Generation of false or misleading facts |
| **Over-reliance on AI (Automation Bias)** | Users blindly trusting incorrect AI decisions |
| **Non-representative Training Data** | Model fails in underrepresented regions or edge cases |
| **Toxic or Harmful Content** | Outputs that promote violence, hate speech, misinformation |
| **Lack of Transparency or Auditability** | Inability to trace data lineage, model decisions, or updates |
| **Misalignment with Human Intent** | Agents taking unintended actions due to mis-specified goals |

### The Expanded Testing Approach

Back to the AI System Architecure, we need to perform a more deeply TM. Here is the result:



To address both **security** and **responsible AI risks**, we define four focused testing domains:

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

The following is the updated version of the four domain-specific tables with test IDs starting from **1** for each category (not 0).


## 🟦 AI Application Testing

| Test ID         | Threat Name                        | Source                  | Link                                                                                      | Suggested Test Name                            |
|-----------------|------------------------------------|-------------------------|-------------------------------------------------------------------------------------------|------------------------------------------------|
| AITG-APP-01     | Prompt Injection                   | OWASP Top 10 LLM 2025   | [LLM01](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)                         | Testing for Prompt Injection                   |
| AITG-APP-02     | Indirect Prompt Injection          | OWASP AI Exchange       | [Indirect Injection](https://owaspai.org/docs/2_threats_through_use/#222-indirect-prompt-injection) | Testing for Indirect Prompt Injection          |
| AITG-APP-03     | Sensitive Information Disclosure   | OWASP Top 10 LLM 2025   | [LLM02](https://genai.owasp.org/llmrisk/llm02-sensitive-information-disclosure/)         | Testing for Sensitive Information Disclosure   |
| AITG-APP-04     | Improper Output Handling           | OWASP Top 10 LLM 2025   | [LLM05](https://genai.owasp.org/llmrisk/llm05-improper-output-handling/)                 | Testing for Improper Output Handling           |
| AITG-APP-05     | Excessive Agency                   | OWASP Top 10 LLM 2025   | [LLM06](https://genai.owasp.org/llmrisk/llm06-excessive-agency/)                         | Testing for Excessive Agency                   |
| AITG-APP-06     | Misinformation Generation          | OWASP Top 10 LLM 2025   | [LLM09](https://genai.owasp.org/llmrisk/llm09-misinformation/)                           | Testing for Misinformation Generation          |
| AITG-APP-07     | Automation Bias                    | Responsible AI          | —                                                                                         | Testing for Automation Bias                    |
| AITG-APP-08     | Hallucinations                     | Responsible AI          | —                                                                                         | Testing for Hallucinations                     |
| AITG-APP-09     | Toxic Content Generation           | Responsible AI          | —                                                                                         | Testing for Toxic Content Generation           |
| AITG-APP-10     | Lack of Explainability             | Responsible AI          | —                                                                                         | Testing for Lack of Explainability             |

---

## 🟪 AI Model Testing

| Test ID         | Threat Name                        | Source                  | Link                                                                                      | Suggested Test Name                            |
|-----------------|------------------------------------|-------------------------|-------------------------------------------------------------------------------------------|------------------------------------------------|
| AITG-MOD-01     | Data and Model Poisoning           | OWASP Top 10 LLM 2025   | [LLM04](https://genai.owasp.org/llmrisk/llm04-data-and-model-poisoning/)                 | Testing for Data and Model Poisoning           |
| AITG-MOD-02     | Model Inversion & Membership Inference | OWASP AI Exchange   | [Inference](https://owaspai.org/docs/2_threats_through_use/#232-model-inversion-and-membership-inference) | Testing for Model Inversion & Membership Inference |
| AITG-MOD-03     | Model Theft via Use                | OWASP AI Exchange       | [Model Theft](https://owaspai.org/docs/2_threats_through_use/#24-model-theft-through-use) | Testing for Model Theft via Use                |
| AITG-MOD-04     | Bias and Discrimination            | Responsible AI          | —                                                                                         | Testing for Bias and Discrimination            |
| AITG-MOD-05     | Lack of Robustness                 | Trustworthy AI          | —                                                                                         | Testing for Lack of Robustness                 |
| AITG-MOD-06     | Overfitting and Generalization Issues | Trustworthy AI        | —                                                                                         | Testing for Overfitting and Generalization     |

---

## 🟩 AI Infrastructure Testing

| Test ID         | Threat Name                        | Source                  | Link                                                                                      | Suggested Test Name                            |
|-----------------|------------------------------------|-------------------------|-------------------------------------------------------------------------------------------|------------------------------------------------|
| AITG-INF-01     | Supply Chain Vulnerabilities       | OWASP Top 10 LLM 2025   | [LLM03](https://genai.owasp.org/llmrisk/llm03-supply-chain/)                              | Testing for Supply Chain Vulnerabilities       |
| AITG-INF-02     | System Prompt Leakage              | OWASP Top 10 LLM 2025   | [LLM07](https://genai.owasp.org/llmrisk/llm07-system-prompt-leakage/)                     | Testing for System Prompt Leakage              |
| AITG-INF-03     | Unbounded Resource Consumption     | OWASP Top 10 LLM 2025   | [LLM10](https://genai.owasp.org/llmrisk/llm10-unbounded-consumption/)                     | Testing for Unbounded Resource Consumption     |
| AITG-INF-04     | Insecure Plugin Design             | Trustworthy AI          | —                                                                                         | Testing for Insecure Plugin Design             |

---

## 🟨 AI Data Testing

| Test ID         | Threat Name                        | Source                  | Link                                                                                      | Suggested Test Name                            |
|-----------------|------------------------------------|-------------------------|-------------------------------------------------------------------------------------------|------------------------------------------------|
| AITG-DAT-01     | Training Data Leakage              | OWASP AI Exchange       | [Training Leakage](https://owaspai.org/docs/2_threats_through_use/#231-sensitive-data-output-from-model) | Testing for Training Data Leakage              |
| AITG-DAT-02     | Non-representative Training Data   | Responsible AI          | —                                                                                         | Testing for Non-representative Training Data   |
| AITG-DAT-03     | Toxic or Harmful Training Data     | Responsible AI          | —                                                                                         | Testing for Toxic or Harmful Training Data     |
| AITG-DAT-04     | Data Privacy Violations            | Trustworthy AI          | —                                                                                         | Testing for Data Privacy Violations            |

