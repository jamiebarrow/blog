# 2017-02-21 Modern Database Development Practices

tags: agile, continuous delivery, continuous deployment, continuous integration, databases, redgate, refactoring, ssdt

Back in November 2012 I presented on this topic at Entelect's Dev Days.

I've also done a blog post previously on [setting up Flyway](/blog/2015-12-02/getting-started-with-automating-database-changes-using-flyway).

I keep referring back to the same links and concepts and this post is here just for that, as a pointer to good resources and brief points about this topic.

I may revisit it and put down my own consolidated content, but for now this will do.

- Reading
  - [Evolutionary Database Design](https://www.martinfowler.com/articles/evodb.html)
    <br>Martin Fowler, 2003
  - [Agile Database Techniques: Effective Strategies for the Agile Software Developer](https://www.amazon.com/Agile-Database-Techniques-Effective-Strategies/dp/0471202835)
    <br>Scott Ambler, 2003
  - [Refactoring Databases: Evolutionary Database Design](https://www.amazon.com/Refactoring-Databases-Evolutionary-paperback-Addison-Wesley/dp/0321774515)
    <br>Scott Amber and Pramod Sadalage, 2006
  - [Catalog of Database Refactorings](http://www.agiledata.org/essays/databaseRefactoringCatalog.html)
    <br>Scott Ambler
  - [Three Rules for Database Work](https://odetocode.com/blogs/scott/archive/2008/01/30/three-rules-for-database-work.aspx)
    <br>K. Scott Allen, 2008
  - [Versioning Databases - The Baseline](https://odetocode.com/blogs/scott/archive/2008/01/31/versioning-databases-the-baseline.aspx)
    <br>K. Scott Allen, 2008
  - [Versioning Databases - Change Scripts](https://odetocode.com/blogs/scott/archive/2008/02/02/versioning-databases-change-scripts.aspx)
    <br>K. Scott Allen, 2008
  - [Versioning Databases - Views, Stored Procedures, and the Like](https://odetocode.com/blogs/scott/archive/2008/02/02/versioning-databases-views-stored-procedures-and-the-like.aspx)
    <br>K. Scott Allen, 2008
  - [Versioning Databases - Branching and Merging](https://odetocode.com/blogs/scott/archive/2008/02/03/versioning-databases-branching-and-merging.aspx)
    <br>K. Scott Allen, 2008
  - [Scott Ambler's Articles](http://www.ambysoft.com/onlineWritings.html)
    <br>Scott Ambler
  - [Stairway to Database Source Control](https://www.sqlservercentral.com/stairways/stairway-to-database-source-control)
    <br>SQL Server Central
- Martin Fowler's Practices
  - DBAs collaborate closely with developers
  - Everybody gets their own database instance
  - Developers frequently integrate into a shared master
  - A database consists of schema and test data
  - All changes are database refactorings
  - Automate the refactorings
  - Automatically Update all Database Developers
  - Clearly separate all database access code
- K. Scott Allen's 3 Rules
  - Never use a shared database for development work
  - Always have an authoritative source for your schema
  - Always version your database
- Tools
  - [Redgate Developer Tools](http://www.red-gate.com/products/)
  - [SQL Server Data Tools (SSDT)](https://blogs.msdn.microsoft.com/ssdt/)
  - [Entity Framework Code First Migrations](https://docs.microsoft.com/en-us/ef/ef6/modeling/code-first/migrations/)
  - [DbUp](https://dbup.github.io/)
  - [Flyway](https://flywaydb.org/)
  - [Open DBDiff](https://github.com/OpenDBDiff/OpenDBDiff/)
  - [sqlcmd](https://msdn.microsoft.com/en-us/library/ms162773.aspx)
  - [tSQLt](https://tsqlt.org/)
  - [dbdeploy](https://github.com/tackley/dbdeploy/)
