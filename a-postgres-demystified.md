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
