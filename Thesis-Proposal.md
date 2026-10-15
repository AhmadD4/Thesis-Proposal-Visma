# Master's Thesis Project Description

See the [writing guide](master-thesis-proposal-guide.md) for what makes a good project description.

## Administrative

- **Student(s):** [Mohanad Al-Falah and Ahmad Debsouzeit]
- **Contact:** [am.debsouzeit@stud.uis.no and mn.al-falah@stud.uis.no]
- **Program:** [Computer Science]
- **Project period:** [Spring 2027]
- **Supervisor(s):** [TBD]
- **External partner:** [Sticos AS (Visma Subsidiary)/ Rune Pedersen]

## Research Question

> How effectively can non-autoregressive decision models evaluate financial transactions for anomaly detection, categorization, and audit risk compared to cloud LLMs and classical rule engines?

## Background and Motivation
Visma processes large volumes of sensitive financial and accounting data across multiple jurisdictions, including purchase invoices, salary records, expense claims, and sales logs.

Automated audit mechanisms have traditionally relied either on rigid rule engines or, more recently, Large Language Models (LLMs). While LLMs excel at general reasoning, they suffer from high inference latency, substantial token costs, potential hallucinations, and strict data privacy constraints when transmitting raw transaction data to third-party cloud APIs.

Decision models (such as open-weight models like Laya or managed services like Jev) present a targeted alternative to generative LLMs. Instead of generating natural language text token-by-token, these non-autoregressive models perform a single forward pass over input context to produce structured choices, ordinal scores, or boolean probabilities with built-in epistemic confidence.

Evaluating open-weight decision models—perhaps hosted directly within Visma's private infrastructure or on-premise environments—presents a high-value research opportunity.

This architecture offers:

Strict Data Governance: Full compliance with financial privacy and GDPR regulations by keeping transaction evaluation entirely inside local parameters (if run locally).

Ultra-Low Latency Triage: Millisecond-level single-pass evaluation capable of processing high-volume transaction feeds.

Calibrated Decision Gates: Leveraging calibrated probability distributions (e.g., via Reinforcement Learning for Calibrated Decisions) to form a "System 1" fast filter. High-confidence routine cases pass automatically, while ambiguous cases are escalated to human auditors or specialized "System 2" LLM reasoning components.

## Evaluation
The prototype will be evaluated using anonymized financial transaction and audit datasets provided by Visma across four primary dimensions:

Predictive Accuracy & Quality: Precision, Recall, F1-score, and ROC-AUC on identifying accounting errors, suspicious patterns, or tax misclassifications.

Calibration Quality: Expected Calibration Error (ECE) and Brier scores to measure how reliably the model's output probabilities align with true risk frequencies.

Computational Footprint: Single-pass latency (p50/p99 in milliseconds), throughput (transactions/sec), and memory footprint when running on local hardware/GPU instances.

Generalization: Performance comparison between zero-shot base models and domain-specialized checkpoints across different accounting domains.

The decision models will be benchmarked against traditional rule-based classifiers and small generative LLMs using structured output.
## Scope

- **Core work:** The project will design, specialize, and benchmark a decision model framework for automated accounting transaction triage and risk scoring.

  The proposed architecture will investigate:

  1. **Model Fine-Tuning & Specialization**  
     Adapting base open-weight decision architectures (e.g., Laya / ModernBERT-based decision heads) on Visma's accounting transaction schemas and historical audit label sets.

  2. **Confidence Calibration & Escalation Thresholds**  
     Fitting temperature parameters and probability boundaries on transaction risk questions (e.g., yes/no suspicious flags, ordinal urgency scores, or tax categorization choices) to ensure decision probabilities accurately reflect real-world error rates.

  3. **Comparative Evaluation**  
     Benchmarking local decision models against traditional rule-based classifiers and small generative LLMs using structured output.

- **Optional work:** Further investigation of a System 1 / System 2 architecture where high-confidence cases are handled directly by decision models while uncertain cases are escalated to human auditors or larger LLM-based reasoning components.

- **Alternatives:** If fine-tuning or local deployment of a selected decision model is not feasible, the project can evaluate available managed decision models and compare them with locally deployable classification models, rule-based systems, and generative LLM baselines.
## References

Jev – System One / decision model example: https://levelup.gitconnected.com/jev-clearly-explained-3203d6d48de3

Additional academic literature and model documentation will be added as the technical approach is refined.
