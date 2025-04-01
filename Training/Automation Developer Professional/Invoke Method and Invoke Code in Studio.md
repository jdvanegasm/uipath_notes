Here’s a clean and structured **English summary** of the full lesson on **using the `Invoke Method` activity in UiPath**, ideal for study or review:

---
## 🧩 Invoke Method Lesson Overview

By the end of this lesson, we’ll be able to:

1. Identify when to use the **Invoke Method** activity.
    
2. Differentiate between **static** and **instance** methods.
    
3. Configure and use the **Invoke Method** activity in UiPath Studio.
    
### 🔧 What is the Invoke Method Activity?

The **Invoke Method** activity allows you to **call methods from classes** that aren’t available in standard UiPath activities.

- It can call **static** or **instance** methods.
    
- The class doesn't need to inherit from any workflow base class.
    
- Useful when dealing with .NET libraries, DLLs, or methods with:
    
    - No return value (e.g., `Reverse()`)
        
    - Multiple outputs (e.g., `Int32.TryParse()`)
        

---

## 🛠️ Key Properties of Invoke Method:

|Property|Description|
|---|---|
|`MethodName`|Name of the method to call|
|`TargetObject`|For instance methods (need an object)|
|`TargetType`|For static methods (use class type)|
|`GenericTypeArguments`|If the method is generic|
|`Parameters`|Input/output parameters|
|`Result`|Variable to store the return value|

---

## 📚 Static vs Instance Methods

|Static Method|Instance Method|
|---|---|
|Called on the class itself|Called on an object instance|
|Uses `TargetType`|Uses `TargetObject`|
|e.g., `Int32.TryParse()`|e.g., `List<T>.Reverse()`|

### ✅ Tip:

Check MSDN or IntelliSense — if the method signature says `static`, it’s a static method.

---

## 📦 DEMO 1: Using a **Static Method** (`Int32.TryParse`)

### Goal: Convert scraped strings to integers safely (without exceptions).

**Steps:**

1. Scrape a list of string numbers.
    
2. Loop through each item with a `For Each`.
    
3. Use `Invoke Method` to call `Int32.TryParse`.
    
    - **TargetType** = `Int32`
        
    - **MethodName** = `"TryParse"`
        
    - **Parameters:**
        
        - In: `AmountText` (String)
            
        - Out: `AmountValue` (Int32)
            
    - **Result** = Boolean variable `ConvertedSuccessfully`
        
4. Log parsed results and totals.
    

**Why not use Assign?**  
`TryParse` needs to return both a value and a success flag — not possible in a simple `Assign`.

---

## 📦 DEMO 2: Using an **Instance Method** (`List<T>.Reverse()`)

### Goal: Reverse the order of a list of strings.

**Steps:**

1. Create a variable `Products` (List of Strings).
    
2. Assign initial values using `New List(Of String) From {"A", "B", "C"}`.
    
3. Use a Log Message to display the list before reversing.
    
4. Use `Invoke Method`:
    
    - **TargetObject** = `Products`
        
    - **MethodName** = `"Reverse"`
        
5. Use another Log Message to display the reversed list.
    

**Why use Invoke Method?**  
The `Reverse()` method is **void** (no return), so it can’t be used in `Assign`.

---

## 🧪 Extra Examples

### ✅ Example 1: Merge Two DataTables

- Build two sample DataTables: `dt1` and `dt2`.
    
- Use `Invoke Method` to call `dt1.Merge(dt2)`.
    
- Display the result with `Output Data Table` + `Message Box`.
    

### ✅ Example 2: Add Number to List

- Create a list variable: `Num_List = New List(Of Int32) From {10, 45, 87}`
    
- Use `Invoke Method` with:
    
    - **TargetObject** = `Num_List`
        
    - **MethodName** = `"Add"`
        
    - **Parameter**: In value (e.g., 99)
        
- Use `For Each` + `Log Message` to print the updated list.
    

---

## ✅ Final Recap

