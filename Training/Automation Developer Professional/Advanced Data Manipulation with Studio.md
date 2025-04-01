### **Introduction to LINQ – Summary for Technical Reference**

#### **Definition**

LINQ (Language-Integrated Query) is a feature introduced in .NET Framework 3.5, allowing queries to be written directly in C# or VB.NET against various data sources (e.g., arrays, lists, XML, SQL, DataTables) using a consistent syntax.

#### **Key Concepts**

- **Namespace**: Requires `System.Linq`.
    
- **Applies to**: Any collection implementing `IEnumerable` or `IEnumerable<T>`.
    
- **Use in UiPath**: Efficient for filtering and transforming DataTables and collections using LINQ inside activities like `Assign`, `ForEach`, and `Invoke Code`.
    

#### **Benefits**

- Less and cleaner code (replaces nested loops).
    
- Faster development.
    
- Improved readability and maintainability.
    
- Standardized querying across different data sources.
    
- IntelliSense support for better query building.
    
- Data shaping: retrieve and transform data as needed.
    

#### **LINQ Syntax Types**

1. **Method Syntax** (Fluent API using extension methods):
    
    ```csharp
    arrValues.Select(item => item * item).ToArray();
    ```
    
2. **Query Syntax** (SQL-like style):
    
    ```csharp
    from item in arrValues select item * item;
    ```
    

#### **Lambda Expressions**

- Anonymous functions used in LINQ.
    
