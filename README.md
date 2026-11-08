<picture><source media="(prefers-color-scheme: dark)" srcset="assets/header_dark.svg"/><img src="assets/header_light.svg" alt="Manas Sakthivel. Three stacked isometric layers of a call graph; one execution trace slowly draws itself through them." width="100%"/></picture>

# Manas Sakthivel

**I study how software behaves at runtime, and how that behaviour can be measured, diffed and diagnosed rigorously.**

Software Developer at IBM Software Labs, working on multi-language source analysis and verification tooling. B.E. Computer Science and Engineering, RV College of Engineering.

[Website](https://manas-sakthivel.vercel.app/) · [LinkedIn](https://www.linkedin.com/in/manassakthivel) · [Email](mailto:manas.mskg@gmail.com) · [Repositories](https://github.com/ManasSakthivel?tab=repositories)

**Open to:** MS/PhD research in program analysis, software behaviour and reliable systems.

## Research thread

Every project here asks one question: how does software behave when it runs, and what changes when it changes? SBG represents behaviour from execution traces, RELIC extracts and diffs behavioural contracts from legacy JCL, and RIFT tries to diagnose behavioural divergence in microservices by intervention instead of correlation. I report each result against its simplest baseline, and I state when the baseline wins.

## Highlights

<table>
<tr>
<td width="33%" valign="top"><h3>0.897 AUROC</h3><b>SBG</b> vs 0.616 for edit size.<br><sub>Synthetic benchmark. A preregistered test (H4) found no gain over simple baselines, and it did not transfer to real bugs.</sub></td>
<td width="33%" valign="top"><h3>0.919 F1</h3><b>RELIC</b> on AWS CardDemo (n = 315).<br><sub>A trivial any-text-change detector scores 0.943. RELIC's edge is specificity: 1.000 vs 0.492.</sub></td>
<td width="33%" valign="top"><h3>664 tests</h3><b>RIFT</b> with 8 safety hard stops.<br><sub>No positive empirical result yet. The confirmatory experiment is preregistered, not run.</sub></td>
</tr>
</table>

## Research projects

<picture><source media="(prefers-color-scheme: dark)" srcset="assets/card1_dark.svg"/><img src="assets/card1_light.svg" alt="SBG. AUROC 0.897 vs 0.616 for edit size on a synthetic benchmark. Limits: H4 null and no real-bug transfer." width="100%"/></picture>

**SBG, Software Behavior Genome** · [Repository](https://github.com/ManasSakthivel/Software-Behavior-Genome-SBG-Execution-Grounded-Behavioral-Representation)

- **Question:** can program behaviour be represented from execution traces alone, and compared across versions?
- **Method:** call-graph, call-order, exception, temporal and value-state features from traces; preregistered, size-aware evaluation (composed pairs, dynamic-oracle labels).
- **Result:** AUROC 0.897 vs 0.616 for edit size (95% CI 0.863 to 0.922; 19 programs, 638 pairs).
- **Honest limit:** the benchmark is synthetic and comes from the same author and generation procedure as development, so it is not independent. H4 is a null (+0.006, 95% CI -0.069 to +0.068). No real-bug transfer: BugsInPy 0.497, QuixBugs 0.444.
- **Reproduce:** `make test`; `make reproduce-output-free` (about 10 minutes). See the repository README.

<details><summary>More detail</summary>

<br>

- With edit size exactly matched, AUROC is 0.875.
- An earlier frozen test did not demonstrate the method, which led to the redesign. The repository lists 8 withdrawn claims.
- A protocol leak was found and fixed: entry-point discovery had traced each program's own unit-test driver, so "output-free" features recorded whether the tests passed. Removing it costs about 0.08 AUROC (0.640 to 0.565).

</details>

<picture><source media="(prefers-color-scheme: dark)" srcset="assets/card2_dark.svg"/><img src="assets/card2_light.svg" alt="RELIC. F1 0.919 on AWS CardDemo with 315 mutants. Limit: a trivial text-change baseline scores 0.943." width="100%"/></picture>

**RELIC, behavioural contracts for legacy JCL** · [Repository](https://github.com/ManasSakthivel/RELIC)

- **Question:** can the unwritten behavioural rules in legacy batch jobs (step order, dataset dependencies, return-code guards) be extracted and checked after a change?
- **Method:** a static contract extractor and differ, evaluated by source-level mutation testing against an oracle.
- **Result:** on AWS CardDemo (315 mutants), precision 1.000, recall 0.850, F1 0.919 (95% CI 0.88 to 0.95). Pooled over three corpora (566 mutants): F1 0.905.
- **Honest limit:** a trivial detector that flags any non-comment text change scores F1 0.943 and beats RELIC. An LLM given both job versions scored 0.985 vs RELIC's 0.908 on a 383-mutant subsample. The oracle is written by the author and has not been checked against real z/OS. The evaluated artefacts are JCL, not COBOL. An earlier F1 of 1.000 was circular and is withdrawn.
- **Reproduce:** `make test`; `make reproduce`. See the repository README.

<picture><source media="(prefers-color-scheme: dark)" srcset="assets/card3_dark.svg"/><img src="assets/card3_light.svg" alt="RIFT. 664 tests and 8 safety hard stops. Limit: no positive empirical result yet." width="100%"/></picture>

**RIFT, intervention-grounded diagnosis** · [Repository](https://github.com/ManasSakthivel/RIFT-Intervention-Grounded-Detection-of-Behavioral-Divergence)

- **Question:** can controlled interventions give better causal evidence than correlation for root-cause analysis in microservices?
- **Method:** FCI/PAG causal discovery, cost-aware intervention selection, latency injection on the Online Boutique testbed, and a Bayesian update that attributes a cause or abstains.
- **Result:** engineering only. 664 tests pass (2 protected-material checks are reported as unavailable, not passed) and 8 safety hard stops. The test count shows discipline, not effectiveness.
- **Honest limit:** no positive empirical result. On the synthetic benchmark's development and validation splits, the best variant (V3) scores a mean utility of -0.338 against 0 for always-abstain. The confirmatory experiment is preregistered but not run. There is no protected held-out validation and no generalisation claim.
- **Reproduce:** `python3.11 -m pytest tests/ -q`; `make reproduce-all`. See the repository README.

## Methodology and integrity

<picture><source media="(prefers-color-scheme: dark)" srcset="assets/integrity_dark.svg"/><img src="assets/integrity_light.svg" alt="Evaluation protocol: preregister, freeze the protocol, run baselines first, then report nulls and withdrawals." width="100%"/></picture>

- **Preregistration.** SBG's hypotheses use Holm-corrected tests fixed in an in-repository plan before evaluation. RIFT's confirmatory experiment is preregistered and has not been run. These plans live in the repositories, not an external registry.
- **Baselines first.** The simplest baseline is always reported. RELIC's trivial text-change detector beats it on F1, and that is in the README. For RIFT the baseline is always-abstain.
- **Withdrawn claims.** SBG's README lists 8 withdrawn claims. RELIC's earlier F1 of 1.000 came from a circular mutation benchmark and is withdrawn.
- **A fixed protocol leak.** SBG's "output-free" protocol was violated by the evaluation harness, not the model. The leak was found, audited (`make audit`) and removed.
- **Size-matched evaluation.** Edit size is the strongest simple confound, so SBG is also evaluated with edit size exactly matched (AUROC 0.875).
- **Synthetic vs real.** Every benchmark above is synthetic or author-generated. None is externally validated, and none has a published paper.

## Claims ledger

| Project | Claim | Baseline | Benchmark and n | 95% CI | Source |
|---|---|---|---|---|---|
| SBG | AUROC 0.897 | 0.616, edit size | V10, synthetic; 19 programs, 638 pairs | 0.863 to 0.922 | [README.md](https://github.com/ManasSakthivel/Software-Behavior-Genome-SBG-Execution-Grounded-Behavioral-Representation/blob/HEAD/README.md) |
| SBG | AUROC 0.875 | edit size exactly matched | V10, synthetic | n/a | [README.md](https://github.com/ManasSakthivel/Software-Behavior-Genome-SBG-Execution-Grounded-Behavioral-Representation/blob/HEAD/README.md) |
| SBG | H4: +0.006 (null) | edit size plus simple execution statistics | V10, synthetic | -0.069 to +0.068 | [README.md](https://github.com/ManasSakthivel/Software-Behavior-Genome-SBG-Execution-Grounded-Behavioral-Representation/blob/HEAD/README.md) |
| SBG | AUROC 0.497 and 0.444 | no transfer | BugsInPy and QuixBugs, real bugs | n/a | [README.md](https://github.com/ManasSakthivel/Software-Behavior-Genome-SBG-Execution-Grounded-Behavioral-Representation/blob/HEAD/README.md) |
| RELIC | F1 0.919 (P 1.000, R 0.850) | 0.943, any text change (specificity 0.492; RELIC 1.000) | AWS CardDemo; 315 mutants | 0.88 to 0.95 | [README.md](https://github.com/ManasSakthivel/RELIC/blob/HEAD/README.md) |
| RELIC | F1 0.905 | same trivial baseline | three corpora pooled; 566 mutants | n/a | [README.md](https://github.com/ManasSakthivel/RELIC/blob/HEAD/README.md) |
| RELIC | F1 0.908 vs LLM-only 0.985 | LLM sees both job versions | random subsample; 383 of 566 | diff -0.14 to -0.03 | [README.md](https://github.com/ManasSakthivel/RELIC/blob/HEAD/README.md) |
| RIFT | 664 tests pass | n/a | `tests/`; 2 protected-material checks unavailable | n/a | [README.md](https://github.com/ManasSakthivel/RIFT-Intervention-Grounded-Detection-of-Behavioral-Divergence/blob/HEAD/README.md) |
| RIFT | V3 mean utility -0.338 | 0, always-abstain | synthetic simulator; 50 dev + 18 validation scenarios | n/a | [README.md](https://github.com/ManasSakthivel/RIFT-Intervention-Grounded-Detection-of-Behavioral-Divergence/blob/HEAD/README.md) |
| RIFT | V2 attributed 60/108 | 63/108, always-abstain | Sprint 4.3 held-out set (already spent) | n/a | [README.md](https://github.com/ManasSakthivel/RIFT-Intervention-Grounded-Detection-of-Behavioral-Divergence/blob/HEAD/README.md) |

<details><summary>Glossary</summary>

<br>

- **AUROC:** the chance that a behaviour-changing pair scores higher than an equivalent one (0.5 is chance).
- **F1:** the harmonic mean of precision and recall.
- **FCI/PAG:** a constraint-based causal discovery method that outputs a partial ancestral graph.
- **H4:** SBG's preregistered hypothesis that it adds something over edit size plus simple execution statistics. It came out null.
- **V5 / V10:** SBG's fifth feature set and its tenth, size-aware evaluation round.
- **Preregistered:** hypotheses and the analysis plan fixed before the evaluation was run.

</details>

## Team and applied work

<picture><source media="(prefers-color-scheme: dark)" srcset="assets/card4_dark.svg"/><img src="assets/card4_light.svg" alt="Electrolyser Telemetry. Five-layer pipeline from physics simulator to mTLS MQTT, InfluxDB, Grafana and React, and ML fault detection. Limit: team project on simulator-generated data only." width="100%"/></picture>

**Electrolyser Telemetry.** [Repository](https://github.com/ManasSakthivel/Electrolyser-Telemetry) · Team project: I am the third of four authors on the draft paper ([RESEARCH_PAPER.md](https://github.com/ManasSakthivel/Electrolyser-Telemetry/blob/HEAD/RESEARCH_PAPER.md)).

- **What it is:** a physics simulator, mTLS MQTT, InfluxDB, Grafana and a React SCADA interface, with ML fault detection (Isolation Forest, Random Forest, LSTM autoencoder).
- **Honest limit:** all telemetry is simulator-generated. There is no real hardware, and fault labels come from the same simulator that produces the features, so I make no performance claim for real electrolysers.
- **Reproduce:** `make test`. See the repository README.

**Blockchain Medical Federated Learning** (earlier work) · [Repository](https://github.com/ManasSakthivel/Blockchain-Medical-Federated-Learning) · My own unpublished draft; it is not an implementation of a published paper.

- **What it is:** a student prototype: a federated-learning simulation on the UCI Cleveland heart-disease data (303 records) with Gaussian differential privacy, additive secret sharing, a Flask EHR app and Solidity contracts.
- **Honest limit:** model hashing is SHA-256 only, and there is no zk-STARK. The contracts' consent gate exists but is disabled by default. The web simulation is not connected to the contracts; a standalone script can submit hashes via Ganache, but I have not run it. Not clinical.

## Timeline

| When | Role | Where |
|---|---|---|
| Aug 2026 to present | Software Developer: multi-language source analysis and verification tooling | IBM Software Labs |
| Mar 2026 to Aug 2026 | Software Developer Intern | IBM Software Labs |
| Aug 2025 to Feb 2026 | Associate Software Engineer Intern (API automation and testing) | DigiCert |
| 2022 to 2026 | B.E. Computer Science and Engineering | RV College of Engineering |

## Stack

- **Languages:** Python, Java, JavaScript, Solidity
- **Analysis and research:** program analysis, AST processing, mutation testing, causal discovery, experimental evaluation
- **Systems:** Linux, Docker, distributed systems, MQTT with mTLS, InfluxDB, Grafana, Prometheus, Jaeger
- **ML and tooling:** PyTorch, scikit-learn, pytest, Flask, React

**Behaviour first. Evidence second. Claims last.**

[Website](https://manas-sakthivel.vercel.app/) · [LinkedIn](https://www.linkedin.com/in/manassakthivel) · [Email](mailto:manas.mskg@gmail.com) · [GitHub](https://github.com/ManasSakthivel)
