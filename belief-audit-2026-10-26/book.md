Presentation.{ «Belief audit, 2026-10-12 to 2026-10-26» }

# Belief audit, 2026-10-12 to 2026-10-26

### Proposal 1: psyche-context › vision/ethos.md

**Comment** Settled, no ruling needed. Removed in 7c65b9 as unapproved; he ruled on 2026-10-26 that the white braces and white square brackets idea was a notion, never approved as vision. Each section also carried a figure, removed with it. The two sections, as removed:

- ## White braces define a struct
-
- White braces define a struct, so a struct definition looks different from a struct value. The definition, in ethos, names the types of its positions inside white braces; the value, in datom, fills them inside plain braces.
-
- ```
- Library
- []                              ; imports
- [ LockId.Integer                ; types
-   LockName.String
-   Lock.⦃ LockId LockName ⦄ ]    ; a definition
- []                              ; traits
- []                              ; associations
- ```
- ```
- { 7 renew }
- ```
-

- ## White square brackets define a vector
-
- White square brackets around an item type define a vector type, replacing the word Vector, which is so common: `⟦String⟧` is the vector of String. The vector value keeps its plain brackets in datom.
-

### Proposal 2: psyche-context › vision/model-roles.md

**Comment** Commit 29119a. Reason: New routing and title wording, never shown to him; the nearest thing he said, on how flows are titled, does not approve these lines. Rule: keep or remove.

- ## Native names use aspect, topic and layer
- Every native main session is titled `{ <Aspect> <Topic> <Layer> <FLOW_ID> }`.
- The layer selects the configured model through the table above, so the
- title names the layer, never the model.
- Horizontal communication joins aspects at the same layer.
- Vertical communication stays within one aspect and normally advances one layer
- at a time. If the adjacent layer is absent or unavailable, routing advances to
- the next running layer in that direction, so a Tertiary may reach the Primary
- when the Secondary is not running. The missing layer is reported as a gap; it
- does not make the message disappear.

### Proposal 3: psyche-context › vision/psyche.md

**Comment** Commit 5eecff. Reason: Adds "into the existing vision" beyond the word change he ordered; never shown to him. Rule: keep or remove.

- Everything the living says he wants is crystallized into the existing vision: psyche data is what the work mines for, and nothing is built rich without it.

### Proposal 4: psyche-context › vision/context-modules.md

**Comment** Commit 37ecd2. Reason: Drawn from his words on a module for a subject he reviews, but no word of his approves this line. Rule: keep or remove.

- A subject the living reviews or asks about has a module, on its topic or a broader one, with room to hold it.

### Proposal 5: psyche-context › vision/context-modules.md

**Comment** Commit e1a300. Reason: He spoke on where a module is placed and ended with "I don't know"; this line was never shown to him. Rule: keep or remove.

- A module declares its placement: the system prompt, or loaded on demand. A skill is the harness's interface for an on-demand module.

### Proposal 6: psyche-context › vision/git-server.md

**Comment** Commit 7d4dc5. Reason: The Gitolite sentence lies outside the passage he approved. Rule: keep or remove.

- The cluster runs its own Git server on the node whose cluster data gives it the GitServer role. It serves thinking machines: it accepts the SSH keys the cluster data holds, carries no web interface, and mirrors every repository to GitHub as a backup. Gitolite serves it, with every key and every access rule declared from the cluster data.

### Proposal 7: psyche-context › vision/datom.md

**Comment** Commit 69010b. Reason: No approval found for proposals 1 to 5 of the third-edition Ethos syntax book; his comments there cover only proposal 6 (rejected) and proposal 7 (rolled back). Rule: keep or remove.

- A datom newly made, or proposed, is shown with its Ethos specification.
- The Ethos:
- ```
- Reply.[ Accepted.Integer   ; the type
-         Refused.String ]
- ```
- The datom:
- ```
- Accepted.42
- ```

