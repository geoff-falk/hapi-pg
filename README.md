hapi-pg
=======
Simple fork to update usage of pg.js to pg.native, all credit to original author for plugin

Wrap Hapi requests with access to a Postgres connection.

It gives you access to `request.postgres.client` within your handlers which you can then use to make Postgres requests. It also takes care of cleaning up the connection after the request.

Usage
-----
```js
var hapiPgOpts = {
  connectionString: 'tcp://postgres@localhost:5432/postgres'
};

// Hapi 6.x syntax
server.pack.register({      
  plugin: require('hapi-pg'),
  options: HapiPgOpts,
}, function(err) {
  if(err) {
    console.error(err);
    throw err;
  }
});

```

It can also take a function to dynamically resolve connection name based on the incoming request.
```js
var hapiPgOpts = {
  connectionString: function(request) {
    return 'tcp://postgres@localhost:5432/' + request.query.database;
  }
};
server.pack.require('hapi-pg', hapiPgOpts, function(err) {});  //Hapi 5.x syntax, not updated for 6.x
```

License
-------
MIT
