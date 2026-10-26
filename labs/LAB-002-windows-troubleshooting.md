# LAB-002 — Windows Troubleshooting

Status: INTERVIEW COMPLETED (SIMULATED) / HANDS-ON PENDING
Target: TSSR RNCP42463 BC01 — assistance technique.
Estimated time: 45–60 minutes.
Format: diagnostic interview followed by practical verification if a safe test environment is available.

## Scenario
A Windows workstation boots normally but intermittently freezes. Some applications take a long time to open. The user reports that the issue began after recent software updates. Important files must be preserved.

## Tasks
1. Interview the user: timeline, scope, recent changes, error messages, impact, backups.
2. Explain your diagnostic order and why each check is relevant.
3. Use Task Manager and Resource Monitor to identify CPU, memory, disk and network bottlenecks.
4. Inspect Event Viewer (System/Application) and Reliability Monitor for correlated errors.
5. Review startup programs, services, recent updates and driver/device status.
6. Propose safe, reversible checks of Windows integrity (e.g., DISM and SFC where appropriate); distinguish observation from repair.
7. Identify at least three competing hypotheses, supporting and refuting evidence.
8. Present a resolution plan, verification steps, rollback and user communication.

## Deliverables
- Incident report in concise technical French, with optional Russian working notes.
- Diagnostic commands or UI paths, sanitized observations and interpretation.
- Evidence table: hypothesis / observation / test / outcome.
- Verification checklist and user handoff.
- Short glossary of French and English troubleshooting terms.

## Acceptance criteria
- Reproducible, risk-aware diagnostic sequence.
- Evidence-based root cause rather than guessing.
- No destructive repair without backup and approval.
- Clear distinction between verified findings and hypotheses.
- Final outcome and unresolved risks documented.

## Assessment
See the diagnostic interview below: **PARTIAL — 3/5 provisional (2026-10-26)**. Hands-on acceptance criteria are not yet met.

---

## Diagnostic interview — assessment (2026-10-26)

- **Format:** simulated support interview, conducted in Russian; no workstation was accessed and no commands or tests were executed.
- **RNCP mapping:** BC01-03 — *Apporter une assistance technique*.
- **Status:** INTERVIEW COMPLETED — PARTIAL; hands-on verification pending.
- **Provisional score:** **3/5**. This is an educational assessment, not RNCP certification or VAE evidence.
- **Assessed by:** AI interviewer; simulated observations were provided by the interviewer rather than collected independently by the candidate.

### Interview evidence — what the candidate demonstrated

