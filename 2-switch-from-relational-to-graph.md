# Switching from the relational to the graph model

### Luca Garulli, creator of OrientDB

So why do RDBMS users not want NoSQL? They're great for big data and big scale, but what about the *model*. What is the NoSQL answer to this? KV? Colunms? Document? **Graph!**

**CAUTION**. This will not show the classic paradigm of friend^n, we'll look at CRMs.

So everyone understands RDBMS, but who knows graph? Time for a crash course!

## Graph theory

- Vertices and edges, and edge connects to vertices
- Property graph model is nice - you can have properties on the edges as well as on the vertices
- Multiple edges between the same vertices possible
- You can extend this to extra node types etc.

And that's it! It's very simple and natural to use.

## Domain

```
Customer <-> Address
   ^
   |
   v
Order <-> Stock
```

Relational word means we join things together in 1-1 relationships. 1-N relationships need to go back the other way. N-M means we now need an intermediary table between the two.

JOINS are evil! We have to do all of these joins all the time and on large data they can be very costly. Best case is to index it, but big relations can cause problems.

How fast is an index lookup? Normally a binary split lookup, but the bigger the data size the more steps it needs. Consequently, RDBMS tend to have preformance implications when the data grows in size.

### A better way?

> A graph db provides index-free adjacency

### Introducing... OrientDB

Open source NoSQL dbms with transactions, extended-SQL, master-master replication etc. but has graph model!

Traverse a relationship is easy - each vertex knows about its edges. It's a physical link! But with RDBMS you have to do this every time - *CRAZY*! Algorithmically, we're `O(logN) -> O(1)`ish.

One of the bluprints for Orient can follow 29.6M records in 5 seconds. Days on an RDBMS.

### Creating the graph

```
> create vertex Customer set name = 'luca'
> create vertex Address set name = 'Rome'
> create edge...
```

Bindings in most languages which are just as natural to use.

Query?

```
> select in.out from Address where name = 'Rome'
Customer 'Luca'
```

Can get sums and follow all connections to an arbitrary depth, and filter while you're at it.
