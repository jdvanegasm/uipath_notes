## 📋 **REFramework Without Queue Items — Summary**

### 🎯 Goal: Build REFramework-based automation using **tabular data** (e.g., Excel, DataTables) instead of **Orchestrator queues**, using the **dedicated checklist**.

---

## ✅ **Main Objectives**

- Implement a simple REFramework process **without queue items**.
    
- Use the **REFramework without Queue Items Checklist** to structure development.
    
- Adjust framework components to work with **custom data types** like `DataRow`.
    

---

## 📂 **Checklist Overview: Key Components**

### 1. **Prerequisites**

- By default, `TransactionItem` = `QueueItem`.
    
- Identify the **actual data type** for the process (e.g., `DataRow`, `String`, `Dictionary`, etc.).
    
- Ensure input data is **available locally** or from a structured source (e.g., Excel).
    

---

### 2. **Configuration in UiPath Studio**

- Create a new project using the **REFramework template**.
    
- Edit the **Config.xlsx** file:
    
    - Add file paths, constants, application settings.
        
    - Define paths to input data files if needed.
        

---

### 3. **Change `TransactionItem` Data Type**

- Open the **Main.xaml** and other dependent workflows.
    
- Update all references of `TransactionItem`:
    
    - Change type from `QueueItem` to e.g. `DataRow` or `String`.
        
    - Update argument types in:
        
        - `GetTransactionData.xaml`
            
        - `Process.xaml`
            
        - `SetTransactionStatus.xaml` (remove if not using queues)
            

---

### 4. **Applications Used: Open / Close / Kill**

- Edit the following files to match your app:
    
    - `InitAllApplications.xaml` → Open/Login apps
        
    - `CloseAllApplications.xaml` → Graceful shutdown
        
    - `KillAllProcesses.xaml` → Force close if needed
        

---

### 5. **Business Process: GetTransactionData & Process Transaction**

- In `GetTransactionData.xaml`:
    
    - Replace `Get Transaction Item` with custom logic to fetch **one item** from a collection (e.g., iterate through a `DataTable`).
        
    - Track current index manually.
        
- In `Process.xaml`:
    
    - Implement logic to **process one transaction** using your defined `TransactionItem` data type.
        
    - Add exception handling as needed.
        

---

## 🧠 Notes

- The checklist covers **basic projects** with structured data.
    
- It doesn’t account for **complex branching logic**, **multiple sources**, or **external system integration**.
    
- Always refer to the REFramework **Documentation PDF** found in the `/Documentation` folder of the template.
    

---

## 🔁 Summary Flow

|Step|Action|
|---|---|
|Set up Config.xlsx|Define paths, constants, app names|
|Change `TransactionItem` type|Use `DataRow`, `String`, or other suitable type|
|Modify Init/Close/Kill flows|Ensure apps open and close properly|
|Customize GetTransactionData|Pull items from your tabular source (e.g., `DataTable`)|
|Edit Process.xaml|Handle one transaction using new data type and logic|

---
## 🧠 **Whiteboarding Automation Workflows (Excel-Based Input)**

### 🎯 Goal: Visually design and break down an automation process into **modular, reusable workflows** before implementation.

---

### ✅ **Key Learning Objectives**

- Whiteboard workflows to **visualize** and **organize** automation logic.
    
- Identify and reuse **pre-built custom workflows** in your project.
    
- Replace **Orchestrator Queues** with **Excel** as the data source.
    

---

### 🔄 **Process Overview**

- Input: **Excel file** with fields: `Cash In`, `On Us Check`, `Not On Us Check`.
    
- Application: **UiDemo**
    
- Objective: For each row in the Excel sheet:
    
    - Open UiDemo
        
    - Type values
        
    - Click Accept
        
    - Log outcome
        
- No queue items → transaction status **must be handled manually** (logging, error handling, etc.).
    

---

### 🧱 **Component Breakdown (Whiteboard View)**

|Component Name|Description|Pre-condition|Outcome|Arguments|State(s) Used|
|---|---|---|---|---|---|
|`UIDemo_Open`|Opens UiDemo and logs in|UiDemo installed at path defined in Asset|UiDemo is open and logged in|`in_CredentialName`, `in_UiDemoAppPath`|Initialization|
|`UIDemo_Close`|Gracefully closes UiDemo|UiDemo is open and logged in|UiDemo closed|None|Process Transaction, End|
|`UIDemo_ForceClose`|Kills UiDemo process|N/A|UiDemo is closed|None|Init, Process, End|
|`UIDemo_AddTransaction`|Enters values and clicks Accept|UiDemo open and logged in|New transaction processed|`in_CashIn`, `in_OnUsCheck`, `in_NotOnUsCheck`, `out_TransactionNumber`|Process Transaction|

