# Database Engineer Interview Preparation Plan

## Goal
Prepare for an open discussion Database Engineer interview focusing on:
- SQL fundamentals
- Database internals
- Scalability concepts
- Real-world production scenarios
- Tradeoff-based discussions

---

# Priority Topics

1. SQL vs NoSQL
2. Indexing
3. Transactions & ACID
4. Replication
5. Sharding
6. Query Optimization
7. Caching
8. CAP Theorem
9. Normalization vs Denormalization
10. Production Debugging Scenarios

---

# DAY 1 — SQL + Relational Databases

## 1. SQL vs NoSQL

### SQL Databases
Examples:
- PostgreSQL
- MySQL

### Strengths
- Strong consistency
- ACID transactions
- Joins
- Structured schema

### Best Use Cases
- Banking
- Payments
- Inventory systems

### Limitations
- Harder horizontal scaling
- Schema rigidity

---

### NoSQL Databases
Examples:
- MongoDB
- Redis
- Cassandra

### Strengths
- Flexible schema
- High scalability
- Distributed architecture

### Best Use Cases
- Social media feeds
- Analytics systems
- Real-time applications

### Limitations
- Weaker consistency
- Joins are difficult
- Data duplication

---

## Important Discussion Point

### When would you choose SQL?
Use SQL when:
- Transactions are critical
- Strong consistency is required
- Complex joins are needed

### When would you choose NoSQL?
Use NoSQL when:
- Massive scale is needed
- Schema changes frequently
- High write throughput is required

---

# 2. ACID Properties

## Atomicity
All operations succeed or fail together.

## Consistency
Database remains valid after transactions.

## Isolation
Concurrent transactions should not interfere.

## Durability
Committed data survives crashes.

---

# 3. Indexing

## What is an Index?
A data structure that improves read performance.

Without index:
- Full table scan
- O(n)

With index:
- Faster lookup
- O(log n)

---

## Why not index every column?
Because:
- More storage needed
- Inserts/updates become slower
- Index maintenance overhead

---

## Composite Index

Example:
(name, age)

Efficient for:
- WHERE name='A'
- WHERE name='A' AND age=20

Not efficient for:
- WHERE age=20

---

# 4. Normalization vs Denormalization

## Normalization
Reduces redundancy.

Advantages:
- Better consistency
- Easier maintenance

Disadvantages:
- More joins
- Slower reads

---

## Denormalization
Duplicates data intentionally.

Advantages:
- Faster reads
- Better performance at scale

Disadvantages:
- Data inconsistency risk

---

# 5. Transactions & Isolation Levels

Understand:
- Dirty reads
- Non-repeatable reads
- Phantom reads

Isolation Levels:
- Read Uncommitted
- Read Committed
- Repeatable Read
- Serializable

---

# DAY 2 — Scaling & Distributed Systems

# 1. Replication

## What is Replication?
Copying data from primary DB to replicas.

### Benefits
- Read scalability
- Failover support
- Backup

### Challenges
- Replication lag
- Stale reads

---

# 2. Sharding

## What is Sharding?
Splitting data across multiple DB servers.

### Why Needed?
Single DB becomes bottleneck due to:
- CPU
- Memory
- Storage

---

## Sharding Problems
- Cross-shard joins difficult
- Rebalancing complexity
- Hot partitions

---

# 3. CAP Theorem

Distributed systems can guarantee only two:
- Consistency
- Availability
- Partition Tolerance

Tradeoffs are important.

---

# 4. Caching

Example:
- Redis

## Why Use Cache?
- Reduce latency
- Reduce DB load

## Common Problems
- Cache invalidation
- Stale data

---

# 5. Query Optimization

Learn:
- Execution plans
- Full table scans
- Cardinality
- Index strategy

---

# 6. Database Failures

## If Primary DB Fails
Possible solutions:
- Failover
- Promote replica
- Load balancer rerouting

---

# Common Interview Questions

## SQL Questions
- Difference between WHERE and HAVING
- Primary key vs unique key
- Clustered vs non-clustered index
- Joins
- Window functions

---

## System Design Questions
- How would you scale a DB?
- When would you shard?
- Why is a query slow?
- How would you reduce latency?
- When would you use Redis?

---

# Strong Scenario-Based Answer

## Application became slow suddenly. What would you check?

1. Slow queries
2. CPU and memory usage
3. Locks
4. Missing indexes
5. Connection pool exhaustion
6. Replication lag
7. Recent deployments

---

# Important Interview Advice

## Speak in Tradeoffs

Avoid:
"MongoDB is better."

Instead say:
"MongoDB is useful when schema flexibility and scalability are priorities, while relational databases are better for strong consistency and complex joins."

---

# Best Resources

## YouTube Channels

### Hussein Nasser
https://www.youtube.com/@hnasr

Recommended topics:
- Indexing
- Replication
- Sharding
- Transactions

---

### CMU Database Systems
https://www.youtube.com/@CMUDatabaseGroup

Great for:
- Database internals
- Query optimization
- Storage engines

---

### ByteByteGo
https://www.youtube.com/@ByteByteGo

Great for:
- Distributed systems
- Scaling concepts
- System design

---

# SQL Practice Resources

## SQLBolt
https://sqlbolt.com/

## LeetCode SQL
https://leetcode.com/problemset/database/

## DataLemur
https://datalemur.com/sql-interview-questions

---

# PostgreSQL Resources

## Official Documentation
https://www.postgresql.org/docs/

---

# Last Minute Revision Topics

Before interview revise:
- SQL vs NoSQL
- Indexes
- ACID
- Transactions
- Replication
- Sharding
- CAP theorem
- Caching
- Query optimization

---

# Final Interview Strategy

Focus on:
- Clear explanations
- Real-world examples
- Tradeoffs
- Scalability thinking
- Production debugging mindset

Do not try to memorize definitions.
Focus on understanding and discussion.
