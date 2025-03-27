## 📄 **REFramework + Orchestrator Queues — Development Checklist Summary**

### 🎯 Purpose: Quickly develop automation processes with REFramework and Orchestrator queues using a guided checklist.

---

### ✅ **Main Objectives**

- Understand and apply the steps to build a **simple REFramework process using Orchestrator queues**.
    
- Use the **dedicated development checklist** to guide implementation.
    
- Streamline and standardize automation design.
    

---

### 🧰 **Checklist Structure (Key Components)**

#### 1. **Prerequisites**

- Ensure **Robot is connected to Orchestrator**.
    
- **Create Queue** in Orchestrator (with the correct name and Retry settings as per spec).
    

#### 2. **UiPath Studio Configuration**

- Create new project from **REFramework template**.
    
- Customize the **Config.xlsx file**:
    
    - Set queue name, constants, assets, application paths, etc.
        

#### 3. **Applications: Open / Close / Kill**

- Modify `InitAllApplications.xaml` to **open required apps**.
    
- Edit `CloseAllApplications.xaml` to **gracefully close apps**.
    
- Use `KillAllProcesses.xaml` if needed to **force-close** apps.
    

#### 4. **Business Logic**

- Edit `GetTransactionData.xaml` to **retrieve queue items**.
    
- Customize `Process.xaml` to **execute business logic** per transaction.
    

---

### 💡 **Best Practices**

- **Always use the checklist** during development to avoid missing steps.
    
- For **Windows Compatibility + C# projects**:
    
    1. Start with **Windows - Legacy + C#** project.
        
    2. Then **convert to Windows compatibility** manually.
        

---

### 📌 **Additional Notes**

- Checklist doesn't cover _all_ REFramework use cases—it's focused on **basic queue-based scenarios**.
    
- Detailed documentation is available inside the **REFramework template** (PDF included).
    

---
## 🛠 **REFramework Project Configuration — Summary**

### 🎯 Purpose: Define all process-specific parameters in the **Config.xlsx** file (Settings, Constants, Assets sheets) for queue-based REFramework automation.

---

### ✅ **Main Objectives**

- Fill in the **Settings**, **Constants**, and **Assets** sheets of the configuration file.
    
- Set up your **Orchestrator Queue**, **Assets**, and define **business logic parameters**.
    
- Align with the **REFramework with Queue Items Checklist**.
    

---

### 🧩 **Config File Sheets — Purpose & Usage**

#### 1. **Settings Sheet**

Used for:

- **Queue name** → `OrchestratorQueueName`
    
- **Credential name** → e.g., `UiDemo_CredentialName`
    
- **Other parameters** → e.g., `OrchestratorQueueFolder`, `ManualTransactionThreshold`
    

💡 Example:

```plaintext
Name: OrchestratorQueueName
Value: UiDemo
```

#### 2. **Assets Sheet**

Used for defining **Orchestrator Assets**, typically:

- Text assets → e.g., `UiDemo Application Path`
    
- Credential assets → defined in Orchestrator, referenced here
    

💡 Best practice: Use **Assets** when values vary per robot (e.g., file paths).

#### 3. **Constants Sheet**

Used for static, global process-wide parameters:

- `MaxConsecutiveSystemExceptions` → e.g., 3
    
- `RetryNumberGetTransactionItem` → e.g., 2
    
- `RetryNumberSetTransactionStatus` → e.g., 2
    
- `ShouldMarkJobAsFaulted` → TRUE → marks job as faulted if init fails or max system exceptions reached
    
- `MaxRetryNumber` → set to `0` if using Orchestrator’s retry mechanism
    

---

### 🧱 **Process Setup Steps (Recap)**

1. **Create project** from REFramework template (naming format: Department_ProcessName_REF).
    
2. Create **UiDemo subfolder** in the project and copy prebuilt workflows:
    
    - AddTransaction.xaml
        
    - Open.xaml
        
    - Close.xaml
        
    - ForceClose.xaml
        