1. **Initial triage:** asked whether user data was backed up; prioritized an independent, verified backup before risky maintenance. Did not systematically ask about failure frequency, reproducible steps, exact update date, scope, error messages or business impact.
2. **First-line Windows performance checks:** independently suggested Task Manager and Resource Monitor; intended to sort processes by memory and disk demand; considered antivirus, RAM pressure and hardware degradation.
3. **Interpretation gap:** incorrectly interpreted **100% Disk** in Task Manager as 100% storage capacity used. The interviewer clarified that this is active time. Subsequently, 140 GB free space and 1,500 ms disk response times were supplied; the candidate wanted to research the cause and check paging-file configuration.
4. **Disk incident:** correctly treated recurrent simulated Event ID 7 (bad block) and 153 (I/O retry) as warning signs of storage failure; prioritized off-disk backup, avoided \`chkdsk /f /r\` and Windows rollback, and recommended on-site assessment.
5. **SMART and recovery:** recognized C5/C6 as warning signs, proposed SSD replacement, considered application-specific migration, clean installation or \`ddrescue\` imaging. Suggested Victoria/HDD Regenerator as possible additional methods; caution: neither should be used as a routine repair attempt on a failing disk, and \`dd\` is not a fault-tolerant substitute for \`ddrescue\`.
6. **Application crash:** proposed investigating logs, searching vendor documentation and contacting support. The specific Windows Event Viewer/Reliability Monitor locations and interpretation of \`0xc0000005\` / \`VCRUNTIME140.dll\` were supplied by the interviewer, **not independently recalled** by the candidate.
7. **Closure:** proposed preserving application projects, applying an official vendor patch, testing open/edit/save/close and observing for further crashes; if worse, investigate logs and escalate. Did not specify a tested rollback procedure, written incident record or formal user handoff.

### Assessment rubric

| Dimension | Score / 5 | Rationale |
|---|---:|---|
| Triage, data protection and risk | 4 | Prioritized backups and avoided destructive repair; incomplete initial symptom interview. |
| Windows monitoring and metric interpretation | 2 | Named appropriate GUI tools, but misread disk active time and did not isolate the process/I/O cause. |
| Windows logs, services, updates and OS integrity | 2 | Understood that logs are needed; specific locations, event interpretation and DISM/SFC workflow were not independently demonstrated. |
| Competing hypotheses and disk recovery | 4 | Sound storage-failure reasoning, SMART risk awareness, SSD replacement and \`ddrescue\`; needs caution on long surface scans and “regeneration”. |
| Verification, rollback and user communication | 3 | Proposed functional application tests and escalation; rollback criteria and documented handoff are incomplete. |
| **Overall** | **3/5** | **Provisional; simulated interview only.** |

### Simulated hypotheses / observation / test / outcome

| Hypothesis | Supplied evidence | Next safe test | Status |
|---|---|---|---|
| Failing HDD causing intermittent freezes | Disk active time 100%, ~2 MB/s throughput, response time ~1,500 ms, Events 7/153, SMART 05=0, C5=24, C6=3 | Verify backup first; examine SMART details and disk/log correlation without stress testing; image with suitable recovery process if needed | **Strongly supported, not independently verified** |
| High memory pressure / paging exacerbating HDD load | RAM 89%; actual paging I/O not measured | Resource Monitor → Memory / Disk; observe hard faults, disk response time and top I/O processes | **Possible contributor, unverified** |
| Windows update caused freezing | User perceived onset after an update | Compare update timeline with reliability/events after data is safe | **Temporal correlation only; not established** |
| Third-party application regression after update | Simulated Event 1000, ClientApp.exe / VCRUNTIME140.dll / 0xc0000005; vendor reportedly issued a fix | Protect project data; install vetted vendor patch; repeat open/edit/save/close and monitor events | **Likely separate application defect; fix not executed or verified** |

### Réponse à l'incident — rapport technique succinct (français, rédigé par l'évaluateur)

**Contexte :** simulation d'assistance à distance sur un poste Windows présentant des ralentissements et blocages intermittents. Les documents de l'utilisateur doivent être protégés.

**Constats simulés :** disque dur actif à 100 %, débit de lecture faible et latence élevée ; événements système 7 et 153 ; attributs SMART C5=24 et C6=3. Après remplacement hypothétique du HDD par un SSD, une application présente des fermetures inattendues (événement 1000).

**Diagnostic :** dégradation du disque dur fortement suspectée. Un problème distinct de l'application après mise à jour est également envisagé. Les causes ne sont pas confirmées par des tests réels.

**Mesures proposées :** sauvegarde vérifiée sur un support indépendant, limitation des accès au HDD défaillant, remplacement par SSD et restauration des données ; vérification de la compatibilité et application du correctif officiel de l'éditeur, après protection des projets de l'application.

**Vérification et clôture :** vérifier les données restaurées, le démarrage et les fonctions métier de l'application (ouvrir, modifier, enregistrer, fermer), surveiller l'absence de nouveaux incidents, préparer une procédure de retour arrière et remettre un compte rendu à l'utilisateur. **Aucune de ces opérations n'a été réellement exécutée pendant l'entretien.**

> Note: the French report and the following reference workflow are authored by the assessor. They are **not** evidence of the candidate's independently demonstrated French or Windows command proficiency.

### Reference workflow for the next hands-on session (not executed)

| Goal | Safe interface / command | Verification target |
|---|---|---|
| Capture baseline | Task Manager → Processes / Performance; \`resmon.exe\` → Disk and Memory | Distinguish active time, utilization, response latency, throughput, page faults and capacity used |
| Correlate failures | \`eventvwr.msc\` → Windows Logs → System / Application | Record event time, source, ID and context; do not infer cause from a single event |
| Review crash history | \`perfmon /rel\` | Associate app crashes with software changes and vendor versions |
| Review environment | Settings → Windows Update → Update history; Device Manager; startup apps; \`services.msc\` | Compare event timeline, driver state and service impact |
| Check OS health only if warranted | \`DISM /Online /Cleanup-Image /ScanHealth\`; \`sfc /verifyonly\` | Record results before choosing any repair commands; only on a stable backed-up system |
| Verify the vendor fix | Preserve application data; note installed version; apply official fix; test workflow and event logs | No recurring crash after meaningful business scenario testing; recovery path documented |

### Verification checklist — still outstanding

- [ ] Practical session on a safe Windows VM or non-production machine.
- [ ] Collect screenshots/sanitized output from Task Manager and Resource Monitor.
- [ ] Inspect System/Application logs and Reliability Monitor independently.
- [ ] Demonstrate update, driver, service and startup checks; explain when DISM/SFC are appropriate.
- [ ] Write at least three hypotheses with evidence for/against and targeted tests.
- [ ] Document backup verification, authorized remediation, rollback and clear user-facing ticket closure.
- [ ] Independently write a short French incident report and explain it orally.

### Glossaire bref (FR → EN → RU)

| Français | English | Русский |
|---|---|---|
| Temps d'activité du disque | Disk active time | Время активности диска |
| Temps de réponse | Response time | Время отклика |
| Journal des événements | Event log | Журнал событий |
| Moniteur de ressources | Resource Monitor | Монитор ресурсов |
| Sauvegarde vérifiée | Verified backup | Проверенная резервная копия |
| Secteur instable | Pending sector | Нестабильный сектор |
| Retour arrière | Rollback | Откат |
| Compte rendu d'intervention | Service report | Отчёт о выполненных работах |

### Follow-up decision

**Keep LAB-002 open for hands-on validation.** Interview stage is completed, but the acceptance criteria requiring a reproducible diagnostic, independently collected evidence, verified final outcome and formal handoff are **not yet met**. The next recommended activity is a short Windows diagnostics practical, not a repeat of the hardware-recovery scenario.
