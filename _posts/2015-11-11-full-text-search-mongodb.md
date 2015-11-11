---
layout: post
title: Full Text Searching in MongoDB
---

I've always had an interest in language. Specifically, I really like the sweet
spot where natural language intersects with mathematical logic. I studied
Ancient Greek in university for two years, but had to eventually stop because I
realized that maaaaaybe I needed to actually take some Economics requirements
and graduate... but during the two blissful years that I was studiously parsing
and translating Homer, my fondest recollection is the (relative) regularity of
Ancient Greek syntax. I liked that you could pretty much identify the role of every 
single word in a sentence based on its declension, which allowed the author
complete freedom over the order in which the words were arranged. This, to me,
felt like a very purpose-driven yet flexible language design.

Recently at work, a few teams have been playing around with various fuzzy
searching libraries. We tend to try to optimize for performance, because our
services process rich data and have to cope with the occasional traffic spike.
One recent optimization we made was to implement text-searching in a service
that pulled records out of a MongoDB.

Text-searching is really interesting to me. I think it's fairly common for
learning developers to try to implement some sort of crude searching algorithm
for a kata or small project. At one point, I wrote a simple Scrabble solver
library that took an input of various letters, produced every possible unique
permutation of those letters, and returned only the ones that were found
against a Scrabble dictionary that was loaded into memory. Even after
implementing an indexed hash lookup and adding some early returns, 
this still was an extremely inefficient way to perform a text search. Besides 
the fact that string manipulation (finding the permutations) tends to be a 
resource-intensive process in most languages, string searching is a 
[solved problem](https://en.wikipedia.org/wiki/String_searching_algorithm)
in computer science if you are savvy enough to use the proper algorithms.

Now, I have no computer science background, so I won't go beyond that with
regards to algorithmic science. Instead, I'll offer a short discussion of how
we implemented full-text searching, the practical benefits and drawbacks, and
limitations of using the native MongoDB tool. (Spoiler: The consensus among
most of the team here is that you should probably just be using ElasticSearch!)
Since this was my first time implementing it, I'm going to err on the side of
explaining more, but assume that you have some rough knowledge of
what databases and collections are in Mongo.

I'd previously written some SQL queries via ActiveRecord for Postgres and
MySQL. A key difference between SQL and NoSQL databases is that while SQL
requires you to declare your data type for each field, NoSQL is document-based,
which basically means that it's a key-value free-for-all. So, in SQL you could
just write text search queries against fields that were already indexed as
text, but in NoSQL, we need to explicitly tell the database that certain fields
are to be handled as text. This is the role of a 
[MongoDB text index](https://docs.mongodb.org/manual/core/index-text/). *This only
works in MongoDB 2.4 and later.*

You can do this in the Mongo console like this:

```
db.collectionName.createIndex( { field: "text" } )
```

The docs say that "A collection can have at most one text index." A text index
is kind of like a traffic warden, pointing the database server towards the
relevant keys to look at -- you can't have more than one at any given time, 
but you can have one that points to multiple places simultaneously. To index
[multiple
fields](https://docs.mongodb.org/manual/tutorial/create-text-index-on-multiple-fields/) as text, you could do something like:

```
db.collectionName.createIndex(
  {  
    username: "text",
    surname: "text",
    company: "text"
  }
)
```

Mongo also supports wildcard operators if you need to automate for many fields.
You can assign names to the text indexes, which could be useful if you need to
activate and deactivate different indexes for different search procedures.

Text indexes can also take a language as a parameter. *This is quite
important, especially if you're not using English.* Different languages decline
words in different ways, so without specifying the language, you're going to
have some really strange stemming behavior.

#### But wait! What is stemming?

The stem of a word is everything up to the end of it (in English, at least)
before it gets changed for number, tense, gender (outside of English), etc.
"Playing", "played", and "play" all have the stem "play", which stemming
libraries try to predict and include in search results. There are various
stemming libraries out there, and they're variously effective at predicting the
stems of English words (because we have some really strange words and
declensions.) Mongo's full-text search uses a stemming library called 
[Snowball](http://snowball.tartarus.org/). Snowball does a reasonably good job
with common words, but we've found that some technical words are outside of its
scope.

#### Sending search queries

[Search queries](https://docs.mongodb.org/manual/reference/operator/query/text/) 
look like this:

```
db.collectionName.find({ $text: { $search: "China" } }) 
```

This searches against all fields included in the current text index.

If you send multiple search terms, by default Mongo inserts an implicit "OR"
between them. 'January China performance' will return every record with
text-indexed fields containing January OR China OR performance. In my
opinion... this is really silly default behavior, because human beings don't
use search engines like this. To change this to an implicit AND, you need to
wrap all search terms with inner quotes...

```
db.collectionName.find({ $text: { $search: "'China' 'September' 'M&A'" }})
```

Using single or double quotes could vary based on what language your wrapper is
written in.

A couple of notes here: 

- MongoDB's full-text search ignores some very short words by default, like "and", "but", "the", etc.
- There are ways to use boolean operators to exclude search results, but
  again, you may have to do some extra string manipulation on the parameters between
  your client and server.

There are other things you can do, like limit the number of results retrieved
and
[skip](https://docs.mongodb.org/manual/reference/operator/aggregation/skip/)
over records for basic server-side pagination.

There are some drawbacks to using Mongo full-text search. The current
restrictions are in the
[documentation](https://docs.mongodb.org/manual/core/index-text/). I think the
biggest one which has the most direct impact on users is that stemming is not
really a substitute for fuzzy searching. From the docs, if you type "blue", it
might match "blues", but not "blueberry". Based on our experience, there are
similar limitations with stemming on proper nouns, i.e. typing "China" won't 
retrieve search results containing "Chinese". The stemming library is also 
hard-coded at the moment, and there is no way to load other text-processing 
engines like Lucene.

In all, I think MongoDB full-text search is a reasonable compromise if you're
moving away from something like client-side search (shudder) but not quite ready to make the
leap to Elasticsearch. I'm also not sure how performant MongoDB is when you
start to index against many fields. It was a fun feature to build, and it
goes to show just how hard it is to write code to deal with natural language,
particularly English! It may work better in other languages that are declined
more regularly, if you've tried it out, let me know --
[@deniseyu](www.twitter.com/deniseyu21).

### Further Reading

[https://blog.codecentric.de/en/2013/01/text-search-mongodb-stemming/](https://blog.codecentric.de/en/2013/01/text-search-mongodb-stemming/)
[https://docs.mongodb.org/manual/administration/indexes-text/](https://docs.mongodb.org/manual/administration/indexes-text/)

