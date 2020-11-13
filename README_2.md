I made some changes to server.js

I'm using Mac

tried with node 13.3.0

now node 14.5.0 LTS

replaced:
  var img = fs.readFileSync('/home/app/images/profile-1.jpg');

with:
  var img = fs.readFileSync(path.resolve(__dirname, "../app/images/profile-1.jpg"));

so the reading succeeds with this (otherwise not)

  and added { useUnifiedTopology: true }

    MongoClient.connect("mongodb://admin:password@mongodb", { useUnifiedTopology: true }, function (err, client) {

  after timeout of 30000 ms server is down (SEE below)


  app listening on port 3000!
/Users/laurikyttala/workspace/Koodit_Docker/TechWorld_Nina/my-app/app/server.js:51
~/workspace/Koodit_Docker/TechWorld_Nina/my-app/app$ node server.js 
(node:93425) Warning: Accessing non-existent property 'count' of module exports inside circular dependency
(Use `node --trace-warnings ...` to show where the warning was created)
(node:93425) Warning: Accessing non-existent property 'findOne' of module exports inside circular dependency
(node:93425) Warning: Accessing non-existent property 'remove' of module exports inside circular dependency
(node:93425) Warning: Accessing non-existent property 'updateOne' of module exports inside circular dependency
app listening on port 3000!
/Users/laurikyttala/workspace/Koodit_Docker/TechWorld_Nina/my-app/app/server.js:51
    if (err) throw err;
             ^

MongoTimeoutError: Server selection timed out after 30000 ms
    at Timeout.<anonymous> (/Users/laurikyttala/workspace/Koodit_Docker/TechWorld_Nina/my-app/app/node_modules/mongodb/lib/core/sdam/topology.js:878:9)
    at listOnTimeout (internal/timers.js:554:17)
    at processTimers (internal/timers.js:497:7) {
  reason: Error: getaddrinfo ENOTFOUND mongodb
      at GetAddrInfoReqWrap.onlookup [as oncomplete] (dns.js:67:26) {
    name: 'MongoNetworkError',
    errorLabels: [ 'TransientTransactionError' ],
    [Symbol(mongoErrorContextSymbol)]: {}
  },
  [Symbol(mongoErrorContextSymbol)]: {}
}



ON console: (see the screenshot)

injection entry point. starting message loop with extension sandbox and waiting for settings...
VM348:1 GET http://localhost:3000/get-profile net::ERR_CONNECTION_REFUSED
(anonymous) @ VM348:1
init @ (index):46
(anonymous) @ (index):57
(index):57 Uncaught (in promise) TypeError: Failed to fetch
async function (async)
init @ (index):46
(anonymous) @ (index):57