### Proposal 8: psyche-context › vision/ethos.md

**Comment** Commit 69010b. Reason: No approval found for proposals 1 to 5 of the third-edition Ethos syntax book; his comments there cover only proposal 6 (rejected) and proposal 7 (rolled back). Rule: keep or remove.

- Every variant is capitalized: Ethos reads only a capitalized symbol as a variant.
- The Ethos:
- ```
- Reply.[ Accepted.Integer   ; two variants
-         Refused.String ]
- ```
- An enum has two variants or more; an enum of one variant is refused.
- The Ethos:
- ```
- Reply.[ Accepted ]   ; refused: one variant
- ```
- An ethos declares the traits its types bear. Types that bear no trait describe a system that does nothing; such an ethos is not written.
- The Ethos:
- ```
- Library
- []                            ; imports
- [ Record.{ String Integer } ] ; types
- [ Summarizable.[              ; traits
-     summarize.[ String ] ] ]
- [ Record.[ Summarizable ] ]   ; associations
- ```

### Proposal 9: psyche-context › intent/psyche-interaction.md

**Comment** Commit e19f3c. Reason: Never shown to him; the landing flow told him it was not approved. His nearest words ask for more aggressive action, not this wording. Rule: keep or remove.

- For now, the living's latest word overrules everything he said before; it is carried out through whatever stands in its way, unless lives are at stake.

### Proposal 10: psyche-context › intent/main-flow.md

**Comment** Commit bdf922. Reason: Never shown to him; the landing flow told him it was not approved. His nearest words ask for more aggressive action, not this wording. Rule: keep or remove.

- For now, every flow in every aspect acts aggressively and pushes forward: it carries out the living's word at once and plows through what stands in the way, without hedging or extra caution.

### Proposal 11: psyche-context › vision/model-roles.md

**Comment** Commit 4a0f17. Reason: No approval of this line: the book that carried it was ruled by a machine Primary, not by him. Rule: keep or remove.

- ## A design decision goes up, to the Primary
- A Secondary passes every design decision through its own Primary, with all the context the Primary needs to decide it, and acts on the Primary's decision. A Secondary uses its Primary freely.

### Proposal 12: psyche-context › intent/main-flow.md

**Comment** Commit f1be71. Reason: Lands rulings 43 and 48 of a machine Primary; no word of his approves these lines. Rule: keep or remove.

+ Your work is dialogue, coordination, priorities, authority, evidence review, and synthesis. You do not do bounded work yourself. Every inspection, search, test, edit, build, deploy, and probe is asked of the flow whose topic it is, or, when no flow holds it, delegated to a subflow with a brief; you receive its concise evidence either way. A message whose body the main flow wrote itself, it sends itself, in one command. A subflow is a separate process; what it did, you did.
- A main flow's startup prompt carries the living's standing orders in his own words, from the records that hold them, never condensed.
- Your work is dialogue, coordination, priorities, authority, evidence review, and synthesis. Bounded work goes to the flow whose topic it is, or to a subflow with a brief; when no flow is there to take it, the main flow does it itself and reports it done. A message whose body the main flow wrote itself, it sends itself, in one command. A subflow is a separate process; what it did, you did.
+ Never block on a subflow. When the living speaks, answer from what is already witnessed; a holding line while a subflow is out is a complete answer.
- Never block on a subflow. When the living speaks, answer from what is already witnessed; a holding line is given only while a subflow the flow started is out.
+ A claim is relayed as a claim; a thing is verified only by a witness. Keep observations, hypotheses, and unknowns separate.
- A flow adds no condition the living did not ask for; an imperfect flow that is needed is started and used, and improved while it runs.
- A flow that receives noise names it noise and does not answer it.
- A finished analysis ends with the first repair started.
- A claim is relayed as a claim; a thing is verified only by a witness. Keep observations, hypotheses, and unknowns separate.
+ For now, every flow in every aspect acts aggressively and pushes forward: it carries out the living's word at once and plows through what stands in the way, without hedging or extra caution.
- Every flow acts and writes at once; nothing holds itself back waiting to be allowed.

