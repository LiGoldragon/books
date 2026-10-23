Presentation.{ «The Memory producer contract: four open questions» }

# The Memory producer contract: four open questions

### Proposal 1: psyche-context › vision/memory.md

**Comment** The module as it stands, shown whole in the lines that situate the landing of Inquiries 1 and 2. Nothing in it changes; the migration comes with the edit, and the descriptor lines proposed below land after it.

  What memory is, long term

  In the long term, memory is the database engine of a Nexus, authored in Ethos so the stored types are visible; its root, Memory, declares record types. It matters more than nexus, because operational editing should yield the migration with the edit.


~~~diff
  Memory
  []                                                        ; imports
  [ Lock.{ LockId LockName FlowId LockPaths LockReason } ]  ; record types
                                                            ; the remaining sections are to be decided
~~~

### Proposal 2: psyche-context › vision/ethos.md

**Comment** The roots and the memory trait as they stand, shown whole. The trait carries the change and, for each version, the upgrade from the previous format; this order, the migration first and the syntax after, stays.

  For now, Library, Signal, Operation, Memory. No version in a file.
  Signal's sections are queries and responses, since there is
  communication; Memory's are record types, the rest to be decided.
  Signal gives a Nexus its main types and Memory its database types.

  Four roots: Library, Signal, Operation, Memory. Signal declares what a Nexus says; Operation what it does, one operation type for every effect; Memory what it remembers; Library what they share. A memory trait carries a standard successful-or-unsuccessful change and, for each version, the upgrade from the previous format; that upgrade is the very edit the type needs.

### Proposal 3: psyche-context › vision/ethos.md

**Comment** The implied traits as they stand, shown whole, with their figure.

  Signal, Operation and Memory imply traits on the types they declare: each type bears its root's trait, generated with it and never written. The record types of Memory bear the memory trait; the types of Signal bear the message trait.

```
+--------------------------------------+
| a type declared in an Ethos file     |
+--------------------------------------+
     |            |            |
     | in Memory  | in Signal  | in Operation
     v            v            v
+----------+ +----------+ +----------+
| bears    | | bears    | | bears    |
| the      | | the      | | the      |
| memory   | | message  | | operation|
| trait    | | trait    | | trait    |
+----------+ +----------+ +----------+
     |            |            |
     | generated with the type, never written
     v            v            v
+--------------------------------------+
| the Rust type and its trait impl     |
+--------------------------------------+
```

  The memory trait is Memorizable.

  The Rust generated from it:

~~~rust
impl Memorizable for Flow { /* generated */ }
~~~

### Proposal 4: psyche-context › vision/ethos.md

**Comment** The generation section as it stands, shown whole. Inquiries 3 and 4 land beside it.

  Generation

  By request to ethos-zero, which is not a daemon, hence its name; committed, held fresh by a test.

~~~sh
ethos-zero 'Generate.{ /abs/orchestrate.ethos /abs/out }'
~~~

### Proposal 5: psyche-context › vision/nexus.md

**Comment** The line that says how an encoded form is identified, shown whole as it stands. Inquiry 2 reads it.

  Every method lives in a trait; an inherent method is a trait not yet extracted. The traits and types of a Nexus are one ontology designed before any body is written; defaults wherever expressible, through rich sub-trait chains. Traits live on data-bearing types; a zero-sized type with behaviour is a namespace pretending. Identity is trait-borne: an encoded form fingerprints itself, by default the hash of its rkyv archive, and every reference names its target by that name. `fn main()` is the only free function; a missing owner is a missing type.

### Proposal 6: Add · mind-context › inquiry/memory-descriptor-semantics.md, a new file

**Comment** Inquiry 1. The Rust that generation will give each Memory table must say how a record is stored and found. The engine already answers this for hand-written tables; what Ethos should declare or imply is not ruled. The code shown is existing code, not a proposal.

+ ---
+ description: What anatomy an executable Memory table descriptor has, and how a record's key is projected, is unresolved.
+ ---
+
+ Terms.
+ - Memory: the Ethos root that declares what a Nexus remembers. Its record types are the stored values.
+ - Table: one place in the engine where records of one type are kept. An Ethos table names a record type and a key type.
+ - Record: one stored value. Key: the value that addresses one record.
+ - RecordKey: the engine's own stored form of a key, the thing it actually files a record under.
+ - TableSpecification: the engine's Rust trait by which one table declares itself: its record type, its key type, its names and hash, and the operations that follow from them.
+ - Assertion: a request to the engine to store one record in a table under a key. Query: a request to read; here, the exact-key query, which names one key and gets that key's record.
+ - Table reference: the typed coordinate of a table that assertions and queries carry.
+ - Executable descriptor: generated Rust that implements TableSpecification for a table, so the engine can register and use it. A type alias is not one.
+
+ What exists now.
+ - The engine's TableSpecification takes the key type and the record type as two separate types. Its record_key turns a key into a RecordKey; nothing in it reads a key out of a record.
+ - Its assertion combines a key given beside a record; its query names the exact key. The table reference names the table.
+ - Ethos tables name a record type and a key type, and lowering requires the key to be a newtype, so that its projection could be read from its shape.
+ - Generation emits no TableSpecification today.
+
+ The question. Which anatomy should an executable Ethos Memory table declare or imply: key and record kept apart, the key taken from the record, or the key's projection declared in Ethos? It is settled by the living's ruling on the anatomy, after which the Rust generated for a table can be checked against it.
+
+ Existing code, from the memory engine, as it stands. Provided methods are shown by signature.

