# DFIR and Detection Range

Five range campaigns inside a five-day DFIR programme, sharing one continuity
scenario so the student works a single organisation across the week rather than
five disconnected exercises.

**60 graded missions.** The campaigns cover days 1, 2 and 4; the remaining
practical sessions use other formats, a tabletop exercise and an
instructor-led capstone, which are not documented here.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="../../diagrams/dfir-range-topology-dark.svg">
  <img alt="DFIR and detection range topology" src="../../diagrams/dfir-range-topology-light.svg" width="760">
</picture>

---

## The scenario

Meridian Logistics, a fictional freight and distribution company. The student
joins as a member of its incident response capability. The company, its estate,
its staff and its incident exist only in the range.

Continuity does real pedagogical work. By day four the student already knows the
estate, so cognitive load moves off orientation and onto the technique being
taught. It also lets an artifact introduced early be recontextualised later,
which is how real investigations actually feel: the thing you logged on Monday
turns out to matter on Thursday.

## The arc

**Foundations & Evidence Orientation** establishes the discipline before the
pressure arrives: what evidence is, how it is handled, what breaks
admissibility, and what the estate looks like.

**First-Response Triage** puts the student into a live incident with the
constraints first responders actually face: incomplete information, a running
system, and decisions that foreclose options if taken in the wrong order.

**Detection & Log Analysis** moves from response to detection, validating
alerts, separating true positives from false, and scoping indicators across the
estate.

**Triage & Severity Scoring** adds the part most training omits. There is more
work than time. The student prioritises a queue, scores severity with CVSS, and
absorbs a threat-intelligence inject that merges two apparently separate alerts
into one campaign.

**Live Volatile Collection** returns to the host to collect volatile evidence in
order of volatility, where the act of collecting changes what is there.

## Teaching approach

**Easy missions are load-bearing.** The programme opens with orientation
questions that look trivial next to a chain-of-custody problem. They exist to
build the habit of establishing context first, and to let a student who has
never touched a range succeed inside ten minutes.

**Rules are taught after the artifacts they govern.** Chain of custody is
introduced once the student has located a registry hive, not before. Teaching
the rule first produces a memorised definition; teaching it second produces an
understanding of why the rule exists.

**Time and identity before findings.** Anchoring the host timezone is a single
low-mark mission placed early, and it governs every timestamp reported for the
rest of the week. Get it wrong and a correct finding becomes a wrong one. Making
it graded forces the habit.

**Destination before collection.** The volatile campaign asks where output goes
before it asks the student to collect anything, because a collection written to
the compromised disk overwrites the unallocated space that may hold the
evidence. Students reliably get this wrong when they meet it later.

**The student analyses their own capture.** Handing over a prepared memory image
teaches analysis. Making them produce the capture first teaches that the quality
of an analysis is bounded by the quality of the collection.

**Judgement is assessed, not just procedure.** The containment mission has a
defensible answer rather than an obvious one. Pulling the cable, killing the
process and shutting the host down all stop the bleeding and each costs
something irreplaceable. The reasoning is the assessed content.

**Standards are named, not paraphrased.** NIST, ACPO, CVSS and order of
volatility are cited by name so a student leaves with vocabulary they can carry
into a real team and a real courtroom.

## Learning outcomes

A student who completes the range can:

- Apply a recognised incident response life cycle and place any given activity
  correctly within it
- Handle digital evidence to a standard that survives handover, including
  integrity hashing and chain-of-custody recording
- Establish host and estate context under first-response constraints without
  destroying volatile state
- Locate persistence by more than one mechanism
- Read an authentication log and reconstruct an access attempt: source, volume,
  target account, timing
- Pivot an indicator across data sources, from authentication to network to
  process to file
- Score an incident with CVSS v3.1 and construct a defensible vector string
- Prioritise a queue of concurrent incidents and articulate why severity and
  priority are not the same thing