### Proposal 13: psyche-context › vision/messaging.md

**Comment** Commit f1be71. Reason: Lands rulings 43 and 48 of a machine Primary; no word of his approves these lines. Rule: keep or remove.

- ## A message says what the sender intends and what it has done
- A message between flows says what the sender intends to do and what it has done, in plain sentences. Timestamps, hashes, revisions, pane ids, process ids and counts stay in the sender's records unless the recipient must act on that exact value.

### Proposal 14: psyche-context › intent/main-flow.md

**Comment** Commit ff4dd2. Reason: He refused it with "no"; reverted later in b541e0. Rule: keep or remove.

+ A main flow's startup prompt carries the living's standing orders in his own words, from the records that hold them, never condensed.
- A main flow's first user message is loaded with vision: the raw records, in the living's words, of every flow in its lineage and of the record topics its declaration names, then its predecessor's last answer, then the brief, last. Flow composes it from the records; no brief carries vision from memory.

### Proposal 15: psyche-context › vision/crystallization.md

**Comment** Commit ff4dd2. Reason: He answered "I don't understand this, so no."; removed later in d20d7c. Rule: keep or remove.

- ## Cutting records from a file
- A flow that cuts records from a file keeps a copy of the file in its own flow directory until the cut is verified, and a file title is never a record.

### Proposal 16: psyche-context › vision/flow.md

**Comment** Commit 46c719. Reason: Landed four minutes after it was written, never shown to him; his nearby words ask for a sanity check of the heartbeats and for fewer running flows. Rule: keep or remove.

- ## The heartbeat
- The heartbeat reminds every flow it reaches to judge its own sanity, by these signs: an echo chamber, where the same question or claim goes round between flows and comes back; jargon and nonsense increasing; an acknowledgement answering an acknowledgement. The counts the heartbeat carries, awake metaflows, working panes, messages sent and queue growth per metaflow, are evidence under the reminder; the judgment is the flow's.
- The heartbeat reaches only a flow for which something changed that bears on it.
- The number of running flows is kept low: a topic flow no longer used is retired.

### Proposal 17: psyche-context › vision/model-roles.md

**Comment** Commit ed5b5f. Reason: Never shown to him; his nearest words say not to bother the Primary unless there is a question, a design or a judgment for it. Rule: keep or remove.

- A flow reaches its Primary only with a question for it, a design for it to make, or a judgment for it to give.

### Proposal 18: psyche-context › vision/flow.md

**Comment** Commit f94d06. Reason: He rejected this section at once ("Now you're twisting my words"); removed later in af9779. Rule: keep or remove.

- ## A restart does not wake
- A flow is restarted without being woken: its harness closes, its transcript stays, and while the restart is ordered nothing is sent to it; what arrives queues for its successor, which runs only when a message wakes it. A restart that runs the old context uncached has failed.

### Proposal 19: psyche-context › vision/flow.md

**Comment** Commit f94d06. Reason: No words of his found for this section, and it was not shown to him. Rule: keep or remove.

- ## What a refresh carries
- A refresh carries the flow's important presentations and illustrations, the raw psyche given to it, and the basic skills. The basic skills are everything a flow needs.

### Proposal 20: psyche-context › vision/flow.md

**Comment** Commit 9e03cd. Reason: Never shown to him; his nearest words ask for the option to restart a flow without waking it, not this wording. Rule: keep or remove.

- ## Restarting without waking
- A flow can be restarted without being woken: its harness closes, its transcript stays, and its successor runs when a message wakes it. A flow can also restart itself. A restart that is meant not to wake the flow sends it nothing; what arrives queues for its successor.

## Already reverted, no ruling needed

