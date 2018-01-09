# MongoDB

## Installation
`brew install mongodb`
## Instantiation
The following code creates a database path and the instantiate service.
```
sudo mkdir -p data/db
mongod
```
Open a new tab in terminal and paste following command for starting mongo shell
```
mongo
```
All the commands for mongodb can be given from this shell

## Analogy with RDBMS
Database in RDBMS is database in MongoDB<br/>
Tables in RDBMS is collections in MongoDB <br/>
Row in a table in RDBMS is document in MongoDB

## Basic commands
show database `show dbs`
use database `use name_of_database`
show collections `show collections`


### Finding Documents
For Tech collections, every data can be pulled by:- `db.tech.find()`

#### Find by Id
Finding a particular row/data
`db.tech.find({"_id" : ObjectId("56b3d22468b2bfa5460d035b")})`

#### Find by Query
` db.tech.find({ "name" : "Angular" })`

### Manipulating Returned data

#### Sorting
Sorting through _name_ for ascending order as denoted by _1_ or _true_ . _-1_ or _false_ is used for reverse order.
```
db.tech.find().sort({"name": 1})
db.tech.find().sort({"name": -1})
```
#### Returning Specific fields
The act of returning just a specific set of fields from a query is known - in the world of MongoDB - as projection. The projection is added as a second parameter to the `find` method. So if you want to return all documents - which you normally leave blank in the find call - you first need to pass an empty object.
```
db.tech.find({""},{"name" : true, "_id" : 0})
db.tech.find({"language":"javascript"},{"name" : true})
```
The first command returns all the rows present in collection with only name coloumn.
The second command returns all the rows in which language is javascript and for those rows it returns only name and id coloumn.

### Updating Documents
```
db.tech.update(
    { "name" : "Angular" },
    { $set : { "name" : "AngularJS" } }
)
```
The above command will search the collection for document with name = Angular and will set that particular name .
```
db.tech.update(
    { },
    { $set : { "language" : "javascript" }},
    {"multi" : true}
)
```
The above command returns all the documents matching the given criteria and sets language to javascript. If language attribute is absent, then it just adds it.

### Deleting Documents
`db.tech.remove({"name" : "nodejs"})`

## Deleting Collections
`db.tech.drop()`
