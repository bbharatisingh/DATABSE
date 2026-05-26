# Database Engineer Interview Preparation Plan

# Goal

Prepare for:
- Open discussion database interviews
- Backend/product company discussions
- Real-world scalability discussions
- SQL + NoSQL fundamentals and advanced concepts

Focus areas:
- SQL vs NoSQL
- DynamoDB
- Redis
- Indexing
- Partitioning
- Fault tolerance
- Scaling
- Cost optimization
- Query optimization

---

# WEEK PLAN

| Day | Focus |
|---|---|
| Day 1 | SQL vs NoSQL fundamentals |
| Day 2 | Indexing + Query Optimization |
| Day 3 | Partitioning + Sharding |
| Day 4 | DynamoDB Deep Dive |
| Day 5 | Redis + Caching |
| Day 6 | Fault Tolerance + Replication |
| Day 7 | Revision + Mock Discussion |

---

# 1. SQL vs NoSQL

# SQL Databases

Examples:
- PostgreSQL
- MySQL

## Features
- Structured schema
- ACID transactions
- Joins
- Strong consistency

## Best Use Cases
- Banking
- Payments
- Inventory systems
- Order management

## Advantages
- Reliable transactions
- Data consistency
- Mature ecosystem

## Limitations
- Hard horizontal scaling
- Expensive joins at scale
- Schema rigidity

---

# NoSQL Databases

Examples:
- DynamoDB
- Redis
- Cassandra

## Features
- Flexible schema
- Distributed architecture
- High scalability
- High throughput

## Best Use Cases
- Social media feeds
- Analytics
- Sessions
- Real-time systems

## Advantages
- Easy horizontal scaling
- Fast reads/writes
- Flexible design

## Limitations
- Complex joins difficult
- Eventual consistency
- Denormalized data

---

# IMPORTANT INTERVIEW DISCUSSION

## When to use SQL?

Use SQL when:
- transactions are critical
- strong consistency required
- relationships are important

Example:
- banking
- orders
- financial systems

---

## When to use NoSQL?

Use NoSQL when:
- scalability is priority
- flexible schema needed
- low latency important

Example:
- activity feeds
- caching
- analytics
- chat systems

---

# STUDY RESOURCES

## Websites

- https://www.geeksforgeeks.org/difference-between-sql-and-nosql/
- https://www.scaler.com/topics/sql-vs-nosql/
- https://www.educative.io/blog/sql-vs-nosql-databases
- https://www.digitalocean.com/community/tutorials/sql-vs-nosql

## Videos

- Hussein Nasser
- ByteByteGo
- Gaurav Sen

---

# 2. INDEXING

# What is Indexing?

Indexes improve query speed.

Without index:
- full table scan
- O(n)

With index:
- fast lookup
- O(log n)

---

# How Indexing Works

Most DBs use:
- B-Tree indexes

Index stores:
- searchable references to rows

---

# Types of Indexes

| Type | Purpose |
|---|---|
| Primary Index | Unique identification |
| Composite Index | Multiple columns |
| Hash Index | Exact lookup |
| Covering Index | Query optimization |

---

# Composite Index Example

Index:
(name, age)

Efficient:
- WHERE name='A'
- WHERE name='A' AND age=20

Not efficient:
- WHERE age=20

---

# Why not index every column?

Because:
- storage overhead
- slower inserts
- slower updates
- maintenance cost

---

# Query Optimization Topics

Learn:
- execution plans
- full table scans
- cardinality
- query planner

---

# STUDY RESOURCES

## Websites

- https://use-the-index-luke.com/
- https://www.sqlshack.com/sql-server-index-basics/
- https://mode.com/sql-tutorial/
- https://www.geeksforgeeks.org/indexing-in-databases-set-1/

## SQL Practice

- https://sqlbolt.com/
- https://leetcode.com/problemset/database/
- https://datalemur.com/sql-interview-questions

---

# 3. PARTITIONING & SHARDING

# What happens when load increases?

As traffic increases:
- CPU usage increases
- memory usage increases
- disk I/O increases
- DB connections increase

Eventually:
single DB becomes bottleneck.

---

# Vertical Scaling

Increase:
- CPU
- RAM

Advantages:
- simple

Limitations:
- expensive
- hardware limit

---

# Horizontal Scaling

Add more servers.

Advantages:
- scalable
- distributed load

Limitations:
- operational complexity

---

# Partitioning

Splitting large tables into smaller logical parts.

## Types

| Type | Example |
|---|---|
| Range | date ranges |
| Hash | hash(user_id) |
| List | country based |

---

# Benefits of Partitioning

- faster queries
- smaller indexes
- easier maintenance

---

# Sharding

Splitting data across multiple DB servers.

Example:
- shard1 → users 1-1M
- shard2 → users 1M-2M

---

# Problems in Sharding

- cross-shard joins difficult
- rebalancing complex
- operational overhead
- hot partitions

---

# DynamoDB Partitioning

DynamoDB automatically partitions data.

Partition key selection is CRITICAL.

---

# Hot Partition Problem

