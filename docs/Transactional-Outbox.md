# Transactional Outbox

Example Problem: You need to write to a database and a message broker when something occurs.  If one of the writes fails (e.g. the message broker is down), the broader system will be in an inconsistent state.

The Transactional Outbox pattern solves this by using the transactional nature of the database.  Within a database transaction, you write 2 rows: 1 is the data itself (e.g. the order, the message, etc), 2 is a row in the outbox table.  A separate process watches the outbox table and publishes to the message broker.  The separate process could use Change Data Capture (CDC) to reduce latency.  This improves reliability and consistency.  The message broker only receives events for data that was actually saved to the database.

## References

- In the context of distributed transactions: [Distributed Transactions Explained: 2 Phase Commit vs Saga Pattern](https://www.youtube.com/watch?v=DOFflggE_0Q).
- [Pattern: Transactional Outbox](https://microservices.io/patterns/data/transactional-outbox.html)
