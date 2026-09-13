# First-Response Triage

**Range:** DFIR and detection · **Day:** 1 · **Missions:** 11

## Scenario

A host is behaving oddly and the student is first on the scene. The machine is
running, the clock is ticking, and some actions foreclose others. This is the
campaign where orientation stops being an exercise.

## Learning objectives

- Describe forensic readiness and what belongs in a jump kit
- Anchor an investigation to the host's own time and user context
- Enumerate accounts and identify an anomalous one
- Locate persistence in the two places it is most often found
- Recover and integrity-hash a dropped file
- Record findings to a standard that survives handover

## Structure

| Block | Focus | Missions |
|---|---|---|
| Prepare before you touch the keyboard | Forensic readiness, jump kit | 1 |
| Anchor the when and the who | Host timezone | 1 |
| Check the accounts | Local administrators, the anomalous account | 2 |
| Know who does what | IR team roles | 1 |
| Hunt for persistence | Run key, scheduled task | 2 |
| The dropped file | Location and integrity hash | 2 |
| Document your findings | Recording context, custody fields | 2 |

## The chain

The ordering is a first responder's ordering, and the first two blocks are the
lesson.

**Preparation comes before action.** The campaign opens on readiness, before
the student is allowed to touch anything, because the most common first-response
failure is acting before establishing what you are able to act with.

**Time and identity come before findings.** Anchoring the host's timezone is a
single mission and it governs every timestamp the student will report for the
rest of the week. Get it wrong and a correct finding becomes a wrong one.

Only then does the campaign move to accounts, persistence and the artifact
itself, and it closes on documentation - because a finding nobody can hand over
is not a finding.

## Design notes

**Timezone is a mission, not a footnote.** It is a single low-mark question
placed early, and it is the one most likely to be skipped by a student in a
hurry. Making it graded forces the habit.

**Two persistence mechanisms, not one.** A run key and a scheduled task are
found by different methods. A student who only ever checks one develops a blind
spot that an intruder relies on.

**Documentation is graded.** The final two missions ask why context is recorded
and what belongs in a custody field. Investigative technique that cannot survive
handover to a colleague or a court has limited value.

---

## Framework alignment

| Standard | Where it is used |
|---|---|
| **NIST SP 800-61** | First response sits inside the Detection and Analysis phase |
| **ISO/IEC 27037** | Preservation constraints on a running system |
| **ACPO** | Principle-driven decisions about acting on live evidence |
| **MITRE ATT&CK** | The persistence mechanisms hunted are T1547.001 and T1053.005 |
| **MITRE D3FEND** | Enumeration and file analysis as defensive techniques |
