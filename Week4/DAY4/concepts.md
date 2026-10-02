# Data Engineering Terminology + Spark, Kafka & Google Sheets 

This is our reference material for the day — read through it before
starting the task. The goal is to build a solid mental model of how these
pieces fit together, not to memorize every term.



## 🧠 Extended Data Engineering Glossary

### Architecture & Processing Patterns
| Term | Plain-English Meaning |
|---|---|
| **Batch processing** | Processing data in scheduled chunks (e.g. once an hour, once a day) rather than as it arrives. |
| **Stream processing** | Processing data continuously, event by event, as it arrives — low latency, always running. |
| **Event-driven architecture** | A system design where components react to events (things that happened) rather than being called directly on a schedule. |
| **Data lake** | Cheap, flexible storage for raw data in its original format (files, JSON, Parquet) — schema is applied when reading, not writing. |
| **Data warehouse** | Structured, query-optimized storage for cleaned, modeled data — schema is enforced before loading. |
| **Lakehouse** | A hybrid: data-lake-style cheap storage with warehouse-style structure and query performance layered on top (e.g. Delta Lake, Iceberg). |
| **Data mart** | A smaller, subject-specific slice of a warehouse (e.g. "sales data mart") built for one team's needs. |
| **OLTP vs. OLAP** | OLTP = fast, small transactional reads/writes (an app's live database). OLAP = big analytical queries over large historical data (a warehouse). |
| **Orchestration** | Scheduling and managing the order and dependencies of pipeline steps (tools: Airflow, Dagster, Prefect). |
| **DAG (Directed Acyclic Graph)** | A diagram of pipeline steps and their dependencies, with no loops — the standard way orchestration tools represent a pipeline. |
| **CDC (Change Data Capture)** | Continuously capturing row-level changes (inserts/updates/deletes) from a source database as they happen, instead of re-scanning the whole table. |

### Streaming-Specific (Kafka world)
| Term | Plain-English Meaning |
|---|---|
| **Message broker** | A system that sits between producers and consumers of data, handling delivery — Kafka is the most common one. |
| **Topic** | A named stream of related events in Kafka — like a labeled channel (e.g. `orders`, `page_views`). |
| **Partition** | A topic is split into partitions for parallelism — each partition is an ordered, append-only log. |
| **Offset** | A position marker in a partition — tells a consumer exactly which messages it has already read. |
| **Producer** | Anything that writes events into a Kafka topic. |
| **Consumer / Consumer group** | Anything that reads events from a topic; a consumer group lets multiple consumers split the work of one topic without duplicating reads. |
| **Replication factor** | How many copies of each partition Kafka keeps across brokers, for fault tolerance. |
| **Retention policy** | How long Kafka keeps messages before deleting them, regardless of whether they've been read. |
| **Kafka Connect** | A framework for plugging Kafka into external systems (databases, files, APIs) without writing custom producer/consumer code. |
| **Schema registry** | A central place that stores and enforces the expected structure (schema) of messages, so producers and consumers agree on format. |
| **Exactly-once / at-least-once delivery** | Guarantees about whether a message might be processed more than once (at-least-once) or is guaranteed to be processed exactly once, even after failures. |
| **Dead-letter queue** | A separate topic/queue where messages that fail processing get routed, instead of blocking or silently dropping them. |

### Processing-Engine-Specific (Spark world)
| Term | Plain-English Meaning |
|---|---|
| **Distributed computing** | Splitting a large computation across many machines (a cluster) so it runs in parallel instead of on one machine. |
| **Cluster** | A group of machines working together — has a driver (coordinator) and executors (workers). |
| **Driver / Executor** | In Spark, the driver plans the work and coordinates; executors actually run the tasks in parallel across the cluster. |
| **RDD** | Spark's original low-level distributed data structure — rarely used directly today, but DataFrames are built on the same ideas. |
| **DataFrame** | A distributed table-like structure in Spark (similar to a pandas DataFrame, but spread across a cluster) — the standard way to work with data in Spark today. |
| **Lazy evaluation** | Spark doesn't run a transformation the moment it's written — it builds a plan and only executes when an action (like `.show()` or writing output) triggers it. |
| **Shuffle** | Redistributing data across the cluster (e.g. for a `groupBy` or join) — expensive, and a common target for performance tuning. |
| **Broadcast join** | Sending a small table to every executor instead of shuffling a huge table, to speed up joins when one side is small. |
| **Partitioning (Spark)** | How Spark splits a DataFrame into chunks processed in parallel — good partitioning avoids uneven workload across executors. |
| **Structured Streaming** | Spark's stream processing API — lets us write streaming logic using the same DataFrame API as batch jobs. |
| **Micro-batch processing** | Structured Streaming's default mode: it processes small batches of data at short intervals, rather than one event at a time. |
| **Watermarking** | Telling Spark how long to wait for late-arriving data in a stream before finalizing a windowed result. |
| **Checkpointing** | Spark periodically saves its streaming progress to storage, so it can recover and resume correctly after a failure. |

### General / Cross-cutting
| Term | Plain-English Meaning |
|---|---|
| **SLA (Service Level Agreement)** | An agreed target for pipeline reliability, e.g. "data must be updated within 15 minutes of an event." |
| **Data freshness** | How up-to-date data is by the time someone uses it — a key metric for streaming vs. batch tradeoffs. |
| **Data observability** | Monitoring pipelines for volume, freshness, schema changes, and quality — catching problems before a human notices bad numbers. |
| **Idempotent consumer** | A consumer designed so that processing the same message twice has no unwanted side effect (e.g. it won't double-count a sale). |
| **Backpressure** | What happens (and how a system handles it) when data arrives faster than it can be processed. |



## 🔗 How Spark, Kafka & Google Sheets Fit Together

These three tools operate at very different layers, and that's exactly why
they're often used *together* rather than as alternatives to each other.

```
[Source systems]                 [Streaming backbone]        [Processing]              [Reporting layer]
POS terminals, apps,   --events-->      Kafka        --stream-->    Spark        --writes-->  Google Sheets
sensors, web clicks              (topics: orders,          (Structured Streaming:      (via Sheets API —
                                   page_views, etc.)         aggregate, clean,          live dashboard for
                                                              window, join)              non-technical users)
```

### What each layer is actually doing

**Kafka — the ingestion and decoupling layer**
Kafka's job is to receive high-volume events reliably and hold them
durably, so producers (e.g. every lemonade stand's POS system) and
consumers (e.g. Spark) never talk to each other directly. If Spark goes
down for maintenance, events keep queuing safely in Kafka and get
processed once Spark comes back — nothing is lost, and producers never
need to know or care whether a consumer is currently running.

**Spark — the transformation and aggregation layer**
Spark (using Structured Streaming) continuously reads from Kafka topics
and does the actual work: cleaning malformed events, joining a stream of
orders against a reference table of products, and computing rolling
aggregates — e.g. "total revenue per region, per 5-minute window." This is
the same kind of cleaning logic from Day 1's task, just running
continuously on a live stream instead of once on a static CSV.

**Google Sheets — the lightweight reporting layer**
Most business stakeholders don't want to log into a BI tool to check a
number. A small job (a Python script or Apps Script) periodically pulls
Spark's latest aggregated output and writes it into a Google Sheet via the
Sheets API. Now a non-technical manager can see "revenue by region, last
updated 3 minutes ago" in a tool they already know how to use — no
dashboard license, no login friction.

### Worked Example: Scaling Up the Lemonade Pipeline

Imagine our Week 4 lemonade dataset, but real and continuous — 200 stands,
each sending an event every time a sale happens:

1. Each POS terminal (**producer**) sends a JSON event to a Kafka
   **topic** called `lemonade_orders` the instant a sale happens.
2. Kafka holds these events durably, split across **partitions** (e.g. one
   per region) so multiple consumers can process in parallel.
3. A Spark Structured Streaming job **consumes** from `lemonade_orders`
   continuously, applies the same logic as Day 1 (standardize product
   names, validate against a reference table, flag anomalies like negative
   quantities), and computes a **windowed aggregate**: revenue per region
   every 5 minutes.
4. Spark writes that aggregate to a lightweight sink (a small database
   table or file).
5. A scheduled script reads the latest aggregate and updates a Google
   Sheet every few minutes — the same "clean_sales.csv → report" step
   from Day 1, just automated and continuous instead of manual and
   one-time.

### Why not just use one tool?
- Kafka alone has no real transformation/aggregation power — it's a
  transport layer, not a compute engine.
- Spark alone, without Kafka, would need to poll each source system
  directly — fragile at scale, and loses the durability/replay guarantees
  Kafka provides if Spark crashes mid-processing.
- Google Sheets alone can't handle high-volume, continuous data — it's a
  reporting surface, not a processing engine; pushing raw events straight
  into a sheet would hit rate limits and become unreadable within minutes.

Each tool is doing the one thing it's actually good at — this is the same
"pipeline stages" thinking from Day 2, just applied at production scale.



## 📚 Further Reading — Spark, Structured Streaming & Beyond

If we want to go deeper before building a real streaming version of this
pipeline, these are the concepts worth reading up on next, roughly in
order:

1. **DataFrame vs. RDD vs. Dataset** — why almost all modern Spark code
   uses DataFrames, and when RDDs still matter.
2. **The Catalyst optimizer & Tungsten execution engine** — how Spark
   turns our code into an efficient physical execution plan behind the
   scenes.
3. **Partitioning strategy** — how the number and size of partitions
   affects performance, and how to avoid "data skew" (one partition doing
   way more work than the others).
4. **Shuffles and when they happen** — `groupBy`, `join`, and `repartition`
   all trigger shuffles; understanding this is most of what "tuning Spark"
   actually means in practice.
5. **Structured Streaming: micro-batch vs. continuous processing mode** —
   the tradeoffs between Spark's default micro-batch engine and its
   lower-latency (but more limited) continuous mode.
6. **Watermarking and late data** — how Structured Streaming decides when
   a windowed aggregate is "final" when events can arrive out of order.
7. **Kafka Connect + Debezium** — the standard way to stream changes out
   of an existing database into Kafka without hand-writing producers
   (this is how CDC pipelines are usually built in practice).
8. **Google Sheets API authentication** — service accounts vs. OAuth, and
   why a backend job writing to Sheets uses a service account, not a
   personal login.

**A note on sourcing:** we don't have live access to search or a document
database while writing this, so if we want links to specific docs,
tutorials, or papers on any of these topics, it's worth asking us to
search for current sources rather than trusting citations from memory.
