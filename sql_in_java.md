# SQL In Java

## JDBC (Java Database Connectivity)

- Use classes to represent tables
- Execute queries with method calls
- Introducing procedures can be done 2 ways
  - Making routines inside of the database itself
  - Or using JDBC to do it programmatically
- Package `java.sql`
- MySQL JDBC driver is called `Connector/J`

### Functionality

- Can access relational databases from Java
- Provides
  - Opening connection to a db
  - Converting SQL types into Java types
  - Sending SQL statements to the DBMS from the Java code

### How To JDBC

1. Load driver
2. Get connection object
3. Create SQL statement object
4. Write SQL query as Java String
5. Call execute method on statement object with your SQL code as string argument
6. Close connection

### In Java

- Following the steps in the `How To JDBC` heading

```java
import java.sql.*;

class MyJDBCExample {
  public static void main(String[] args) throws SQLException, InstantiationException, IllegalAccessException, ClassNotFoundException {
    Class.forName("com.mysql.jdbc.Driver").newInstance();

    Connection conn = DriverManager.getConnection("URL", "USERNAME", "PASSWORD");

    Statement stm = conn.createStatement();

    String s = "Staff";
    String SQL = "SELECT * FROM " + s;
    // .executeQuery is for select statments only
    ResultSet rset = stm.executeQuery(SQL);

    System.out.println("Data in staff table:\n");
    while (rset.next()) {
      System.out.println("StaffNo: " + rset.getString("StaffNo") + ", Lastname: " + rset.getString("lname") + ", Salary: " + rset.getFloat("Salary"));
    }

    rset.close();
    stm.close();
    conn.close();
  }
}

M E T A
E T A T
T A T E
A T E M
```

- Handle the exceptions with simple `try ... catch` blocks

#### Meta Data

- Can get the columns/types in java like this

```java
ResultSetMetaData rmd = rs.getMetaData();
String col1Type = rmd.getColumnType(1);
String col1Name = rmd.getColumnName(1);
```

- Can also get the connection meta data

```java
DatabaseMetaData dbmd = conn.getMetaData();
String userName = dbmd.getUserName();
String url = dbmd.getURL();
```

#### Non-Select queries

```java
stm.executeUpdate(SQL);
```

#### Combining Select And Update

- Updatable updated the db with changes u make
- Scroll sensitive makes the current view react to scrolling

```java
Statement stm = conn.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE, ResultSet.CONCUR_UPDATABLE);

ResultSet rs = stm.executeQuery("SELECT salary FROM Staff WHERE staffNo = 9");
if (rs.first()) {
  rs.updateString("staffNo", 420);
  rs.updateString("lname", "dogg");
  rs.updateFloat("salary", 42069.0f);
  rs.insertRow();
  rs.moveToCurrentRow();
}
```

## Stored Routines Or Java

- Stored routines
  - Stored routines are optimized
  - Don't need to convert between types
- Java
  - Superior programming model
  - Type system is better suited than procedural SQL for component-oriented programming
  - DB is already overloaded with data so procedures not rly a good option
