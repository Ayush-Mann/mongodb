#### write commands for following mongodb opertaions

1. create a database named `sports`
// Answer here ..
use sports

2. list all databases present in local mongod server.
// Answer here..
show dbs
3. create 3 collections named `cricket`, `football`, `TT` in sports database.
use sports
db.createCollection("cricket",{capped:false, size:30000})
db.createCollection("football",{capped:false, size:23000})
db.createCollection("TT",{capped:false, size:21000})
4. add 3 players in each of above collections which should have fields like `name`, `age`, `email`, state and auction_price.
db.cricket.insertMany([{name:"ayush",age:23,email:"ayu@gmail.com",state:"assam",auction_price:1234},{name:"piyush",age:23,email:"piyu@gmail.com",state:"karnataka",auction_price:234},
{name:"ashwin",age:23,email:"ashu@gmail.com",state:"manipur",auction_price:134}])

5. list all collections in sports database.
show collections
6. rename `TT` collection to `tennis`.
db.TT.renameCollection("tennis")
7. create a capped collection called `khokho` which should have max 3 documents.
db.createCollection("khokho",{capped:true, size:2100, max:2})
db.khokho.insertMany([{name:"ayush",age:23,email:"ayu@gmail.com",state:"assam",auction_price:1234},{name:"ayush",age:23,email:"ayu@gmail.com",state:"assam",auction_price:1234},{name:"ayush",age:23,email:"ayu@gmail.com",state:"assam",auction_price:1234},{name:"ayush",age:23,email:"ayu@gmail.com",state:"assam",auction_price:1234}])
  Try inserting more than 3 and output the result here ?
only 3 items get listed instead of 4

8. check whether a collection is capped or not?
db.sports.isCapped()

9. remove all documents from `football` collection.
db.football.remove({})

10. delete cricket collection completely.
db.cricket.drop()

11. rename database sports to games
db.copyDatabase('sports','games')

12. delete sports database. 
use sports
db.dropDatabase()
