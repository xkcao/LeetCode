# Introduction
Hight Level Design

Low Level Design

# System Design Basics
## Application Architectures
Monolithic Architecture

Microservice Architecture

## Inter-service communication
Sync
- Only for Mandatory services

Async
- Message Queue: Kafka, Rabbit MQ, Active MQ

Hybrid solution
- Increased Stability
- Enhanced Scaling
- Reduced Cost
- Reduced Code Complexity

## Protocols for communication
client-server communication

HTTP(s): Client driver, Request response model, Occasional requests, Stateless
- REST API: GET, DELETE, PUT
- Low throughput (per user), Low infra cost
- Examples: Amazon

Websockets
- Persistent connection, Bidirectional, High throughput communication
- Reduced Latency, High infra Cost
- Examples: Whatsapp

## Consistent Hashing
Hashing
- Convert one value to the other value
- Examples: MD5, SHA1, SHA256

Consistent Hashing
- Add/remove machines, without moving all the data
- Examples: Cassandra, Dynamo DB, Couchbase

## Caching
What is cache
- High speed, Data access and storage layer for quickly fetching previously computed data

When to cache
- Save computation heavy data, Save network calls, Commonly/Recently used data, RAM/SSD based

When Not to cache
- when you need high consistency
- Write heavy/Read once
- Low repetition

How much to cache
- Time based Expiration
- Size based (FIFO, LFU, LRU, etc.)

Metrics
- Size
- Latency
- Cache hit rate, Cache miss rate

Industry standards
- Redis, Memcached, Hazelcast, Ehcache

## Database
NFR requirements are impacted by the choice of database

Main factors: Structure of data, query pattern, the amount of scale

Non DB types
- Key value store caching solutions: Redis and others.
- File/Blob storage for images/videos: Amazon S3, Content Delivery Network
- Text search engine: Elasticsearch, Fuzzy search
- Time series database: OpenTSDB
- Data warehouse: Hadoop

DB types
- Relational database (structured data and need ACID): Mysql, Oracle, SQL server, Postgres
- DocumentDB (non structured data, lots of queries): MongoDB, couchbase
- Columnar DB (non structured data, ever increasing data): Cassandra, Hbase

In real world, may need to combine multiple types of databases.