# Redis, Steady, Go!

### Peter Cooper, publisher, programmer and author

Redis is pretty! That's the plan.

Antirez wrote it.

## What is Redis?

Remote dictionary server (or hash server). It's a data structure server? But... No 'tables', SQL, enforced relationships... Lots of 'primitives'. It's just keys and values!

Let's store some strings...

`SET A hello - > GET A`

Like an assembly language.

So Redis is a DSL for abstract data types. Open source, from 2009. Full time dev from 2010. It's basically memcached++ - more commands, presistence, data types and more.

## LIVE DEMO!

From source to working over telnet in under a minute. Impressive!

## Back to the talk

Hosting is available, but it's latent that way.

## Three big uses

- As a database
- As a messaging service
- As a cache

Also:

- Real time logging

You get basic data types like ints, sets, lists etc. It's aso got expiry so can be used for rate logging. It's good for scoreboards and sorted sets are ideal.

## Characteristics

Single threaded, event driven. Very high performance, but can be limited. Every operation is atomic so it's easy to make sure data isn't mucked up.