- Use **Invoke Method** when standard activities fall short.
    
- Know the **difference between static and instance methods**.
    
- For static: use **TargetType**. For instance: use **TargetObject**.
    
- Can handle methods with:
    
    - No output (`void`)
        
    - Multiple outputs
        
    - External libraries
        

---
## 🧩 Invoke Code Lesson Overview

By the end of this lesson, you’ll be able to:

1. Identify when to use the **Invoke Code** activity.
    
2. Configure and use the activity to execute custom code in your workflows.

### 🔧 What is the Invoke Code Activity?

The **Invoke Code** activity allows you to write and execute **VB.NET or C# code directly within UiPath**.

- It **runs synchronously**
    
- Supports **input/output arguments**
    
- Code must not include **functions, procedures, or methods**
    
- Use it when:
    
    - You need to simplify data manipulation
        
    - You want to reduce multiple Assign or Invoke Method activities
        
    - You need to write **custom logic inline**
        

---

## ⚙️ Key Properties

|Property|Description|
|---|---|
|**Arguments**|Supports In, Out, or In/Out types|
|**Code**|The actual VB.NET or C# snippet to be executed|

---

## 🧪 Example 1 – Add Two Numbers (VB.NET)

1. Drag **Invoke Code** to the Designer Panel
    
2. Select **VB.NET** as the language
    
3. Use the code editor to input logic like:
    
    ```vb
    result = number1 + number2
    ```
    
4. Define:
    
    - `number1` and `number2` as **In** arguments
        
    - `result` as an **Out** argument
        

---

## 🧪 Example 2 – Check Leap Year (VB.NET)

1. Use `Invoke Code` activity to check if a year is leap:
    
    ```vb
    If (year Mod 4 = 0 And year Mod 100 <> 0) Or (year Mod 400 = 0) Then
        isLeap = True
    Else
        isLeap = False
    End If
    ```
    
2. Define `year` as **In**, `isLeap` as **Out**
    

---

## ➕ Importing Namespaces

To use certain classes in `Invoke Code`, import their **namespaces**:

1. Open the **Imports Panel** in Studio.
    
2. Type or browse for namespaces (e.g., `System.IO`, `System.Security.Cryptography`)
    
3. Select to add to the project.
    

> 🔔 Note: You can’t define classes, modules, or methods in Invoke Code. Stick to logic inside the code editor using variables and basic operations.

---

## 📦 DEMO: Compare Two Files Using SHA256 Hash

### Objective: Check if two files have the same content by comparing their hash codes.

**Workflow Steps:**

1. **Start with a Sequence**
    
2. **Select files** using two **Select File** activities:
    
    - `FirstFilePath`
        
    - `SecondFilePath`
        
3. Add **Invoke Code** to calculate hash for the first file:
    
    - Use VB.NET SHA256 logic
        
    - Pass `FirstFilePath` as **In**
        
    - Return `FirstFileHashCode` as **Out**
        
4. Log the first file hash code
    
5. Repeat steps 3–4 for the second file
    
6. Add an **If Activity**:
    
    - Condition: `FirstFileHashCode.Equals(SecondFileHashCode)`
        
    - If True → Log “Files are identical”
        
    - Else → Log “Files are different”
        

---

### 🧬 Hash Code Snippet Used in Invoke Code (simplified):

```vb
Dim encryptor As New System.Security.Cryptography.SHA256CryptoServiceProvider
Dim fileStream As FileStream = File.OpenRead(FilePath)
fileStream.Position = 0
Dim bytesToHash() As Byte = encryptor.ComputeHash(fileStream)
fileStream.Close()
Result = ""
For Each item As Byte In bytesToHash
    Result += item.ToString("x2")
Next
```

> Replace `FilePath` and `Result` with arguments in the activity.

---

## ✅ Final Recap

- `Invoke Code` executes custom VB.NET/C# logic **inline**
    
- Supports **In/Out** arguments
    
