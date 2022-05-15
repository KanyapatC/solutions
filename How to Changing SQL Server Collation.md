# How to Changing SQL Server Collation After installation

# Probleam:

  For change collation new after install, because has issues query data but has syntax wrong it affects script data not working. So must change collation new again after installation

# Collation:

A collation specifies the bit patterns that represent each character in a data set. Collations also determine the rules that sort and compare data. SQL Server supports storing objects that have different collations in a single database. For non-Unicode columns, the collation setting specifies the code page for the data and which characters can be represented. Data that is moved between non-Unicode columns must be converted from the source code page to the destination code page. 

# Resolve

Step 1 
Let's confirm the current collation assigned to database <Yourdatabase>:

```
SELECT name, collation_name FROM sys.databases WHERE name = '<Yourdatabase>';
```

Step 2
We can now redefine the desired collation for database Products with the following code:

```
-- make sure no one else is using database
ALTER DATABASE <Yourdatabase> SET SINGLE_USER WITH ROLLBACK IMMEDIATE

-- change collation to Modern_Spanish_CI_AI_WS
ALTER DATABASE <Yourdatabase> COLLATE Thai_CI_AS;

-- allow users back into the database
ALTER DATABASE <Yourdatabase> SET MULTI_USER
```
Step 4

Let's check again if the change was successful:
```
SELECT name, collation_name FROM sys.databases WHERE name = '<Yourdatabase>';
```

ref. https://www.mssqltips.com/sqlservertip/3519/changing-sql-server-collation-after-installation/