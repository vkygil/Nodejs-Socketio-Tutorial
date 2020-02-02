# Nodejs Socketio Tutorial

**Node.js v13.x**:

```sh
# Using Ubuntu
curl -sL https://deb.nodesource.com/setup_13.x | sudo -E bash -
sudo apt-get install -y nodejs
```

**Instalar Express y Socket.io**:
```sh
npm install express socket.io
```

**Integrando Socket.IO al lado servidor** - Parte 1:
```sh

var app = require('express')();
var http = require('http').createServer(app);
var io = require('socket.io')(http);

app.get('/', function(req, res){
  res.sendFile(__dirname + '/index.html');
});

io.on('connection', function(socket){
  console.log('a user connected');
});

http.listen(3000, function(){
  console.log('listening on *:3000');
});
```
**Integrando Socket.IO al lado cliente** - Parte 1:
```sh
<script src="/socket.io/socket.io.js"></script>
<script>
  var socket = io();
</script>
```
