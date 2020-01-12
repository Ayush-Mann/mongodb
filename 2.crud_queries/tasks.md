1. Create a database named `blog`.
use blog

2. Create a collection called 'articles'.
db.createCollection("articles",{capped:false,size:4000})

3. Insert multiple documents(at least 3) into articles. It should have fields
db.articles.insertMany([{title:"one",author:"frethor"},{title:"two",author:"frethor"},{title:"three",author:"frethor"}])

4. Find all the articles using `db.COLLECTION_NAME.find()`

db.articles.find()

5. Find a document using _id field.
db.articles.find({id:Object})
6. Find documents using title and author's name field.
db.articles.find({title:"one"}&&{author:"frethor"})

7. Find document using a specific tag.
db.articles.find({tags:'html'})

8. Update title of a document using its _id field.
db.articles.update({"_id" : ObjectId("5e16d599d323e6b5c468d3cb")},{$set:{title:"new title"}}

9. Update a author's name using article's title.
db.articles.update({"title" : "new title"},{$set:{'author.name':"newMan"}}

10. rename details field to description from articles collection. 
<!-- db.articles.update($rename:{"description":"details"}) -->
11. Add additional tag in a specific document.
db.articles.update({title:"new title"},{$push:{tags:"nosql"}})

12. Update an article's tags using $set and without $set.
<!-- > db.articles.find()
{ "_id" : ObjectId("5e16d599d323e6b5c468d3cb"), "title" : "new title", "description" : "india assam", "author" : { "name" : "newMan", "email" : "bhav@gmail.com", "age" : "43" }, "tags" : [ "mongo", "node", "nodejs", "nosql" ], "age" : 10 }
> db.articles.update({title:"new title"},{$set:{description:"assam"}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.articles.find()
{ "_id" : ObjectId("5e16d599d323e6b5c468d3cb"), "title" : "new title", "description" : "assam", "author" : { "name" : "newMan", "email" : "bhav@gmail.com", "age" : "43" }, "tags" : [ "mongo", "node", "nodejs", "nosql" ], "age" : 10 }
> db.articles.update({title:"new title"},{description:"karnataka"})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.articles.find()
{ "_id" : ObjectId("5e16d599d323e6b5c468d3cb"), "description" : "karnataka" } -->

  - Write the differences here ?
  with $set the it just refractors the code and the previous items in the code remains intact whereas without the use of $set it repalces the original item completely


13. Increment an auhtor's age by 5.  

db.articles.update({title:"new title"},{$inc{age:5}})

14. Delete a document using _id field with `db.COLLECTION_NAME.remove()`.
db.articles.remove({"_id" : ObjectId("5e16d599d323e6b5c468d3cc")})

Use sample.js data for below queries.

1. Find all males who play cricket.
db.users.find({"sports":"cricket"}&&{genedr:"Male"})

2. Update user with extra golf field in sports array whose name is "Steve Ortega".
db.users.update({name:"Steve Ortega"},{$push:{"sports":"golf"}})

3. Find all users who play either 'football' or 'cricket'.
db.users.find({sports:"football"}||{sports:"cricket"})

4. Find all users whose name includes 'ri' in their name.
db.users.find({name: /ri/i})