- Collect volatile evidence in order of volatility to a sound destination
- Choose a containment action that preserves the evidence needed afterwards

## Why it matters operationally

**The authentication log is where most intrusions become visible first.** The
sequence the student practises, source then volume then target then timing, is
the shape of nearly every credential-based intrusion, which is why it is drilled
as a sequence rather than as four separate lookups.

**Investigations that stay in one data source find only what that source
records.** The pivot is the assessed skill because it is the one that separates
an analyst from a log reader, and it is the step where real investigations stall.

**Triage failure is a capacity problem, not a knowledge problem.** Real SOCs
have more alerts than analysts. Treating a CVSS score as the decision, rather
than an input to it, is the most common failure in junior triage and the reason
a lower-scoring incident on a business-critical system can outrank a higher
score elsewhere.

**Volatile evidence is lost by the responder more often than by the adversary.**
Order of volatility exists because the wrong first action destroys the thing you
came for. Teaching the destination decision before the collection reflects the
order in which the damage actually happens.

**Deprecated tooling still runs the estate.** The collection uses a tool a
student will meet on older servers, and a mission asks what replaced it.
Teaching only the modern tool leaves a responder stuck in front of a 2012 box.

## Framework grounding

| Framework | How it is used |
|---|---|
| **NIST SP 800-61** Computer Security Incident Handling Guide | The incident response life cycle, its phase boundaries, and the precursor / indicator distinction used in its SP 800-61 sense |
| **ISO/IEC 27037** | Identification, collection, acquisition and preservation of digital evidence |
| **ACPO** Good Practice Guide for Digital Evidence | The handling principles applied to live decisions on a running host |
| **RFC 3227** | Order of volatility, governing the live collection sequence |
| **CVSS v3.1** | Base metrics, base score, severity rating, vector string construction |
| **MITRE ATT&CK** | The adversary behaviour present in the telemetry the student investigates |
| **MITRE D3FEND** | Alert validation, indicator scoping and evidence analysis as named defensive techniques |
| **NICE / DCWF 511 and 531** | The work roles the campaigns assess against: Cyber Defense Analyst and Cyber Defense Incident Responder |

## What building this required

**The telemetry had to be produced before it could be investigated.** A
detection exercise is only honest if the evidence in it is the evidence the
technique actually leaves. That means performing the intrusion, not describing
it, and knowing what each step emits across authentication, process, network and
registry sources.

**Evidence had to be planted where it genuinely lands.** A persistence artifact
in the wrong registry path, or a dropped file with an implausible timestamp, is
a mission that teaches the wrong lesson. Placement required knowing the
attacker's behaviour and the host's recording behaviour at once.

**The benign background had to be real enough to hide in.** An investigation is
only an investigation if the signal sits inside noise. Building an estate whose
normal activity is plausible is a larger job than building the intrusion.

**Grading demanded deterministic evidence.** Every graded answer has to be
something the environment reliably produces and the student can reach by doing
the taught work. That constrains the intrusion design as much as the mission
design.

## The environment

A segmented corporate estate: domain infrastructure, user workstations, servers,
and the security tooling an analyst works through. Students hold the access an
analyst would hold, not administrative access to everything.

## Campaigns

| Day | Campaign | Missions |
|---|---|---|
| 1 | [Foundations & Evidence Orientation](01-foundations-evidence-orientation.md) | 13 |
| 1 | [First-Response Triage](02-first-response-triage.md) | 11 |
| 2 | [Detection & Log Analysis](03-detection-log-analysis.md) | 12 |
| 2 | [Triage & Severity Scoring](04-triage-severity-scoring.md) | 12 |
| 4 | [Live Volatile Collection](05-live-volatile-collection.md) | 12 |
| | **Total** | **60** |

---

> **Confidentiality.** These cyber ranges were designed and built for private
> clients. This page documents design and architecture only. Scenario content,
> mission structure, answer keys and walkthroughs remain confidential, and are
> neither published here nor available on request.