---

### 🧩 **Best Practices**

- Always **whiteboard your custom workflows** before development.
    
- Focus on **reusability** — components like `Open`, `Close`, and `AddTransaction` may be shared across projects.
    
- Avoid whiteboarding **internal framework logic** — focus on **your business process**.
    
- Use the provided **Process Whiteboard Template.xlsx** to draft components visually.
    

---

### 📦 **Provided Resources**

- ✅ `UiDemo Process_Custom-Built Workflows.zip` → Contains prebuilt component workflows
    
- ✅ `Process Whiteboard Template.xlsx` → Template for documenting your project’s modular design
    

---

### 📌 Summary

Whiteboarding is the planning step before building automation. In this case, although the input is **Excel** and not **Queues**, the business process remains the same. Use the **same reusable components**, adapted to work with your Excel-driven transaction loop.

---
## ⚙️ **REFramework Project Configuration (No Queues)**

### 🎯 Purpose: Configure the `Config.xlsx` file for a REFramework project that processes data from an **Excel file (tabular data)** instead of Orchestrator queues.

---

### ✅ **Key Objectives**

- Populate the **Settings**, **Constants**, and **(optionally) Assets** sheets.
    
- Handle **credentials** using **Windows Credential Manager**.
    
- Define all process-specific paths and thresholds.
    

---

## 🗂️ **Config File Setup**

### 1. **Settings Sheet**

|Key|Value (Example)|Purpose|
|---|---|---|
|`logF_BusinessProcessName`|`Finance_REF_UiDemo`|Used in logs and reports|
|`UiDemo_ApplicationPath`|Full or relative path to the `.exe` file|To start UiDemo application|
|`UiDemo_CredentialName`|`UiDemo_Credential` (in Credential Manager)|Used for logging into UiDemo|
|`InputFilePath`|`Data\Input\UiDemo-Transactions.xlsx`|File with transaction data (Cash In, Checks...)|
|`ManualTransactionThreshold`|`10000`|Triggers Business Rule Exception above this sum|

> ❌ Remove queue-related keys: `OrchestratorQueueName`, `OrchestratorQueueFolder`.

---

### 2. **Constants Sheet**

|Constant|Value|Purpose|
|---|---|---|
|`MaxRetryNumber`|`1`|Retries 1 time on **system exceptions**|
|`MaxConsecutiveSystemExceptions`|`3`|Job fails if 3 system exceptions occur in a row|
|`RetryNumberGetTransactionItem`|default|Not relevant unless fetching from Orchestrator|
|`RetryNumberSetTransactionStatus`|default|Also irrelevant without Orchestrator|
|`ShouldMarkJobAsFaulted`|`TRUE`|Marks job as Failed if init fails or max exceptions exceeded|

---

### 3. **Assets Sheet**

- **Not used** in this project (Orchestrator not involved).
    
- Credentials handled via **Windows Credential Manager**:
    
    - Go to Control Panel → Credential Manager → **Add Generic Credential**
        
        - Name: `UiDemo_Credential`
            
        - User: `admin`, Password: `password`
            

---

### 📥 **Input Data**

- File: `UiDemo-Transactions.xlsx`
    
- Location: `Data/Input/`
    
- Used instead of queues; each **row = transaction**
    

---

### 🧩 **Workflow Organization**

- Add workflows into a `UiDemo/` folder inside the project:
    
    - `UiDemo_Open.xaml`
        
    - `UiDemo_Close.xaml`
        
    - `UiDemo_ForceClose.xaml`
        
    - `UiDemo_AddTransaction.xaml`
        

---

### 🧠 Summary Points

- No queues: use **Excel (DataTable)** as the source.
    
- Define **all paths and parameters** in `Config.xlsx`.
    
- Store **credentials securely** using **Credential Manager**, not plain text.
    
- Set `MaxRetryNumber` manually since there’s no Orchestrator retry logic.
    
- Remove queue-related config values.
    
- No need to edit the Assets sheet unless you later add Orchestrator integration.
    

---

### 📌 Tip for Logging

- The value in `logF_BusinessProcessName` will prefix all log messages → useful for tracking execution in logs or dashboards.
    

---
## 🔄 **Change TransactionItem Data Type — Summary**

### 🎯 Goal: Update the **TransactionItem type from `QueueItem` to `DataRow`** to support tabular data input (e.g., Excel).

---

### ✅ **Key Objectives**

- Modify the **TransactionItem variable and arguments** to match the tabular data type.
    
- Update **workflow arguments and assignments** to remove validation errors.
    
- Adapt REFramework logic to process **`DataRow`** objects instead of queue items.
    

---

