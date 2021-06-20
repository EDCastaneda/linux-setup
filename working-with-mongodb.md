# MongoDB

## Set up MongoDB

Install mongoDB following the [instructions](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/).

Install tool compass following the [instructions](https://docs.mongodb.com/compass/current/install/).

Set the mondgo deamon in the operating system

```bash
sudo service mongod start
```


Then load the files into a new db named `scanner`:

```bash
mongoimport --db=scanner --jsonArray --file=/tmp/wetransfer-0d1c30/coins.json
```

## Working with MongoDB

```bash
# open the db
$ mongo

# shows all data bases
> show dbs;

# shows all collections
> show collections;

# gets the curent db
> db.getName();

# creates a collection with empty object
> db.new_collection_name.insertOne({});

# creates sub-collections
> db.new.subcollection.insertOne({})

# shows content from data base named scanner
> db.scanner.find()

# prettyfies output
> db.scanner.find().pretty()

# gets a specific doc
> db.coins.find({"nm_id":"BTC"}).pretty()

# gets all coins in the db
> db.coins.find({}, {"nm_id":1}).pretty() 

# counts all items in expression
> db.coins.find().count()

# limits the number of objects from query
> db.coins.find({}, {"nm_id":1}).limit(6)

# gets the upper level schema and types
> var schematodo = db.coins.findOne()
> for (var key in schematodo) { print (key, typeof key) ; }
```

Chained Examples

```bash
# sorted by field ascending
> db.coins.find({}, {"nm_id":1}).sort({"nm_id": 1}).limit(3)
{ "_id" : ObjectId("609e5813b787fb4594c9a651"), "nm_id" : "1INCH" }
{ "_id" : ObjectId("609e5813b787fb4594c9a61e"), "nm_id" : "AAVE" }
{ "_id" : ObjectId("609e5813b787fb4594c9a608"), "nm_id" : "ADA" }

# sorted by field descending
> db.coins.find({}, {"nm_id":1}).sort({"nm_id": -1}).limit(3)
{ "_id" : ObjectId("609e5813b787fb4594c9a646"), "nm_id" : "ZRX" }
{ "_id" : ObjectId("609e5813b787fb4594c9a632"), "nm_id" : "ZIL" }
{ "_id" : ObjectId("609e5813b787fb4594c9a641"), "nm_id" : "ZEN" }

# skips a number of items
> db.coins.find({}, {"nm_id":1}).sort({"nm_id": -1}).skip(1).limit(3)
{ "_id" : ObjectId("609e5813b787fb4594c9a632"), "nm_id" : "ZIL" }
{ "_id" : ObjectId("609e5813b787fb4594c9a641"), "nm_id" : "ZEN" }
{ "_id" : ObjectId("609e5813b787fb4594c9a62b"), "nm_id" : "ZEC" }
```

To optimize queries add indices as needed

```bash
# shows the performance of a query
> db.coins.find({"nm_id": "ZEN"}, {"nm_id": 1}).explain("executionStats");

# show indices
> db.coins.getIndexes();

# creates a descending order index
> db.coins.createIndex({"nm_id": -1});

# removes index
> db.coins.dropIndex("nm_id_-1");
```

## MongoDB Compass

To work with the compass tool

```bash
$ mongodb-compass
```

## Python integration

Install API

```bash
python3 -m pip install pymongo
```

