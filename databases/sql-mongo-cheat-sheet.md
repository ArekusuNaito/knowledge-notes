---
description: For study reference too.
---

# SQL - Mongo Cheat Sheet

* [Get all data](broken-reference)
* [Get specific fields from a table](broken-reference)
* [Queries with constraints](broken-reference)
  * [Logical Operators / Comparison Operators](broken-reference)
    * [Equal \[=\]](broken-reference)
    * [Not Equal](broken-reference)
    * [Does the data exists? (NULL)](broken-reference)
    * [Lesser than \[<\]](broken-reference)
    * [Lesser than or equal \[<=\]](broken-reference)
    * [Greater than \[>\]](broken-reference)
    * [Greater than or equal \[>=\]](broken-reference)
    * [IN - is your data inside this list of things?](broken-reference)
    * [AND Operator - AND](broken-reference)
    * [OR Operator - OR](broken-reference)
    * [Between / Not Between](broken-reference)
    * [NOT Operator](broken-reference)
* [Finding text/strings with wildcards/regular-expressions (regex)](broken-reference)
* [I want to sort my results - Max to Min, Min to Max](broken-reference)
* [I want to limit my number of results and/or skip some results](broken-reference)
* [Aggregations](broken-reference)
* [I want to look for non-duplicate data - Intro to Aggregations](broken-reference)
* [Pending to explain - Examples Aggregation](broken-reference)
* [👇 Pending](broken-reference)
* [I wanna do operations between my fields](broken-reference)
* [I want to query multiple tables.](broken-reference)

***

![](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LYKrvLNajtqKSu0MDNO%2Fuploads%2FHQTq7o04jwByjVYKoY6y%2Fimage.png?alt=media\&token=481f9742-0b17-49e7-ad83-a965f7001399)

***

```js
const fs = require('fs');

let items = JSON.parse(fs.readFileSync('./mongo-items.json','utf8'))
let set = new Set();
items.forEach(item=>
    {
        Object.keys(item).forEach(key=>set.add(key))
    })

//Given the items database, with these fields.
console.log(set) 
//=> { '_id', 'name', 'description', 'category', 'stackSize' }
```

Note: Table and Collection will be synonims in this cheat sheet.

## Get all data

```
SELECT * FROM items;
```

```js
db.items.find().pretty();
//.pretty() is used for a readable json format
```

## Get specific fields from a table

```
SELECT name,description FROM items;
```

```js
db.article.aggregate
(
  { $project : { name : 1, description : 1 } }
);
```

However you can also do it with the find method

```js
db.items.find({},{name:1,description:1})
```

## Queries with constraints

We will find that just selecting everything from a database is pretty much something that realisticly we won't do. The things that we want from a database are more specific, each person might ask for different things, thus the need to add constraints.

```
SELECT name,stackSize FROM items
WHERE stackSize <= 20;
```

```js
db.items.find(
    {stackSize:{$lte:20}}
)
```

We have different sets of operators here's a list

### Logical Operators / Comparison Operators