~~~rust
+ pub trait TableSpecification {
+     type Record;
+     type Key;
+     const TABLE_NAME: TableName;
+     const FAMILY_NAME: &'static str;
+     const SCHEMA_HASH: SchemaHash;
+     fn descriptor() -> TableDescriptor<Self::Record>;
+     fn table_reference() -> TableReference<Self::Record>;
+     fn record_key(key: &Self::Key) -> Result<RecordKey>;
+     fn assertion(key: &Self::Key, record: Self::Record) -> Result<KeyedAssertion<Self::Record>>;
+     fn query(key: &Self::Key) -> Result<QueryPlan<Self::Record>>;
+ }
~~~

```
+------------------------------+
| a record to store            |
+------------------------------+
     |                    |
     | is paired with     | has its key
     | a supplied key     | extracted
     v                    v
+--------------+   +--------------+
| a key and a  |   | a record     |
| record, two  |   | whose key is |
| inputs       |   | its own      |
+--------------+   +--------------+
     |                    |
     | builds             | builds
     v                    v
+------------------------------+
| an assertion                 |
+------------------------------+
     | stores a record in
     v
+------------------------------+
| the table                    |
+------------------------------+
```

### Proposal 7: Alternative 1 of Inquiry 1 · psyche-context › vision/memory.md

**Comment** Key and record stay apart, as the engine has them, and the key's projection is structural: a newtype's one payload. The lines land at the end of the section «What memory is, long term», after the example. This alternative is proposed, not approved; no handwritten fixture, adapter or legacy branch stands in for it.

+ A Memory table pairs a record type with a key type, declared apart. A record is stored with a key given beside it, and read by naming that key exactly; the key is never taken from the record.
+ A key is a newtype, and its one payload is its projection into the stored key.

### Proposal 8: Alternative 2 of Inquiry 1 · psyche-context › vision/memory.md

**Comment** Key and record stay apart, but each key type says in Ethos how it becomes the stored key, so no projection is assumed from its shape. Same landing as Alternative 1.

+ A Memory table pairs a record type with a key type, declared apart. A record is stored with a key given beside it, and read by naming that key exactly; the key is never taken from the record.
+ Each key type declares in Ethos how it becomes the stored key; no projection is assumed from the shape of the key.

### Proposal 9: Alternative 3 of Inquiry 1 · psyche-context › vision/memory.md

**Comment** The key is taken from the record, so an assertion takes the record alone. Same landing as Alternative 1.

+ A Memory table names its record type and the part of the record that is its key. A record is stored alone, its key taken from it, and read by naming that key exactly.

### Proposal 10: Add · mind-context › inquiry/memory-runtime-identity.md, a new file

**Comment** Inquiry 2. Generation knows a table by an unspelled identity and by two fingerprints; the engine asks for a table name, a family name and a schema hash. Which feeds which is not ruled. The code shown is existing code, not a proposal.

+ ---
+ description: How a lowered Memory table's identities become the engine's table name, family name and schema hash is unresolved.
+ ---
+
+ Terms.
+ - Encoded name: the unspelled, stable identity a declaration has in Ethos, before any word is chosen for it.
+ - Spelling: the current word for a declaration, kept in the name tree and resolved only when Rust is written.
+ - WholeLogosTable: the lowered form of one Memory table. It carries the table's encoded name, its record type, its key type and the key's source-declared identity, and the storage fingerprints of the record and of the key.
+ - Storage fingerprint: a hash of the stored shape of a type, including every type inside it, and for a type from outside the document the shape its owner published.
+ - TableName: the engine's current storage coordinate of a table, a text that may change with a respelling.
+ - FamilyName: the engine's stable identity of the table's family of records, independent of the current spelling.
+ - SchemaHash: the engine's 32-byte content identity of the table's record and key shape.
+
+ What exists now.
+ - The lowered table carries the encoded name and two storage fingerprints, one for the record and one for the key; it carries no spelling.
+ - The engine's TableSpecification asks for a table name, a family name and a schema hash. Its registered family identity is the family name and schema hash, with the table name as the coordinate only.
+ - The Nexus vision says an encoded form fingerprints itself, by default the hash of its archive; it does not say how a table's fingerprint becomes a schema hash.
+ - No rule says which of the encoded name, the spelling and the fingerprints becomes which of the three.
+
+ The question. From what is each of the engine's table name, family name and schema hash made? It is settled by the living's ruling on the mapping, after which a generated table's three values can be checked against it.
+
+ Existing code, from the memory engine, as it stands.

