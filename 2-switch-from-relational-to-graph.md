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

JOINS are evil! We have to do all of these joins all the time and on large data they can be very costly. Best case is to index it, but big relatinos can cause problems.
