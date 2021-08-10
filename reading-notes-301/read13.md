 # Which HTTP Status Code to Use for Every CRUD App
 > The HTTP specification defines many status codes we can use when responding to our clients. Some APIs only use the most basic codes and define their own error signaling mechanisms on top of it; others want to make full use of HTTPs collection of codes to tell their clients what’s going on. If you belong to the latter, this article is for you. This guide walks through the various CRUD operations and which status codes you should be using for clean API design.


 # CRUD (Create, Read, Update, Delete)


 >The HTTP creators thought about many status codes when designing it and even added a bunch of new ones over the years. If they’re used correctly they can help to improve developer experience greatly by leveraging automatic redirect follows of clients and explaining what happened more clearly.

>Sometimes there are multiple codes we could use for one particular case, the important thing is that we keep our usage consistent over the whole API surface.