## 🔧 **Steps to Change TransactionItem to `DataRow`**

### 1. **In `Main.xaml`**

- Change:
    
    ```vb
    TransactionItem: QueueItem → System.Data.DataRow
    ```
    

---

### 2. **Fix Validation Errors**

#### 🔹 **Get Transaction Data state**

- **Assign → Then Block (Stop requested)**
    
    - Reset the assignment: clear value, retype `Nothing` to refresh type match.
        
- **Invoke GetTransactionData.xaml**
    
    - Update `Out_TransactionItem` argument to type: `DataRow`
        
- **Try/Catch → End Process Assign**
    
    - Also reassign `TransactionItem = Nothing` to refresh type.
        

---

#### 🔹 **Process Transaction state**

- **Invoke Process.xaml**
    
    - Update `in_TransactionItem` argument → type: `DataRow`
        
- **SetTransactionStatus.xaml Invocations** (Success, Business, System Exception):
    
    - Update `in_TransactionItem` to `Nothing`
        
        - Reason: The workflow checks if it's a `QueueItem` internally; using `Nothing` disables status reporting.
            
        - Optional: Update SetTransactionStatus to support `DataRow` if needed.
            

---

### 🧠 Best Practices

|Tip|Why It Matters|
|---|---|
|`TransactionItem` can be of any collection item type|Supports flexibility for Email (`MailMessage`), File path (`String`), etc.|
|Always reassign or refresh `Assign` activity values after type change|Prevents type mismatch validation errors|
|Set `in_TransactionItem = Nothing` in `SetTransactionStatus`|Prevents Queue-only logic from throwing errors|

---

### 🗂 Summary of Changes

|Component / File|Change Made|
|---|---|
|`Main.xaml`|Variable `TransactionItem` type → `DataRow`|
|`GetTransactionData.xaml`|Output argument type changed, updated Assign activities|
|`Process.xaml`|Input argument changed|
|`SetTransactionStatus.xaml` calls|`in_TransactionItem` set to `Nothing` in all 3 branches|

---

### 📌 Recap

- Transaction data comes from **Excel**, not Orchestrator.
    
- Therefore, each **transaction item is a `DataRow`**.
    
- After changing the type:
    
    - Refresh Assign activities
        
    - Update arguments in all affected workflows
        
    - Set unused arguments to `Nothing` if the invoked logic expects `QueueItem`.
        

---
## 🧰 **Configure Application Handling in REFramework**

### 🎯 Goal: Integrate and configure **custom workflows** to **open**, **close**, and **force-close** applications (e.g., **UiDemo**) in REFramework.

---

### ✅ **Key Objectives**

- Modify `InitAllApplications.xaml`, `CloseAllApplications.xaml`, and `KillAllProcesses.xaml`.
    
- Use the custom workflows:
    
    - `UiDemo_Open.xaml`
        
    - `UiDemo_Close.xaml`
        
    - `UiDemo_ForceClose.xaml`
        
- Retrieve credentials securely via **Windows Credential Manager**.
    
- Fix missing activity issue by installing the correct **package**.
    

---

## 🧩 **Workflow Configuration**

### 1. **InitAllApplications.xaml**

- **Purpose**: Open & configure apps at the start.
    
- **Invoked Workflow**: `UiDemo_Open.xaml`
    
- **Arguments passed**:
    
    ```vb
    in_CredentialName: in_Config("UiDemo_CredentialName").ToString
    in_UiDemoAppPath: in_Config("UiDemo_ApplicationPath").ToString
    ```
    

#### Inside `UiDemo_Open.xaml`

- Uses `Get Secure Credential` to retrieve credentials from **Windows Credential Manager**.
    
    - Target: `in_CredentialName`
        
    - Output: `Username`, `Password`
        
- **Fix missing activity**:
    
    - Install package: `UiPath.Credentials.Activities`
        

---

### 2. **CloseAllApplications.xaml**

- **Purpose**: Gracefully close all applications after transaction processing or errors.
    
- **Invoked Workflow**: `UiDemo_Close.xaml`
    
- No input arguments required.
    

---

### 3. **KillAllProcesses.xaml**

- **Purpose**: Force close applications if they’re still running (e.g., after exception).
    
- **Invoked Workflow**: `UiDemo_ForceClose.xaml`
    
- No input arguments required.
    

---

## 🛠 Best Practices

|Practice|Why?|
|---|---|
|Use **separate workflow per app**|Promotes reusability and modularity|
|Reference values from `Config.xlsx`|Makes updates easier without modifying the code|
|Retrieve credentials from **Credential Manager**|Keeps credentials secure and manageable|
|Rename activities (e.g., `GetSecureCredential for UiDemo`)|Improves readability and debugging|
|Save frequently|Prevents loss of configuration and avoids prompts|

