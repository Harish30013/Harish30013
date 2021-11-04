
Connect to SQLite Database

import java.sql.Connection;  
import java.sql.DriverManager;  
import java.sql.SQLException;  
   
public class Connect {  
    public static void connect() {  
        Connection conn = null;  
        try {  
            
            String url = "jdbc:sqlite:C:/sqlite/JTP.db";  
            conn = DriverManager.getConnection(url);  
  
            System.out.println("Connection to SQLite has been established.");  
              
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        } finally {  
            try {  
                if (conn != null) {  
                    conn.close();  
                }  
            } catch (SQLException ex) {  
                System.out.println(ex.getMessage());  
            }  
        }  
    }  
    
    public static void main(String[] args) {  
        connect();  
    }  
}  
Create Database using java

import java.sql.Connection;  
import java.sql.DatabaseMetaData;  
import java.sql.DriverManager;  
import java.sql.SQLException;  
   
public class Create {  
  
    public static void createNewDatabase(String fileName) {  
   
        String url = "jdbc:sqlite:C:/sqlite/" + fileName;  
   
        try {  
            Connection conn = DriverManager.getConnection(url);  
            if (conn != null) {  
                DatabaseMetaData meta = conn.getMetaData();  
                System.out.println("The driver name is " + meta.getDriverName());  
                System.out.println("A new database has been created.");  
            }  
   
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        }  
    }  
  
    public static void main(String[] args) {  
        createNewDatabase("MOVIES.db");  
    }  
}  

Create a table using java

import java.sql.Connection;  
import java.sql.DriverManager;  
import java.sql.SQLException;  
import java.sql.Statement;  
   
public class CreateTable {  
   
    public static void createNewTable() {  
        String url = "jdbc:sqlite:C://sqlite/MOVIES.db";  
          
        String sql = "CREATE TABLE IF NOT EXISTS MOVIES(\n"  
                + " MoiveName text PRIMARY KEY,\n"  
                + " actor text NOT NULL,\n"  
                + " actress text NOT NULL,\n"  
                + " director text NOT NULL,\n"  
                 + " Year of Release Date NOT NULL,\n"  
                + ");";  
          
        try{  
            Connection conn = DriverManager.getConnection(url);  
            Statement stmt = conn.createStatement();  
            stmt.execute(sql);  
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        }  
    }  
    public static void main(String[] args) {  
        createNewTable();  
    } 
}  
Insert Record in the table


import java.sql.Connection;  
import java.sql.DriverManager;  
import java.sql.PreparedStatement;  
import java.sql.SQLException;  
   
public class InsertRecords {  
   
    private Connection connect() {  
        String url = "jdbc:sqlite:C://sqlite/SSSIT.db";  
        Connection conn = null;  
        try {  
            conn = DriverManager.getConnection(url);  
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        }  
        return conn;  
    }  
   
  
    public void insert(String name, double capacity) {  
        String sql = "INSERT INTO Movies(Mivename,actor,actress,director,yearofrelease) VALUES(?,?)";  
   
        try{  
            Connection conn = this.connect();  
            PreparedStatement pstmt = conn.prepareStatement(sql);  
            pstmt.setString(1, name);  
            pstmt.setDouble(2, capacity);  
            pstmt.executeUpdate();  
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        }  
    }  
   
    public static void main(String[] args) {  
   
        InsertRecords app = new InsertRecords();  
        app.insert("temper",”Ntr”,”kajal”,”puri”, 2015);  
        app.insert("legend",”balakrishna”,”samantha”,”Bsrinu”,” 2014);  
        app.insert("Jersy",”nani”,”kajal”,”boby”,2019”, 50000);  
    }  
   
}  

Select Records

import java.sql.DriverManager;  
import java.sql.Connection;  
import java.sql.ResultSet;  
import java.sql.SQLException;  
import java.sql.Statement;  
   
public class SelectRecords {  
   
