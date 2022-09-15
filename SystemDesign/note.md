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

## Rate Limiting
Rate limiting is a method of limiting the amount of network traffic that can be sent or received for a particular entity in a time window.
- Network traffic: # of requests, # of reads/writes, size of payload
- Entity: User, IP Address, data centers

Why to rate limit?
- Prevent Bots, DoS/DDoS, Spam

Implementation
- Entity
- Action counters
- Configuration
- Decision

Rate Limiting Algorithms
- Leaky Bucket
- Fixed window
- Sliding window


# System Design Case Studies
## Facebook System Desgin
Functional Requirements
- Make post
- Like, comment, share
- Add friends
- See timeline
- See a user's Post, profile
- Activity log

Non Functional Requirements
- Read heavy
- Fast rendering, posting
- Lag is OK
- Access pattern
- Global
- Scale

Users
- Famours
- Active
- Live
- Passive
- Inactive

Architecture
- User service: Mysql, Redis, Kafka
- Graph service: Mysql, Redis, Kafka
- Short URL service
- Asset service
- Post service
- Post ingestion service
- Archival service
- Timeline service
- Like service
- Activity tracker

## Amazon System Design
FR
- Search
- Cart/WishList
- Checkout
- View order

NFR
- Low latency
- High availability
- High consistency

Architecture
- User home page, user search page
- In Bound service: Kafka
- Item service: MongoDB
- search consumer: Elastic search
- Search service:
- Serviceability + TAT service:
- Wishlist service: Mysql
- Cart service: Mysql
- Analytics: Kafka, Spark streaming, Hadoop cluster, Spark cluster
- Recommendation service: 
- User service
- Logistic service
- Warehouse service
- Order taking service:
- Inventory service: Mysql 
- Archival service
- Order processing service
- Historical order service: Cassandra
- Order view
- Notification service

## Uber System Design
FR
- see cabs
- ETA & approximate price
- book a cab
- location tracking

NFR
- global
- low latency
- high availability
- high consitency
- scale

Achitecture
- Map service
- User app
- user Service: Mysql, Redis
- Cab request service
- Cab finder
- Driver app
- driver service: mysql, redis
- location service: cassandra, redis
- websocket handler
- websocket manager: redis
- trip service: mysql, cassandra
- trip archiver
- payment service: mysql
- spark streaming cluster, hadoop cluster, Spark ML jobs

## WhatsApp System Design
FR
- one to one chat
- group chat
- text/images/video
- read receipt
- last seen

NFR
- low latency
- high availability
- no lag
- scale

Architecture
- web socket handler
- web socket manager: redis
- message service: cassandra
- Asset servcie: S3, CDN
- user app
- user service: mysql, redis
- group service: mysql, redis
- analytics service: kafka, hadoop
- last seen service: cassandra

## Twitter System Design
FR
- tweet
- re-tweet
- follow
- search

NFR
- read heavy platform
- fast rendering
- fast tweet
- lag OK in some cases
- scale

Users: famous, active, live, passive, inactive