---

## 📦 Required Package

|Package Name|Purpose|
|---|---|
|`UiPath.Credentials.Activities`|Required for `Get Secure Credential` activity|

---

## 🧠 Summary Table

|Workflow File|Invoked In|Purpose|
|---|---|---|
|`UiDemo_Open.xaml`|`InitAllApplications.xaml`|Launch UiDemo and log in|
|`UiDemo_Close.xaml`|`CloseAllApplications.xaml`|Close UiDemo gracefully|
|`UiDemo_ForceClose.xaml`|`KillAllProcesses.xaml`|Force-terminate UiDemo if needed|

---

## 🧾 Additional Notes

- The app path and credential name should be stored in the **Settings** sheet of `Config.xlsx`.
    
- Credential should exist in **Windows Credential Manager** as a **Generic Credential**.
    
- Typical values:
    
    - Credential name: `UiDemo_Credential`
        
    - Username: `admin`, Password: `password` (demo credentials)
        

---
## 📥 **Configure `GetTransactionData.xaml` for Tabular Data**
### 🎯 Goal: Replace the default Orchestrator-based logic with **Excel-based logic** to retrieve one `DataRow` per transaction.

---

### ✅ **Key Objectives**

- Remove Orchestrator dependency by deleting `Get Transaction Item`.
    
- Use a **local Excel file** to fetch transaction data.
    
- Retrieve and serve **one `DataRow` per transaction**.
    
- Implement **retry-friendly logic** using `TransactionNumber`.
    

---

## 🔧 **Step-by-Step Breakdown**

### 1. **Change Output Argument Type**

- `out_TransactionItem`:  
    `QueueItem → System.Data.DataRow`
    

---

### 2. **Delete `Get Transaction Item` Activity**

- It is only useful for Orchestrator queues.
    
- Replace with **logic to read Excel data**.
    

---

### 3. **Use `Workbook Read Range` to Load Data (Once)**

- Path: `in_Config("InputFilePath").ToString`
    
- Sheet: `"Sheet1"` (or default)
    
- Range: _empty_ (reads all)
    
- Headers: ✔️ enabled
    
- Output: `io_dt_TransactionData`
    
    - **Direction**: `In/Out`
        
    - Used to **load once**, then iterate over memory.
        

#### Wrap in:

```vb
If io_dt_TransactionData Is Nothing Then
    Read Excel to io_dt_TransactionData
End If
```

---

### 4. **Add IF Logic to Serve One Row at a Time**

```vb
If in_TransactionNumber <= io_dt_TransactionData.Rows.Count Then
    out_TransactionItem = io_dt_TransactionData(in_TransactionNumber - 1)
Else
    out_TransactionItem = Nothing
End If
```

#### Why?

- `TransactionNumber` tracks index.
    
- Used for retrying failed transactions (don’t increment).
    
- Keeps compatibility with REFramework loop logic.
    

---

### 5. **Set Logging Fields**

Used in `SetTransactionStatus.xaml` to improve log context.

|Field|Value|
|---|---|
|`logF_TransactionID`|`Now.ToString("yyyyMMddHHmmssfff")` (or any unique timestamp)|
|`logF_TransactionField1`|Example: `row("Cash In") & "-" & row("On Us Check") & "-" & row("Not On Us Check")`|
|`logF_TransactionField2`|Optional (use for other transaction metadata)|

---

## 📌 Optional Design Tip

You _could_ move the file reading to `InitAllSettings.xaml`, and assign it to a global `dt_TransactionData` variable. This avoids redundant logic in `GetTransactionData.xaml`, but you lose retry-specific control.

---

### 🧠 Summary Table

|Element|Purpose|
|---|---|
|`Workbook Read Range`|Reads Excel into `io_dt_TransactionData`|
|`io_dt_TransactionData`|Stores full DataTable, `In/Out` argument|
|`TransactionNumber`|Index of current transaction (starts at 1, maps to row index -1)|
|`out_TransactionItem`|One `DataRow` per execution cycle|
|`logF_TransactionID`|Unique ID for tracking/logging|
|`logF_TransactionField1`|Additional transaction info (concatenated fields for logging)|

---

### 🧠 Reflection Questions

- Why remove `Get Transaction Item`?  
    → It only applies to Orchestrator queues.
    
- Why `io_dt_TransactionData` as `In/Out`?  
    → Loaded once, reused across transaction cycles.
    
- Why use `TransactionNumber`?  
    → Enables retry by index, and tracks transaction progress.
    

---
## 🧠 **Configure `Process.xaml` for Tabular Data**

### 🎯 Goal: Process one `DataRow` transaction, perform validation, and handle **Business Rule Exceptions**.

