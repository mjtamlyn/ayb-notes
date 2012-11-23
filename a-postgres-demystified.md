# Postgres Demystified

### Craig Kersteins

Postgres.app! It's a winner.

Agenda: History, developing, performance, querying.

## History

The naming is it's biggest mistake. It's community owned, around since 1989/1995 depending on how you count. It has MVCC - every query sees transactions committed before it. Its locks for writing don't conflict with reading.

## Why postgres?

It's a emacs of databases... Or the vim.

Basics: psql is your friend. It's really easy to do stuff and it tab completes. `\e` allows you to edit the commands directly in an editor.

Datatypes! We have many. Really awesome one - arrays. Works great for tagging. Timezonetz is really awesome too.

Extensions! Many of them. citext - case insensitive text. hstore - KV store in your SQLs. Now we also have JSON - this validates itself which is good, but then we add PLV8 - run a language inside your db. Lol Javascript injection attacks.

Range types - great for from-to timestamps. This can be used to prevent time conflicts.

Full text search works pretty well, for a good number of rows.

Low level GIS works out of the box, or use PostGIS for more advanced stuff that's optimised.

## Performance

Sequential scans. They're normally bad. Indexes are good most of the time. There's a few different types of index, which are useful.

- B-Tree: this is normally what you want.
- GIN: great for arrays etc
- GIST: Full text search and spatial.

`EXPLAIN SELECT FROM ...` This kinda gives you a query plan. `EXPLAIN ANALYSE` gives you the real data.

So let's do a simple index - its now an index scan and we're 1.7ms.

### Index pro tips

`CREATE INDEX CONCURRENTLY` - does this in the background. 2-3x Slower, but useful.

Conditional indexes - `CREATE INDEX WHERE...`

`LIKE %foo%` is BAD. One at the end is ok though.

### Monitoring

Cache hit rate: This is a mega useful query. Tells you how often you're hitting cache not the db. This, and the corresponding Index hit rate should be 99%+.

pg\_stats statements - good for checking stuff

## Querying

### Window functions

"who's my biggest spender by state?" Really good for these kind of statements.

Fuzzystrmatch - cool for looking at "similar" strings.

Moving data - there's a COPY statement. You can do this with a `db_link` and query across dbs.

Foreign data wrappers - access redis or whatever from within Postgres. Pretty cool - not all equal...

Readability!
