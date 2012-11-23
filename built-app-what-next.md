# You've built your application, so what next?

Today is... Black friday. Need to be able to get from small to big as easily as possible. Probably clouds right?

Need a database that... is scaleable easily.

## Is it mission impossible?

- Partitioning of data (hashes v ranges, physical v logical) and consistency problems. Either eventual or immediate?

It's not easy. There's a tradeoff between scale and functionality. Mongo sits in the middle, between KV stores/memcached and RDBs.

## How is mongo?

### Sharding

#### Range distribution.

Mongo splits the ranges again and automatically relocates chunks to different shards ad hoc (while keeping it consistent) to maintain load equilibrium between your shards.

What happens when you query? Mongo routes your query appropriately. But what if the query's not what you're sharding on? Well now you have to ask everything. Building systems on archictecture like this is a waste of time if you're not able to query it sensibly.

#### Caching

Aggregate the horizontal resource of memory across each shard to ensure everything is in memory.

So sharding allows us to scale reads and writes. What happens when a node fails? Doh it's all gone! So we need copies!

### Replication

Replica the sets across. The db automatically selects a secondary to be promoted if the first one fails. When one recovers and works, it then catches up and the promotes itself to a full secondary status. This is all the sort of thing which 'just happens' in the background.

Obviously read scaleability can come from this as you can read from the secondaries, but the system is asyncronous, so you have to be careful as to when you get things.
