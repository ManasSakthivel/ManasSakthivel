# Manas Sakthivel

**Software Engineer · AI/Systems Researcher**

B.E. Computer Science, RV College of Engineering (CGPA 8.29/10)  
Software Developer, IBM Software Labs · Prior: DigiCert

---

## Research

I investigate how complex software systems behave, how that behavior can be represented and validated, and how causal and AI-based methods can reason about behavioral changes across software transformations, legacy modernization, and distributed system failures.

**Central questions:**

- Can execution-grounded representations detect semantic changes that structural analysis misses? → [SBG](#sbg)
- Can behavioral contracts preserve semantic obligations when legacy software is modernized? → [RELIC](#relic)
- Can controlled interventions improve causal attribution of behavioral divergence in distributed systems? → [RIFT](#rift)

---

## Research Projects

### [SBG — Software Behavioral Genome](https://github.com/ManasSakthivel/Software-Behavior-Genome-SBG-Execution-Grounded-Behavioral-Representation)

*Can execution-grounded behavioral representations detect semantic changes in software beyond simple execution-volume shortcuts?*

5 research versions (V1–V5) with pre-registered hypotheses and a frozen test set. 3,777-pair benchmark across 24 transformation types (12 semantics-preserving, 14 semantics-changing).

**Primary finding:** The behavioral genome does not outperform the `exception_fraction` shortcut on the aggregate benchmark (AUROC 0.551 vs 0.593). But on adversarially designed hard-negative pairs — where shortcuts are explicitly defeated — the behavioral representation achieves 12/12 correct vs 5/12 for the shortcut. On 15 real regression pairs, 14/15 detected vs 3/15 by the shortcut, including 9 bugs entirely invisible to exception-based detection.

516 unit tests · 8 adversarial reviews (ICSE/NeurIPS criteria) · Holm-Bonferroni correction · SHA-256 artifact hashes · 42 prior works surveyed  
**Status:** Research frozen. Target: MSR / ISSTA empirical study track.

### [RELIC — Behavioral Contracts for Legacy Modernization](https://github.com/ManasSakthivel/RELIC)

*Can behavioral contract graphs detect semantic regressions that structural dependency analysis misses?*

Extracts Behavioral Contract Graphs from JCL/COBOL artifacts; identifies behavioral obligations (ordering constraints, return-code guards, dataset dependencies) that become invisible when systems are migrated to cloud-native orchestration. Differencing via confidence-delta detects weakened contracts that structural baselines miss entirely.

On the AWS CardDemo COBOL benchmark: 104/104 violating mutations detected, 0 false positives on 144 semantics-preserving negatives (F1 = 1.000). Outperforms structural, dependency, and LLM baselines.

305 tests · Docker one-command reproduction · Manuscript under review  
**Scope:** Single application (CardDemo). Results are benchmark-specific, not production-wide claims.

### [RIFT — Intervention-Grounded Causal Diagnosis](https://github.com/ManasSakthivel/RIFT-Intervention-Grounded-Detection-of-Behavioral-Divergence)

*Can controlled runtime interventions improve causal attribution of behavioral divergence in distributed microservice systems?*

Combines FCI/PAG causal discovery from time-series telemetry, do-calculus intervention semantics, Wasserstein W1 divergence measurement, and iterative Bayesian closed-loop graph update. When a hidden confounder makes attribution non-identifiable, RIFT abstains — 100% correct abstention on 24 confounded development scenarios.

624 tests · 14 registered experiments · 8 safety hard-stops · Online Boutique testbed (14 services)  
**Status:** Implementation complete; live empirical evaluation (H1–H4) pending final Linux execution campaign.

---

## Engineering

### [Electrolyser Telemetry System](https://github.com/ManasSakthivel/Electrolyser-Telemetry)

End-to-end secure IIoT platform for green hydrogen plant monitoring. Physics-based digital twin (Butler-Volmer + Nernst + Ohmic voltage model, Faraday's law, 16 injectable fault modes) feeds real-time telemetry through mTLS/X.509 MQTT → Telegraf → InfluxDB → Grafana → ML fault detection (Isolation Forest, Random Forest, LSTM autoencoder). Zero-trust certificate architecture; full Docker deployment.

### [Blockchain Medical Federated Learning](https://github.com/ManasSakthivel/Blockchain-Medical-Federated-Learning)

Privacy-preserving federated learning for medical imaging: Gaussian differential privacy (ε,δ budget accounting), additive SMPC gradient aggregation (aggregator never sees raw gradients), Solidity smart contracts for reputation staking and audit trail, GDPR Art. 7/17 consent and erasure. Evaluated on UCI Cleveland Heart Disease dataset. Implementation of accepted journal paper (2024).

---

## Research Methodology

Every empirical project follows:

- Pre-registered hypotheses committed to version control before test-set evaluation
- Frozen test sets — no post-hoc tuning or hypothesis revision
- Shortcut controls — competing against the simplest possible baselines
- Holm-Bonferroni multiple comparison correction
- Comprehensive negative-result documentation — failed hypotheses reported, not hidden
- Adversarial review before claims are finalized
- SHA-256 artifact hashing for reproducibility

---

## Technical Stack

**Languages:** Python · Java · COBOL · Solidity · SQL  
**Systems:** Docker · Linux · tc/netem · InfluxDB · Prometheus · OpenTelemetry · Mosquitto MQTT  
**ML/AI:** scikit-learn · PyTorch · causal-learn (FCI/PC) · differential privacy · federated learning  
**Research tools:** pytest · bootstrap CI · Wilcoxon/Mann-Whitney · permutation tests · Holm-Bonferroni

---

## Contact

[LinkedIn](https://www.linkedin.com/in/manassakthivel) · manas.mskg@gmail.com
