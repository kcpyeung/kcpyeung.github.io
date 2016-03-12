---
layout: post
title:  "Graph databases and neo4j"
date:   2013-04-24 08:47:19 +0800
categories: programming
---
On April 19, 2013,  I gave a talk at [NUS Hackers](http://nushackers.org/) on graph databases and neo4j. I find neo4j attractive for several reasons but primarily for its being non-intrusive in my domain code. It has its quirks and weirdness but for most part it's better than any ORM I've used. Why am I talking about ORM? Because a graph maps very closely to an OO model - Nodes being objects, and relationships are, well, relationships between objects.

I presented code samples for solving [shortest path](https://github.com/kcpyeung/neo4j-shortest-path) and [what's cooking](https://github.com/kcpyeung/neo4j-whats-cooking). The latter is about given a set of recipes (eg, BLT burger requires bacon, lettuce and tomato; macaroon requires egg whites, almond meal and sugar) and some ingredients you have in your kitchen (eg, 500g of flour, 2 tomatoes, 1kg minced beef), what you can cook for dinner tonight. The code is amazingly simple, consisting of a series of map-reduce as the graph is traversed.

Of course that terseness is only possible if you are using [neo4j.rb](https://github.com/andreasronge/neo4j). If you're using Java then you have substantially more code to test (and write). I may try out implementing the solutions using clojure in the future. Stay tuned.
