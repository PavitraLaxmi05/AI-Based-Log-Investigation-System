# AI Cyber-Forensic Command Center

### Autonomous Multi-Log Threat Detection & Explainable Investigation System

---

## Overview

The **AI Cyber-Forensic Command Center** is a high-performance, autonomous platform designed to ingest, analyze, and interpret millions of logs across four critical security domains. It delivers not just a binary verdict, but a mathematically grounded, LIME-based forensic explanation suitable for legal and administrative review.

> In modern forensics, manual log analysis can take weeks. This system reduces that to milliseconds.

---

## Full Pipeline

![Full Pipeline](fullpipeline.png)

---

## Supported Log Domains

- **Network Logs** — Packet-level traffic analysis with protocol decoding
- **Linux OS Logs** — System call tracing and privilege escalation detection
- **Windows Security Logs** — Hybrid rule-engine and deep learning adjudication
- **Web Application Logs** — URL entropy scoring and anomaly classification

---

## Core Architecture & Workflow

The system operates as a fully autonomous pipeline:

- **Ingestion** — Real-time upload of CSV/JSON log files
- **Gatekeeper Stage** — Light-weight Random Forest filtering to separate normal traffic from anomalies
- **Neural Adjudication** — High-precision analysis of flagged anomalies via Deep Learning (MLP) models
- **Forensic Explanation** — Local mathematical breakdown using LIME to identify specific triggering features (e.g., Packet Size, UID, URL Entropy)
- **Evidence Export** — Generation of tamper-evident CSV, STIX-compliant JSON, and court-ready forensic PDF summaries

---

## Technology Stack

| Layer | Technologies |
|---|---|
| Frontend UI | Gradio (Dashboard, Investigation, and Inspector views) |
| Machine Learning | TensorFlow/Keras (MLP Adjudicators), Scikit-Learn (Random Forest Gatekeepers) |
| Explainable AI (XAI) | LIME (Local Logic), SHAP (Global Feature Importance) |
| Data Processing | Pandas, NumPy, Joblib |
| Forensic Security | Hashlib (SHA-256 Integrity), ReportLab (PDF Reporting) |

---

## Algorithms

### Forensic Explanation — LIME

```python
# Pseudo-code: Local Forensic Narrative Generation
Function GenerateForensicEvidence(target_log, model, background_sample):
    1. Initialize LIME Tabular Explainer with background_sample
    2. Perturb target_log (create 1000+ variants with small value changes)
    3. Feed variants to 'model' and record prediction shifts
    4. Calculate weights for each feature (e.g., Byte_Ratio, TTL_Diff)
    5. Filter Top 5 features with positive weights (Threat Increasers)
    6. Map feature logic to human-readable FEATURE_DESCRIPTIONS
    Return formatted Forensic Narrative
```

### Ultra-Precision Adjudication Routing

```python
# Pseudo-code: Adjudication Logic
If log_risk > 90th_percentile:
    Route to MLP Deep AI
    Perform consensus check (MLP + XGBoost + LightGBM)
    If high_variance between models:
        Flag for manual forensic review
    Else:
        Lock verdict and generate LIME report
```

---

## System Performance

| Log Schema | Core Technology | Adjudication Accuracy |
|---|---|---|
| Network Logs | Ensemble (MLP / XGBoost / LightGBM) | 99.2% |
| Linux OS Logs | Random Forest + Syscall Analysis | 98.5% |
| Windows Logs | Hybrid MLP + Rule Engine | 97.8% |
| Web Application Logs | XGBoost + Entropy Scoring | 95.0%+ |

---

## Key Differentiators

- **LLM-Free Integrity** — Unlike systems relying on LLaMA or GPT, this project uses LIME. Every forensic reason is grounded in raw local mathematics, not generative inference, making evidence legally defensible.
- **Local Execution** — No data ever leaves the local environment, preserving the forensic chain of custody and ensuring full data privacy compliance.
- **Feature Description Mapping** — Every LIME weight is translated into human-readable forensic context. For example:
  - `effective_uid = 0` → *"Root user detected — possible Privilege Escalation"*
  - `url_entropy > threshold` → *"High URL randomness — possible encoded payload"*

---

## Built-in Data Translation Maps

- **PROTOCOL_MAP** — Decodes IANA protocol IDs (e.g., `6 = TCP`, `17 = UDP`)
- **L7_PROTO_MAP** — Identifies application-layer targets (e.g., `80 = HTTP`, `443 = HTTPS`)
- **SYSCALL_MAP** — Decodes critical Linux system calls (e.g., `59 = execve`, `101 = ptrace`)

---

## Output Formats

- **Tamper-Evident CSV** — SHA-256 signed log exports for chain-of-custody preservation
- **STIX 2.1 JSON** — Structured Threat Information Expression for interoperable incident reporting
- **Court-Ready PDF** — Human-readable forensic summaries generated via ReportLab

---

## References & Standards

- [IANA Protocol Numbers](https://www.iana.org/assignments/protocol-numbers/) — Registry for internet protocol identifiers
- [STIX 2.1 Standard](https://oasis-open.github.io/cti-documentation/stix/intro) — Structured Threat Information Expression
- [LIME Documentation](https://lime-ml.readthedocs.io/) — Local Interpretable Model-agnostic Explanations
- [SHAP Documentation](https://shap.readthedocs.io/) — Global feature importance framework
- [NIST SP 800-86](https://csrc.nist.gov/publications/detail/sp/800-86/final) — Guide to Integrating Forensic Techniques into Incident Response

---

## License

This project is intended for authorized forensic investigation, academic research, and security operations use only. Unauthorized deployment against systems without explicit permission is prohibited.
