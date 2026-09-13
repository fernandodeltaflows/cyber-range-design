# Triage & Severity Scoring

**Range:** DFIR and detection · **Day:** 2 · **Missions:** 12

## Scenario

Three incidents are open at once and the student cannot work all of them. An
internet-facing reverse proxy, an internal warehouse inventory service, and an
employee self-service portal. Score them, rank them, and defend the ranking.

## Learning objectives

- Read and interpret CVSS v3.1 base metrics
- Calculate base scores and derive severity ratings
- Construct a CVSS vector string
- Prioritise a queue of concurrent incidents
- Distinguish severity from priority
- Place a triage decision within the OODA loop

## Structure

| Block | Focus | Missions |
|---|---|---|
| CVSS v3.1 base metrics | Reading User Interaction and Attack Complexity | 2 |
| INC-201: internet-facing reverse proxy / WAF | Base score, severity, vector string | 3 |
| INC-202: internal warehouse inventory service | Base score, severity | 2 |
| INC-203: internal employee self-service portal | Base score, severity | 2 |
| Prioritising the queue | Ranking, severity vs priority, OODA | 3 |

## The chain

Two metric-reading missions come first so the student is scoring from
understanding rather than from a calculator.

Three incidents are then scored in sequence. They are chosen to differ on the
axes that matter: exposure, business function and user interaction. The
internet-facing proxy and the internal portal will not score the same, and the
student should be able to say why before they compute anything.

The final block is where the campaign earns its place. Having produced three
scores, the student must rank the queue - and then answer why severity and
priority are not the same thing. A lower-scoring incident on a
business-critical system can outrank a higher-scoring one, and a student who
cannot articulate that will mis-triage in a real SOC.

## Design notes

**Three incidents, not one.** A single scoring exercise teaches the tool.
Three, scored in a row and then ranked against each other, teaches judgement.
The ranking mission is the one that matters.

**Severity versus priority is the campaign's thesis.** CVSS produces a number.
Triage produces a decision. Treating the number as the decision is the most
common failure in junior triage, and it is assessed explicitly here.

**OODA anchors the decision.** The closing mission places triage inside a
decision framework, so the student leaves with a model rather than a procedure.
