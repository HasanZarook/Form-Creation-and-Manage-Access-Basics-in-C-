
# 💻 DB Role Access - WinForms Application

This project is a **C# Windows Forms Application** for accessing and manipulating a **SQL Server database** (`Northwind`). It allows the user to view, insert, and count records from database tables based on user credentials.

---

## 📝 Features

* ✅ Connect to SQL Server using **user-specific credentials**
* ✅ View records from tables:

  * Customers
  * Employees
  * Orders
* ✅ Insert new records into **Customers** table
* ✅ Count records in **Customers** table
* ✅ Provides **status messages** for all operations

---

## 🔧 Components

### Forms

| Form      | Purpose                                         |
| --------- | ----------------------------------------------- |
| **Form1** | Main interface: view, insert, and count records |
| **Form2** | Secondary form (currently placeholder)          |

### Controls

* **TextBox**: for entering IDs and Company Names
* **RadioButtons**: select table (Customers, Employees, Orders)
* **DataGridView**: display table data
* **Buttons**:

  * View Records
  * Insert Record
  * Count Records

---

## ⚡ How It Works

1. **Connect to SQL Server** using credentials from login form:

```csharp
var datasource = @"(local)\SQLEXPRESS";
var database = "Northwind";
var thisUsername = frmLogin.username;
var thisPassword = frmLogin.password;

string connString = @"Data Source=" + datasource + ";Initial Catalog=" + database + ";Persist Security Info=True;User ID=" + thisUsername + ";Password=" + thisPassword;
SqlConnection conn = new SqlConnection(connString);
conn.Open();
```

2. **View Table Records**:

```csharp
command.CommandText = "select * from " + currentTable;
SqlDataAdapter da = new SqlDataAdapter(command);
DataTable dt = new DataTable();
da.Fill(dt);
dataGridView1.DataSource = dt;
```

3. **Insert Record** into Customers table:

```csharp
command.CommandText = "insert into Customers (ID, Company) values('" + txtID.Text + "','" + txtCompanyName.Text + "')";
command.ExecuteNonQuery();
```

4. **Count Records** in Customers table:

```csharp
command.CommandText = "select count(*) from Customers";
int count = (int)command.ExecuteScalar();
```

---

## ⚠️ Notes

* Ensure **Northwind database** is installed on your local SQL Server.
* Connection string uses **SQL Server authentication** with username and password.
* This project uses **WinForms**, **ADO.NET**, and **DataGridView** for data presentation.
* Proper error handling implemented with `try-catch` for database operations.

---

## 📂 Getting Started

1. Open the solution in **Visual Studio**.
2. Ensure **SQL Server** is running and the database `Northwind` exists.
3. Adjust **connection strings** in `Form1.cs` if necessary.
4. Build and run the application.

---

✅ Ready for viewing, inserting, and counting database records!

---
