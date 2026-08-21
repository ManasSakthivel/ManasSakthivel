# Manas Sakthivel

**Software Engineer · AI/Systems Researcher**  
RV College of Engineering, B.E. Computer Science · IBM Software Labs

---

## Research

I investigate how complex software systems behave, how that behavior can be represented and validated, and how causal and AI-based methods can reason about behavioral changes across software transformations, legacy modernization, and distributed system failures.

**Central questions:**
- Can execution-grounded representations detect semantic changes that structural analysis misses?
- Can behavioral contracts preserve semantic obligations when legacy software is modernized?
- Can controlled interventions improve causal attribution of behavioral divergence in distributed systems?

---

## Research Projects

### [SBG — Software Behavioral Genome](https://github.com/ManasSakthivel/Software-Behavior-Genome-SBG-Execution-Grounded-Behavioral-Representation)

*Can execution-grounded behavioral representations detect semantic changes in software beyond simple execution-volume shortcuts?*

- 5 research versions (V1–V5) with pre-registered hypotheses and frozen test sets
- 3,777-pair benchmark across 24 transformation types (12 semantics-preserving, 14 semantics-changing)
- Primary finding: nuanced negative+positive — aggregate benchmark beaten by exception-fraction shortcut (AUROC 0.551 vs 0.593), but behavioral representation achieves 12/12 on adversarial hard-negative pairs and 14/15 on real regressions where shortcuts fail
- 516 unit tests · 8 adversarial reviews modeled on ICSE/NeurIPS criteria · Holm-Bonferroni correction · SHA-256 artifact hashes
- **Status:** Research frozen. Publication target: MSR / ISSTA empirical study track.

### [RELIC — Behavioral Contracts for Legacy Modernization](https://github.com/ManasSakthivel/RELIC)

*Can behavioral contract graphs detect semantic regressions that structural dependency analysis misses?*

- Extracts Behavioral Contract Graphs from JCL/COBOL artifacts; compares versions via confidence-delta differencing
- On AWS CardDemo COBOL benchmark: 104/104 violating mutations detected, 0 false positives on 144 semantics-preserving negatives (F1 = 1.0)
- Outperforms structural, dependency, and LLM baselines on the benchmark
- 305 tests · Docker reproduction · Manuscript under review
- **Scope:** Single application (CardDemo). Results are benchmark-specific, not production-wide claims.

### [RIFT — Intervention-Grounded Causal Diagnosis](https://github.com/ManasSakthivel/RIFT-Intervention-Grounded-Detection-of-Behavioral-Divergence)

*Can controlled runtime interventions improve causal attribution of behavioral divergence in distributed microservice systems?*

- Combines FCI/PAG causal discovery, do-calculus intervention semantics, Wasserstein divergence measurement, and iterative Bayesian closed-loop graph update
- Correctly abstains (100%) on all 24 confounded scenarios where attribution is not identifiable
- 624 tests · 14 registered experiments · 8 safety hard-stops · Online Boutique testbed
- **Status:** Implementation complete. Live empirical evaluation (H1–H4) pending final Linux execution campaign.

---

## Engineering

### [Electrolyser Telemetry System](https://github.com/ManasSakthivel/Electrolyser-Telemetry)

End-to-end secure IIoT platform for green hydrogen plant monitoring: physics-based digital twin → mTLS/X.509 MQTT → Telegraf → InfluxDB → Grafana → ML fault detection (Isolation Forest, Random Forest, LSTM autoencoder). 16 injectable fault modes, zero-trust certificate architecture, full Docker deployment.

### [Blockchain Medical Federated Learning](https://github.com/ManasSakthivel/Blockchain-Medical-Federated-Learning)

Privacy-preserving federated learning for medical imaging: Gaussian differential privacy, additive SMPC gradient aggregation, Solidity smart contracts for audit trail and reputation, GDPR-compliant consent management. Evaluated on UCI Cleveland Heart Disease dataset.

---

## Research Practices

- Pre-registered hypotheses committed to version control before test-set evaluation
- Frozen test sets; no post-hoc hypothesis revision
- Holm-Bonferroni multiple comparison correction
- Comprehensive negative-result reporting — failed hypotheses documented, not hidden
- Ablation studies and shortcut controls in all empirical projects
- SHA-256 artifact hashing for reproducibility
- Adversarial/hostile review process before claiming results

---

## Technical Stack

**Languages:** Python · Java · COBOL · Solidity · SQL  
**Systems:** Docker · Linux · tc/netem · InfluxDB · Prometheus · OpenTelemetry · Mosquitto MQTT  
**ML/AI:** scikit-learn · PyTorch · causal-learn (FCI) · differential privacy · federated learning  
**Research tools:** pytest · statistical bootstrap · Wilcoxon/Mann-Whitney · permutation tests

---

## Contact

[LinkedIn](https://www.linkedin.com/in/manassakthivel) · manas.mskg@gmail.com
