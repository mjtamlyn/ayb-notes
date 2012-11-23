# MySQL @Twitter

### Lisa Phillips, Senior MySQL DBA for Twitter

MySQL does still scale! The numbers are mental - 400M tweets per day.

Architecture is Sharded master slave.

8 Full time DBAs working on 1000s of dbs. That team supports ~600 engineers.

Pragmatism: use commodities, queues and async, eventual consistency, some delay tolerance, new awesome tools *if* needed, and use MySQL if it works, something else when it doesn't.

Always soft launch things, and increase the numbers slowly to see what the impact is. Iterate and improve, and never roll back.

DBAs and Engineers bascially have to trust each other.

### Why MySQL?

Pretty fast, usually. Robust, replication usually works. It's easy to use and easy to run. Hiring is easier!

### Why not?

Really bad at ID generation at scale. Not so good at graphs. Replication sucks. Stability vs fancy new features?

"Large datasets" (>1.5 TB!)
