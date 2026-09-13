# Detection & Log Analysis

**Range:** DFIR and detection · **Day:** 2 · **Missions:** 12

## Scenario

An alert has fired. The student's job is to decide whether it is real, and if it
is, how far it reaches. This is the campaign that turns a single detection into
a scoped incident.

## Learning objectives

- Identify the data sources detection is built on
- Read an authentication log and reconstruct an access attempt
- Distinguish a precursor from an indicator
- Pivot from authentication evidence to network and process evidence
- Classify indicator types
- Validate an alert and produce the output the next phase needs

## Structure

| Block | Focus | Missions |
|---|---|---|
| From detection to a scoped incident | Detection data sources | 1 |
| Reading the authentication log | Source, failure count, account, timing, precursor vs indicator | 5 |
| Pivoting | C2 domain, indicator types, process, file integrity | 4 |
| Validation and handoff | Alert validation, phase output | 2 |

## The chain

The campaign is a single investigation told in the order it would actually
happen.

The authentication log block is deliberately the largest. The student
establishes where the access came from, how many times it failed before it
succeeded, which account fell, and when. That sequence - source, volume,
target, timing - is the shape of nearly every credential-based intrusion, and
practising it as a sequence is the point.

The pivot block then moves off the authentication log entirely, because an
investigation that stays in one data source finds only what that source records.
The student moves to network evidence, then to process evidence, then to the
file itself.

The campaign closes on validation and handoff rather than on the finding,
mirroring the life cycle taught on Day 1.

## Design notes

**Precursor versus indicator is placed inside the log block, not before it.**
The distinction is abstract when taught from a definition and obvious when the
student has just read both in the same log.

**The pivot is the assessed skill.** Any student can be walked through one log.
Moving from authentication to network to process, carrying an indicator across
each boundary, is what separates an analyst from a log reader.

**Integrity hashing recurs.** It appears here as it did on Day 1 and will again
on Day 4. Deliberate repetition across campaigns makes it routine rather than a
thing that was mentioned once.
