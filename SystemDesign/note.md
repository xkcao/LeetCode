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