~~~rust
+ const TABLE_NAME: TableName;
+ const FAMILY_NAME: &'static str;
+ const SCHEMA_HASH: SchemaHash;
~~~

```
+-----------+ +--------------+ +-----------+
| encoded   | | record and   | | current   |
| name      | | key storage  | | spelling  |
|           | | fingerprints | |           |
+-----------+ +--------------+ +-----------+
      |             |                |
      | feeds       | feeds          | feeds
      v             v                v
+----------------------------------------+
| the runtime identity mapping, not yet  |
| ruled                                  |
+----------------------------------------+
      |             |                |
      | yields      | yields         | yields
      v             v                v
+------------+ +------------+ +------------+
| FamilyName | | SchemaHash | | TableName  |
+------------+ +------------+ +------------+
```

### Proposal 11: Alternative 1 of Inquiry 2 · psyche-context › vision/memory.md

**Comment** The stable identity is the encoded name and is the family name; the current spelling is the table name; the schema hash is made from the two storage fingerprints. The lines land after the example in «What memory is, long term». Proposed, not approved.

+ A Memory table's family name is its encoded name, which does not change with a respelling. Its table name is its current spelling. Its schema hash is made from the storage fingerprints of its record type and its key type.

### Proposal 12: Alternative 2 of Inquiry 2 · psyche-context › vision/memory.md

**Comment** The encoded name is both the table name and the family name, so a respelling never reaches the stored coordinate. Same landing as Alternative 1.

+ A Memory table's family name and table name are both its encoded name; its spelling reaches no stored coordinate. Its schema hash is made from the storage fingerprints of its record type and its key type.

### Proposal 13: Alternative 3 of Inquiry 2 · psyche-context › vision/memory.md

**Comment** Names as in Alternative 1; the schema hash is the table declaration's own fingerprint, by the Nexus rule that every encoded form fingerprints itself. Same landing as Alternative 1.

+ A Memory table's family name is its encoded name, which does not change with a respelling. Its table name is its current spelling. Its schema hash is the fingerprint of its own table declaration, as every encoded form fingerprints itself.

### Proposal 14: Add · mind-context › inquiry/memory-generation-inputs.md, a new file

**Comment** Inquiry 3. Generation of Memory is a chain from an approved source to Rust text. Which inputs are authoritative, and which executable output the chain must give, are not ruled. The figure shows the chain as it exists.

+ ---
+ description: Which inputs authorize generation of a Memory table, and what executable artifact it must produce, is unresolved.
+ ---
+
+ Terms.
+ - MemoryBootstrapAuthority: the component that approves a Memory source and where it is placed, and seals the result.
+ - Sealed assembly: the approved, read-only result of that authority; the only form generation accepts.
+ - lower_memory: the step that turns a sealed Memory into WholeLogos, checking that each table's record and key are declared and that its key is a newtype.
+ - WholeLogos: the whole lowered form of a document, one item for each declared type and table.
+ - RustLogos: the emitter that writes Rust text from WholeLogos.
+ - ArtifactSet: the two outputs of one generation, the canonical Ethos source and the generated Rust.
+ - External type paths: where, in Rust, the types a document takes from outside are found.
+ - External storage provenance: the stored shape of an outside type, as its owner published it at a stated revision.
+ - Tuple alias: a Rust line giving a table the name of a pair of its record type and key type.
+
+ What exists now.
+ - Generation takes the sealed assembly, the emitter, the external type paths, the external storage provenance and the two output paths. It creates or infers none of them.
+ - Its Memory output is a tuple alias for each table, and nothing more: no TableSpecification, no names, no hash, no key projection.
+ - The Generate request to ethos-zero names an Ethos file and an output directory only.
+
+ The question. Which inputs are authoritative for generating a Memory, where are they supplied, and what executable artifact must the chain produce? It is settled by the living's ruling on the inputs and on the artifact.

```
+------------------------------+
| a Memory source              |
+------------------------------+
     | is authorized by
     | MemoryBootstrapAuthority
     v
+------------------------------+
| a sealed assembly            |
+------------------------------+
     | is lowered by
     | lower_memory
     v
+------------------------------+
| WholeLogos                   |
+------------------------------+
     | is emitted by RustLogos
     v
+------------------------------+
| an ArtifactSet               |
+------------------------------+
     | carries for each table
     v
+------------------------------+
| a tuple alias only           |
+------------------------------+
```

