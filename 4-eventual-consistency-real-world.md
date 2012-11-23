# Eventual consistency in the real world

### Matt Heitzenroder, Basho technologies

- or... Why you already know about eventual consistency
- or... eventual consistence is better than eventual availability

Works at Basho. Make Riak, a distributed system.

## Brewer's conjecture

In any system, you want three guarantees: Consistency, availability, partition tolerance. In failures, you can only have 2.

This became the CAP theorem proved in 2002 at MIT.

Because patition tolerance is hard to not have, it's basically consistency OR availability.

## Life is full of trade-offs

Amazon's Dynamo paper. READ IT! This basically spawned the ideas for things like Cassandra. So Amazon chose availability over consistency, cos it makes them money. This paper (2007) coined the term "eventual consistency" - it'll be consistent, but eventually.
