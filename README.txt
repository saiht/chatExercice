/**********************************
*       INSTRUCTIONS MANUAL       *
* This is all the manual you need *
*             RTFM !              *
***********************************/

You have to create a chat web client in angular.
You can go as far as you'd like. You have 24h plain.
A clean and functionnal code is the main goal. It can
be a very simple chat or a full features one.

You have to use angular and socketIo. The rest is up
to you, just consider the best to do in this situation.
Think ! before act, crawl the internet, don't worry ! :)

Have fun ! :)

/***************
*              *
* BASIC ROUTES *
*              *
****************/

// data needs to be sent in x-www-form-urlencoded standard
// cf. http://stackoverflow.com/questions/26723467/what-is-the-difference-between-form-data-x-www-form-urlencoded-and-raw-in-the-p

/*
 * Signup route
 */
// SEND
POST: 'http://caty.herokuapp.com/signup'
data: {
	username,
	password,
	password2
}
// RECEIVE
'success' || Object

/*
 * Connect route
 */
// SEND
POST: 'http://caty.herokuapp.com/connect'
data: {
	username,
	password
}
// RECEIVE
'success' || Object

/*
 * Disconnect route
 */
// SEND
GET: 'http://caty.herokuapp.com/disconnect'
// RECEIVE
sad-empty-html


/***********************************
*                                  *
* THIS...IS...SOOOOOCKKEEEEETTTTio *
*                                  *
*   Just take a look at socketIo   *
*                                  *
*      http://socket.io/docs/      *
*                                  *
************************************/

// IMPORTANT: version used by server: 1.0.4+

// NOTE: you can connect to 'Public' chatroom
//       without being connected, crazy right ?! :)

/*
 *
 * Client possible inputs (sent by the server)
 *
 */

// connected (as anonymous or registered)
'init'
data: {
	userName: String
}

// inform reconnection
'connect'

// inform disconnection
'disconnect'

// a user left
'user:leave'
data: {
	roomName: String,
	userName: String
}

// username change response
'self:newUsername'
data: userName: String || null

// some user changed his nick
'user:newUsername'
data: {
	userName: String,
	newUsername: String
}

// a user joined a room you're in
'user:join'
data: {
	userName: String,
	roomName: String
}

// someone else sent a message in a room you're in
'send:message'
data: {
	roomName: String,
	userName: String,
	date: ?,
	time: ?,
	message: String
}

// let's play ping-pong :)
'pong'

/*
 *
 * Client accepted outputs (what you may send to the server)
 *
 */

// tell the server you're leaving
'self:leaving'
data: {
	roomName: String
}

// let's play ping-pong :)
'ping'

// ask the server to join a room
// if the room doesn't exist it may be created (needs basic rights)
'self:join'
data: roomName: String

// send your message
'send:message'
data: {
	message: String,
	roomName: String
}

// ask nicely the server to change your nickname
'self:nick'
data: userName: String


/*************
* BONUS ZONE *
*************/

-use compass (scss + mixins + compass mixins + ??)
-use templates
-make a nice interface with the css framework you'd like
-use a router (ngRoute or uiRouter)
-implement custom messages (toastr-like)
-implement signup/connection/disconnection interface
-handle multiple rooms
-show users and show if they spoke recently or not
-show beautiful dates and auto-scroll when you speak
-notify the browser if someone spoke
-play sounds !!
-play chess !!
-play go !!
-build an ia to play go !!
-or maybe chess...it'd be a lot easier