# Movement, Privilege Escalation, Persistence

**Range:** Adversary emulation · **Day:** 2 of 3 · **Duration:** 4 hours
**Difficulty:** Medium · **Missions:** 26

## Scenario

The student begins from the position Day 1 established: a mapped domain, a
known set of routes, and a low-privilege foothold. The question is no longer
where to go but how to get there, what to do on arrival, and how to still be
there tomorrow.

## Learning objectives

- Analyse identity, token and cached credential material on a compromised host
- Move laterally between hosts using service execution, WMI and WinRM, and
  choose between them on operational grounds
- Simulate privilege escalation by identifying and validating a misconfiguration
- Establish persistence by three mechanisms and describe the telemetry each
  produces
- Verify that a host has been returned to a clean state
- Critically review AI-generated persistence code

## Structure

| Module | Focus | Missions |
|---|---|---|
| 1 | Identity, token and credential analysis | 5 |
| 2 | Lateral movement: service, WMI, WinRM | 8 |
| 3 | Privilege-escalation simulation with PowerUp | 6 |
| 4 | Persistence: registry, scheduled task, WMI eventing | 7 |

**Module 1** establishes what the student actually holds: primary versus
impersonation tokens, the privileges on them, cached Kerberos material, and the
service identities present on the host. Movement without this is guesswork.

**Module 2** is the core of the day. The student recovers a movement
credential, then moves by more than one channel and compares them. The module
deliberately includes a mission on which channel is quietest and one on
validating the tooling before use.

**Module 3** runs automated checks, finds the writable path, profiles the
abusable service and validates the escalation. It closes on validating before
acting, which is the module's real lesson.

**Module 4** establishes persistence three ways and, critically, ends by
proving the host is clean again. The final mission reviews AI-generated
persistence code.

## The chain

Movement depends on credential material, so Module 1 precedes Module 2.
Escalation is more useful once you can reach more than one host, so Module 3
follows Module 2. Persistence is last because it is the thing you do once you
have something worth keeping.

The cleanup mission is not an afterthought. A student who establishes
persistence and cannot demonstrably remove it has not finished the exercise,
and on a real engagement would have left a liability behind.

## Tooling exercised

Built-in PowerShell, PowerUp, WMI and WinRM remoting, service control tooling.

## Design notes

**Three channels, not one.** Teaching a single lateral movement technique
produces students who use it everywhere. Teaching three, then asking which is
quietest, produces students who choose. The comparison mission is worth more
than any of the three execution missions individually.

**Escalation is simulated, and labelled as such.** The environment carries a
deliberate, documented misconfiguration. The student practises identification
and validation rather than exploit development, which is the skill the module
is actually for.

**Prove the host is clean.** This mission exists because it is the one students
skip. Including it as a graded item makes cleanup part of the technique rather
than an optional courtesy.
