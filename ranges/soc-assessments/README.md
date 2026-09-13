# SOC Analyst Assessment Programme

A three-tier assessment programme that measures whether a SOC analyst can find
an intrusion inside telemetry, built as graded hands-on ranges rather than as a
written exam.

| Tier | Assessment | Work role | Sector | Starting position |
|---|---|---|---|---|
| **I** | [SIEM Intrusion Triage](01-soc-i-siem-intrusion-triage.md) | DCWF 511 Cyber Defense Analyst | Financial services | One detection |
| **II** | [Intrusion Containment](02-soc-ii-intrusion-containment.md) | DCWF 531 Cyber Defense Incident Responder | Electricity distribution | A triaged foothold |
| **III** | [Hunt & Attribution](03-soc-iii-hunt-attribution.md) | DCWF 141 Threat/Warning Analyst | Telecommunications | One external indicator, no incident |

Each tier is a two-hour, time-limited, numerically scored Challenge. Candidates
are ranked rather than marked pass or fail.

**The starting position column is the design.** What the candidate is handed at
minute zero is what separates the tiers: a detection, a foothold, or something
that may mean nothing at all. Each sits in a different critical-infrastructure
sector, so a candidate cannot carry estate familiarity from one tier to the next.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="../../diagrams/soc-assessment-tiers-dark.svg">
  <img alt="SOC analyst assessment tier progression and framework grounding" src="../../diagrams/soc-assessment-tiers-light.svg" width="760">
</picture>

---

## What it measures, and why that is different from teaching

A training lab teaches a technique and confirms the student performed it. An
assessment has to answer a harder question: **would this person have found it?**

That difference drives every design decision here. A lab can hand the student a
prepared artifact; an assessment cannot, because being handed the evidence is
the thing being measured. A lab can signpost; an assessment must not. A lab's
value survives being described in public; an assessment's value is precisely
that the candidate does not know what is coming.

The consequence is that the environment has to contain a genuine intrusion
buried in genuine noise, and the candidate has to reach the answer by analysis
rather than by recognition.

## Grounded in published workforce standards

The tiering is not invented. It is taken from the doctrinal ladder that already
exists, so a result means something outside the organisation that issued it.

| Framework | What it supplies |
|---|---|
| **DoD 8140 / DCWF** (DoDM 8140.03) | **The primary tiering standard.** Basic / Intermediate / Advanced, with work roles **511 Cyber Defense Analyst**, **531 Cyber Defense Incident Responder** and **141 Threat/Warning Analyst** mapping to tiers I, II and III |
| **NICE Workforce Framework** (NIST SP 800-181r1) | Work roles and the assessable Task, Knowledge and Skill statements each tier is written against |
| **MITRE ATT&CK Enterprise** | The adversary behaviour the telemetry actually contains |
| **MITRE D3FEND** (v1.3.0) | The defensive counterpart: what the analyst is expected to do about it |
| **SFIA** | Responsibility and autonomy levels, for organisations that grade on SFIA |

**Why DCWF rather than NICE for tiering.** NICE describes work roles well but
does not supply a native proficiency ladder. DCWF does, and it is doctrinal
rather than improvised, so the three tiers inherit a defensible definition of
what "more advanced" means instead of asserting one.

## The proficiency gradient

The three tiers are not three difficulty settings on one exercise. The same
competency is assessed at increasing depth:

- **Tier I** asks whether the analyst can recognise an intrusion in front of them
- **Tier II** asks whether they can act on it without destroying what it is made of
- **Tier III** asks whether they can find one nobody has flagged, and say who it
  was and what they were after

Each tier therefore requires a materially different environment, not a longer
version of the previous one. Tier I can present alerts. Tier II needs a live
estate where containment decisions have consequences. Tier III needs an
intrusion with no starting anchor at all, sitting inside enough benign history
that finding it is genuine work.

## Building this required offensive capability as well as defensive

This is the part most easily missed, and it is the reason the programme could
not have been built by a defensive specialist alone.

**You cannot measure whether someone can find an intrusion in telemetry unless
you have produced telemetry that contains a real intrusion.** Not described, not
simulated at the log line, but performed: implants and their process trees, C2
beaconing with realistic timing, named-pipe IPC, credential access, Kerberoasting,
lateral movement, service persistence, collection and staging, exfiltration, and
an objective the adversary was denied.

**A defender can only learn to recognise evidence that exists, and the only way
it exists is to perform the behaviour that leaves it.**

That imposes requirements in both directions at once:

| Offensive capability required | Defensive capability required |
|---|---|
| Execute the full intrusion chain against a live estate | Know what each step emits, across process, authentication, network, registry and application telemetry |
| Make adversary behaviour realistic in timing and sequence, not just present | Build benign background activity plausible enough that the intrusion genuinely hides in it |
| Understand tradecraft well enough to leave the artifacts an analyst would really meet | Design missions whose answers are reachable by analysis, at the right tier |
| Know which techniques leave no usable evidence, and avoid designing a mission around them | Know which evidence is decisive and which is merely suggestive |

**The two halves constrain each other.** An intrusion step that leaves no
recoverable artifact cannot carry a graded mission. A mission that asks for an
artifact the technique does not actually produce is a mission that teaches a
falsehood. Getting both right at once is the work, and it is why this sits
beside an adversary emulation range in the same portfolio rather than
accidentally near it.

## What makes the instrument unusual

**Difficulty is measured, not asserted.** Three things that most training
content collapses into one number are kept apart: what a mission was **priced**
at when authored, what a proposed change was **projected** to buy, and what a
blind solver **actually experienced**. Only the third describes the shipped
product, and only it may be quoted as the difficulty.

**Answers are anchored to the environment.** A graded answer must be derivable
only by doing the work in the range. This is applied at authoring time rather
than as a hardening pass, because retro-fitting it means re-anchoring missions
already built around the wrong property.

**Assessment integrity is treated as a threat model.** Three routes to an answer
are considered explicitly: obtaining it off-box, reading it on-box, and guessing
it. An answer readable on the host, or reachable in a handful of blind
submissions, is not an assessment question regardless of how hard the intended
path is.

**Nothing ships on the author's word.** Mechanical validation gates plus a blind
solve by someone who did not build it. A check that cannot report how much of
the population it examined is not treated as a check.

## Deliberately not documented here

Mission structure, band composition, scenario, estate, actors, difficulty
arithmetic, and anything tier-specific beyond the competency focus named above.

**These are measuring instruments, not teaching labs.** A lab's value survives
being described; an assessment's value is precisely that the candidate does not
know what is coming. The programme architecture and its framework grounding can
be shown without degrading the instrument. The content cannot.

---

> **Confidentiality.** These cyber ranges were designed and built for private
> clients. This page documents design and architecture only. Scenario content,
> mission structure, answer keys and walkthroughs remain confidential, and are
> neither published here nor available on request.
