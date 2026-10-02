# 📘 Task: Concepts Check — Spark, Kafka & Google Sheets

**Time window:** 6 hours (self-paced, spread across the day)
**Actual hands-on effort:** ~1–1.5 hours — this is a recall + light
reasoning task. No building, no coding.
**Reference material:** `concepts.md`

---

## 🎯 Objective
Check our own understanding of the extended glossary and the Spark/Kafka/
Sheets architecture before we build a real version of this pipeline.

---

## Part 1 — Match the Term (fill in the blank)

Write the correct term next to each definition. One word/phrase per blank.

1. TOPIC  — A named stream of related events in Kafka, like a labeled channel.
2. Lazy Evaluation___ — Spark doesn't run a transformation until an action triggers it.
3. Shuffle — Redistributing data across a cluster for a `groupBy` or join — expensive, and a common tuning target.
4. Offset — A position marker telling a Kafka consumer which messages it has already read.
5. Data Lake — Cheap, flexible storage for raw data in its original format, with schema applied on read.
6. CDC — Continuously capturing row-level changes from a source database as they happen.
7. Watermarking — Telling Spark how long to wait for late-arriving stream data before finalizing a windowed result.
8. Broadcast join — Sending a small table to every executor instead of shuffling a large one, to speed up a join.

---

## Part 2 — Short Answer (2–3 sentences each)

1. Why does Kafka sit *between* producers and Spark, instead of Spark
   reading directly from the source systems (POS terminals, apps, etc.)?

 - Kafka acts as a reliable middle layer that collects events from many producers, such as POS terminals and apps, and passes them to Spark. This keeps Spark from having to connect directly to every source system and helps handle large amounts of data reliably.

2. In the lemonade example, what job is Spark doing that Kafka can't do on
   its own?

- Spark processes and transforms the data, such as calculating totals, detecting patterns, or cleaning incorrect values. Kafka mainly stores and transports the event data; it does not perform complex data processing like Spark.
  
3. Why does the reporting layer in this architecture end up being Google
   Sheets and not the raw event stream itself?
- Google Sheets contains processed and summarized information that is easier for people to understand and use for reporting. The raw event stream contains individual events and is not designed to be a convenient reporting format.
  
4. What would likely break if we tried to skip Kafka entirely and have
   Spark poll each POS terminal directly for new orders?

- Spark would need to maintain separate connections and polling logic for every POS terminal, which would become difficult to scale and manage. If a terminal went offline or produced data very quickly, events could also be missed, duplicated, or overload Spark.
---

## Part 3 — True or False (with one-sentence justification)

1. Kafka permanently guarantees no data loss even without setting a
   replication factor. (T/F — why?)
   
   - False (F) — Kafka does not permanently guarantee no data loss without replication. Data durability depends on settings such as replication factor and producer acknowledgements; with no replication, a broker failure can cause data loss.
     
2. A Spark DataFrame is processed the moment we write the transformation
   code, not when an action is called. (T/F — why?)

- False (F) — Spark DataFrame transformations are lazy. Spark builds a plan when you write transformations like select() or filter(), but actually executes them only when you call an action, such as show(), count(), or write().
  
4. Structured Streaming's micro-batch mode processes data in small
   scheduled batches rather than one event at a time. (T/F — why?)

- True (T) — In micro-batch mode, Structured Streaming collects incoming events and processes them in small batches at regular intervals. It is therefore different from processing every individual event completely separately.
  
5. Google Sheets is well-suited to receiving raw, high-volume event data
   directly from Kafka. (T/F — why?)

- False (F) — Google Sheets is designed for human-readable reporting and relatively small datasets, not high-volume raw event streams. Kafka data should first be processed and aggregated before selected results are sent to Sheets.

---

## 📦 Deliverable
- `concepts_check_answers.md` with all 3 parts filled in

## 🧭 Definition of Done
- All 8 terms in Part 1 are correctly matched
- Part 2 answers reference the actual architecture (not generic statements)
- Part 3 answers include a justification, not just T/F
