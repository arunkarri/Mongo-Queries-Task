# Mongo-Queries-Task


Data:


[{
	"_id" : ObjectId("6024c073d68cfdc16649e2d0"),
	"id" : 2,
	"title" : "A Bug's Life",
	"director" : "John Lasseter",
	"year" : 1998,
	"length_minutes" : 95
}
{
	"_id" : ObjectId("6024c073d68cfdc16649e2c6"),
	"id" : 13,
	"title" : "Brave",
	"director" : "Brenda Chapman",
	"year" : 2012,
	"length_minutes" : 102
}
{
	"_id" : ObjectId("6024c073d68cfdc16649e2d1"),
	"id" : 7,
	"title" : "Cars",
	"director" : "John Lasseter",
	"year" : 2006,
	"length_minutes" : 117
}
{
	"_id" : ObjectId("6024c073d68cfdc16649e2ca"),
	"id" : 12,
	"title" : "Cars 2",
	"director" : "John Lasseter",
	"year" : 2011,
	"length_minutes" : 120
}
{
	"_id" : ObjectId("6024c073d68cfdc16649e2c5"),
	"id" : 5,
	"title" : "Finding Nemo",
	"director" : "Andrew Stanton",
	"year" : 2003,
	"length_minutes" : 107
}
{
	"_id" : ObjectId("6024c073d68cfdc16649e2c7"),
	"id" : 14,
	"title" : "Monsters University",
	"director" : "Dan Scanlon",
	"year" : 2013,
	"length_minutes" : 110
}
{
	"_id" : ObjectId("6024c073d68cfdc16649e2cd"),
	"id" : 4,
	"title" : "Monsters, Inc.",
	"director" : "Pete Docter",
	"year" : 2001,
	"length_minutes" : 92
}
{
	"_id" : ObjectId("6024c073d68cfdc16649e2cf"),
	"id" : 8,
	"title" : "Ratatouille",
	"director" : "Brad Bird",
	"year" : 2007,
	"length_minutes" : 115
}
{
	"_id" : ObjectId("6024c073d68cfdc16649e2cb"),
	"id" : 6,
	"title" : "The Incredibles",
	"director" : "Brad Bird",
	"year" : 2004,
	"length_minutes" : 116
}
{
	"_id" : ObjectId("6024c073d68cfdc16649e2c4"),
	"id" : 1,
	"title" : "Toy Story",
	"director" : "John Lasseter",
	"year" : 1995,
	"length_minutes" : 81
}
{
	"_id" : ObjectId("6024c073d68cfdc16649e2cc"),
	"id" : 3,
	"title" : "Toy Story 2",
	"director" : "John Lasseter",
	"year" : 1999,
	"length_minutes" : 93
}
{
	"_id" : ObjectId("6024c073d68cfdc16649e2ce"),
	"id" : 11,
	"title" : "Toy Story 3",
	"director" : "Lee Unkrich",
	"year" : 2010,
	"length_minutes" : 103
}
{
	"_id" : ObjectId("6024c073d68cfdc16649e2c9"),
	"id" : 10,
	"title" : "Up",
	"director" : "Pete Docter",
	"year" : 2009,
	"length_minutes" : 101
}
{
	"_id" : ObjectId("6024c073d68cfdc16649e2c8"),
	"id" : 9,
	"title" : "WALL-E",
	"director" : "Andrew Stanton",
	"year" : 2008,
	"length_minutes" : 104
}]



Find all the information about each film

db.films.find().pretty()

Find the title of each film

db.films.aggregate({$project : {title : 1}}).pretty();

Find the director of each film

db.films.aggregate({$project : {director: 1}}).pretty();

Find the title and director of each film

db.films.aggregate({$project : {title:1,director: 1}}).pretty();

Find the title and year of each film

db.films.aggregate({$project : {title:1,year: 1}}).pretty();

Find the movie with a row id of 6

db.films.find({id: 6}).pretty();

Find the movies released in the years between 2000 and 2010

db.films.find({$and : [ {year:{ $gt: 2000}}, {year:{ $lt: 2010}} ]}).sort({year: 1}).pretty();

Find the movies not released in the years between 2000 and 2010

db.films.find({$or : [ {year:{ $lt: 2000}}, {year:{ $gt: 2010}} ]}).sort({year: 1}).pretty();

Find the first 5 Pixar movies and their release year

db.films.find({},{year: 1}).limit(5).pretty();

Find all the Toy Story movies

db.films.find({title: {$regex : “Toy Story.*”}}).pretty();

Find all the movies directed by John Lasseter

db.films.find({director: “John Lasseter”}).pretty();

Find all the movies (and director) not directed by John Lasseter

db.films.find( { director: { $not: /^John Lasseter.*/} },{title: 1, director: 1}).pretty();


Find all the WALL-* movies

db.films.find({title: {$regex : “WALL-*”}}).pretty();

List the last four Pixar movies released (ordered from most recent to least)

db.films.find().sort({year: -1}).limit(-4).pretty();

List the first five Pixar movies sorted alphabetically

db.films.find().sort({title: 1}).limit(5).pretty();

List the next five Pixar movies sorted alphabetically

db.films.find().sort({title: 1}).skip(5).limit(5).pretty();
