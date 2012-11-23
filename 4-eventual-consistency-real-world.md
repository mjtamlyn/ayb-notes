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