- Syntax (C#): `parameter => expression`
    
- Example: `(x => x * x)` returns square of x.
    

#### **Using LINQ in UiPath**

- **Import `System.Linq`** via the _Imports_ panel.
    
- **Invoke Code**: Embed LINQ directly using C#.
    
- **Assign Activity**: Store LINQ query results (e.g., filter DataTable rows).
    
- **Common in DataTable filtering**, object collections, or string manipulation tasks.
    

---
## **Filtering Data in Collection with LINQ – Technical Summary**

### **Objective**

Use LINQ in UiPath to:

- Filter overdue invoices in USD.
    
- Sort invoices by Total (descending).
    
- Identify invoices with totals > 100,000.
    

---

### **Initial Setup**

**Project**: `Demo1_FilterInvoiceData`  
**Workflows**:

- `LoginAndExtractData`: Logs into ACME website, extracts invoices.
    
- `FilterInvoiceData`: Applies LINQ filtering and processing.
    
- `Main`: Invokes the two workflows above.
    

---

### **Steps Overview**

#### **1. Login and Extract Invoice Data**

- Create an **Orchestrator Credential asset** (`ACMECredential`) for ACME login.
    
- Use `Get Credential` to retrieve login details.
    
- Automate login with `Use Browser`, navigate to Invoices page.
    
- Extract invoice table with **Table Extraction** wizard.
    
- Export the data as a **CSV file**.
    
- Create output argument: `out_InvoiceData` (DataTable).
    

---

### **2. Filter Data with LINQ**

Workflow: `FilterInvoiceData`

#### **Setup**

- Input Argument: `in_InvoicesDt` (DataTable)
    
- Variables:
    
    - `dt_FilteredInvoices` (DataTable)
        
    - `FilteredInvStr` (String)
        
    - `AnyLargeTotals` (Boolean)
        
    - `GivenDateStr = "2018-05-01"` (String)
        

#### **LINQ Query 1 – Filter Overdue USD Invoices**

```vb
dt_FilteredInvoices = in_InvoicesDt.AsEnumerable().
  Where(Function(row) 
    Not row("Date").ToString.Contains("0000") AndAlso 
    DateTime.ParseExact(row("Date").ToString, "yyyy-MM-dd", Nothing) < DateTime.Parse(GivenDateStr) AndAlso 
    row("Currency").ToString = "USD").
  CopyToDataTable()
```

#### **Log Filtered Results**

- Convert DataTable to String using `Output Data Table`
    
- Log the string result with `Log Message`
    

---

### **3. Remove Currency From Total (Invoke Code)**

**Purpose**: Convert `"12345 USD"` to `"12345"`  
**Code**:

```vb
For Each row As DataRow In dt_FilteredInvoices.Rows
    row("Total") = row("Total").ToString.Split(" "c)(0)
Next
```

---

### **4. Sort by Total Descending**

```vb
dt_FilteredInvoices = dt_FilteredInvoices.AsEnumerable().
  OrderByDescending(Function(row) CInt(row("Total").ToString)).
  CopyToDataTable()
```

---

### **5. Check for Totals > 100,000**

```vb
AnyLargeTotals = dt_FilteredInvoices.AsEnumerable().
  Any(Function(row) CInt(row("Total").ToString) > 100000)
```

- Output the result with `Log Message`.
    

---

### **6. Final Integration**

In `Main` workflow:

- Create a local variable `dt_Invoices` (DataTable).
    
- **Invoke** `LoginAndExtractData` → store result in `dt_Invoices`.
    
- **Invoke** `FilterInvoiceData` → pass `dt_Invoices` as input.
    
- Ensure browser is closed/logged out before running.
    

---

### **Key LINQ Applications Recap**

- `Where()` → filter rows based on multiple conditions.
    
- `OrderByDescending()` → sort by numerical value.
    
- `Any()` → check for conditional existence.
    
- `AsEnumerable()` and `CopyToDataTable()` → required for DataTable queries.
    
- Use `Invoke Code` to pre-process string values in columns.
    

---
## 🧩 **Working with JSON Objects in UiPath**

### **What is JSON?**

- A **lightweight, text-based format** for data exchange (commonly used in APIs and web services).
    
- Represents data as:
    
    - **Key-value pairs** (objects)
        
    - **Ordered lists** (arrays)
        
- Example:
    

```json
{
  "name": "John Doe",
  "age": 30,
  "skills": ["RPA", "Python"],
  "address": { "city": "New York" }
}
```

### **Key Terms**

- **Serialization**: Convert object → JSON string (for transmission).
    
- **Deserialization**: Convert JSON string → .NET object (to manipulate).
    

### **UiPath Activity: `Deserialize JSON`**

- **Input**: JSON string (from file, API, etc.)
    
- **Output**: JObject (or JArray)
    
- **Usage**: Use the `Newtonsoft.Json.Linq` namespace to access keys:
    
    ```vb
    jsonObj("name").ToString
    jsonObj("address")("city").ToString
    jsonObj("skills")(0).ToString
    ```
    

### **Steps to Work with JSON**

1. Use `Read Text File` to get the JSON string.
    
2. Use `Deserialize JSON` to convert string into JObject.
    
3. Access elements using key names.
    

---

## 🕒 **Working with DateTime Objects in UiPath**

### **What is DateTime?**

- A `.NET type`: `System.DateTime`
    
- Stores **date and time** values.
    

### **Common Use Cases**

- Comparing deadlines (e.g., overdue invoices).
    
- Formatting for logs or UI.
    
- Time calculations (add/subtract days, hours).
    
- String parsing with known formats.
    

---

### **Key Methods & Operations**

#### 📌 **Declare and Initialize**

```vb
DateTimeVar = Now  ' Gets current date and time
```

#### 📌 **Convert DateTime → String**

```vb
DateTimeVar.ToString()                      ' Default format
DateTimeVar.ToString("yyyy-MM-ddTHH:mm:ss") ' Custom format (ISO 8601)
```

#### 📌 **Convert String → DateTime**

```vb
DateTime.Parse("04/16/2021") ' Assumes MM/dd/yyyy (Invariant Culture)
```

#### 📌 **Strict Parsing with Format**

```vb
DateTime.ParseExact("16/04/2021", "dd/MM/yyyy", CultureInfo.InvariantCulture)
```

#### 📌 **Multiple Format Support**

```vb
DateTime.ParseExact("16.04.2021", {"dd/MM/yyyy", "dd.MM.yyyy"},
  CultureInfo.InvariantCulture, DateTimeStyles.None)
```

---

### **Add/Subtract Time**

```vb
DateTimeVar.AddHours(2)     ' Add 2 hours
DateTimeVar.AddDays(-14)    ' Subtract 14 days
```

---

### **Date Difference**

```vb
DateTimeVar.Subtract(OtherDate).TotalDays.ToString

' Get absolute value:
Math.Abs((DateTimeVar - OtherDate).TotalDays).ToString
```

---

### **Summary of Methods**

|Method|Description|
|---|---|
|`ToString()`|Converts DateTime to string|
|`Parse()`|Converts string to DateTime (default format)|
|`ParseExact()`|Converts string to DateTime with known format|
|`AddDays()`, `AddHours()`|Adds/subtracts time units|
|`Subtract()`|Gets difference between two DateTimes|
|`Math.Abs()`|Ensures positive result when subtracting dates|
