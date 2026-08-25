# PostgreSQL Indexing - Structured Roadmap

A structured learning roadmap for understanding PostgreSQL indexes, how they work internally, how the query planner uses them, and how to optimize queries in real-world scenarios.

## 📚 Roadmap

### 1. Index Fundamentals — Sehran Aghayev

* What is an index?
* Why indexes improve query performance
* Read vs. write trade-offs
* How databases search for data
* Basic index concepts


### 2. B-Tree Structure — Əli Bağırzadə

* How B-Tree works internally
* How searching happens in **O(log n)**
* Why PostgreSQL uses B-Tree as the default index type
* Pages, nodes, and pointers
* How index traversal works
 

### 3. Clustered vs. Unclustered Index — Zeynab Mammadova

Understanding index structure first makes it easier to understand how indexes relate to physical data storage.

* What is a clustered index?
* What is a non-clustered / unclustered index?
* How table data is physically stored
* How physical ordering affects read performance
* Key differences between clustered and non-clustered indexes
 

### 4. Index Maintenance — Əli Bağırzadə

* Index fragmentation
* When and why index reorganization is needed
* `REBUILD` vs. `REINDEX`
* Impact of maintenance operations on performance
* When index maintenance is actually necessary
 

### 5. PostgreSQL Index Types — Nijat Mammadli

Explore the most important PostgreSQL index types and when to use them.

* **B-Tree** — default index type
* **GIN** — arrays, `JSONB`, and full-text search
* **Composite indexes** — multi-column indexes
* **Partial indexes** — indexes based on a filter condition
* Choosing the right index type for a use case
 
### 6. When Indexes Don't Work — Ismayil Ibrahimov

Understanding when PostgreSQL **cannot effectively use an index** is as important as knowing how to create one.

Common cases include:

* Using `!=` or `<>`
* Applying functions to indexed columns

```sql
-- Index may not be used effectively
WHERE LOWER(name) = 'john'
```

* Leading wildcards

```sql
-- B-Tree index generally cannot efficiently support this
WHERE name LIKE '%abc'
```

* Low-selectivity columns
* Other situations where a sequential scan can be cheaper

 
### 7. Index Usage with JOINs — Osman Afandiyev

* How indexes are used during `JOIN` operations
* What happens when both tables have indexes
* Indexing join keys
* `Nested Loop` vs. `Hash Join` vs. `Merge Join`
* How indexes influence join performance

 
### 8. Multi-Index Behavior & Query Planning — Javad Aghayev

* What happens when multiple indexes exist on a table
* Why PostgreSQL often chooses a single index
* Bitmap Index Scans
* Combining multiple indexes
* The role of the query planner
* How PostgreSQL decides between different execution strategies

 
### 9. Partitioning — Kanan Muradli

* What is table partitioning?
* How partitioning affects data access
* Partition pruning
* Relationship between partitioning and indexes
* When partitioning can improve query performance

---

## 🗺️ Learning Flow

The roadmap follows a progression from fundamentals to practical optimization:

```text
Index Fundamentals
        ↓
B-Tree Structure
        ↓
Clustered vs. Unclustered Index
        ↓
Index Maintenance
        ↓
PostgreSQL Index Types
        ↓
When Indexes Don't Work
        ↓
Indexes in JOINs
        ↓
Multi-Index Behavior & Query Planner
        ↓
Partitioning 
```

## 🎯 Learning Goal

By the end of this roadmap, participants should be able to:

* Explain how database indexes work internally
* Understand PostgreSQL B-Tree indexes
* Choose appropriate PostgreSQL index types
* Understand the impact of indexes on read and write performance
* Identify cases where an index may not be useful
* Understand index usage in `JOIN` operations
* Interpret query execution plans
* Understand how PostgreSQL's query planner chooses indexes
* Recognize the relationship between indexes, partitioning, and disk I/O
 
