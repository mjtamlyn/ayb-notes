# You've built your application, so what next?

Today is... Black friday. Need to be able to get from small to big as easily as possible. Probably clouds right?

Need a database that... is scaleable easily.

## Is it mission impossible?

- Partitioning of data (hashes v ranges, physical v logical) and consistency problems. Either eventual or immediate?

It's not easy. There's a tradeoff between scale and functionality. Mongo sits in the middle, between KV stores/memcached and RDBs.

## How is mongo?

### Sharding
