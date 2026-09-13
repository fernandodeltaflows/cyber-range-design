# Foundations & Evidence Orientation

**Range:** DFIR and detection · **Day:** 1 · **Missions:** 13

## Scenario

The student's first contact with the estate. Before any incident, before any
pressure: learn the ground, learn what evidence is, and learn the rules that
govern handling it.

## Learning objectives

- Define the scope of digital forensics and incident response
- Establish basic orientation on an unfamiliar host
- Place a response activity correctly in the incident response life cycle
- Locate the principal sources of evidence on a Windows system
- Explain chain of custody and why integrity hashing exists
- Apply the ACPO principles to a handling decision

## Structure

| Block | Focus | Missions |
|---|---|---|
| Know your environment | Orientation on the host and the estate | 6 |
| The incident response life cycle | Ordering the phases | 1 |
| Where evidence lives on Windows | Event logs, prefetch, registry hives | 3 |
| Integrity and custody | Hashing, custody records, ACPO | 3 |

## The chain

The campaign is deliberately ordered from the mundane to the consequential.

It opens with orientation - identity, hostname, addressing, build, local
accounts - because a responder who cannot describe the machine they are on
cannot describe what changed on it. These are easy missions by design; they
build the habit of establishing context first.

It then places that activity inside the life cycle, so the student has a frame
for everything the rest of the week will do.

Only then does it introduce evidence sources, and only after that, the rules for
handling them. Teaching custody before the student knows what an artifact is
produces a memorised definition. Teaching it after they have located a registry
hive produces an understanding of why the rule exists.

## Design notes

**The easy missions are load-bearing.** Six orientation questions look trivial
next to a chain-of-custody question. They exist to establish a routine that the
later campaigns depend on, and to let a student who has never touched a range
succeed in the first ten minutes.

**Hashing is taught as a custody mechanism, not a command.** The mission asks
for the hash of an evidence file, but the mission beside it asks what chain of
custody is for. Separating the two stops the technique being learned without
the reason.

**Standards are named.** ACPO and the NIST life cycle are cited directly rather
than paraphrased, so a student can carry the vocabulary into a real team.

---

## Framework alignment

| Standard | Where it is used |
|---|---|
| **NIST SP 800-61** Computer Security Incident Handling Guide | The incident response life cycle and the ordering of its phases |
| **ISO/IEC 27037** | Identification, collection, acquisition and preservation of digital evidence |
| **ACPO** Good Practice Guide for Digital Evidence | The handling principles applied to a live decision |
| **MITRE D3FEND** | Evidence sources framed as defensive observation surfaces |

Standards are cited by name in the campaign itself rather than paraphrased, so a
student leaves with vocabulary they can carry into a real team.
