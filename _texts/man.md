---
layout: page
title: /usr/bin/man
---

The historical Linux Programmer’s Manual<br>

<table>
  <tr>
    <th>Section</th>
    <th>Content Type</th>
  </tr>
  <tr>
    <td>1</td>
    <td>User Commands</td>
  </tr>
  <tr>
    <td>2</td>
    <td>System Calls</td>
  </tr>
  <tr>
    <td>3</td>
    <td>Library Functions</td>
  </tr>
  <tr>
    <td>4</td>
    <td>Special Files</td>
  </tr>
  <tr>
    <td>5</td>
    <td>File Formats</td>
  </tr>
  <tr>
    <td>6</td>
    <td>Games</td>
  </tr>

  <tr>
    <td>7</td>
    <td>Conventions, Standards, and Miscellaneous</td>
  </tr>
  <tr>
    <td>8</td>
    <td>System Administration and Privileged Commands</td>
  </tr>
  <tr>
    <td>9</td>
    <td>Linux Kernel API</td>
  </tr>
</table>

<p>To distinguish identical topic names in different sections, man page references include the section number in parentheses after the topic. <code>passwd(1)</code> describes the command to change passwords, while <code>passwd(5)</code> explains the <code>/etc/passwd</code> file format for storing local user accounts. </p>

<p><code># man passwd</code> displays <code>passwd(1)</code> by default<br>
<code># man 5 passwd</code> displays <code>passwd(5)</code>
</p>

<p><code><i>/STRING</i></code> Searches forward (down) for <i>STRING</i> in the man page<br>
When performing searches, <i>STRING</i> allows regular expression syntax.
</p>

<p>A keyword search of man pages is performed using <code># man -k <i>KEYWORD</i></code>, which displays a list of keyword-matching man page topics with section numbers.<br>
<img src="https://cjs6891.github.io/el7_blog/public/img/1482960859.png" alt="" style="">
The <code># man -K </code>option performs a full-text page search, not just titles and descriptions like the <code># man -k </code>option.
</p>

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

SQLite - DELETE Query<br>
The basic syntax of DELETE query with WHERE clause is as follows:<br>
<pre><code>DELETE FROM table_name
WHERE [condition];</code></pre>

<img src="https://cjs6891.github.io/el7_blog/public/img/1482939558.png" alt="" style="">

If you want to DELETE all the records from a table, you do not need to use WHERE clause with DELETE query, which would be as follows:<br>
<code>DELETE FROM table_name;</code>

SQLite - LIKE Clause<br>
The basic syntax of % and _ is as follows:<br>
<pre><code>SELECT FROM table_name
WHERE column LIKE 'XXXX%'

or 

SELECT FROM table_name
WHERE column LIKE '%XXXX%'

or

SELECT FROM table_name
WHERE column LIKE 'XXXX_'

or

SELECT FROM table_name
WHERE column LIKE '_XXXX'

or

SELECT FROM table_name
WHERE column LIKE '_XXXX_'</code></pre>

You can combine N number of conditions using AND or OR operators. Here XXXX could be any numeric or string value.<br>

<img src="https://cjs6891.github.io/el7_blog/public/img/1482941528.png" alt="" style="">