---

### ✅ **Key Objectives**

- Convert `in_TransactionItem` to **`DataRow`**.
    
- Extract & convert values to `Decimal`.
    
- Add **business rule validation**.
    
- Invoke `UiDemo_AddTransaction.xaml` with validated data.
    

---

## 🔧 Step-by-Step Breakdown

### 1. **Change Argument Type**

- `in_TransactionItem`:  
    `QueueItem → System.Data.DataRow`
    

---

### 2. **Extract Data from TransactionItem**

- Create variables of type `Decimal`:
    
    - `CashIn`
        
    - `OnUsCheck`
        
    - `NotOnUsCheck`
        
- Use a **Multiple Assign** activity:
    
    ```vb
    CashIn = CDec(in_TransactionItem("CashIn"))
    OnUsCheck = CDec(in_TransactionItem("OnUsCheck"))
    NotOnUsCheck = CDec(in_TransactionItem("NotOnUsCheck"))
    ```
    

---

### 3. **Input Validation — Business Rule**

#### Sequence: `"Input data validation"`

##### Variable:

- `TransactionSum` → Type: `Decimal`
    

##### Assign:

```vb
TransactionSum = CashIn + OnUsCheck + NotOnUsCheck
```

##### IF condition:

```vb
TransactionSum > CDec(in_Config("ManualTransactionThreshold"))
```

##### Then (Invalid):

- Use `Throw` activity:
    

```vb
New BusinessRuleException("Transaction value exceeds threshold.")
```

##### Else (Valid):

- Proceed to process the transaction.
    

---

### 4. **Invoke Business Logic Workflow**

- **Workflow**: `UiDemo_AddTransaction.xaml`
    
- **Arguments passed**:
    
    ```vb
    in_CashIn = CashIn
    in_OnUsCheck = OnUsCheck
    in_NotOnUsCheck = NotOnUsCheck
    out_TransactionNumber → TransactionNumber (new variable)
    ```
    

---

## 🛠 Best Practices Used

|Practice|Reason|
|---|---|
|Changed argument type to `DataRow`|To match new data source (Excel)|
|Used `Decimal` conversions explicitly|Ensures correct arithmetic & validation|
|Used `Throw BusinessRuleException`|Clean separation of validation vs. system errors|
|Annotated and renamed activities|Improves maintainability and readability|
|Logged values (e.g., TransactionNumber)|Enhances traceability in logs/reports|

---

## 🧾 Summary Table

|Step|Details|
|---|---|
|Argument Changed|`in_TransactionItem → DataRow`|
|Extract Values|Convert using `CDec(row("ColumnName"))`|
|Validate Business Rule|`TransactionSum > ManualTransactionThreshold`|
|Throw on Invalid|`Throw New BusinessRuleException(...)`|
|Invoke Transaction Logic|`UiDemo_AddTransaction.xaml`|
|Output Transaction Number|Stored in `TransactionNumber` variable|

---

## 📌 Reflection Q&A

|Question|Answer|
|---|---|
|What data type is `in_TransactionItem` now?|`System.Data.DataRow`|
|Where is the business rule defined?|In the **validation sequence** inside `Process.xaml`|
|What triggers a `BusinessRuleException`?|If `TransactionSum > ManualTransactionThreshold`|
|Why do we use `TransactionNumber` variable?|To track and possibly log or retry transaction processing|

---
## 🧠 **Configure `Process.xaml` for Tabular Data**

### 🎯 Goal: Process one `DataRow` transaction, perform validation, and handle **Business Rule Exceptions**.

---

### ✅ **Key Objectives**

- Convert `in_TransactionItem` to **`DataRow`**.
    
- Extract & convert values to `Decimal`.
    
- Add **business rule validation**.
    
- Invoke `UiDemo_AddTransaction.xaml` with validated data.
    

---

## 🔧 Step-by-Step Breakdown

### 1. **Change Argument Type**

- `in_TransactionItem`:  
    `QueueItem → System.Data.DataRow`
    

---

### 2. **Extract Data from TransactionItem**

- Create variables of type `Decimal`:
    
    - `CashIn`
        
    - `OnUsCheck`
        
    - `NotOnUsCheck`
        
- Use a **Multiple Assign** activity:
    
    ```vb
    CashIn = CDec(in_TransactionItem("CashIn"))
    OnUsCheck = CDec(in_TransactionItem("OnUsCheck"))
    NotOnUsCheck = CDec(in_TransactionItem("NotOnUsCheck"))
    ```
    

---

### 3. **Input Validation — Business Rule**

#### Sequence: `"Input data validation"`

##### Variable:

- `TransactionSum` → Type: `Decimal`
    

