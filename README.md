# Lost.js - Cache everything.

Lost.js is a javascript library to cache function result.

## Usage

Cache function result:
```javascript
var lost = require('lost');
var fib = function () {/* ... */};
var lostFib = lost(fib);
lostFib(20);
```

Async function cache:
```javascript
var query = function (username, callback) {};
var lostQuery = lost.async(query);
lostFib('pw', function (err, ret) {
});
```

Promise cache:
```javascript
var fetchUsers = function (userAge) {};
var lostFetchUsers = lost.promise(fetchUsers);
lostFetchUsers(20).then(function () {
}, function () {
});
```

Use lrucache:
```javascript
var LRU = require('lru-cache');
var cache = LRU({
    max: 500
});

var lruLost = lost.config({
    store: cache
});
lruLost(fib);
lruLost.async(query);
lruLost.promise(fetchUsers);
```

Use redis:
```javascript
var redis = require('redis');
var client = redis.createClient();
var redisLost = lost.config({
    store: client
});
```

Custom store:
```javascript
var customLost = lost.config({
    store: {
        get: function (key) {
        },
        set: function (key, value) {
        }
    }
});
```
