---
layout: page
title: SQLite
---

[SQLite](https://www.sqlite.org/index.html) is an in-process library that implements a self-contained, serverless, zero-configuration, transactional SQL database engine.

[SQLite Tutorial](https://www.tutorialspoint.com/sqlite/index.htm)

## Reference
SQLite - CREATE Database<br>
Basic syntax of SQLitecommand is as follows:<br>
<code># /usr/bin/sqlite3 DatabaseName.db</code>

<img src="https://cjs6891.github.io/el7_blog/public/img/1482865400.png" alt="" style="">

SQLite - CREATE Table<br>
Basic syntax of CREATE TABLE statement is as follows:
<pre><code>CREATE TABLE database_name.table_name(
   column1 datatype  PRIMARY KEY(one or more columns),
   column2 datatype,
   column3 datatype,
   .....
    ...
     .
   columnN datatype,
);</code></pre>

<img src="https://cjs6891.github.io/el7_blog/public/img/1482866621.png" alt="" style="">

SQLite - DROP Table<br>
Basic syntax of DROP TABLE statement is as follows. You can optionally specify database name along with table name as follows:<br>
<code>DROP TABLE database_name.table_name;</code>

<img src="https://cjs6891.github.io/el7_blog/public/img/1482872760.png" alt="" style="">

SQLite - INSERT Query<br>
There are two basic syntaxes of INSERT INTO statement as follows:
<pre><code>INSERT INTO TABLE_NAME [(column1, column2, column3,...columnN)]  
VALUES (value1, value2, value3,...valueN);</code></pre>

Here, column1, column2,...columnN are the names of the columns in the table into which you want to insert data.

You may not need to specify the column(s) name in the SQLite query if you are adding values for all the columns of the table. But make sure the order of the values is in the same order as the columns in the table. The SQLite INSERT INTO syntax would be as follows:<br>
<code>INSERT INTO TABLE_NAME VALUES (value1,value2,value3,...valueN);</code>

<img src="https://cjs6891.github.io/el7_blog/public/img/1482875405.png" alt="" style="">

SQLite - SELECT Query<br>
The basic syntax of SQLite SELECT statement is as follows:<br>
<code>SELECT column1, column2, columnN FROM table_name;</code><br>
Here, column1, column2...are the fields of a table, whose values you want to fetch. If you want to fetch all the fields available in the field then you can use following syntax:<br>
<code>SELECT * FROM table_name;</code>

<img src="https://cjs6891.github.io/el7_blog/public/img/1482936733.png" alt="" style="">

You can list down complete information about a table as follows:<br>
<code>SELECT sql FROM sqlite_master WHERE type = 'table' AND tbl_name = 'TableName';</code>

<img src="https://cjs6891.github.io/el7_blog/public/img/1482937384.png" alt="" style="">

SQLite - UPDATE Query<br>
The basic syntax of UPDATE query with WHERE clause is as follows:<br>
<pre><code>UPDATE table_name
SET column1 = value1, column2 = value2...., columnN = valueN
WHERE [condition];</code></pre>

<img src="https://cjs6891.github.io/el7_blog/public/img/1482939153.png" alt="" style="">

 - - - - - 

SQLite Version<br>
<code>sqlite> SELECT sqlite_version () AS 'SQLite Version';</code>

- [git config](https://git-scm.com/docs/git-config) Get and set repository or global options
- [git init](https://git-scm.com/docs/git-init) Create an empty Git repository or reinitialize an existing one
- [git clone](https://git-scm.com/docs/git-clone): Clone a repository into a new directory



## Current Features
- Templates for narrative, drama and poetry
- Responsive design for mobile phones, tablets and PCs.
- Relatively easy to learn and teach
- Works well in high- or low- bandwitdh scenarios
- Easier for digital archives and libraries to preserve
- Open source, open access
- Unobtrusive footnotes
- Metadata in Dublin Core and OpenGraph to play nice with Zotero, libraries and social media.
- Automatic table of content generation
- Simple search functionality
- Annotations via [hypothes.is](https://hypothes.is/)
- Optional: Ability to generate well-formatted bibliographies and linked citations


## Installing and using Ed

To learn how to install and begin using Ed, please visit our [documentation page](http://elotroalex.github.io/ed/documentation/).