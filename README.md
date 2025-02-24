# Feather-Client
var feathers = require('feathers/client');
var io = require('socket.io-client/socket.io');
var socketio = require('feathers-socket.io/client');
var hooks = require('feathers-hooks');
var auth = require('feathers-authentication/client');

var socket = io('http://localhost:3030', {
 transports: ['websocket']
});
var app = feathers()
 .configure(socketio(socket))
 .configure(hooks())
 .configure(auth());

var messageService = app.service('/match/the/server/url/for/messages');

messageService.find({query:{put query here}}).then(function(response){
// Messages will be at response.data if you have pagination turned on.
// Otherwise response will be an array of messages.
});
