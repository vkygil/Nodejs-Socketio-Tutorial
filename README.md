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

**Integrando Socket.IO al lado servidor** - Parte 2:
```sh
var app = require('express')();
var http = require('http').Server(app);
var io = require('socket.io')(http);
var port = process.env.PORT || 3000;

app.get('/', function(req, res){
  res.sendFile(__dirname + '/index.html');
});

io.on('connection', function(socket){
  socket.on('chat message', function(msg){
    io.emit('chat message', msg);
    console.log(msg[1]);
  });
});

http.listen(port, function(){
  console.log('listening on *:' + port);
});
```

**Integrando Socket.IO al lado cliente** - Parte 2:
```sh
<!doctype html>
<html>

<head>
    <title>Socket.IO chat</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-size: large;
        }

        body {
            font: 13px Helvetica, Arial;
      
            background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAATklEQVQoU2NkYGAwZmBgOMuAACA+CKCIMSIpADGRNaEYgKwQ3WQUjTCF6CYhWw2WAynEpgjmIpg7jUlSiM0TWK2GWUOUZ7ApxggeogIcABHJFtftKVfJAAAAAElFTkSuQmCC) repeat;
        }

        form {

            padding: 3px;
            position: fixed;
            bottom: 0;
            width: 100%;
        }

        form input {
            border: 4px solid;
            padding: 10px;
            border-radius: 30px;
            width: 90%;
            margin-right: .5%;
        }

        form button {
            width: 9%;
            border-radius: 30px;
            background: rgb(55, 255, 23);
            border: none;
            padding: 10px;
        }

        #messages {

            list-style-type: none;
            margin-bottom: 40px;
            margin: 0 10px;
            padding: 0;
        }

        #messages li {
            background: gainsboro;
            padding: 10px 20px;
            margin-top: 20px;
            margin-bottom: 20px;
            border-radius: 50px;
            display: table;
        }

        .miMensaje {
            background: greenyellow !important;
            margin-left: auto;
        }
    </style>
</head>

<body>
    <ul id="messages"></ul>
    <form action="">
        <input id="m" autocomplete="off" /><button>Send</button>
    </form>
    <script src="/socket.io/socket.io.js"></script>
    <script src="https://code.jquery.com/jquery-1.11.1.js"></script>
    <script>
        var user = "";
        user = prompt("Por favor introduce tu nombre:", "Popo");

        $(function () {
            var socket = io();
            $('form').submit(function () {
                if ($('#m').val() != "")
                    socket.emit('chat message', [user, $('#m').val()]);
                $('#m').val('');
                return false;
            });
            socket.on('chat message', function (msg) {
                if (msg[0] == user) {
                    $('#messages').append($('<li>').text(msg[1]).addClass("miMensaje"));
                } else {
                    var txt1 = $("<b>").text(msg[0]);
                    var txt2 = document.createElement("br");
                    var txt3 = $("<p>").text(msg[1]);

                    var txt4 = $('<li>').append(txt1);
                    txt4.append(txt2);
                    txt4.append(txt3);

                    $('#messages').append(txt4);
                }
                window.scrollTo(0, document.body.scrollHeight);
            });
        });
    </script>
</body>

</html>
```

**TTTTTTT** - tttttttttttt:
```sh
XXXXXXXXXXXX
``` 
