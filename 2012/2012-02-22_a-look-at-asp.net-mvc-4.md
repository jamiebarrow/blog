# 2012-02-22 A look at ASP.NET MVC 4

tags: ASP.NET, async, await, bundling, C#, CoffeeScript, Entity Framework, LESS, Microsoft, Migrations, minification, MVC, performance, SignalR, Visual Studio, WCF, Web API, website performance

I just watched the talk by Scott Guthrie at Techdays 2012 in the Netherlands entitled ["A look at ASP.NET MVC 4"](https://channel9.msdn.com/Events/TechDays/Techdays-2012-the-Netherlands/2364).

In the talk, Scott talks about some of the new features in ASP.NET 4, as well as touching on some new features of Entity Framework Code First. The highlights of the features are:
- Database Migrations
- Bundling/Minification Support
- Web APIs
- Mobile Web
- Real Time Communication (SignalR)
- Asynchronous Support using language features (async and await)

An extremely useful addition to EF Code First is that of database migrations, allowing you to progressively develop your code and database. Migrations allow you to deploy/rollback different versions of your database. Each migration can add/remove its parts to the database (e.g. adding a column when migrating up, or removing the column when migrating down, even perhaps extracting data to a temp table and processing it during a possibly destructive migration). The one project I was on had a whole custom written database patching/versioning framework which enabled true integration testing, as well as generation of deployment scripts, which EF Code First with migrations can probably provide out of the box now. Very nice.

The bundling and minification support is a welcome addition too. By convention, instead of referencing specific scripts or CSS, if you reference a folder, all the relevant resources in that folder will be bundled and processed together. An HTML helper is also available which also provides versioning of the bundles by appending a hash of the resources to the query string. Custom bundles can be defined and custom processors can be implemented as well, for example, in the talk Scott illustrates that you could use CoffeeScript and LESS processors in a bundle, greatly improving a web developers life.

The WCF Web API, is now part of ASP.NET and is now known as the ASP.NET Web API. It provides the power of WCF with the ease of ASP.NET MVC, while respecting the HTTP protocol a lot more. It provides built in support for writing code once and supporting multiple response types (JSON/XML), OData for querying, filtering and sorting data by just adding to the query string (no code change... as long as your code supports returning an IQueryable), and also provides a nicer programming model for HTTP responses.

The default MVC project templates come with CSS that uses media queries for a more adaptive feel to the application. And for scenarios where media queries aren't enough, there's also support for detecting a mobile client, and returning a completely different template or view for a request. This allows for creating a single web application, but catering for a wider range of clients.

The Real Time Communication with SignalR allows for the server to push through to the clients. SignalR can detect if the client supports WebSockets, or if not falls back to various methods that enable the expected behaviour, e.g. long polling.

The Async support just leverages existing asynchronous controller functionality, but allows you to do so using the async and await keywords that are part of the next version of .NET.

I highly suggest that you watch the whole video, as always, the Gu's talk is full of useful information.
