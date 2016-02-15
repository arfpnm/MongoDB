# MongoDB
Nashita Software Solution ltd Repositories for MongoDB


install mongodb
create mongo folder in /opt/mongodb and extract the zip file here
add path of bin file in bash_profile
create /data/db in root file
to start the mongo db server type : mongod
once the server starts, open a new terminal and say mongo
This will open a shell prompt and enter the following command as below.

Arifs-MBP:~ arifmohammed$ mongo
MongoDB shell version: 3.2.1
connecting to: test
Welcome to the MongoDB shell.
For interactive help, type "help".
For more comprehensive documentation, see
	http://docs.mongodb.org/
Questions? Try the support group
	http://groups.google.com/group/mongodb-user
Server has startup warnings: 
2016-02-03T20:58:24.262+0000 I CONTROL  [initandlisten] 
2016-02-03T20:58:24.262+0000 I CONTROL  [initandlisten] ** WARNING: soft rlimits too low. Number of files is 256, should be at least 1000
> use customerManager
switched to db customerManager
> show dbs
local  0.000GB
> db.customers.insert({_id:1, name:"Poonam"}, {_id:2, name:"Nashita"})
WriteResult({ "nInserted" : 1 })
> show dbs
customerManager  0.000GB
local            0.000GB
> db.customers.insert({_id:1, name:"Arif", address :{street:"1 The High Street", city:"High Town"}})
WriteResult({
	"nInserted" : 0,
	"writeError" : {
		"code" : 11000,
		"errmsg" : "E11000 duplicate key error collection: customerManager.customers index: _id_ dup key: { : 1.0 }"
	}
})
> db.customers.insert({_id:3, name:"Arif", address :{street:"1 The High Street", city:"High Town"}})
WriteResult({ "nInserted" : 1 })
> show collections
customers
> db.customers.find()
{ "_id" : 1, "name" : "Poonam" }
{ "_id" : 3, "name" : "Arif", "address" : { "street" : "1 The High Street", "city" : "High Town" } }
> db.customers.find(_id=3)
2016-02-03T21:22:05.681+0000 E QUERY    [thread1] Error: don't know how to massage : number :
DBCollection.prototype._massageObject@src/mongo/shell/collection.js:156:11
DBCollection.prototype.find@src/mongo/shell/collection.js:196:42
@(shell):1:1

> db.customers.find(_id:3)
2016-02-03T21:22:22.707+0000 E QUERY    [thread1] SyntaxError: missing ) after argument list @(shell):1:21

> db.customers.find(name:"Arif")
2016-02-03T21:22:47.543+0000 E QUERY    [thread1] SyntaxError: missing ) after argument list @(shell):1:22

> db.customers.find({name:"Arif"})
{ "_id" : 3, "name" : "Arif", "address" : { "street" : "1 The High Street", "city" : "High Town" } }
> db.customers.find({name:"Arif"}, {name:true})
{ "_id" : 3, "name" : "Arif" }
> db.customers.find({name:"Arif"}, {name:true, _id:false})
{ "name" : "Arif" }
> db.customers.find({}, {name:true})
{ "_id" : 1, "name" : "Poonam" }
{ "_id" : 3, "name" : "Arif" }
> db.customers.find()
{ "_id" : 1, "name" : "Poonam" }
{ "_id" : 3, "name" : "Arif", "address" : { "street" : "1 The High Street", "city" : "High Town" } }
> db.customers.insert( {_id:2, name:"Nashita"})
WriteResult({ "nInserted" : 1 })
> db.customers.find()
{ "_id" : 1, "name" : "Poonam" }
{ "_id" : 3, "name" : "Arif", "address" : { "street" : "1 The High Street", "city" : "High Town" } }
{ "_id" : 2, "name" : "Nashita" }
> db.customers.find({}, {name:true})
{ "_id" : 1, "name" : "Poonam" }
{ "_id" : 3, "name" : "Arif" }
{ "_id" : 2, "name" : "Nashita" }