* [Docs Manual](https://docs.mongodb.com/manual/reference/operator/query-comparison/) Here'a list of the operators.
* Equal To
* Not Equal To
* Lesser Than
* Lesser Than or Equal
* Greater Than
* Greater Than or Equal
* IN => \[2,5,10,18]
* NOT IN => \[30,4,9,81]
* Existence / NULL / Undefined checks
* BETWEEN / NOT BETWEEN
* NOT

#### Equal \[=]

If we want to EXACTLY look for something, we will use equals.

```
SELECT * FROM items
WHERE stackSize = 1;
```

```js
db.items.find({stackSize:1})
```

Alternatively there's an `$eq` operator. You can use a regular expression here.

```js
db.items.find({stackSize:{$eq:1}})
```

* [Docs Manual](https://docs.mongodb.com/manual/reference/operator/query/eq/)

#### Not Equal

If we want to do the opposite, we will use the not equals operator. For SQL is `!=` or `<>`

```
SELECT * FROM items
WHERE stackSize != 1;
```

For MongoDB we use the `$ne` which stands for `Not Equal` or `Inequailty`.

```js
db.items.find({stackSize:{$ne:1}})
```

* [Docs Manual](https://docs.mongodb.com/manual/reference/operator/query/ne/)

Note: A big difference between SQL and Mongo here is that SQL will not return rows where the data doesn't exist, and mongo will return them even if they are undefined.

#### Does the data exists? (NULL)

I believe it's a good moment, even if we are just getting started with operators to talk about `NULL` or `inexistence`. Because sometimes, for random reasons your data won't have all fields with data. In our example, some itemes don't have a `stackSize`, yet they are still items.

```
SELECT * FROM items
WHERE stackSize IS NULL;
```

Similar to the `equals` and `not equals` operator. You have a `NOT` after the `IS` keyword.

```
SELECT * FROM items
WHERE stackSize IS NOT NULL;
```

For Mongo we can use the `$exists` operator.

```js
//Exists = True is equivalent to IS NOT NULL
db.items.find({stackSize:{$exists:true}})
//Exists = True is equivalent to IS NULL
db.items.find({stackSize:{$exists:false}})
```

You can also use the `$ne` or `$eq` operator to check for `null`.

```js
db.items.find({stackSize:{$eq:null}})
```

The following four operators work pretty much the same, but they inquire for different things. As their name suggest you wanna now if something is lesser or greater than other things.

#### Lesser than \[<]

```
SELECT * FROM items
WHERE stackSize < 10;
```

Mongo Operator: `$lt`

```js
db.items.find({stackSize:{$lt:10}})
```

#### Lesser than or equal \[<=]

```
SELECT * FROM items
WHERE stackSize < 10;
```

Mongo Operator: `$lte`

```js
db.items.find({stackSize:{$lte:10}})
```

#### Greater than \[>]

```
SELECT * FROM items
WHERE stackSize < 10;
```

Mongo Operator: `$gt`

```js
db.items.find({stackSize:{$gt:10}})
```

#### Greater than or equal \[>=]

```
SELECT * FROM items
WHERE stackSize < 10;
```

Mongo Operator: `$gte`

```js
db.items.find({stackSize:{$gte:10}})
```

#### IN - is your data inside this list of things?

The `IN` operator pretty much asks for a lists of things. Is your data inside this array?

```
SELECT * FROM items
WHERE stackSize IN (10,20,30,40,50);
```

```js
db.items.find({stackSize:{$in:[10,20,30,40,50]}})
```

Just like Equal/NotEqual, Null/Exists, you can ask for `NOT IN`.

```
SELECT * FROM items
WHERE stackSize NOT IN (5,10,15,20);
```

```js
db.items.find({stackSize:{$nin:[5,10,15,20]}})
```

#### AND Operator - AND

Just like in programming, we will use the `AND` operator. This is used when you want 2 or more conditions to be met. Example: Find an Item that is from the `Usable` category and that it has a `stackSize` greater than 20. If `ALL` conditions are met, it will return a data set for the conditions. There's no need to check for other conditions if one is NOT met.

```
SELECT * FROM items
WHERE category="Usable" AND stackSize > 20;
```

For Mongo it will look a bit different, since with an `AND` its plural for 2 or more, we will use an array for this operator.

```js

db.items.find( { $and: [ { category: "Usable" }, {stackSize:{$gt:20}} ] } )
```

As you can see, the `$and` relies on an array to fulfill as many conditions as desired.

#### OR Operator - OR

Just like `AND` it will prompt for an array or conditions. However the difference is that `OR` will trigger if `ANY` of the conditions are met. There's no need to check for other conditions if one is met.

```
SELECT * FROM items
WHERE category="Usable" OR stackSize > 20;
```

For Mongo it will look a bit different, since with an `AND` its plural for 2 or more, we will use an array for this operator.

```js

db.items.find( { $or: [ { category: "Usable" }, {stackSize:{$gt:20}} ] } )
```

#### Between / Not Between

The between method doesn't exist on Mongo, however, we know that the "primitive" way to do a between functionality is to put things between a greater/lesser than equal conditions. This is, if we want to find an Item that stackSize is between 10 AND 30, we can say.

```
SELECT * FROM items
WHERE stackSize >= 10 AND stackSize <=30;
```

In SQL we can use a `BETWEEN` keyword.

```
SELECT * FROM items
WHERE stackSize BETWEEN 10 AND 30;
```

For mongo we will need the logical operators.

```js
db.items.find({stackSize: {$gte:10,$lte:30}} )
```

There's also the `NOT BETWEEN`, which is basically a negation of the range that we wanted.

```
SELECT * FROM items
WHERE stackSize NOT BETWEEN 10 AND 30;
```

```
SELECT * FROM items
WHERE NOT (stackSize >= 10 AND stackSize <= 30);
```

```js
db.items.find({ stackSize:{$not:{$gte:10,$lte:30}}} )
```

#### NOT Operator

Like the previous example, we are asking for the opposite of what we asking. I want these items that `DO NOT` fulfill this conditions.

* [Docs Manual](https://docs.mongodb.com/manual/reference/operator/query/not/)

```
SELECT * FROM items
WHERE NOT (stackSize >= 10 AND stackSize <= 30);
```

```js
db.items.find({ stackSize:{$not:{$gte:10,$lte:30}}} )
```

## Finding text/strings with wildcards/regular-expressions (regex)

In many cases we will look for a special keyword, for example, in our table, we can search for all items that have the `sword` word in there. Let's explain what would happen first in SQL. Consider the following query:

```
SELECT name FROM items
WHERE name="Sword"
```

Considering our table's data, we won't find anything there, because when we use the `equality [=] `operator, we looking for a 100% match of that word. In our table we don't have an item whose's name is literally: "Sword". Hence, we require to soften our search. What if its written in lower case as `sword`? For this, we can use the `LIKE` keyword. And thing for ourselves: _"Ok, I want you to find items that are `LIKE`, you know, something that has the `sword` word in it, even if its lower or upper case."_

```
SELECT name FROM items
WHERE name LIKE "Sword"
```

However, this query is still limited to just one word, we are looking for just one word regarding upper/lower casing. Now we will use a thing called a wildcard, which will allow us to look for that word `ANYWHERE` in our item's name.

```
SELECT name FROM items
WHERE name LIKE "%Sword%"
```

Each `%` means that I want to check before the word, and after the word. And with this, we can find for `ANY` item that has the word `sword` in it.

There's also another operator that can be used to wildcard just one character. For example if we want to find any of the following:

* Fire Sword +
* Fire Sword X

It would look like this:

```
SELECT name FROM items
WHERE name LIKE "%Fire Sword _%"
```

The `_` will find for anything that matches just one character.

Regarding regular expressions for SQL, I am not going to handle them at the moment, but they exists, they use the `~*` operator. And you can use stuff like grouping and using `OR` inside of it for example: `"%(sword|shield)%")`, however I'm not sure if this is avaiable for all SQL engines.

I will now explain how this can be achieved in MongoDB, we can use regular expressions here, and they can be used in many many expressions, not just on an equality expression, feel free to research if your query ideas support regex.

Considering the same example to look for all Swords in the game.

```js
db.items.find({name:/sWorD/i} )
```

This is very powerful, because now we will just rely on regular expression logic. We can use their flags as well. For this example, I just asked to look for the `sWorD` word, but the `i` flag will look for it case insensitive, `i` stands for `insensitive`.

Like our previous examples, you can combine this with the other operators we've learned, you can use the `NOT` operator, for example. Stuff like this will make you sure that you will create powerful and creative queries to solve your needs.

You can use a regex playground here: [Click here](https://regex101.com)

For example, if we want to find all items that have the possesion `'` character.

```js
db.items.find({name:/\s.+'/} )
```

## I want to sort my results - Max to Min, Min to Max

What if you want to sort all your items and order them by max stats? You can do it! Here's how you do it on both of them.

From Max to min

```
SELECT * FROM items
ORDER BY stackSize DESC;
```

From Min to Max

```
SELECT * FROM items
ORDER BY stackSize ASC;
```

* BY default, data is sorted on ascending order.
* We use the keywords `ASC`, and `DESC`.
* There's no need to write `ASC`, but we can do it.

In Mongo we have to use the `sort` function. And then we just specify the field and use the `1` is `Ascending` and `-1` which is `Descending`.

From Max to Min

```js
db.items.find({stackSize:{$exists:true}}).sort({stackSize:-1})
```

From Min to Max

```js
db.items.find({stackSize:{$exists:true}}).sort({stackSize:1})
```

There's another way that we can `sort` things and it gets a bit more complicated, we will now go to a topic called `aggregation`.

## I want to limit my number of results and/or skip some results

I want to list the Top 3 best weapons in the game. You can do it by using `LIMIT` and `OFFSET/SKIP`. As the name indicates, your return is limited to `n`, where `n` is the number of results we want.

Top 3 of Stack Size

```
SELECT * FROM items
ORDER BY stackSize DESC
LIMIT 3;
```

Now I want to just get the Weapons \[4,5,6] with top stats. We will limit to 3, but first we will skip the first 3, so we can get \[4,5,6]. We indicate this with the `OFFSET` keyword.

```
SELECT * FROM items
ORDER BY stackSize DESC
LIMIT 3 OFFSET 3;
```

On mongo we use a similar thing like `sort()`, we will use a function called `limit()` and `skip()`, in Mongo there's no `OFFSET` keyword, but we think of it as to `skip these results`.

Top 3 of Stack Size

```js
db.items.find({stackSize:{$exists:true}}).sort({stackSize:-1}.limit(3))
```

Next Top 3.

```js
db.items.find({stackSize:{$exists:true}}).sort({stackSize:-1}.skip(3).limit(3))
```

We `skip` first, then we `limit` the result.

## Aggregations

Aggregations are most commonly explained as `helper functions` to our queries. For example, we previously used the `sort(), limit() and skip()` function. And if you noticed, we used them AFTER we did our query. This is called a `chain of execution` and the order in which things are executed matter. This is called the `aggregation pipeline`, just like in `UNIX` we can find commands that use the `pipe` to send data to the next command, this is pretty much the same.

Aggregations allow us to do operations to our data, this is useful as we might think that this is something that the backend developers have to do, which it does make sense, but with the power that nowadays databases have, we can do a lot of their job here as database engineers.

Order of execution matters, both in SQL and Mongo. SQL has its own proper execution, and in Mongo we can define it depending on the order we add the aggregations, which is a double-edge sword, but there's more benefits than loses.

Here's an example to understand

## I want to look for non-duplicate data - Intro to Aggregations

With the following query we can list all the DIFFERENT/NON-DUPLICATED categories.

```
SELECT DISTINCT category FROM items;
```

On Mongo can be done with:

```js
db.items.distinct("category")
```

Indeed, that's a helper function, but there must be a way to manipulate and query this data on a pipeline, right?

We are now going to introduce the `GROUP BY` clause/functionality. This will shrink down the result to pretty much non-duplicates. So the `DISTINCT` function is probably made from the `GROUP BY` function, a wrapper we might say.

```
SELECT category FROM items
GROUP BY category;
```

And now this is things get very different on Mongo, we will now use a function called `aggregate()`. This function's input is an array, this array is the `operations/aggregators` we wanna use for our query. Since its an array, it will be iterated and the order of elements here, will be the order of execution.

```js
db.items.aggregate(
[
    {$group : { _id : '$category' }
])
```

## Pending to explain - Examples Aggregation

```js
db.universities.aggregate([
  { $group : { _id : '$name', totaldocs : { $sum : 1 } } }
]).pretty()
```

```js
db.items.aggregate(
[
    {$match:{category:{$exists:true}}},
    {$group : { _id : '$category', Total:{$count:{}}} }
]).pretty()
```

```js
db.items.aggregate(
[
    {$group : { _id : '$category', Total:{$sum:"$stackSize"}} }
]).pretty()
```

***

## 👇 Pending

## I wanna do operations between my fields

Possible on SQL. Research on MongoDB Example, find all the odd numbers from a field.

## I want to query multiple tables.

For SQL we will use the `JOIN` keywords.

* `JOIN` aka `INNER JOIN`
* `LEFT JOIN` aka `LEFT OUTER JOIN`
* `RIGHT JOIN` aka `RIGHT OUTER JOIN`
* `FULL JOIN` aka `FULL OUTER JOIN`

However, in MongoDB is very different, from my research, there's not much normalization, there's not much use of `foreign keys`, which are references to other tables to be able to link those tables.