### Proposal 15: Alternative 1 of Inquiry 3 · psyche-context › vision/ethos.md

**Comment** Generation takes the sealed source and the other named inputs, and the Rust gains each table's executable descriptor beside its types. The lines land in the Generation section, after the Generate request. Proposed, not approved; no handwritten fixture, adapter or legacy branch stands in for generation.

+ Generating a Memory takes its authority-sealed source, the emitter, the Rust paths of the outside types it names, and the stored shape of those outside types as their owners published it. It gives the canonical source and the Rust.
+ The Rust carries, with the types, each table's executable descriptor.

### Proposal 16: Alternative 2 of Inquiry 3 · psyche-context › vision/ethos.md

**Comment** The same inputs, but the executable descriptor is its own committed file beside the types. Same landing as Alternative 1.

+ Generating a Memory takes its authority-sealed source, the emitter, the Rust paths of the outside types it names, and the stored shape of those outside types as their owners published it. It gives the canonical source and the Rust.
+ Each table's executable descriptor is a third committed file beside the types.

### Proposal 17: Alternative 3 of Inquiry 3 · psyche-context › vision/ethos.md

**Comment** The request keeps its two inputs, so the outside types and their stored shapes must be named in the Ethos file itself. Same landing as Alternative 1.

+ Generating a Memory takes the Ethos file and the output directory alone; the outside types it names and their published stored shapes are named in the Ethos file. It gives the canonical source and the Rust.
+ The Rust carries, with the types, each table's executable descriptor.

### Proposal 18: Add · mind-context › inquiry/memory-freshness.md, a new file

**Comment** Inquiry 4. Ethos says generated output is committed and held fresh by a test. What the check witnesses today is narrower than every input of generation. The figure shows what the source digest covers and what it does not.

+ ---
+ description: What witnesses that generated Memory output is fresh, and what refuses it when stale, is unresolved.
+ ---
+
+ Terms.
+ - Freshness: the committed generated files are exactly what generation would write now, from every input it takes.
+ - Source digest: a hash of the canonical source, written into the second line of the generated Rust.
+ - Freshness witness: the committed thing, and the check on it, that shows freshness.
+ - Generator inputs: the canonical source, the external type paths, the external storage provenance and the emitter's settings.
+ - Stale rejection: a test in which one input is changed and the check must refuse.
+
+ What exists now.
+ - The check compares the digest in the Rust with the digest of the committed source file. It proves the Rust names that source; it says nothing of the type paths, the storage provenance or the emitter.
+ - The one negative test changes an Interface source file; none changes an executable Memory, a type path, a provenance or the emitter.
+ - The engine holds no generation or freshness test now, only tests of direct behaviour.
+ - The existing mechanisms stay until the living rules.
+
+ The question. Where does the freshness witness live, which inputs must it cover, how is it regenerated and compared, and which changes must the stale test refuse? It is settled by the living's ruling on the witness and on the stale cases.

```
+------------------+  +--------------------+
| canonical source |  | external type      |
+------------------+  | paths, external    |
     |                | storage provenance,|
     | is hashed into | emitter settings   |
     v                +--------------------+
+------------------+           |
| source digest    |           |
+------------------+           |
     | is embedded in          | shapes
     v                         v
+----------------------------------------+
| generated Rust                         |
+----------------------------------------+
```

### Proposal 19: Alternative 1 of Inquiry 4 · psyche-context › vision/ethos.md

**Comment** A test regenerates everything and compares it whole; the digest only shows which source a file came from. The lines land in the Generation section, after the line that outputs are committed and held fresh by a test. Proposed, not approved; the stale test is part of the witness.

+ A test regenerates every committed output from all the inputs of generation and refuses any difference. The digest in the Rust shows only which source it came from.
+ The test also changes each input in turn, the source, the outside type paths, their published stored shapes and the emitter's settings, and expects a refusal.

### Proposal 20: Alternative 2 of Inquiry 4 · psyche-context › vision/ethos.md

**Comment** The digest is widened to every input, and the check recomputes it. Same landing as Alternative 1.

+ The digest in the generated Rust covers every input of generation, not the source alone; the check recomputes it from all of them and refuses a difference in any.
+ The test also changes each input in turn, the source, the outside type paths, their published stored shapes and the emitter's settings, and expects a refusal.

### Proposal 21: Alternative 3 of Inquiry 4 · psyche-context › vision/ethos.md

**Comment** A committed record beside the outputs names every input by its fingerprint, and the test compares record and outputs. Same landing as Alternative 1.

+ A committed record beside the outputs names every input of generation by its fingerprint. The test regenerates, then compares the record and the outputs with the committed ones, and refuses a difference in any.
+ The test also changes each input in turn, the source, the outside type paths, their published stored shapes and the emitter's settings, and expects a refusal.
