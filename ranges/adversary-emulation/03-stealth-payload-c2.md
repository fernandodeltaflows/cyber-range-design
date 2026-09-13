# Stealth, Payload Handling and C2

**Range:** Adversary emulation · **Day:** 3 of 3 · **Duration:** 4 hours
**Difficulty:** Medium · **Missions:** 22

## Scenario

The student has access and has kept it. Now the environment is watching. Script
block logging is on, in-memory inspection is active, and the question for the
day is whether the student can operate against a defender who is paying
attention, and then report honestly on what the defender could have caught.

## Learning objectives

- Confirm what host-based code inspection is active, and what it actually sees
- Execute tooling in memory and fingerprint what that leaves behind
- Apply and recognise obfuscation, including its tells
- Integrate with a C2 framework: listener, stager, callback and tasking
- Clean up operational artefacts, and identify what cleanup itself leaves
- Produce a detection-opportunities report
- Critically review and harden AI-generated PowerShell, including scope enforcement

## Structure

| Module | Focus | Missions |
|---|---|---|
| 1 | Code inspection and script-block logging | 5 |
| 3 | Critical review and hardening of AI-generated PowerShell | 5 |
| 4 | In-memory execution | 3 |
| 5 | Obfuscation | 2 |
| 6 | C2 framework integration | 4 |
| 7 | OPSEC, artefact cleanup and the detection report | 3 |

**Module 1** starts by confirming the watcher is live and reading its log,
because a student who assumes what logging is enabled is guessing. It includes
decoding a planted command, which is the defender's side of the same skill.

**Module 3** is the AI-review module. The student is given generated PowerShell
containing a cmdlet that does not exist and a target outside the engagement
scope. They identify both, verify a cmdlet properly, enforce scope, and run the
hardened version.

**Module 4** executes tooling in memory and then fingerprints what ran, which
is the detection counterpart.

**Module 5** obfuscates a benign loader and then identifies the obfuscation
tell, teaching both directions at once.

**Module 6** covers two C2 frameworks hands-on - listener, stager, callback and
tasking on one, agent build and tasking on the other - with a third covered
awareness-only. It closes on the tooling boundary: what is in scope for this
engagement and what is not.

**Module 7** reverses a persistence artefact, then establishes that cleanup
itself leaves traces, and produces the detection-opportunities report.

## The chain

The day runs attacker-side and defender-side in alternation by design. Every
offensive module is followed or accompanied by the question of what it looked
like from the other side, and the campaign terminates in a written detection
report rather than in a successful callback.

That ordering is what makes this an active defense course rather than an
offensive one. The deliverable is not access. The deliverable is a defender who
knows what to look for.

## Tooling exercised

Built-in PowerShell, in-memory loaders, an obfuscation toolkit, and two C2
frameworks hands-on with a third taught awareness-only.

## Design notes

**Confirm the watcher before evading it.** Module 1 could have opened with an
evasion technique. Opening instead with "prove what is logging" means every
subsequent technique is measured against observed reality rather than an
assumption about a default configuration.

**Cleanup leaves traces.** This is the mission most likely to surprise a
student, and it is the honest lesson of the day: there is no operation that
leaves nothing, only operations whose traces nobody looked for.

**The tooling boundary is a graded mission.** Naming the out-of-scope target
and enforcing scope are assessed items, not briefing notes. On an engagement,
scope is the difference between a test and an incident.

---

## Framework alignment

| Tactic | Technique |
|---|---|
| Defense Evasion | T1562.001 Impair Defenses: Disable or Modify Tools |
| Defense Evasion | T1027 Obfuscated Files or Information |
| Defense Evasion | T1027.010 Obfuscated Files: Command Obfuscation |
| Defense Evasion | T1620 Reflective Code Loading |
| Defense Evasion | T1070 Indicator Removal |
| Execution | T1059.001 Command and Scripting Interpreter: PowerShell |
| Command and Control | T1071.001 Application Layer Protocol: Web Protocols |
| Command and Control | T1105 Ingress Tool Transfer |

The campaign terminates in a detection-opportunities report rather than in a
successful callback, so every technique above is assessed twice: once as
execution, once as the detection surface it exposes.
