# Mobile web persistence strategies for offline clients

### Brian LeRoux, creator of Lawnchair, PhoneGap developer

Lawnchair - simple json storage.

## Phonegap

Live demo time - build a phone gap app. It works. They're packaged apps which live on the device. Installed apps might not be online na dhtis is the first thing apple test. So we need network introspection and persistence apis.

### Network introspection

Need to know what kind of connection you're on. Carriers lie, so a new spec for measuring the actual speed. It can be Infinity. Inifinity in JS is weird. WTFJS?

Lol `navigator.onLine`. Why capitalised???!?

### Persistence

Cookies - they're not really offline.

SQL in the browser - SQLite (probably?). The situation is messy, but hey ho. There are different apis, which may or may not be the same thing. Not in IE or FF.

SQLite is an implementation NOT a standard.

Relational data on the client is questionable... Likely you want something else anyway.

Ok, so web storage: let's hack you! But it's syncronous, data size is limited, no complex types or querying...

Remember that "supported basically everywhere" isn't the same as "supported everywhere"... Opera mini is 15% globally.

Ok, so we need async api, transactional etc. Solve ALL the problems. Renamed to Indexed DB (not simple...). It's not very nice but it's better.

Anyway, hence **lawnchair**, which hides all this behind a better api.

### Evil things on the web

- You can use flash to set unkillable cookies.
- window.name can be used to store unlimited data and it works for X-domain... and totally insecure.
- Web sockets could now open a DB connection themselves. NSFL?
