# Welcome to tansu.io!

Tansu is an Apache Kafka API compatible broker written in async 🚀 Rust 🦀 with PostgreSQL, S3 or memory storage engines.

- Apache Kafka API compatible
- Available with [PostgreSQL](https://www.postgresql.org), [S3](https://en.wikipedia.org/wiki/Amazon_S3) or memory storage engines
- Topics [validated](https://github.com/tansu-io/tansu/blob/main/docs/schema-registry.md) by [JSON Schema](https://json-schema.org), [Apache Avro](https://avro.apache.org)
  or [Protocol buffers](protocol-buffers) can be written as 🆕 [Apache Iceberg tables](https://iceberg.apache.org) **or** [Delta Lake](https://delta.io) tables.
  See [examples using pyiceberg](https://github.com/tansu-io/example-pyiceberg), [examples using Apache Spark](https://github.com/tansu-io/example-spark) or [examples using Delta Lake](https://github.com/tansu-io/example-delta-lake).