##### Assign:

```vb
TransactionSum = CashIn + OnUsCheck + NotOnUsCheck
```

##### IF condition:

```vb
TransactionSum > CDec(in_Config("ManualTransactionThreshold"))
```

##### Then (Invalid):

- Use `Throw` activity:
    

```vb
New BusinessRuleException("Transaction value exceeds threshold.")
```

##### Else (Valid):

- Proceed to process the transaction.
    

---

### 4. **Invoke Business Logic Workflow**

- **Workflow**: `UiDemo_AddTransaction.xaml`
    
- **Arguments passed**:
    
    ```vb
    in_CashIn = CashIn
    in_OnUsCheck = OnUsCheck
    in_NotOnUsCheck = NotOnUsCheck
    out_TransactionNumber → TransactionNumber (new variable)
    ```
    

---

## 🛠 Best Practices Used

|Practice|Reason|
|---|---|
|Changed argument type to `DataRow`|To match new data source (Excel)|
|Used `Decimal` conversions explicitly|Ensures correct arithmetic & validation|
|Used `Throw BusinessRuleException`|Clean separation of validation vs. system errors|
|Annotated and renamed activities|Improves maintainability and readability|
|Logged values (e.g., TransactionNumber)|Enhances traceability in logs/reports|

---

## 🧾 Summary Table

|Step|Details|
|---|---|
|Argument Changed|`in_TransactionItem → DataRow`|
|Extract Values|Convert using `CDec(row("ColumnName"))`|
|Validate Business Rule|`TransactionSum > ManualTransactionThreshold`|
|Throw on Invalid|`Throw New BusinessRuleException(...)`|
|Invoke Transaction Logic|`UiDemo_AddTransaction.xaml`|
|Output Transaction Number|Stored in `TransactionNumber` variable|

---

## 📌 Reflection Q&A

|Question|Answer|
|---|---|
|What data type is `in_TransactionItem` now?|`System.Data.DataRow`|
|Where is the business rule defined?|In the **validation sequence** inside `Process.xaml`|
|What triggers a `BusinessRuleException`?|If `TransactionSum > ManualTransactionThreshold`|
|Why do we use `TransactionNumber` variable?|To track and possibly log or retry transaction processing|

---
## 📊 Build an Execution Report in REFramework Without Queues

### ⏱ Duration: 15 min

### 🎯 Goal: Capture transaction outcomes in a local Excel file since Orchestrator queues aren’t being used.

---

## 🧠 Why This Matters:

Without Orchestrator queues, we **lose built-in visibility** of:

- Transaction success/failure status
    
- Execution logs per transaction
    

💡 **Solution:** Build a **custom execution report** using Excel and update it after every transaction in `SetTransactionStatus.xaml`.

---

## 🔧 Step-by-Step Configuration

### ✅ **1. Create the Report Template**

- Create `Status.xlsx` in `Data/Output/`
    
- Add column headers:
    
    - `TransactionID`
        
    - `Fields`
        
    - `Status`
        

---

### ✅ **2. Update the Config File**

- Go to **Settings sheet** in `Config.xlsx`
    
- Add:
    
    - **Name:** `StatusFilePath`
        
    - **Value:** `Data/Output/Status.xlsx`
        

---

### ✅ **3. Edit `SetTransactionStatus.xaml`**

#### 🧩 Add Logic to Write to the Report

#### ➤ Create a new sequence

- Name it: `Write Status to file`
    

#### ➤ Assign status label

Inside each branch:

|Sequence|Assign `TransactionStatus =`|
|---|---|
|Success|`"Success"`|
|Business Exception|`"Business Exception"`|
|System Exception|`"Application Exception"`|

> 📌 Set `TransactionStatus` variable **scope to the entire SetTransactionStatus workflow**

---

### ✅ **4. Append Status to Excel**

Inside `Write Status to file` sequence:

#### ➤ Add `Build Data Table`

- Columns: `TransactionID`, `Fields`, `Status`
    
- Save output as: `TransactionStatusDT`
    

#### ➤ Add Data Row

- Use `Add Data Row` activity:
    

```vb
{ in_TransactionID, in_TransactionField1, TransactionStatus }
```

#### ➤ Append to Excel

- Use `Append Range (Workbook)` activity
    
    - FilePath: `in_Config("StatusFilePath").ToString`
        
    - Sheet: `Sheet1`
        
    - DataTable: `TransactionStatusDT`
        

---

## 💡 Best Practices Recap

✅ Capture status **immediately after each transaction**  
✅ Append row-by-row (so partial execution is still logged)  
✅ Use the same **custom log fields** (`TransactionID`, `TransactionField1`)  
✅ Do **not** store in memory for end-of-run write (risk of data loss)

