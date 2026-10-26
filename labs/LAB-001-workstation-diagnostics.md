# LAB-001 — Diagnostic d'un poste Windows lent

Date: 2026-10-26
RNCP42463: BC01 — support aux utilisateurs; assistance technique.
Type: simulated ticket and oral diagnostic interview. No real workstation tested.

## Scenario
Windows 10, Core i5-6500, 8 GB RAM, 500 GB Seagate HDD. Slow boot and application freezes. Disk active time 98–100%, read rate 0.5–3 MB/s. SMART raw 05=0, C5=24, C6=3. Client has about 15 GB of important documents, with no confirmed backup.

## Candidate response
- Boot Windows PE independently of installed Windows.
- Inspect disk health using Victoria / HDD Sentinel; consider offline antivirus scanning (Dr.Web), Windows faults, RAM (Memtest), temperature, cabling and cooling.
- Candidate has prior experience using Windows PE and R-Studio for recovering deleted files and damaged partitions, but not advanced disk imaging.
- Initial knowledge gap: interpretation of SMART 05/C5/C6.
- After reviewing SMART warnings, candidate chose to copy the client's essential 15 GB of documents to healthy storage first, then attempt sector-level imaging of the full HDD. Reason: prioritize irreplaceable data before prolonged disk reading.

## Evaluation
**PASS — diagnostic reasoning (simulated), 4/5 provisional.**
Strengths: practical troubleshooting, sound data priorities, familiarity with Windows PE and recovery tools.
Improvement: SMART attribute interpretation, understanding that reading can stress a failing drive, verification of copied files, cautious use of surface scans and filesystem repair.

**Evidence classification:** verbal simulated assessment only. No hands-on verification and no professional VAE proof. The candidate's historical experience is self-reported and needs documentary evidence.

## Next
LAB-002: Windows Troubleshooting — Event Viewer, Resource Monitor, services, startup, drivers, system integrity and incident report.