3. **Create Orchestrator folder**: `REFUiDemo`
    
4. Create **Queue**: `UiDemo` (auto-retry ON, MaxRetry = 1)
    
5. Upload **CSV test data** using **Upload Items**
    
6. Update **Settings** in Config.xlsx:
    
    - `OrchestratorQueueName`, `OrchestratorQueueFolder`, `UiDemo Credential Name`, etc.
        
7. Define **Assets** in Orchestrator (type: Text / Credential)
    
    - E.g., `UiDemo Application Path`, `UiDemo_CredentialName`
        
8. Update **Assets** sheet with corresponding entries
    
9. Configure **Constants** sheet with error-handling and retry logic
    

---

### 🚨 Key Warnings & Best Practices

- Missing assets declared in the Config file will cause the process to **fail during Init**.
    
- Set `ShouldMarkJobAsFaulted = TRUE` to mark job as **failed on Init errors**.
    
- If using **Orchestrator retries**, set `MaxRetryNumber = 0` in Constants.
    
- Use **text assets** for values that may change per robot (like file paths).
    
- Use **Credential assets** for secure logins; define them in Orchestrator and reference via `Settings`.
    

---

### 📌 Frequently Asked Questions

|What to configure?|Where?|
|---|---|
|Queue Name|Settings sheet|
|Text Asset Names|Assets sheet|
|Credential Asset Names|Settings sheet|
|Max Number of Retries > 0|In Orchestrator Queue settings|
|Retry values for activities|Constants sheet (`RetryNumber*`)|

---
## 🖥️ **Applications: Open / Close / Kill — REFramework Configuration**

### 🎯 Purpose: Configure REFramework to handle external applications (e.g. **UiDemo**) by **opening**, **closing**, or **killing** them appropriately.

---

### ✅ **Main Objectives**

- Modify **InitAllApplications**, **CloseAllApplications**, and **KillAllProcesses** workflows to handle app lifecycle.
    
- Use arguments and Config values correctly to make workflows dynamic.
    
- Align changes with the **"Applications Used: Open/Close/Kill"** section of the REFramework with Queues checklist.
    

---

### 🧱 **Workflow Responsibilities**

|Workflow|Purpose|Invoked In|Triggered When|
|---|---|---|---|
|`UiDemo_Open.xaml`|Opens UiDemo & performs login|`InitAllApplications.xaml`|During Initialization|
|`UiDemo_Close.xaml`|Gracefully closes UiDemo|`CloseAllApplications.xaml`|End of Process / System Exception|
|`UiDemo_ForceClose.xaml`|Force-kills UiDemo process|`KillAllProcesses.xaml`|If `Close` fails in Init, Process, End|

---

### 🧩 **Steps to Configure Each Workflow**

#### 🟢 **InitAllApplications.xaml**

1. Invoke `UiDemo_Open.xaml`.
    
2. Import arguments:
    
    - `in_UiDemoAppPath` ← `in_Config("UiDemo_Application Path").ToString`
        
    - `in_CredentialName` ← `in_Config("UiDemo_CredentialName").ToString`
        

#### 🔴 **CloseAllApplications.xaml**

1. Invoke `UiDemo_Close.xaml`.
    
2. No arguments needed.
    
3. Save.
    

#### ⚫ **KillAllProcesses.xaml**

1. Invoke `UiDemo_ForceClose.xaml`.
    
2. No arguments needed.
    
3. Save.
    

---

### 📌 **Best Practices**

- Place **each app-specific logic in separate workflows** (Open, Close, Kill).
    
- Always use **Config file parameters** for dynamic paths and credentials.
    
- Ensure workflows are invoked in the **correct framework states**:
    
    - Init → `InitAllApplications`
        
    - Process / End → `CloseAllApplications`, `KillAllProcesses`
        

---

### 🔄 **Workflow Invocation Logic in States**

