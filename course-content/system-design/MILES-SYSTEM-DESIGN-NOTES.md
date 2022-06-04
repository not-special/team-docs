System Design Overview
3-Tier Architecture - Backend infrastructure composed of a web server, an app server, and database
Vertical Scaling - Adding more “power” to a single server/node (CPU, RAM, etc) to handle more load.
Horizontal Scaling - Add more ‘commodity hardware’ nodes to system. Nodes group handles increased
load.
CAP Theorem - Consistency, Availability, Partition Tolerance. You can only have two at once. BUT since
there WILL be network partitions, really only can choose Consistency OR Availability
ERD - Entity Relationship Diagram. Used to demo organization of relationships in a database
QPS - Queries Per Second, usually related to database metrics
ACID - Atomicity, Consistency, Isolation, Durability. ACID databases assoc. w/ RDBMS (SQL, Postgres, etc.)
SQL DBs - (MySQL, SQLite, Postgres, etc.) Prefer Consistency over Availability, good for more highly
interrelated data, but slower/lower Read/Write QPS. Associated with Strong Consistency.
Scaling is harder: Replication thru Primary/Replicas, multiple primaries (split-brain prob), sharding is difficult
BASE - Generally associated with NoSQL DBs (Document, Time Series, Key Value, Column-Family, Graph)
NoSQL DBs - Need to know which part of ACID you are sacrificing. Generally prefer Availability over
Consistency and faster/higher Read/Write QPS. But not black and white, there is more of a spectrum
depending on specific DB. NoSQL is associated with Eventual Consistency. Scaling is usually easy.
Normalization - Process of rearranging data into separate/smaller tables to reduce data redundancy and
improve data integrity. Done by following “normal forms” 1 thru 3.
Indexes - Sorted table-like structure in RDBMS. Speeds related queries to Log N time.
Partitioning/Sharding Data - Last resort. Solves the problem of a database getting too large. When you split
your data, each DB node is responsible for one piece of the whole.
Consistent Hashing - Popular methodology for sharding a database to keep the distribution as even as
possible and keep re-sharding impact on moving data to a minimum.
“Tail the Logs” - To watch/capture the most recent system logs. Usually related to debugging.
Caching - Improve performance by storing/serving a subset of data vs needing to get from DB
LRU - Least Recently Used: a cache invalidation method. Hash Map+Doubly Linked List queue
TTL - Time To Live: a cache and CDN invalidation method. When time expires, data is evicted.
Websockets - Connection for fully bi-directional data transfer between two endpoints
Load Balancer - Sits in front of a group of nodes to evenly distribute traffic between nodes. Multiple routing
strategies: Round Robin (or Weighted), Least Connections, Hash, etc.
CDN - Content Delivery Network. Good for static data and larger files. Purpose is to improve performance by
storing data physically closer to the client, thus reducing response time.
Background Jobs - Job given a task to run asynchronously, thus speed client response time.
CRON Job - Background job that runs on a time-schedule (“chronological” job)
Consensus - Process (and assoc. problems) of deciding on a new leader node, if lead node fails (Paxos,
Raft)
Monolith Architecture - One main app, does many things, has many parts. But tightly coupled
Microservices Architecture - Many “service” apps connected. Flexibly scalable (ea. service can scale as
needed). Loosely coupled. More complex. Usually associated w/ HTTP req/res.
Event Based Architecture - A system that works by each service reacting to msgs that it receives
Webhook - One-way data sharing of an event from the webhook provider to the subscriber
Message Queue - A queue w/ one msg/one consumer. Acts as a buffer. Decouples producer from consumer
Pub/Sub - Publisher subscriber pattern for streaming data. One producer can msg multiple subscribers
API Gateway - Typically for microservices. Reverse proxy to route traffic to specific services
Service Mesh - Connection infrastructure for microservices: communication, observability, security, etc.
Two main components: sidecars(proxy instances per service), and “control plane” to coord all sidecars
Kafka - dist. data streaming tech. Can publish, sub to, store, and process streams of records
Materialize.io - Service to keep results of complex queries highly available by incrementally updating them