# Live Volatile Collection

**Range:** DFIR and detection · **Day:** 4 · **Missions:** 12

## Scenario

A host is live, compromised, and cannot simply be pulled. Evidence is
disappearing as the student watches, and the act of collecting changes what is
there. Collect it in the right order, to the right place, and find the intruder
in what you captured.

## Learning objectives

- Apply order of volatility to a live collection
- Select a defensible output destination for collected evidence
- Capture live system state and integrity-hash the outputs
- Identify a beacon process, its image path and its C2 endpoint
- Locate the persistence mechanism and hash the binary
- Choose a containment action that preserves evidence
- Identify the modern replacement for a deprecated collection tool

## Structure

| Block | Focus | Missions |
|---|---|---|
| Collect in the right order | Order of volatility, output destination | 2 |
| Capture the live state | Running the collection set, hashing outputs | 2 |
| Find the intruder | Beacon process, image path, C2 address, C2 port | 4 |
| Persistence and the binary | Run key, binary hash | 2 |
| Contain without destroying | Evidence-preserving containment, tooling succession | 2 |

## The chain

The campaign inverts the usual teaching order deliberately. It does not start
with "find the malware." It starts with **where the output goes**, because a
collection written to the compromised disk overwrites the unallocated space that
may hold the evidence.

Order of volatility then governs the capture itself. Only once the student has
captured correctly do they analyse what they captured - beacon, path, endpoint,
port - which means the analysis is performed on their own evidence rather than
on something handed to them.

The closing block is the hardest judgement in the campaign: containment that
does not destroy evidence. Pulling the network cable, killing the process and
shutting the host down all stop the bleeding and each costs something
irreplaceable.

## Design notes

**Destination before collection.** The second mission of the campaign is where
to write output. It is placed before any collection because getting it wrong
invalidates everything after it, and because students reliably get it wrong
when they meet it later.

**The student analyses their own capture.** Handing a student a prepared memory
dump teaches analysis. Making them produce the capture first teaches that the
quality of an analysis is bounded by the quality of the collection.

**Containment is a trade-off, not a procedure.** The mission has a defensible
answer rather than an obvious one, and the reasoning is the assessed content.

**Deprecated tooling is taught with its successor.** The collection uses a tool
the student will meet on older estates, and a mission asks what replaced it.
Teaching only the modern tool leaves a student stuck on a 2012 server.
