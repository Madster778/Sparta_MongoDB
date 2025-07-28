# MongoDB

## What is MongoDB?

MongoDB is a **NoSQL** (non-relational) document-oriented database. It stores data as **BSON** (Binary JSON), allowing flexible and scalable storage of unstructured data. MongoDB is ideal for high-volume applications where schema flexibility is required.

![SQL vs NoSQL](images/sql-nosql-table.png)

---

## What are Collections and Documents?

In MongoDB:

- A **Collection** is like a table in SQL.
- A **Document** is like a row, but stored in JSON-like format (BSON).

Documents can contain nested objects or arrays.

### Example of an **Embedded Document**:

![Embedded Document](images/embedded-document.png)

### Example of a **Referenced Document**:

![Referenced Document](images/referenced-document.png)

---

## MongoDB Architecture

MongoDB uses a client-server architecture:

- Clients communicate with the **mongod** server process.
- The **storage engine** handles data persistence.
- **mongosh** (Mongo Shell) is used to interact with the database.

---

## What are Replica Sets?

A **Replica Set** is a group of MongoDB servers that maintain the same data set.

- One **primary** node receives all write operations.
- One or more **secondary** nodes replicate the data from the primary.
- If the primary fails, one of the secondaries is automatically promoted.

### Advantages:

- High availability
- Automatic failover
- Redundancy

### Disadvantages:

- More complex deployment
- Slight latency during failover

---

## What is Sharding?

**Sharding** is MongoDB’s method for **horizontal scaling** – it splits large data sets across multiple machines.

### How it works:

- MongoDB uses a **shard key** to divide data.
- A **config server** stores metadata and configuration settings.
- A **mongos router** routes queries to appropriate shards.

> Useful for managing huge databases with heavy read/write operations.

### Advantages:

- Scalability
- Better performance for big data

### Disadvantages:

- Complex setup
- Poor shard key choice can cause imbalances

---

## MongoDB Use Cases

MongoDB is ideal for applications requiring flexibility, scalability, and high throughput.

### Case Study 1: **Uber**

Uber uses MongoDB for geospatial data storage and real-time tracking of drivers and users due to its fast write and read speeds.

### Case Study 2: **MetLife**

MetLife used MongoDB to unify customer data from 70+ systems into a single customer view to enhance service quality.

---

## Bonus: Class Notes Summary

### MongoDB Shell Basics (`mongosh`)

```bash
show dbs                   # List all databases
use testDB                 # Switch/create database
show collections           # List collections in current database
db.getCollectionNames()    # Alternate way to list collections
db.users.insertOne({ name: "Mahdi", age: 230 })
db.users.find()
db.users.updateOne({ name: "Mahdi" }, { $set: { age: 23 } })
db.users.deleteOne({ name: "Mahdi" })
```