---

## 🧪 Result Example

|TransactionID|Fields|Status|
|---|---|---|
|`20240327153022`|100-25-0|Success|
|`20240327153101`|6000-0-5000|Business Exception|

---

## ❓ Reflection Questions

- What custom fields were reused from log messages?
    
- Why do we write to the report immediately instead of at the end?
    
- What is the fallback if execution is stopped midway?
    

---
## 🧪 **Testing REFramework with Tabular Data**
### 🎯 Goal: Use and customize REFramework’s built-in test cases to validate a project using Excel input (not Orchestrator queues)

---

### ✅ **What You Will Learn**

- Use REFramework's built-in test cases for unit testing
    
- Customize tests for non-queue (tabular) data
    
- Validate workflows using the `Test Suite` and `Test Explorer`
    

---

## 🗂 Built-in Test Cases in REFramework

|Test Case Name|Purpose|
|---|---|
|**GeneralTestCase**|Data-driven tests from Excel sheet (compares expected vs. actual result)|
|**InitAllSettingsTestCase**|Checks if Config dictionary is initialized and contains required keys|
|**InitAllApplicationsTestCase**|Verifies that applications open and required UI elements appear|
|**GetTransactionDataTestCase**|Confirms transaction data is retrieved correctly from Excel file|
|**ProcessTestCase**|Tests whether transaction item is processed successfully|
|**MainTestCase**|Verifies output report/status file against expected result|
|**WorkflowTestCaseTemplate**|Template to create custom tests for user-defined workflows|

---

## 🔧 Key Testing Concepts

### 🧩 **Test Case Structure**

Each test case follows a **Given – When – Then** format:

- **Given**: Setup context (e.g., config, application)
    
- **When**: Invoke workflow to test
    
- **Then**: Validate the result with assertions (e.g., check value, element exists)
    

---

## 🛠️ Test Case Customizations (for Tabular Data)

|Test Case|Customization Steps|
|---|---|
|`GetTransactionDataTestCase`|- Change `TransactionItem` type to `DataRow`- Remove "If TransactionItem Is Nothing" block|
|`ProcessTestCase`|- Map arguments from Excel- Update `in_TransactionItem` type to `DataRow`- Add logic to extract & verify `TransactionNumber`|
|`GeneralTestCase`|- Update Excel sheet with workflow path & expected result|
|`InitAllApplicationsTestCase`|- Use **Check App State** for validation- Assert on UiDemo title|
|`UiDemo_OpenTestCase` (custom)|- Use `WorkflowTestCaseTemplate`- Invoke `UiDemo_Open.xaml` in When section- Verify app opened with expected UI element|
|`UiDemo_AddTransactionTestCase` (custom)|- Run with **data variation**- Verify successful transaction and closing|

---

## 🔍 Test Data Excel (Tests.xlsx)

|Column|Description|
|---|---|
|`Workflow Path`|Path to workflow to test|
|`Expected Result`|Outcome: `Success`, `System.Exception`, or `BusinessRuleException`|

---

## ✅ Output Expectations

|Verification|Outcome if Passed|
|---|---|
|Transaction retrieved|"TransactionItem is not Nothing"|
|Transaction processed|`TransactionNumber` is not empty|
|Application opened|`Check App State = True`|
|Config loaded|`Config.Count > 0` + required key|
|Main workflow report check|Output matches expected report|

---

## 🧾 Summary Table of Customization Steps

|Workflow|Required Customization|
|---|---|
|All test cases|Change `TransactionItem` type to `DataRow`|
|`WorkflowTestCaseTemplate`|Copy and rename to create tests for your custom workflows|
|`GeneralTestCase`|Add rows to Excel with expected outcomes|
|`Process.xaml`|Ensure business rule logic and input data validation are included|

---

## 🔁 Data Variation Testing

Use `Run with Data Variation` to:

- Test workflows against multiple data sets
    
- See if outcomes match expectations (Success or Exception)
    
- Get detailed test run metrics in `Test Explorer`
    

---

## 🧠 Reflection Questions

- What key information is stored in the **TestData Excel file**?
    
- How does testing **tabular data** differ from testing with **queue items**?
    
- What workflows did you test, and what were the expected vs. actual outcomes?
    
- How can you create a new test case using the **WorkflowTestCaseTemplate**?
    

---
## 🔄 REFramework with Different Data Types (No Queues)
### 🎯 Goal: Configure REFramework to handle custom data types like `String`, `Decimal`, `MailMessage`, etc.

---

## 🧠 Why This?

By default, REFramework uses `QueueItem`.  
You've already adapted it for `DataRow` (tabular data).  
Now you can adapt it to **any collection type** — strings, decimals, emails, etc.