- Does **not support methods or functions**
    
- Great for:
    
    - Custom logic
        
    - Reducing Assign/Invoke Method clutter
        
    - Hashing, calculations, or conditions
        
- Always import needed **namespaces** for the code to work
    

---

## ✅ Best Practices for `Invoke Method`

By the end of this lesson, you’ll be able to:

✔️ Apply **best practices** when using `Invoke Method` and `Invoke Code`  
✔️ Write **cleaner, safer, and more maintainable** automations

1. **Know Your Method**
    
    - Understand the **input parameters** and **expected output** before using the method.
        
    - Refer to documentation or IntelliSense for method signatures.
        
2. **Use Try-Catch**
    
    - Always wrap the `Invoke Method` activity in a **Try-Catch block** to avoid runtime crashes.
        
    - Catch and log exceptions to improve debugging and stability.
        
3. **Verify Output**
    
    - After invocation, check that the method actually **returned the expected result**.
        
    - Use log messages or conditions to confirm.
        

---

## ✅ Best Practices for `Invoke Code`

1. **Keep It Simple**
    
    - Write **clean and readable** code inside the activity.
        
    - Avoid overly complex logic—split into multiple steps if needed.
        
2. **Handle Variable Scope**
    
    - Variables declared **inside** `Invoke Code` have **local scope**.
        
    - Use **arguments** (In/Out/InOut) for interaction with the rest of the workflow.
        
3. **Use Try-Catch**
    
    - Wrap code logic in a **Try-Catch** block to handle unexpected errors gracefully.
        
    - Log exceptions to trace issues effectively.
        

---

## 🎯 Final Tip:

Whether using `Invoke Method` or `Invoke Code`, aim for:

- **Clarity**
    
- **Error handling**
    
- **Reusability**
    

These practices not only **improve reliability**, but also make your automation easier to maintain and scale.

---
## 🧩 Lesson Overview🔧 What Are Coded Automations?

By the end of this lesson, you’ll be able to:

1. Understand what **coded automations** are and their **types**.
    
2. Create and integrate coded automations in your UiPath projects.
    

**Coded automations** let you build automation using **code (C#)** instead of drag-and-drop activities.  
This approach is ideal for **developers**, **complex logic**, and **collaborative projects**.

You can:

- Use **UiPath services** (like activity packages)
    
- Integrate **APIs**
    
- Add **external .NET NuGet packages**
    
- Write your own **C# classes**
    

> ✅ Coded workflows behave just like standard workflows and can be invoked using `Invoke Workflow File`.

---

## 📂 Types of Coded Automations

1. **Coded Workflows** – Full automations written in code
    
2. **Coded Test Cases** – Used for automation testing
    
3. **Code Source Files** – Reusable code components for other coded files
    

---

## 🛠 How to Use Coded Automations

You need the **UiPath.CodedWorkflows** package, which is:

- **Pre-installed** in new projects using `System.Activities`, `UIAutomation.Activities`, etc. (version 23.10+)
    
- Automatically added when you create a new coded file
    
- Available via **Manage Packages** if not pre-installed
    

This package includes:

- `CodedWorkflowBase` class
    
- `CodedWorkflow` partial class
    

---

## ✅ Benefits of Coded Automations

|Benefit|Description|
|---|---|
|**Enhanced productivity**|Use your coding skills to build faster, smarter workflows|
|**Handles complexity**|Ideal for custom logic, advanced exception handling, reusable functions|
|**Hybrid approach**|Combine code with low-code workflows seamlessly|
|**Better performance**|Write efficient code to boost speed and resource usage|
|**Improved readability**|Clean, organized, documented code is easier to maintain and share|

---

## 🧾 Lesson Summary

- **Coded automations** let you write C#-based workflows directly in UiPath Studio.
    
- They are **flexible, powerful**, and ideal for complex or collaborative automation projects.
    
- Use them alongside low-code workflows for **hybrid automation solutions**.
    

---