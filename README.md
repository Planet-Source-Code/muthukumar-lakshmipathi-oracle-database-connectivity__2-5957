<div align="center">

## Oracle database connectivity


</div>

### Description

simple and effective program for connecting oracle with java and methods available for insertion, updation and deletion
 
### More Info
 
not required

i used JDBC and ODBC bridge so i works in Windows only


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Muthukumar Lakshmipathi](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/muthukumar-lakshmipathi.md)
**Level**          |Beginner
**User Rating**    |5.0 (15 globes from 3 users)
**Compatibility**  |Java \(JDK 1\.5\)
**Category**       |[Databases/ JDBC](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/databases-jdbc__2-61.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/muthukumar-lakshmipathi-oracle-database-connectivity__2-5957/archive/master.zip)





### Source Code

```
/*
 programmer name:Muthukumar and Deva
steps for creating data source
control panel->Administrative Tools->Data Sources (ODBC)->
select user DSN tab then click add button
select Microsoft ODBC driver for Oracle
fill your data source (here it is patni)
and username and servername(oracle)
click of
Limitations:
   This code only works in Windows platform
*/
import java.sql.*;
class Connectivity
{
  Connection conn;
 Statement stmt;
 PreparedStatement s1;
 void connect()
 {
  try
  {
   Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
   conn = DriverManager.getConnection("jdbc:odbc:patni","devarajan","devarajan");
   // patni--->datasource,devarajan---->username,devarajan->password
  }
  catch(Exception e)
  {
   System.out.println("ee"+e.getMessage());
  }
 }
 void insertData(String nme,String roll)
 {
  try
  {
   s1=conn.prepareStatement("insert into stu values(?,?)");
    s1.setString(1,nme);
    s1.setString(2,roll);
    s1.executeUpdate();
    System.out.println("Record inserted");
    s1.close();
  }
  catch(Exception s)
  {
   System.out.println(s.getMessage());
  }
 }
  void updateData()
 {
  try
  {
    stmt=conn.createStatement();
    int i=stmt.executeUpdate("update stu set name='muthukumar4u' where roll='05mx23'" );
    System.out.println("\t\t\t"+i +" record updated in updation funtion");
    stmt.close();
  }
  catch(Exception s)  {
   System.out.println(s.getMessage());
  }
 }
 void deleteData()
 {
  try
  {
    stmt=conn.createStatement();
    int i=stmt.executeUpdate("delete from stu where name='muthukumar4u'" );
    System.out.println(i+" records Deleted");
    stmt.close();
  }
  catch(Exception s)  {
   System.out.println(s.getMessage());
  }
 }
 void displayData()
 {
  try
  {
    stmt=conn.createStatement();
    ResultSet rs = stmt.executeQuery("select * from stu");
    System.out.println("The table contains:");
    while(rs.next())
    {
     System.out.println("Name:"+rs.getString("name"));
     System.out.print("  Roll no:"+rs.getString("roll"));
    }
  }
  catch(Exception e)
  {
   System.out.println(e.getMessage());
  }
 }
}
public class JavatoOracle
{
public static void main(String args[])
{
 Connectivity c=new Connectivity();
  c.connect();
  c.insertData("muthukumar", "05mx23");
  c.displayData();
  c.updateData();
  c.displayData();
  c.deleteData();
  c.displayData();
}
}
```