|REFramework State|Workflow Called|Purpose|
|---|---|---|
|Initialization|`InitAllApplications.xaml`|Open & login to UiDemo|
|End Process|`CloseAllApplications.xaml`|Cleanly close UiDemo|
|Any failure fallback|`KillAllProcesses.xaml`|Force kill UiDemo if close fails|

---
## 🔁 **REFramework — Get Transaction Data & Process Transaction**

### ⏱ Duration: ~20 min

### 🎯 Purpose: Configure how the process retrieves, validates, and processes **transaction items** from an **Orchestrator queue**, including **business rule handling** and retry logic.

---

### ✅ **Main Objectives**

- Understand and use **GetTransactionData.xaml** to retrieve queue items.
    
- Implement **business logic and rule checks** inside **Process.xaml**.
    
- Apply **best practices** for logging, error handling, and modularity.
    

---

## 📤 **GetTransactionData.xaml**

### 🔧 Default Behavior:

- Uses **`Get Transaction Item`** activity (inside a Try-Catch and RetryScope) to pull data from the Orchestrator queue.
    
- Queue name and retry values are pulled from the **Config file**.
    

### 🧠 Customization:

- No structural changes needed.
    
- Set custom **Transaction metadata** (log fields):
    

#### Example Fields:

|Field|Value|
|---|---|
|`TransactionID`|`Now.ToString` (timestamp-based unique identifier)|
|`TransactionField1`|Concatenation of `CashIn`, `OnUsCheck`, and `NotOnUsCheck` fields|
|`TransactionField2`|Optional additional context (can be left blank or used for reporting)|

> Extract queue data using:

```vb
CDec(in_TransactionItem.SpecificContent("CashIn"))
```

---

## ⚙️ **Process.xaml (Process Transaction State)**

### 🧩 Workflow Used:

- **Invoke:** `UiDemo_AddTransaction.xaml`
    
- **Inputs Required:** `CashIn`, `OnUsCheck`, `NotOnUsCheck` (as `Decimal`)
    
- **Output:** `TransactionNumber`
    

---

### 🧪 **Business Rule Validation:**

- Condition: `CashIn + OnUsCheck + NotOnUsCheck > ManualTransactionThreshold`
    
- Threshold value comes from `Config("ManualTransactionThreshold").ToString` → Converted to `Decimal`
    

#### ⚠️ Exception Trigger:

```vb
Throw New BusinessRuleException("Transaction sum exceeds the threshold.")
```

When thrown:

- Status = **Failed** in Orchestrator
    
- Error type = **Business**
    
- Robot skips to **next transaction**
    

---

### 🛠 Activity Summary in Process.xaml

|Task|Activity Type|Notes|
|---|---|---|
|Read queue values|`Assign`|Cast Object to Decimal using `CDec()`|
|Validate sum|`If`|If sum > threshold, throw exception|
|Throw exception|`Throw`|`BusinessRuleException` with meaningful message|
|Process valid transaction|`Invoke Workflow`|Call `UiDemo_AddTransaction.xaml` and pass variables|
|Log meaningful info|`Log Message`|Add annotations and proper naming for auditability|

---

## 🔁 **Retry Configuration**

|Type|Controlled By|Where to Set|
|---|---|---|
|Get Transaction Item|`RetryScope` + Config value|`Constants` sheet → `RetryNumberGetTransactionItem`|
|Set Transaction Status|`RetryScope` + Config value|`Constants` sheet → `RetryNumberSetTransactionStatus`|

---

### 🧠 Best Practices Followed

- Group related activities into **sequences** (e.g., `Input data validation`)
    
- Use **meaningful names** and **annotations** on all activities
    
- **Convert types properly** (`Object` to `Decimal`) before processing
    
- Log **Transaction ID** and field values for visibility
    
- Separate **Business Rules** from application logic
    

---

### 🔄 **Exception Handling Fix (FYI)**

> Previously: Process killed prematurely → transaction marked **Successful**  
> Fixed by:

- Adding **Try-Catch wrapped invocation** of `SetTransactionStatus.xaml` in:
    
    - `Try` block after `Process.xaml` for success
        
    - `Catch` blocks for System and Business exceptions
        

