# L5 Narrow / L2 General Classification — api-oss-playground
**Platform:** Anticloud | **PAX:** 27B | **IP:** USPTO pending 2026, Anticloud FZ LLE
**Domain:** Interactive sovereign playground: test PAX 27B queries in a local web UI

## L5 Narrow
api-oss-playground specializes in interactive sovereign playground: test pax 27b queries in a local web ui within the Anticloud sovereign deployment boundary. All operations stay local — no cloud services, no external APIs, no data exfiltration. The narrow scope ensures deterministic, auditable behavior that PAX 27B can reason about precisely.

## L2 General
L2 General means api-oss-playground is available to all 9 Anticloud tiers without per-tier configuration. The same API serves hospital, defense, robotics, and research deployments.

## PAX Integration
PAX 27B is the inference backend for the playground. All queries, responses, and configurations are local. The playground UI mirrors the production INTE11ECT_APP interface for developer testing.

## AIOSS Audit Relevance
Every playground session (query hash + response hash + session ID + model config) is AIOSS-chained: H_n = SHA3-256(H_{n-1} || entry_hash_n || timestamp_n).
Tamper-evident, offline-verifiable, zero cloud dependency.

## Regulatory / Compliance
GDPR Art. 25 (playground data never leaves device), ISO 27001 A.12.6
