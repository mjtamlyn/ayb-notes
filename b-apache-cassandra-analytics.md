# Apache Cassandra, and why BASE is great for real-time analytics

### Tim Moreton, Acunu

Cassandra - what is it? Why and for what? DIY real time analytics in Cassandra (and the easy option).

Where did it come from? Facebook mixed up stuff from Amazon and Google and created Cassandra. That was open sourced in 2008 and then went into the Apache foundation. It's big usage!

Multi-master architecture, tunable consistency and great for multi-datacenter support. High performance and optimised for writes. Atomic counters.

## Data model

Row-key - easy to access stuff across a row. But each column can have compound keys.

This means that the schemas are very flexible - and the rows can be *VERY* wide.

## Tunable consistency

You can specify ONE, QUORUM or ALL depending on how you want to store things. ALL will never work if it's "ok".

## Multiple datacenter aware

The write goes everywhere (eventually).

## Use cases

Session stores: Read dominated, updates and it probably fits in RAM. Distribute for availability. Really what we want is atomicity - test then set thing.

Real time analytics: Write dominated, updates are rare. Mostly read "results". Distributed for availability, performance and capacity. We want rich queries.

So an example is twitter's promoted tweets. They have big numbers and difficult to calculate it. It's all numbers, so we count. This sort of query would have to process about 4.2TB of data.

Basically we do this by storing keys/values carefully.

## Acunu

Denormalises on top of Cassandra - you build the queries you want (which tend to be simple) and it'll move the calculation and storage step out of your head.
