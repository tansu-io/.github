# Diskless Apache Kafka compatible broker

Features:

- **Broker**. Each broker is completely stateless acting as the leader for any topic partition, transaction or consumer group. Storage is separate to the broker. Schema validation with open table support. Quick starting: spin the broker down between API requests.
- **Proxy**. A high volume, low latency proxy for Kafka traffic adding security, multi tenancy, schema validation, throttling or batching.
- **CLI**. A developer friendly CLI that can be used to administer the broker or produce to schema backed topics.
             
Storage:

- [PostgreSQL](https://docs.tansu.io/docs/storage-engine-pg). Multiple brokers can use the same PostgreSQL database as storage. Topic data is partitioned, splitting what is logically one large table into smaller physical pieces. Simple for existing Operational teams to manage.
- [SQLite](https://docs.tansu.io/docs/storage-engine-sqlite). Super simple to setup. Embedded in the Tansu binary. Single broker only. Widely adopted and very fast. A single database file can easily reproduce an environment on demand.
- [S3](https://docs.tansu.io/docs/storage-engine-s3). AWS S3 is designed to exceed 99.999999999% (11 nines) data durability. Multiple brokers can use the same S3 bucket using conditional writes, without an additional coordinator.
- [memory](https://docs.tansu.io/docs/storage-engine-memory). Designed for ephemeral development or test environments. Quick to setup. Even quicker to tear down.

- **Broker Schema Validation**. [AVRO](https://docs.tansu.io/docs/schema-registry-avro), [Protocol buffer](https://docs.tansu.io/docs/schema-registry-protobuf) and [JSON](https://docs.tansu.io/docs/schema-registry-json) schema backed topics are automatically validated by the broker. Validation is embedded in the broker, with no other moving parts.
- **Open Table Format**. Automatic conversion of schema topics into [Delta Lake](https://docs.tansu.io/docs/delta-lake), [Apache Iceberg](https://docs.tansu.io/docs/iceberg) or Parquet open table/file formats. Sink topics can skip the Kafka metadata overhead writing directly into the [Data Lake](https://docs.tansu.io/docs/data-lake).

Articles:

- [Tuning Tansu: 600,000 record/s with 13MB of RAM](https://blog.tansu.io/articles/performance-tuning-i) tuned the broker with the [null](https://docs.tansu.io/docs/storage-engine-null) storage engine using [cargo flamegraph](https://github.com/flamegraph-rs/flamegraph)
- [Using flame graphs to remove a hot path, stop copying data and switching to a fast CRC32](https://blog.tansu.io/articles/performance-tuning-ii-sqlite) which tuned a hot regular expression, stopped copying uncompressed data and used a faster CRC32 implementation using the [SQLite](https://docs.tansu.io/docs/storage-engine-sqlite) storage engine
- [Route, Layer and Process Kafka Messages with Tansu Services](https://blog.tansu.io/articles/route-layer-service), the composable layers that are used to build the Tansu [broker](https://docs.tansu.io/docs/cli-broker) and [proxy](https://docs.tansu.io/docs/cli-proxy)
- [Apache Kafka protocol with serde, quote, syn and proc_macro2](https://blog.tansu.io/articles/serde-kafka-protocol), a walk through of the low level Kafka protocol implementation used by Tansu
- [Effortlessly Convert Kafka Messages to Apache Parquet with Tansu: A Step-by-Step Guide](https://blog.tansu.io/articles/parquet), using a schema backed topic to write data into the Parquet open table format
- [Using Tansu with Tigris on Fly](https://blog.tansu.io/articles/fly-with-tigris), spin up (and down!) a broker on demand
- [Smoke Testing with the Bash Automated Testing System 🦇](https://blog.tansu.io/articles/gh-smoke-test-with-bats), a look at the integration tests that are part of the Tansu CI system


Examples:
  - [pyiceberg](https://github.com/tansu-io/example-pyiceberg)
  - [Apache Spark](https://github.com/tansu-io/example-spark)
  - [Delta Lake](https://github.com/tansu-io/example-delta-lake)
