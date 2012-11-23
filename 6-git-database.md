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