    private Connection connect() {  
        
        String url = "jdbc:sqlite:C://sqlite/SSSIT.db";  
        Connection conn = null;  
        try {  
            conn = DriverManager.getConnection(url);  
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        }  
        return conn;  
    }  
   
  
    public void selectAll(){  
        String sql = "SELECT * FROM employees";  
          
        try {  
            Connection conn = this.connect();  
            Statement stmt  = conn.createStatement();  
            ResultSet rs    = stmt.executeQuery(sql);  
              
            while (rs.next()) {  
                System.out.println(rs.getString("MoiveName") +  "\t" +   
                                   rs.getString("actor") + "\t" +  
                                 rs.getString("actress") + "\t" +  
                               rs.getString("Directorr") + "\t" +  
                                rs.getDate("YearofRelease") + "\t" +  
            }  
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        }  
    }  
      
     
    
    public static void main(String[] args) {  
        SelectRecords app = new SelectRecords();  
        app.selectAll();  
    }  
   
}  

Select Records parameter like Actor name.

import java.sql.DriverManager;  
import java.sql.Connection;  
import java.sql.ResultSet;  
import java.sql.SQLException;  
import java.sql.Statement;  
   
public class SelectRecords {  
   
    private Connection connect() {  
        
        String url = "jdbc:sqlite:C://sqlite/SSSIT.db";  
        Connection conn = null;  
        try {  
            conn = DriverManager.getConnection(url);  
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        }  
        return conn;  
    }  
   
  
    public void selectAll(){  
        String sql = "SELECT * FROM employees";  
          
        try {  
            Connection conn = this.connect();  
            Statement stmt  = conn.createStatement();  
            ResultSet rs    = stmt.executeQuery(sql);  
              
            while (rs.next()) {  
                System.out.println(rs.getString("MoiveName") +  "\t" +   
                                   rs.getString("actor") + "\t" +  
                                 
                                            }  
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        }  
    }  
      
     
    
    public static void main(String[] args) {  
        SelectRecords app = new SelectRecords();  
        app.selectAll();  
    }  
   
}  


import java.sql.Connection;  
import java.sql.DriverManager;  
import java.sql.SQLException;  
   
public class Connect {  
    public static void connect() {  
        Connection conn = null;  
        try {  
            
            String url = "jdbc:sqlite:C:/sqlite/JTP.db";  
            conn = DriverManager.getConnection(url);  
  
            System.out.println("Connection to SQLite has been established.");  
              
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        } finally {  
            try {  
                if (conn != null) {  
                    conn.close();  
                }  
            } catch (SQLException ex) {  
                System.out.println(ex.getMessage());  
            }  
        }  
    }  
    
    public static void main(String[] args) {  
        connect();  
    }  
}  
Create Database using java

import java.sql.Connection;  
import java.sql.DatabaseMetaData;  
import java.sql.DriverManager;  
import java.sql.SQLException;  
   
public class Create {  
  
    public static void createNewDatabase(String fileName) {  
   
        String url = "jdbc:sqlite:C:/sqlite/" + fileName;  
   
        try {  
            Connection conn = DriverManager.getConnection(url);  
            if (conn != null) {  
                DatabaseMetaData meta = conn.getMetaData();  
                System.out.println("The driver name is " + meta.getDriverName());  
                System.out.println("A new database has been created.");  
            }  
   
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        }  
    }  
  
    public static void main(String[] args) {  
        createNewDatabase("MOVIES.db");  
    }  
}  

Create a table using java

import java.sql.Connection;  
import java.sql.DriverManager;  
import java.sql.SQLException;  
import java.sql.Statement;  
   
public class CreateTable {  
   
