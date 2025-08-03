# MongoDB Revision Notes

These notes prepare you for the MongoDB multiple choice assessment (24 questions, 65% pass mark, 60 minutes).

---

## NoSQL Database Types

- **Document Stores** – e.g., MongoDB: JSON-like documents.
- **Key-Value Stores** – e.g., Redis: data stored as key-value pairs.
- **Column-Family Stores** – e.g., Cassandra: tables with flexible schemas.
- **Graph Databases** – e.g., Neo4j: data stored as nodes and relationships.

---

## Normalisation vs Denormalisation

- **Normalisation**: Data split into multiple collections (referenced). Reduces redundancy. Good for write-heavy applications.
- **Denormalisation**: Embeds related data in one document. Improves read performance. Suited for read-heavy applications.

---

## MongoDB Architecture

- **mongod**: Database server (stores data, handles queries).
- **mongos**: Router for sharded clusters.
- **Shards**: Hold portions of data (for horizontal scaling).
- **Config Servers**: Store metadata about shard distribution.
- **Replica Set**: Group of nodes (1 primary, many secondaries) for redundancy.

---

## Relationships in MongoDB

- **Embedded documents**: Ideal for 1-to-1 or 1-to-many (denormalised).
- **Referenced documents**: Ideal for many-to-many (normalised).

---

## Querying in MongoDB

- Use `find()` for basic queries.
- Support rich operators like:

```js
$eq, $ne, $gt, $gte, $lt, $lte, $in, $nin;
```

### Example:

```bash
db.collection.find({ age: { $gte: 25 } })
db.collection.find({ status: { $in: ["active", "pending"] } })
```

---

## MongoSH Commands

```bash
show dbs
use myDatabase
show collections
db.collection.insertOne({...})
db.collection.find()
db.collection.updateOne()
db.collection.deleteOne()
```

> Use `NumberInt()` or `NumberLong()` for numeric precision.

---

## Replica Sets

- Ensure **high availability** and **data redundancy**.
- One **primary** node receives writes.
- **Secondaries** replicate data.
- **Automatic failover** if primary fails.

---

## Sharding

- MongoDB’s **horizontal scaling** solution.
- Splits data across **shards** using a **shard key**.
- Managed by **mongos** router.
- Requires careful shard key selection.

---

## .aggregate() Method

Used for data processing and transformation.

```bash
db.collection.aggregate([
  { $match: { field: value } },
  { $group: { _id: "$field", total: { $sum: 1 } } }
])
```

Supports stages like `$match`, `$group`, `$sort`, `$project`, `$limit`.

---

## The `_id` Field

- Each document has a unique `_id`.
- Defaults to an `ObjectId`.
- Can be used for referencing across collections.

---

## Comparison Operators Reference

```bash
# Equal
db.collection.find({ age: { $eq: 25 } })

# Greater Than / Greater Than or Equal
db.collection.find({ age: { $gt: 25 } })
db.collection.find({ age: { $gte: 25 } })

# Less Than / Less Than or Equal
db.collection.find({ age: { $lt: 25 } })
db.collection.find({ age: { $lte: 25 } })

# Not Equal
db.collection.find({ status: { $ne: "inactive" } })

# In / Not In
db.collection.find({ status: { $in: ["active", "pending"] } })
db.collection.find({ status: { $nin: ["cancelled", "archived"] } })
```

---
