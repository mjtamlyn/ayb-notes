# Apache Cassandra, and why BASE is great for real-time analytics

### Tim Moreton, Acunu

Cassandra - what is it? Why and for what? DIY real time analytics in Cassandra (and the easy option).

Where did it come from? Facebook mixed up stuff from Amazon and Google and created Cassandra. That was open sourced in 2008 and then went into the Apache foundation. It's big usage!

Multi-master architecture, tunable consistency and great for multi-datacenter support. High performance and optimised for writes. Atomic counters.

## Data model

Row-key - easy to access stuff across a row. But each column can have compound keys.

This means that the schemas are very flexible - and the rows can be *VERY* wide.

## Tunable consistency

You can specify ONE, QUORUM or ALL depending on how you want to store things.
