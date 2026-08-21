# Manas Sakthivel

Hi, I'm Manas — a CS graduate from RV College of Engineering, currently working as a Software Developer at IBM.

Most of my recent projects started as engineering questions that gradually turned into something deeper. I got interested in how software actually behaves at runtime — not just what the code says it does, but what it does when executed — and that thread has connected a lot of my work over the past couple of years.

---

## What I'm interested in

- Program analysis and software behavior
- Legacy software and modernization
- Distributed systems and observability
- AI-assisted software engineering
- Systems that have to be reliable

---

## Projects

### [Software Behavior Genome (SBG)](https://github.com/ManasSakthivel/Software-Behavior-Genome-SBG-Execution-Grounded-Behavioral-Representation)

I wanted to understand whether you could represent how a program *behaves* at runtime in a structured, comparable form — separate from what the code looks like statically. SBG extracts behavioral features from execution traces (call patterns, state transitions, exception behavior, timing) and uses them to compare two versions of a program. The main finding was nuanced: the representation doesn't consistently beat simpler baselines on the aggregate benchmark, but works better on harder cases where the simple shortcuts fail. I found that more interesting than a clean win.

### [RELIC](https://github.com/ManasSakthivel/RELIC)

Legacy systems like COBOL/JCL encode behavioral rules that aren't written down anywhere — step ordering, return code guards, dataset dependencies. When you modernize the system, those rules often get lost. RELIC tries to make them explicit by extracting behavioral contracts from the code, then checking whether they're preserved after a transformation. Evaluated on the AWS CardDemo COBOL codebase.

### [RIFT](https://github.com/ManasSakthivel/RIFT-Intervention-Grounded-Detection-of-Behavioral-Divergence)

When something goes wrong in a microservice system, standard observability tools tell you what metrics changed together. That's correlation, not cause. RIFT explores whether deliberately perturbing a service — injecting controlled latency — and watching what changes downstream can give better causal signal for root-cause analysis. Implementation is complete; the live empirical evaluation on a real testbed is still in progress.

### [Electrolyser Telemetry System](https://github.com/ManasSakthivel/Electrolyser-Telemetry)

An end-to-end IIoT platform I built for monitoring green hydrogen electrolysers. Physics-based simulation feeds real telemetry through a secured MQTT broker into InfluxDB, visualized in Grafana and a React SCADA interface, with ML-based fault detection on top. Mostly an exercise in building a full system stack from scratch.

### [Blockchain Medical Federated Learning](https://github.com/ManasSakthivel/Blockchain-Medical-Federated-Learning)

An earlier project exploring privacy-preserving ML in a medical context — federated learning with differential privacy and secure aggregation, with a blockchain layer for audit trail and GDPR consent management. Implementation of a published paper. The interest here was less blockchain-for-its-own-sake and more: what does a privacy-first ML architecture actually look like in practice?

---

## Work

**IBM** — Software Developer. Working on enterprise software, mostly backend systems.

**DigiCert** — Previously interned on API automation and software testing.

---

## Education

**RV College of Engineering** — B.E. Computer Science & Engineering

---

[LinkedIn](https://www.linkedin.com/in/manassakthivel) · manas.mskg@gmail.com
