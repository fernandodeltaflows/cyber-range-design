# AD Enumeration & Path Discovery

**Range:** Adversary emulation · **Day:** 1 of 3 · **Duration:** 4 hours
**Difficulty:** Medium · **Missions:** 19

## Scenario

The student holds an authorised low-privilege foothold on a member workstation
inside an isolated lab Active Directory domain. No administrative rights, no
prior knowledge of the estate, and no map.

The task is the one that opens every real engagement: work out where you are,
what the domain looks like from here, and which routes exist between this
foothold and anything that matters.

## Learning objectives

- Explain PowerShell's role in authorised AD enumeration and path discovery
- Automate host and domain reconnaissance using built-in PowerShell
- Enumerate a domain with PowerView to the point of reading its trust and
  privilege relationships
- Collect and interpret graph data to identify routes from a foothold toward
  high-value targets
- Critically review AI-generated PowerShell before running it
- Describe what each of these activities looks like to a defender

## Environment

| Role | Purpose |
|---|---|
| Domain controller | The directory the student enumerates |
| Member workstation | The student's starting foothold |
| Servers | Supply the privilege relationships that make path discovery non-trivial |
| Operator host | Tooling workstation the student launches from |

The student begins as a standard domain user with interactive access to the
foothold only. Credentials are issued at delivery and are not published.

## Structure

| Block | Focus | Missions |
|---|---|---|
| A | Foothold and host reconnaissance | 6 |
| B | Domain enumeration with PowerView | 8 |
| C | Graph collection and lateral-movement path discovery | 5 |

**Block A** stays on the machine the student is standing on: operating context,
host identity, the services running and the identities they run as, and who
administers the box. It closes by profiling a second host, which is the first
time the student looks outward.

**Block B** moves into the directory: sizing the user and computer populations,
locating the controller, and finding the accounts and rights that matter -
service accounts with SPNs, human domain admins, and the ACL right that turns
an ordinary object into a route.

**Block C** converts a flat list of objects into a graph and reads it. The
student collects with SharpHound, analyses in BloodHound, and identifies the
pivot account, the AdminTo relationship and the GenericAll holder. The block
ends on a defensive question: given this graph, which single edge would you cut?

The final mission of the campaign hands the student AI-generated PowerShell and
asks what is wrong with it.

## The chain

The ordering is the teaching content, not administrative convenience.

1. **Profile the host you are on** before querying anything else. You cannot
   judge what the domain tells you without knowing your own position in it.
2. **Establish domain context** - move from local to directory.
3. **Enumerate principals and relationships** - users, groups, memberships,
   and the rights between them.
4. **Discover paths** - turn objects into a graph.
5. **Interpret the graph** - the final step is analytical rather than
   technical. A path that exists is not a path worth taking.

Blocks A and B use built-in PowerShell before any tooling is introduced.
A student who reaches for a tool before understanding what the operating system
already exposes learns the tool rather than the technique, and is helpless the
moment the tool is unavailable.

## Tooling exercised

Built-in PowerShell, PowerView, SharpHound, BloodHound.

## Design notes

**Answers are environment-derived.** Every graded value has to be produced by
querying the range. A mission answerable from prior knowledge measures what the
student arrived with, not what the range taught.

**The defensive cut is the point of Block C.** The graph missions could have
ended at "find the path." Asking which edge to remove forces the student to
reason about the relationship rather than follow the tool's own highlighting,
and it is the mission that most reliably separates students who understand the
graph from students who can operate BloodHound.

**Difficulty comes from analysis, not obscurity.** The intended hard step is
reading the path graph and judging which route is worth taking. Difficulty
manufactured by hiding things is fragile: it disappears the moment one student
tells another where to look.

---

## Framework alignment

Techniques exercised, mapped to MITRE ATT&CK Enterprise. This is a
technique-level correspondence describing what a student actually performs, not
a formal control mapping.

| Tactic | Technique |
|---|---|
| Discovery | T1033 System Owner/User Discovery |
| Discovery | T1082 System Information Discovery |
| Discovery | T1007 System Service Discovery |
| Discovery | T1087.002 Account Discovery: Domain Account |
| Discovery | T1069.002 Permission Groups Discovery: Domain Groups |
| Discovery | T1018 Remote System Discovery |
| Discovery | T1482 Domain Trust Discovery |
| Execution | T1059.001 Command and Scripting Interpreter: PowerShell |

The defensive counterpart is covered throughout: each technique is paired with
the telemetry it produces, which is where MITRE D3FEND and the detection side of
the DFIR range meet this one.
