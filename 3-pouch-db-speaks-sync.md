# PouchDB is the database that speaks sync - why does this matter?

### Dale Harvey, creator of PouchDB

Firefox OS/Boot2Gecko developer, writes PouchDB, committer to CouchDB, OSS + web geek.

## What is pouch db?

CouchDB, but written for Javascript. JSON used internally. Can be used in indexedDB on the web, or webSQL, or levelDB on nodeJS or TouchDB or CouchDB on the cloud. Pouch is effectively a front end to all of these possibilities.

## CouchDB invented the first telephone...

Lots of good things, but the main interesting point is master-master replication. This is awesome for distributed web systems, and it can sync stuff from one server to another.

`Pouch.replicate('ldb://...', 'http://...')`

## Pouch db

Designed for building offline applications. Works well offline and allows you to sync data. Sync always happens in the background.

It's been developed in spurts, really busy for a while then really quiet. Lol jobs. But it's now at the point where people can (and need) to use it.

New adapters in progress/newly merged. More docs etc coming. Lots of good projects coming, like backbone integration etc.

It was kind of before its time, WebSQL and IndexedDB is only just becoming stable. We're also in the days before armies of NodeJS devs...