    public static void createNewTable() {  
        String url = "jdbc:sqlite:C://sqlite/MOVIES.db";  
          
        String sql = "CREATE TABLE IF NOT EXISTS MOVIES(\n"  
                + " MoiveName text PRIMARY KEY,\n"  
                + " actor text NOT NULL,\n"  
                + " actress text NOT NULL,\n"  
                + " director text NOT NULL,\n"  
                 + " Year of Release Date NOT NULL,\n"  
                + ");";  
          
        try{  
            Connection conn = DriverManager.getConnection(url);  
            Statement stmt = conn.createStatement();  
            stmt.execute(sql);  
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        }  
    }  
    public static void main(String[] args) {  
        createNewTable();  
    } 
}  
Insert Record in the table

import java.sql.Connection;  
import java.sql.DriverManager;  
import java.sql.PreparedStatement;  
import java.sql.SQLException;  
   
public class InsertRecords {  
   
    private Connection connect() {  
        String url = "jdbc:sqlite:C://sqlite/SSSIT.db";  
        Connection conn = null;  
        try {  
            conn = DriverManager.getConnection(url);  
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        }  
        return conn;  
    }  
   
  
    public void insert(String name, double capacity) {  
        String sql = "INSERT INTO Movies(Mivename,actor,actress,director,yearofrelease) VALUES(?,?)";  
   
        try{  
            Connection conn = this.connect();  
            PreparedStatement pstmt = conn.prepareStatement(sql);  
            pstmt.setString(1, name);  
            pstmt.setDouble(2, capacity);  
            pstmt.executeUpdate();  
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        }  
    }  
   
    public static void main(String[] args) {  
   
        InsertRecords app = new InsertRecords();  
        app.insert("temper",”Ntr”,”kajal”,”puri”, 2015);  
        app.insert("legend",”balakrishna”,”samantha”,”Bsrinu”,” 2014);  
        app.insert("Jersy",”nani”,”kajal”,”boby”,2019”, 50000);  
    }  
   
}  

Select Records

import java.sql.DriverManager;  
import java.sql.Connection;  
import java.sql.ResultSet;  
import java.sql.SQLException;  
import java.sql.Statement;  
   
public class SelectRecords {  
   
    private Connection connect() {  
        
        String url = "jdbc:sqlite:C://sqlite/SSSIT.db";  
        Connection conn = null;  
        try {  
            conn = DriverManager.getConnection(url);  
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        }  
        return conn;  
    }  
   
  
    public void selectAll(){  
        String sql = "SELECT * FROM employees";  
          
        try {  
            Connection conn = this.connect();  
            Statement stmt  = conn.createStatement();  
            ResultSet rs    = stmt.executeQuery(sql);  
              
            while (rs.next()) {  
                System.out.println(rs.getString("MoiveName") +  "\t" +   
                                   rs.getString("actor") + "\t" +  
                                 rs.getString("actress") + "\t" +  
                               rs.getString("Directorr") + "\t" +  
                                rs.getDate("YearofRelease") + "\t" +  
            }  
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        }  
    }  
      
     
    
    public static void main(String[] args) {  
        SelectRecords app = new SelectRecords();  
        app.selectAll();  
    }  
   
}  

Select Records parameter like Actor name.


import java.sql.DriverManager;  
import java.sql.Connection;  
import java.sql.ResultSet;  
import java.sql.SQLException;  
import java.sql.Statement;  
   
public class SelectRecords {  
   
    private Connection connect() {  
        
        String url = "jdbc:sqlite:C://sqlite/SSSIT.db";  
        Connection conn = null;  
        try {  
            conn = DriverManager.getConnection(url);  
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        }  
        return conn;  
    }  
   
  
    public void selectAll(){  
        String sql = "SELECT * FROM employees";  
          
        try {  
            Connection conn = this.connect();  
            Statement stmt  = conn.createStatement();  
            ResultSet rs    = stmt.executeQuery(sql);  
              
            while (rs.next()) {  
                System.out.println(rs.  
                                 
                                            }  
        } catch (SQLException e) {  
            System.out.println(e.getMessage());  
        }  
    }  
      
     
    
    public static void main(String[] args) {  
        SelectRecords app = new SelectRecords();  
        app.selectAll();  
    }  
   
}  

