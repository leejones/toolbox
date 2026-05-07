# Distributed Transactions

How to keep data consistent across different systems.

## 2 Phase Commit vs Saga Pattern

- On paper, 2 Phase Commit (2PC) is the way to go for consistency across systems.
- 2PC has a coordinator that reaches out to each system and asks if it can peform the operation.  If a system says yes, it gaurantees it will be able to peform it and it cannot change it's answer afterward.  If all systems say yes, the coordinator tells all systems to commit the change.  If any says no, the coordinator tells all systems to abort.  While waiting for the commit/abort instruction from the coordinator, all systems have to lock the relevant rows so they can fullfill the gaurantee they made to the coordinator in phase 1.
- 2PC is problematic in practice.
  - Reliability is based on every system be available.
  - Latency is based on the slowest system.
  - Requires a coordinator, which introduces reliability and durability concerns in itself.
  - Rows are locked on each system while waiting for confirmation from the coordinator if it should commit/abort.
  - In practice this results in bottlenecks and unreliability
- Most internet scale companies use the Saga Pattern
  - Embraces eventual consistency.
  - Uses "compensating transactions" to handle failures, sortof like an "undo".
  - Event based.
  - Two ways of coordinating
    - Choreography - (distributed coordination) each system listens for relevent events and responds acorrdingly. Then it emits event(s) acordingly.
    - Orchestration - (centralized coordination) a centralized system calls the systems in sequence and adjust according to the responses.
  - Choreography is hard to debug and reason about because the state is distributed across multple systems.  Might work for small systems.
  - Orchestration is often used because it's easier to reason about and the centralized system can use durable storage to resume sagas after the orchestartor is restarted.
  - Example services for distributed transation orchstration are AWS Step Functions and Temporal.

References

- [Distributed Transactions Explained: 2 Phase Commit vs Saga Pattern](https://www.youtube.com/watch?v=DOFflggE_0Q) (15m video).