---

## ✅ Checklist Summary (use: **REFramework without Queue Items Checklist**)

---

### 🔧 **1. Main.xaml**

**Change variable types:**

|Variable|From|To|
|---|---|---|
|`TransactionItem`|`QueueItem`|`YourType` (e.g., `String`)|
|`TransactionData`|`DataTable`|Collection of `YourType`|

> ✅ Examples:

- `String[]` or `List<String>` if processing text lines
    
- `MailMessage[]` if processing emails
    
- `List<Decimal>` if handling currency amounts
    

---

### 🔧 **2. GetTransactionData.xaml**

Update **Arguments** and **Workflow Logic**:

|Argument|From|To|
|---|---|---|
|`out_TransactionItem`|`QueueItem`|`YourType`|
|`io_TransactionData`|`DataTable`|`YourCollectionType`|

**Replace `Get Transaction Item`** activity with the appropriate logic to retrieve your data.

✅ Add logic to:

- Load the collection **only once** (e.g. read Excel/Outlook only if `TransactionData Is Nothing`)
    
- Extract one item by index using `TransactionNumber`
    

```vb
out_TransactionItem = io_TransactionData(in_TransactionNumber - 1)
```

---

### 🔧 **3. Process.xaml**

**Update Arguments and Workflow Content**:

|Argument|From|To|
|---|---|---|
|`in_TransactionItem`|`QueueItem`|`YourType`|

🧩 Add processing logic based on the new data type:

- For strings → parse/process text
    
- For emails → open, download, or reply
    
- For numbers → calculations or formatting
    

---

### 🛠 Additional Notes

- The **retry logic** and **log fields** still apply — just make sure to adapt them to the new type.
    
- Use custom identifiers for `TransactionID`, and `TransactionField1` for logging/reporting.
    
- Customize the `SetTransactionStatus.xaml` if needed — the default logic expects `QueueItem`, but you can bypass it or use `Nothing` for `in_TransactionItem`.
    

---

## 🧾 Example: Using `MailMessage`

### Variables:

- `TransactionItem`: `System.Net.Mail.MailMessage`
    
- `TransactionData`: `List<System.Net.Mail.MailMessage>`
    

### In `GetTransactionData.xaml`:

- Use **Get Outlook Mail Messages** to populate `io_TransactionData`
    
- Retrieve 1 email per transaction:
    

```vb
out_TransactionItem = io_TransactionData(in_TransactionNumber - 1)
```

### In `Process.xaml`:

- Read subject, body, attachments, etc.
    

---

## ✅ Summary

|Step|What to Change|
|---|---|
|`TransactionItem`|Change to required single-item type|
|`TransactionData`|Change to collection of that type|
|`GetTransactionData.xaml`|Replace `Get Transaction Item`, set logic for extraction|
|`Process.xaml`|Add business logic to handle the new type|

---
## 🛠 REFramework for **Linear Processes**
### 🎯 Goal: Adapt REFramework to automate processes that only run **once** (no queue, no table, just one sequence)

---

## 🔄 What’s a Linear Process?

- A **linear process** is a **one-time, sequential task**.
    
- You do **not** loop through multiple transactions.
    
- Examples:
    
    - Single-time data entry or validation.
        
    - A one-time report generation.
        
    - Configuration or system setup.
        

---

## ✅ Why use REFramework for linear processes?

- Built-in:
    
    - Logging
        
    - Exception handling
        
    - Clean state management (Init, End)
        
- You can **reuse** framework components while running the process only once.
    

---

## ⚙️ Minimal Changes to REFramework

Only **one workflow** needs to be modified:  
`GetTransactionData.xaml`

---

### 🧩 Change Logic in `GetTransactionData.xaml`

Add an `If` activity:

```vb
If in_TransactionNumber = 1 Then
    out_TransactionItem = New Object()  ' Or actual object needed by your process
Else
    out_TransactionItem = Nothing
End If
```

- ✅ First run → process is triggered.
    
- ❌ Second run → `TransactionItem = Nothing` → leads to `End Process` state.
    

---

## 🧠 Key Notes

|Component|Change Needed?|Notes|
|---|---|---|
|`TransactionItem`|Yes (if needed)|Set to `Object` or the actual data you want to use|
|`TransactionNumber`|No|Will be 1 by default on first run|
|`SetTransactionStatus`|Optional|You can skip Queue updates since it’s not used here|

---

## 🏁 Summary

- **REFramework supports linear processes** with one small tweak.
    
- Just modify `GetTransactionData.xaml` to:
    
    - Run the process if `TransactionNumber = 1`
        
    - End if not.
        
- Everything else — **Init**, **Process**, **End**, **error handling** — stays the same.