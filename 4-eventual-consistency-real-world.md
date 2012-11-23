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

Amazon's Dynamo paper. READ IT! This basically spawned the ideas for things like Cassandra. So Amazon chose availability over consistency, cos it makes them money. This paper (2007) coined the term "eventual consistency" - it'll be consistent, but eventually. This is scary, but eventual availability is often worse.

#### 502 Bad gateway

This sucks.

## So back to the real world...

I don't go to my normal bank every time. I get money out from a distributed system of ATMs all over the world. But! An excavator cuts the network cable. Bummer! So what does the bank do? What is the best UX? Is it that HSBC has perfectly straight records or is it that the money is available to me. This is much more important! And it is what happens in a lot of places.

## Back to Riak

A single node with a load of partitions. Allows us to detemine data location based on a sha1 hash and a ring topology. Inserting a new object goes onto the right node, and 2 others nearby.

Read repair means if a node goes down and there are two versions then the handler looks up all the options, sees which one is out of date and updates it.

## Divergent object versions

aka siblings. Now we don't store timestamps, but that's observed. So we tell causality with something like commit hashes, called vector clocks. Riak will actually give you back multiple values. You are then in control of how to resolve those sort of weird conflicts.

Opinions:

- Never just pick a particular one!
- Merge the two together
- Take the union of all siblings in the array
- For timestamps, either the minimum or the maximum depending on which one it was
- Update with a time sorted list
