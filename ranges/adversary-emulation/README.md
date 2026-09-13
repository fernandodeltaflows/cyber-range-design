# Adversary Emulation Range

Three campaigns over three days against an isolated lab Active Directory
domain. The student works as an operator on an authorised engagement, and every
technique is framed as emulation carried out to improve the defender.

**67 graded missions.** Built for an expert-level audience: penetration
testers, red team operators, SOC analysts who run threat emulation, and Windows
post-access specialists.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="../../diagrams/adversary-emulation-topology-dark.svg">
  <img alt="Adversary emulation range topology" src="../../diagrams/adversary-emulation-topology-light.svg" width="760">
</picture>

---

## The arc

The three days follow the shape of an authorised engagement, and the ordering
is the teaching content rather than administrative convenience.

**Day 1 is about knowing the ground.** You cannot move through an environment
you have not mapped, so the range opens with host and domain profiling. The
student finishes holding a picture of the domain and the routes across it,
which is the input the next day consumes.

**Day 2 is about moving through it.** Working from the paths Day 1 discovered,
the student reuses token context, moves between hosts by more than one channel,
escalates where the environment permits, and establishes persistence under
controlled conditions.

**Day 3 is about doing so quietly.** Having established access, the student has
to keep it against a defender who is watching: script-block and transcription
logging, in-memory inspection, and a C2 channel that has to survive contact.

Each day is playable alone, but the sequence is the point. Day 2 assumes the map
Day 1 produced; Day 3 assumes the access Day 2 established.

## Teaching approach

Six decisions shape how this range teaches, and each of them cost something to
implement.

**Built-ins before tooling.** Blocks that could have opened with PowerView or
BloodHound instead open with what the operating system already exposes. A
student who reaches for a tool before understanding the underlying object model
learns the tool, and is helpless the moment it is unavailable or blocked.

**Every technique is paired with its telemetry.** This is a Red-stream course
taught for active defense, so each offensive step is followed by the question of
what the defender sees. The final campaign terminates in a
detection-opportunities report rather than in a successful callback.

**More than one way to do it, then a choice.** Lateral movement is taught three
ways and then assessed on which is quietest. Teaching one channel produces
students who use it everywhere; teaching three and asking them to choose
produces operators.

**Confirm the environment before acting on it.** The stealth campaign opens by
proving what logging is actually enabled rather than assuming a default. Every
evasion technique afterwards is measured against observed reality.

**Cleanup is graded.** Establishing persistence and being unable to
demonstrably remove it is an unfinished exercise and, on a real engagement, a
liability left behind. Proving the host is clean is a scored mission.

**AI-generated code is treated as untrusted input.** Students are given
generated PowerShell containing a cmdlet that does not exist and a target
outside engagement scope. They find both, verify properly, enforce scope, and
run a hardened version. This is now how offensive scripts actually get written,
and the place to learn that lesson is a lab.

## Learning outcomes

A student who completes the range can:

- Profile a Windows host and an Active Directory domain using built-in tooling
  alone, and explain what each query exposes
- Collect and interpret graph data to identify routes from a foothold toward
  high-value targets, and judge which routes are worth taking
- Reuse credential and token material to move laterally by service execution,
  WMI and WinRM, and select a channel on operational grounds
- Identify, validate and simulate a privilege-escalation path
- Establish persistence by three distinct mechanisms and describe the telemetry
  signature of each
- Operate against script-block logging and in-memory inspection, and recognise
  the tells their own evasion leaves
- Integrate with a C2 framework end to end: listener, stager, callback, tasking
- Review AI-generated offensive code critically before executing it
- Produce a detection-opportunities report a blue team can act on

The last outcome is the one that matters most. A student who can run a domain
enumeration but cannot tell a SOC which log sources would have caught it has
learned half the lesson.

## Why it matters operationally

The techniques here are not exotic. They are the ones that appear in real
intrusions precisely because they are reliable and quiet.

**Directory enumeration is the universal first move.** Every intrusion that
reaches an Active Directory environment has to answer the same questions the
student answers on Day 1: who am I, what can I reach, and what is worth
reaching. The graph relationships that BloodHound surfaces are the same ones
that turn a foothold into domain compromise.

**Living-off-the-land is the norm, not the exception.** WMI, WinRM, scheduled
tasks and registry autoruns are native administrative machinery. That is what
makes them attractive to an adversary and hard for a defender: the same event
that indicates compromise also indicates a Tuesday afternoon.

**Persistence is where intrusions become incidents.** An intrusion that is
evicted is an alert. One that survives eviction is a breach. The range teaches
three mechanisms because defenders who check only one develop a blind spot an
adversary relies on.

**The defender is now instrumented.** Script-block logging, transcription and
in-memory inspection changed what offensive operations have to account for. The
campaign teaches operating against them honestly, including the finding students
least expect: cleanup leaves traces too.

## Framework grounding

| Framework | How it is used |
|---|---|
| **MITRE ATT&CK Enterprise** | Every campaign carries a tactic-and-technique alignment table. Coverage spans Discovery, Credential Access, Privilege Escalation, Lateral Movement, Persistence, Defense Evasion, Execution and Command and Control |
| **MITRE D3FEND** | The defensive counterpart. Each technique is paired with the observation surface it exposes, which is what makes the detection report at the end of Day 3 possible |

The ATT&CK mapping is a technique-level correspondence describing what a student
actually performs, not a formal control mapping.

## What building this required

The range could not have been designed by someone who only teaches, and it is
worth being explicit about why.

**Every technique had to work in the environment before it could be graded.**
An emulation range is not a slide deck: the domain has to be misconfigured in
exactly the way the escalation mission requires, the service account has to
carry the SPN the enumeration mission finds, and the graph has to contain a real
path rather than a described one. Building it meant standing the estate up,
running the technique, and confirming it produced the artifact the mission asks
for.

**Grading forced the offensive work to be precise.** A mission whose answer is
"whatever you found" cannot be scored. Every graded value had to be anchored to
something the environment deterministically produces, which means knowing not
just that a technique works but exactly what it emits.

**The defensive half had to be built alongside it.** Pairing each technique with
its telemetry required knowing what the logging actually captures, which is
defensive engineering rather than offensive tradecraft.

## The environment

An isolated Active Directory domain with a domain controller, member
workstations and file and application servers. The student starts from an
authorised low-privilege foothold, with no administrative rights and no prior
knowledge of the domain.

The range has no route to anything outside itself. Every host, account, domain
and organisation in it is invented.

## Framing

The vocabulary is operator, lab host, emulation and post-access operations
rather than attacker and victim, because the language shapes how the work is
understood and governed. Where a tool's own documentation uses different terms,
the tool's terms are used while teaching it and the surrounding narrative keeps
the engagement framing.

## Campaigns

| Day | Campaign | Missions |
|---|---|---|
| 1 | [AD Enumeration & Path Discovery](01-ad-enumeration.md) | 19 |
| 2 | [Movement, Privilege Escalation, Persistence](02-movement-privesc-persistence.md) | 26 |
| 3 | [Stealth, Payload Handling, C2](03-stealth-payload-c2.md) | 22 |
| | **Total** | **67** |

---

> **Confidentiality.** These cyber ranges were designed and built for private
> clients. This page documents design and architecture only. Scenario content,
> mission structure, answer keys and walkthroughs remain confidential, and are
> neither published here nor available on request.