Bad partition key:
country = India

Good partition key:
user_id

---

# STUDY RESOURCES

## Websites

- https://www.geeksforgeeks.org/difference-between-database-sharding-and-partitioning/
- https://www.cockroachlabs.com/blog/what-is-database-sharding/
- https://systemdesign.one/database-sharding-explained/
- https://www.baeldung.com/cs/database-sharding

## Videos

- ByteByteGo
- Gaurav Sen
- Hussein Nasser

---

# 4. DYNAMODB DEEP DIVE

# Important Concepts

## Partition Key
Determines data distribution.

## Sort Key
Supports range queries.

Example:
- user_id + timestamp

---

# Strengths

- serverless
- highly scalable
- low latency
- auto scaling

---

# Limitations

- limited joins
- access pattern driven
- hot partitions possible

---

# Important Discussion Point

DynamoDB schema design depends on:
- access patterns
- query requirements

NOT traditional normalization.

---

# Consistency

## Eventual Consistency
- faster
- cheaper

## Strong Consistency
- accurate
- more expensive

---

# STUDY RESOURCES

## Websites

- https://www.alexdebrie.com/posts/dynamodb-single-table/
- https://www.serverlesslife.com/DynamoDB_Design_Patterns_for_Single_Table_Design.html
- https://dynobase.dev/dynamodb-learning/
- https://www.dynamodbguide.com/

## Videos

- Hussein Nasser DynamoDB videos
- Be A Better Dev
- AWS DynamoDB tutorials

---

# 5. REDIS & CACHING

# What is Redis?

In-memory key-value store.

Very fast because:
- data stored in RAM

---

# Common Redis Use Cases

- caching
- sessions
- rate limiting
- leaderboards

---

# Cache Aside Pattern

1. Check cache
2. Cache miss
3. Fetch DB
4. Update cache

---

# Cache Invalidation

Common issue:
- stale data

---

# Redis Limitations

- RAM expensive
- persistence tradeoffs
- not ideal for complex queries

---

# Redis Eviction Policies

Learn basics:
- LRU
- TTL expiration

---

# STUDY RESOURCES

## Websites

- https://www.freecodecamp.org/news/redis-for-beginners/
- https://www.geeksforgeeks.org/what-is-redis-introduction-and-explanation/
- https://roadmap.sh/redis
- https://systemdesign.one/redis-cache-system-design/

## Videos

- Hussein Nasser Redis videos
- ByteByteGo Redis explanations

---

# 6. NORMALIZATION & DENORMALIZATION

# Normalization

Goal:
Reduce redundancy.

Benefits:
- consistency
- cleaner schema
- easier updates

Problems:
- too many joins

---

# Denormalization

Duplicate data intentionally.

Benefits:
- faster reads
- scalability
- fewer joins

Common in:
- NoSQL systems
- distributed systems

---

# Strong Interview Point

NoSQL systems often denormalize intentionally because joins across distributed systems are expensive.

---

# STUDY RESOURCES

## Websites

- https://www.studytonight.com/dbms/database-normalization.php
- https://www.guru99.com/database-normalization.html
- https://www.javatpoint.com/dbms-normalization

---

# 7. FAULT TOLERANCE & REPLICATION

# Replication

Copying data to replicas.

---

# Benefits

- failover
- high availability
- read scalability
- backups

---

# Replication Problems

## Replication Lag
Replica may return stale data.

---

# Fault Tolerance

System survives failures.

Methods:
- replication
- backups
- failover
- distributed nodes

---

# CAP Theorem

Distributed systems tradeoff:
- Consistency
- Availability
- Partition Tolerance

---

# Strong DynamoDB Discussion

DynamoDB prioritizes:
- availability
- partition tolerance

while allowing eventual consistency.

---

# STUDY RESOURCES

## Websites

- https://www.geeksforgeeks.org/fault-tolerance-in-dbms/
- https://www.baeldung.com/cs/cap-theorem
- https://systemdesign.one/cap-theorem/
- https://www.educative.io/blog/cap-theorem

---

# 8. COST OPTIMIZATION

# SQL Cost Challenges

Costs increase due to:
- larger machines
- replicas
- storage
- licenses

---

# NoSQL Cost Benefits

- distributed scaling
- auto scaling
- pay-per-request models

---

# Redis Cost Tradeoff

Redis is fast but:
- RAM is expensive

---

# Strong Interview Statement

Database choices are tradeoffs between:
- scalability
- consistency
- latency
- operational complexity
- cost

---

# FINAL REVISION TOPICS

Before interview revise:
- SQL vs NoSQL
- indexing
- partitioning
- sharding
- DynamoDB partition keys
- Redis caching
- normalization
- replication
- CAP theorem
- fault tolerance
- query optimization

---

# FINAL INTERVIEW STRATEGY

During discussions:
- explain tradeoffs
- use real-world examples
- discuss scaling limitations
- mention operational complexity
- mention cost considerations

Avoid:
"This DB is best."

Prefer:
"This DB is more suitable depending on scalability, consistency, latency, and query requirements."