---

### 📌 Summary Table

|Workflow|Purpose|Custom Logic|
|---|---|---|
|`GetTransactionData.xaml`|Retrieve queue items from Orchestrator|Set log fields, no major edits|
|`Process.xaml`|Validate and process data into UiDemo|Business Rule check, invoke `UiDemo_AddTransaction`|
|`UiDemo_AddTransaction`|Types values & gets transaction number|Pre-built custom workflow|

---
## ✅ **REFramework Testing with UiPath Test Suite**

### ⏱ Duration: ~15 min

### 🎯 Purpose: Learn how to **unit test REFramework components** using **UiPath Test Suite** to ensure stability before production.

---

## 🧪 **What is UiPath Test Suite?**

- A complete **RPA + Application testing** solution integrated into UiPath.
    
- Used to **test workflows early**, automate regression testing, and validate process behavior.
    
- Includes:
    
    - **Test Manager**
        
    - **Studio**
        
    - **Orchestrator**
        
    - **Test Robots**
        

---

## 📂 **Test Folder Structure**

- Project contains a `Tests` folder with prebuilt test cases.
    
- Each test case verifies individual components/workflows.
    
- Testing is **data-driven** using a `Tests.xlsx` file.
    

---

## 🧩 **Key Test Cases and What They Do**

|Test Case Name|Verifies / Purpose|
|---|---|
|`GeneralTestCase.xaml`|Generic test runner using `Tests.xlsx`. Invokes workflows & compares expected output.|
|`InitAllSettingsTestCase.xaml`|Checks if `Config.xlsx` is correctly read and config dictionary is built (e.g., 18 keys).|
|`InitAllApplicationsTestCase.xaml`|Tests if UiDemo opens and login works. Uses `Verify Control Attribute`.|
|`GetTransactionDataTestCase.xaml`|Validates queue is accessible, item retrieved is not null, and progress can be updated.|
|`ProcessTestCase.xaml`|Processes one transaction item and checks if a transaction number is generated.|
|`MainTestCase.xaml`|End-to-end scenario validation, including output verification.|
|`WorkflowTestCaseTemplate.xaml`|Template to test any workflow (Given → When → Then pattern).|
|`UiDemo_AddTransactionTestCase.xaml`|Data-driven variation test for AddTransaction workflow. Tests transaction number output.|
|`UiDemo_OpenTestCase.xaml`|Opens UiDemo app, verifies it launches and logs in (no transaction processing).|

---

## 📌 **Test Structure: Given → When → Then**

|Section|Purpose|
|---|---|
|**Given**|Set up context (load Config, initialize)|
|**When**|Execute main action (e.g., open app)|
|**Then**|Validate result and cleanup|

---

## 🔁 **Test Execution & Behavior**

- Run with: **"Run file with data variations"** for data-driven tests.
    
- Validates:
    
    - Settings load
        
    - Application state
        
    - Transaction retrieval
        
    - Business rules
        
    - Exception handling
        
- Uses **`UiPath.Testing` Activities** (e.g., `Verify Control Attribute`).
    

---

## 🛠 **Best Practices**

- Add test cases for **each critical workflow**.
    
- Use **descriptive names** and **annotations**.
    
- Implement cleanup in `Then` (e.g., close apps).
    
- Automate **test execution** via Orchestrator/Test Manager for CI/CD pipelines.
    

---

## 📥 **Resources**

- 📁 Download: `REFramework_With_Testing.zip`
    
- 📄 Docs: `REFramework Documentation-EN.pdf`
    

---

## 🧠 Summary

UiPath Test Suite enables **robust, reusable tests** for REFramework processes. Use the provided templates to build test cases for:

- Settings
    
- Application launch
    
- Queue access
    
- Transaction processing
    
- Output validation
    

> 🔁 Automate test runs to detect issues **before going to production**.

---

Let me know if you’d like a **custom test case template** or help writing your **own unit tests** using the `WorkflowTestCaseTemplate`.