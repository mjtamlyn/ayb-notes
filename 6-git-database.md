# Git: The NoSQL database

### Brandon Keepers, Github

## 2 million years ago...

A revolution! We invented tools. And that's awesome. Now other animals do that, but we started to *develop* our tools to make them better and we reused and improved and taught.

## Git

It's amazing at storing code. How is it for data? Developed gaskit.

Disclaimer: NoSQL is marketing bollocks. Non-relational and often schema-less.

1. Git as a data store
2. Features
3. Anti-features

## Data store

`$ man git > the stupid content tracker`

So, how do we store data in it? The naive way is to create a repo and dump things in files, and commit them. TADA! But this is just the file system right?

So what's the data model of git? In `.git/objects` there's a load of files - commits, trees or blobs. Blobs are basically files, then we make a tree from that blob which gives blobs names, and trees point to ther trees, and commits point to a particular tree. They also look at parent versions. Last kind of object is a reference, in this case called "master" which points to a commit.

An update! We create a new blob, a new tree to go with that and a new commit. This commit has a parent and it says where we came from so we can walk through what happened.

Let's do it programattically! Grit (a ruby lib) or libgit2 which is a C implementation with various bindings.

Let's look at grit a bit - grab a repo, create a new index that we can modify, get the head and copy the state to our index. We can then explicitly add the content and commit it with the history, and update the head. Reading is simple, we can get things out of it in the same way.

Too much work! Where's my ORM? Some libraries: Toystore + AdapterGit or GitModel. It kinda looks and works a bit like ActiveRecord.

## Features!

### Versioning

We can look back at previous issues really easily. Related is diffs - what changed between a and b.

### Hooks

We can use these to update caches, alternate formats or index searches.

### Non-relational

Question everything about relational data design. There's no Big Design Up Front - you optimize the storage based on the usage patterns. We're schemaless and we can change the data as we go along.

### Transactions

These are basically commits - many changes can happen together. There can be really long lived ones - they're called branches!

### Replication

Every clone is a full copy of the data, and that's pretty cool. Now we can do that replication in hooks... or not.

## Anti-features

All the features - they're not here.

### Querying!

Find it yourself.

### Concurrency

Er, no chance.

### Merge conflicts

Merge it automatically or you've got a very unhelpful format of knowing what was wrong.

### Scale?

Git is not web scale. Commits per second? Nearly 100! But that's a major bottleneck. But if our data gets bigger (1000 files in a folder) we're now at 14 commits a second. So nest everything! Get back to 67 commits per second cos we're not rewriting nested files. Large repos with long histories get *very* slow.

So how is github fast? Smoke - grit in the cloud. The git operations are highly distributed, so we have loads of repos.

## The point

Abuse your tools, and imagine how to make them better.
