# 2012-11-11 Refactoring Databases

tags: agile, databases, dbdeploy, redgate, refactoring, sql, ssdt, versioning

On Friday I did a presentation at Entelect's internal dev days regarding Modern Database Development, and how best practices of Agile Development are widely known and regarded in the community, but how we rarely see the same rigour with database development.

And it's not new. Martin Fowler, Scott Ambler and Pramod Sadalage have written books and blog posts on Evolutionary Database Design and Refactoring Databases, going back to at least 2003. But we don't always see people employing the techniques and tools that have been discussed in the past ten years.

I didn't even know about dbdeploy nor the Red Gate developer tools until this year. I've only been on one real life project that used a custom developed database patching tool to roll out database changes and a base for integration testing. But I definitely believe these tools and techniques must be employed more regularly.

I have to say, the presentation went well. I received a lot of positive comments from people and I think that the audience may have got something out of my talk, which is great news. In fact, I was even asked straight afterwards to help someone out in how to help them compare the data in two production databases.

Look up the tools I mentioned, [dbdeploy](http://dbdeploy.com/), Red Gate [SQL Source Control](https://www.red-gate.com/products/sql-development/sql-source-control/), [SQL Compare](https://www.red-gate.com/products/sql-development/sql-compare/) and [SQL Data Compare](https://www.red-gate.com/products/sql-development/sql-data-compare/), as well as Microsoft's [SQL Server Data Tools](https://docs.microsoft.com/en-us/sql/ssdt/sql-server-data-tools). dbdeploy is open source, the Red Gate Developer Tools comes with a trial version, and SSDT is free if you have Visual Studio.

Let's all get better at what we do.