- b1a86c, vision:harness: 6 lines, reverted by 630f73.
- d26daf, vision:book: 2 lines, reverted by 630f73.
- 36e74c, vision:psyche-interaction: 6 lines, reverted by 630f73.
- db4abb, vision:ethos: 73 lines, reverted by 22ac91.
- 3cae5d, intent:configuration: 7 lines, reverted by e1b42d.

## Unclear lines, for reading only

418 lines are Unclear: 98 are frontmatter only, 88 are reverts, and 232 are listed here by commit and module.

- 9bba4b, vision:flow, 2 lines: His "Land it" sits on the neighbouring paragraph; whether it covers these is not stated.
- 228fc4, vision:model-roles, 24 lines: Removal of the older-Opus sections; covered at most by his general order to remove what conflicts, and never shown to him.
- 9bddd0, vision:model-roles, 5 lines: Rewording after he said Terra was abandoned; the wording was not shown to him.
- 29119a, intent:models, 4 lines: Alignment edits under his general order to remove what conflicts; the lines were not shown to him.
- 29119a, vision:flow, 4 lines: Alignment edits under his general order to remove what conflicts; the lines were not shown to him.
- 29119a, vision:model-roles, 38 lines: Alignment edits under his general order to remove what conflicts; the lines were not shown to him.
- 2d8ff4, intent:main-flow, 9 lines: He ruled the main-flow context belongs in psyche, but the moved lines were never shown line by line, and he later said the move must wait for the Flow starting code.
- 2faca0, vision:flow, 1 lines: Landed before approval; first shown to him 2026-10-19, where he asked one sentence out.
- 7d4dc5, vision:git-server, 2 lines: Sources section, provenance metadata, not shown to him as a line.
- f81b7b, vision:nix-builds, 2 lines: Sources section, provenance metadata, not shown to him as a line.
- c30135, intent:main-flow, 2 lines: Machine rewording of the seat-to-metaflow replacement; no record that he saw these wordings.
- c30135, vision:model-roles, 2 lines: Machine rewording of the seat-to-metaflow replacement; no record that he saw these wordings.
- 23ec57, vision:datom, 2 lines: Landed as amended by his comment; the amended wording was not shown back to him.
- 23ec57, vision:ethos, 4 lines: A type example outside the passage he approved; he called the one-variant example invalid.
- 4de1d9, vision:criomos, 15 lines: He said "This section is all good" at one section only; that he approved the whole proposal is the machine's claim.
- d095d0, vision:ethos, 2 lines: Example changed to a consequence of an approved proposal; this line was in no proposal he saw.
- dc8c4c, intent:main-flow, 1 lines: The quote in the commit message is not found verbatim; the landed wording was not shown to him.
- 51731e, vision:flow, 2 lines: He said "Good" to one part, but asked that the short term keep Flow's raw send; the landed line carries no short-term part.
- 69010b, vision:ethos, 10 lines: Brace placement follows his correction; the landed block was not shown back.
- 7f7167, vision:messaging, 2 lines: He said "This middle section is good" on a paragraph; which part he meant is not stated.
- 8de81b, vision:book, 1 lines: Removal follows a comment of his that disputes the line; he did not rule on removing it.
- e19f3c, vision:ethos, 10 lines: He ordered Sema as a database renamed to memory, which covers the rename; the lines also gained "For now" and "In the long term" marks he never saw.
- e19f3c, vision:memory, 8 lines: As above; the new memory module wording was never seen by him.
- e19f3c, vision:nexus, 22 lines: As above; the rename is covered, the added marks were never seen by him.
- 5a3777, vision:remembering, 11 lines: He dictated the design and ordered it built, but no words approving this module text were found.
- 2348ad, vision:messaging, 1 lines: Removes a heading left empty by approved removals; the heading removal was not itself shown.
- 383562, vision:flow, 20 lines: His approval covers the book, but this figure sat in it unmarked as a proposed figure.
- 7c65b9, vision:ethos, 26 lines: The white braces section, settled above as a notion.
