---
layout: page
title: SQLite
---

[SQLite](https://www.sqlite.org/index.html) is an in-process library that implements a self-contained, serverless, zero-configuration, transactional SQL database engine.

[SQLite Tutorial](https://www.tutorialspoint.com/sqlite/index.htm)

## Reference
SQLite - CREATE Database<br>
- Basic syntax of SQLitecommand is as follows:<br>
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
<code>sqlite> DROP TABLE tbl1;</code>

<img src="https://cjs6891.github.io/el7_blog/public/img/1482872760.png" alt="" style="">

SQLite - INSERT Query<br>
<pre><code>INSERT INTO tbl1 (ID,WebSite,Username,Notes)
VALUES (NULL, 'https://www.google.com/', 'zero@google.com', 'Join Date: 1970.01.01');</code></pre>

<img src="https://cjs6891.github.io/el7_blog/public/img/1482875405.png" alt="" style="">

SQLite - SELECT Query<br>
<code>SELECT * FROM tbl1;</code>


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