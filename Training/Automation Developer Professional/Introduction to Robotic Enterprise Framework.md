## 🔁 **Types of Processes in UiPath (From a Transaction Perspective)**

|Type|Description|Example|
|---|---|---|
|**Linear**|One-time execution per run. No loops.|One email triggers data collection and reply.|
|**Iterative**|Loops through a dataset, but **all items processed in one execution**.|Loop over multiple emails in a folder.|
|**Transactional**|Each unit of data (transaction) is processed **independently**, supports retries & isolation.|Process each invoice/email/person independently.|

### 🧠 Evolution (Maturity Stages)

- Start simple with **Linear**
    
- Move to **Iterative**
    
- Mature to **Transactional** for scalability and error handling
    

---

## 🔹 **What is a Transaction?**

- **Definition**: Atomic unit of work/data processed independently (e.g., one email, one invoice, one row in Excel).
    
- **Properties**:
    
    - No data shared between transactions
        
    - Processed individually
        
    - Isolated error handling and retry possible
        

### 🔍 **Examples of Transactions**

|Scenario|Transaction Unit|
|---|---|
|Process invoices from folder|Each invoice file|
|Send personalized emails|Each row in spreadsheet|
|Scrape apartments info from a site|Each apartment detail page|

---

## ⚙️ **REFramework**

- Supports all process types, especially **Transactional**
    
- Default config designed for unattended, transactional, queue-driven processes
    

---

## 🔄 **Dispatcher/Performer Model**

### 📤 **Dispatcher**

- Reads raw data (Excel, email, DB, etc.)
    
- Pushes **queue items** to **Orchestrator**
    
- One item per transaction (structured with required data)
    
- ❗ Focus: Data acquisition and structuring
    

### 📥 **Performer**

- Pulls queue items from Orchestrator
    
- Processes **one item at a time**
    
- Uses built-in **retry & error handling**
    
- ❗ Focus: Business logic execution
    

---

### 🧪 **Example: Email Campaign**

- **Dispatcher**:
    
    - Reads from Excel: Name, Email
        
    - Pushes rows to Orchestrator queue
        
- **Performer**:
    
    - Pulls one item
        
    - Builds personalized message from template
        
    - Sends email
        

---

## ✅ **Benefits of Dispatcher/Performer + REFramework**

- ✨ **Separation of Concerns**: Cleanly separates input preparation (Dispatcher) from logic (Performer)
    
- 📊 **Scalability**: Multiple Performers can consume the same queue in parallel
    
- 🛡️ **Error Management**: Retry + Exception handling at item level
    
- 🔁 **Reusability**: Components can be reused across projects
    
- 🔗 **Orchestrator-Ready**: Built-in queue and config integration
    
- ⚡ **Performance**: Asynchronous, non-blocking architecture
    

---

The **REFramework (Robotic Enterprise Framework)** is a UiPath Studio template designed to help you develop production-ready automation projects. It is particularly useful for scalable automation processes. Here’s an overview of what you’ll learn:

### Key Mechanisms in the REFramework Template:

1. **State Machine Architecture**: REFramework utilizes state machines, which are the core design principle. These state machines define different stages of the process such as initialization, data retrieval, processing, and completion.
    
2. **Pre-built States**: REFramework has pre-built states that handle the major parts of an automation project, such as:
    
    - **Initialization**: Initializes applications and prepares for data processing.
        
    - **Data Retrieval**: Handles data input, which could come from various sources (queues, files, databases).
        
    - **Data Processing**: The actual processing of the data.
        
    - **Transaction Completion**: Handles the final steps like logging and finishing the process.
        
3. **Transitions**: Transitions between these states are managed, providing a clear structure for handling automation tasks.
    

### Benefits of Using the REFramework Template:

1. **Built-in Exception Handling**:
    
    - **Problem**: The robot can stop if an unexpected error occurs.
        
    - **Solution**: REFramework has a robust exception handling mechanism to catch errors and allows the process to continue running, improving stability.
        
2. **Automatic Recovery from Application Failures**:
    
    - **Problem**: If an application crashes, the robot stops.
        
    - **Solution**: REFramework has a retry mechanism that restarts the application and attempts the transaction again from the initialization state.
        
3. **Handling Invalid Data**:
    
    - **Problem**: Invalid input data can cause the automation to stop.
        
    - **Solution**: REFramework uses **BusinessRuleException** to mark transactions with invalid data as ‘failed’ and continues with the next valid transaction, ensuring smooth processing.
        
4. **Configuration Management**:
    
    - **Problem**: Hardcoded values (e.g., file paths, credentials) are difficult to manage and affect security.
        
    - **Solution**: REFramework centralizes configuration using a configuration file and Orchestrator assets, making it easier to maintain and secure.
        
5. **Enhanced Troubleshooting**:
    
    - **Problem**: Errors in production can be difficult to troubleshoot.
        
    - **Solution**: REFramework logs errors and automatically takes screenshots when an unexpected issue occurs, helping developers quickly diagnose problems.
        
6. **Better Project Organization**:
    
    - **Problem**: Large projects can become hard to maintain.
        
    - **Solution**: REFramework’s use of state machines and modular workflows for each stage of the process allows for better project organization and maintenance.
        

### Two Ways to Implement REFramework:

1. **With Queues**: This involves using Orchestrator Queues to manage transaction data. The transactions are processed from the queue and then entered into the application (e.g., UiDemo).
    
2. **Without Queues**: Instead of using queues, other types of transaction items such as rows from an Excel file, emails, or file paths can be used. This is suitable for simpler scenarios where queues aren’t necessary.
    

### Key Concepts in the REFramework Template:

1. **The Main Workflow**:
    
    - **State Machine Layout**: The main workflow in the REFramework uses a state machine structure. It consists of four main states:
        
        - **Initialization**: Initializes the application and reads the configuration file. In our case, this is where the UI Demo application is launched and logged in.
            
        - **Get Transaction Data**: Retrieves transaction data, typically from an Orchestrator Queue, for processing. It gets the transaction items, such as Cash In, On Us Check, and Not On Us Check from the data file.
            
        - **Process Transaction**: This is where the automation enters the retrieved transaction data into the UiDemo application and clicks "Accept" to process it.
            
        - **End Process**: Marks the end of the process, stopping further execution once all transactions have been processed or if an error occurs.
            
2. **States and Their Roles**:
    
    - **Initialization State**: Responsible for preparing the automation environment. If an error occurs in this state, the process terminates and goes to the **End Process** state.
        
    - **Get Transaction Data State**: Retrieves transaction data one at a time. If data is available, it proceeds to the **Process Transaction** state; if not, it moves to **End Process**.
        
    - **Process Transaction State**: Executes the business logic, processes the data, and updates the transaction status (success, failure, or retry). There are three possible outcomes here:
        
        1. **Success**: The data is processed successfully, and the system loops back to retrieve the next transaction.
            
        2. **Business Rule Exception**: The data violates a business rule (e.g., transaction > $10,000 requires manager approval). The item is marked as failed, and the process moves to the next transaction.
            
        3. **System Exception**: An unexpected error occurs, and the process retries by returning to the **Initialization** state to restart the application.
            
3. **Error Handling**:
    
    - **System Exceptions**: If an exception is encountered, the process closes all applications and retries by restarting from the **Initialization** state.
        
    - **Business Rule Exceptions**: These don’t trigger a retry, but they mark the transaction as failed and require manual intervention.
        
    - **Logging and Screenshot**: The REFramework includes logging mechanisms to help troubleshoot and track the process. Screenshots are taken in case of unexpected errors.
        
4. **Queue Items**:
    
    - In this scenario, transaction data comes from an Orchestrator Queue, where each item contains the transaction details (e.g., Cash In, On Us Check). After each successful transaction, the queue item is marked as "Successful."
        
    - If a **System Exception** occurs, the item status is changed to "Retried" and re-added to the queue. If only one retry is allowed, the status will eventually change to **Failed** or **Successful** depending on the outcome.
        
5. **Business Process Example**:
    
    - The example used in the demo involves posting financial transactions to UiDemo. The data is provided in an Excel file, with each row representing a transaction. A business rule is that transactions over $10,000 require manager approval.
        
    - If the system fails three times consecutively, the automation stops.
        

### Key Takeaways:

- **REFramework** is an ideal starting point for complex automation projects because it incorporates best practices like exception handling, retry mechanisms, and logging.
    
- The **Main.xaml** workflow in REFramework is based on a **state machine** that guides the process through stages of initialization, transaction data retrieval, processing, and completion.
    
- The template ensures that the automation is robust and production-ready by handling system and business rule exceptions, retry mechanisms, and transaction management.
    

---

## 🔄 **Initialization State Overview**

The **Initialization state** is the first step in the REFramework process, and it is **crucial** for setting up the environment correctly before any data is processed.

### ✅ **Main Responsibilities**:

- Read and store configuration values from `Config.xlsx`.
    
- Force close (Kill) any previously running instances of the required applications.
    
- Initialize and log into applications (e.g., UiDemo).
    
- Set global logging parameters and custom fields.
    
- Handle exceptions during the setup phase.
    
- Check for maximum allowed consecutive system exceptions.
    

---

## ⚙️ **Key Workflows in Initialization State**

### 1. **InitAllSettings.xaml**

- Reads the configuration file `Config.xlsx` (from `Data/` folder).
    
- Returns a `Dictionary<String, Object>` called `Config` used throughout the process.
    
- Invoked only if `Config` is `Nothing`.
    

#### 🧠 **Arguments:**

- `in_ConfigFile`: Path to Config file.
    
- `in_ConfigSheets`: Sheets to be read (Settings, Constants, Assets).
    
- `out_Config`: Dictionary passed back with all config data.
    

---

### 2. **KillAllProcesses.xaml**

- Forcefully closes any lingering instances of the applications being automated.
    
- Used as a **failsafe** to ensure clean startup.
    
- Especially important if an app may crash or be left open in an inconsistent state.
    

---

### 3. **InitAllApplications.xaml**

- Starts and logs into all required applications (e.g., UiDemo).
    
- Logic for each app is usually split into separate invoked workflows for modularity.
    
    - e.g., `UiDemo_Open.xaml` for launching and logging in.
        

---

### 🧨 **Exception Handling**

- Uses a **Try Catch** block throughout the state.
    
- If an exception occurs:
    
    - `SystemException` is set.
        
    - A **Fatal log** is created.
        
    - The process transitions to the **End Process** state.
        

---

## 📊 **The Configuration File (Config.xlsx)**

Located in the **Data** folder, this file is used to avoid hardcoding values. It contains three sheets:

---

### 1. **Settings Sheet**

- For **business-related configuration**.
    
- Examples:
    
    - `OrchestratorQueueName`
        
    - `UiDemo_Credentials`
        
    - URLs, file paths, thresholds, etc.
        

#### 💡 Columns:

- `Name`: The key in the Config dictionary.
    
- `Value`: The corresponding value (can be overridden by runtime arguments).
    
- `Description`: For developers (not used by robot).
    

---

### 2. **Constants Sheet**

- For **technical and control parameters**.
    
- Examples:
    
    - `MaxRetryNumber`: Controls retries if queues are **not used**.
        
    - `MaxConsecutiveSystemExceptions`: Stops job after N system exceptions.
        
    - `RetryNumberGetTransactionItem` & `RetryNumberSetTransactionStatus`: Custom retry logic.
        
    - `ShouldMarkJobAsFaulted`: When `TRUE`, ends job if system failures exceed limit.
        

---

### 3. **Assets Sheet**

- For **Orchestrator assets** (excluding credentials).
    
- Examples:
    
    - File paths, URLs, timeouts.
        

#### 🧠 Columns:

- `Name`: Key in Config dictionary.
    
- `Asset`: Asset name in Orchestrator.
    
- `OrchestratorAssetFolder`: Optional – specifies folder location of asset.
    

❗ **Credentials** (e.g., for UiDemo login) should **not** be stored in Assets sheet — they are defined in **Settings**, and handled securely with `Get Credential`.

---

## 🔄 **System Exception Counter Logic**

- Variable: `ConsecutiveSystemExceptions`
    
- Updated via `SetTransactionStatus.xaml`
    
- If **3 system exceptions** occur consecutively (default in Constants), the job stops.
    
- If a **successful transaction** happens, the counter is reset.
    

---

## 🧠 Key Takeaways

- **Initialization** is the foundation: If it fails, the job doesn’t run.
    
- **KillAllProcesses** ensures a clean slate before starting.
    
- **Config.xlsx** allows projects to be easily maintained, reused, and migrated across environments.
    
- **Exception handling** in Initialization is fully built-in — you only need to customize what’s initialized.
    
- Avoid **hardcoding** — always use Config where possible.
    
- Configurable parameters like retries, thresholds, and log options improve process robustness.
    

---
## 📥 **What is the Get Transaction Data State?**

This state is responsible for **retrieving one transaction item at a time** to be processed by the robot. It serves as the **bridge** between the Initialization and Process Transaction states.

---

### ⚙️ **Key Responsibilities**

1. **Check for Stop Request** from Orchestrator.
    
2. **Retrieve the next transaction item** (e.g., a Queue Item).
    
3. **Prepare and assign logging fields** for visibility and traceability.
    
4. **Decide where to go next**:
    
    - If an item is retrieved: → go to **Process Transaction**.
        
    - If no items remain: → go to **End Process**.
        

---

## 🔄 **Control Flow Logic**

### 1. **Stop Request Check**

- The very first action is using **`Should Stop`**.
    
- If a stop is requested from Orchestrator (manually or from a schedule), the process exits **before pulling a new item**, and transitions to **End Process**.
    
- This allows for **graceful stopping** without leaving items "In Progress."
    

---

### 2. **GetTransactionData.xaml Workflow**

#### 🧠 **Arguments**:

- `in_TransactionNumber` (Int32): Tracks how many items have been processed.
    
- `in_Config` (Dictionary): The configuration dictionary.
    
- `out_TransactionItem` (default type: QueueItem): The item to process.
    
- `out_TransactionField1`, `out_TransactionField2`, `out_TransactionID`: Used for **custom logging**.
    
- `in_TransactionData` (optional): Used when working with non-queue sources (e.g., Excel, Email).
    

---

## 🔄 **Retry Mechanism**

- The **Get Transaction Item** activity is wrapped in both a **Retry Scope** and **Try Catch**.
    
- Retry count is controlled by the **`RetryNumberGetTransactionItem`** constant in the `Config.xlsx` file.
    
- If a failure occurs (like a temporary Orchestrator outage), the process retries safely before throwing an error.
    

---

## 🧾 **Logging Fields**

To enhance traceability and business insights, REFramework provides:

- `out_TransactionID`: Unique ID for the transaction (default is system timestamp).
    
- `out_TransactionField1` and `out_TransactionField2`: Custom info from the transaction, e.g., amount, date, email, etc.
    

📌 Example:  
For UiDemo, `TransactionField1` is set as a concatenation of Cash In, On Us Check, and Not On Us Check.

---

## 🧨 **End Condition**

- When `TransactionItem = Nothing`, the robot transitions to **End Process**.
    
- For queues, this happens automatically when all new items are processed.
    
- For non-queue inputs (like Excel), you'll manually set `TransactionItem = Nothing` when reaching the last row or email.
    

---

## 💬 **What is a Transaction?**

- A **transaction** is the **smallest independent unit of work** in a business process.
    
- Example: One row from a data table, one email, one file, one queue item.
    
- Once processed, it's marked as successful or failed, and is not reused.
    

---

## 📌 Main Takeaways

- `Get Transaction Data` is where your robot **fetches what to process next**.
    
- It supports both **Queue-based** and **non-Queue-based** automations.
    
- Includes a **Stop mechanism** for graceful exit without interrupting transactions.
    
- **Exception handling and retry logic** ensure robustness in data retrieval.
    
- Custom **logging fields** allow for better monitoring and reporting.
    

---
## ⚙️ **Process Transaction State**

This is the **core state** where the robot executes the actual business logic using the transaction data retrieved earlier.

---

### 🔁 **Structure**

#### ✅ Try Block:

1. **Invoke Process.xaml**
    
    - Inputs: `in_TransactionItem`, `in_Config`
        
    - Contains the business logic (e.g., typing data into UiDemo and clicking Accept)
        
2. **If Successful**
    
    - Status is set to `Success` using **SetTransactionStatus.xaml**
        

#### ❌ Catch Blocks:

1. **Business Rule Exception**
    
    - Triggered manually via `Throw` activity
        
    - Transaction is marked **Failed - Business**
        
    - REFramework transitions to **Get Transaction Data** state
        
2. **System Exception**
    
    - Triggered by unhandled errors (e.g., app crash)
        
    - Transaction is marked **Failed - Application**
        
    - Retry logic is applied
        
    - All apps are closed, and the framework loops back to **Initialization**
        

---

## 📦 **SetTransactionStatus.xaml**

Handles **setting the status** of the processed transaction based on the outcome.

### Three Paths:

1. **Success**
    
    - Marks queue item as `Successful`
        
    - Logs details
        
    - Resets: `RetryNumber`, `ConsecutiveSystemExceptions`
        
    - Increments: `TransactionNumber`
        
2. **Business Exception**
    
    - Marks item as `Failed - Business`
        
    - Logs details
        
    - Resets `RetryNumber`, `ConsecutiveSystemExceptions`
        
    - Increments `TransactionNumber`
        
3. **System Exception**
    
    - Marks item as `Failed - Application`
        
    - Logs details + captures screenshot path
        
    - **Increments** `ConsecutiveSystemExceptions`
        
    - Executes **RetryCurrentTransaction.xaml**
        

---

## 🔁 **RetryCurrentTransaction.xaml**

Manages retry behavior depending on transaction type.

### For **Queue Items**:

- Orchestrator handles retries natively
    
- Robot proceeds to next transaction
    

### For **non-Queue Items** (e.g., Excel rows):

- Controlled by `MaxRetryNumber` from `Config.xlsx`
    
- If `RetryNumber < MaxRetryNumber`, retry the same item
    
- Otherwise, log error, reset retry count, and move on
    

---

## 🔧 **Important Arguments**

- `in_TransactionItem`, `in_Config`
    
- `in_BusinessRuleException`, `in_SystemException`
    
- `io_TransactionNumber`, `io_RetryNumber`, `io_ConsecutiveSystemExceptions`
    
- `in_TransactionID`: used for logging
    

---

## ✅ **Outcome Transitions**

- **Success** → Get next transaction
    
- **Business Rule Exception** → Get next transaction
    
- **System Exception** → Initialization (restart applications)
    

---

## 🛑 **End Process State**

The **final state** of the REFramework. It handles proper closure of the process and applications.

---

### 🔁 Try Block

- Invokes **CloseAllApplications.xaml**
    
    - Used for graceful shutdown
        
- Logs a closing message
    

### ❌ Catch Block

- If `CloseAllApplications` fails, invokes **KillAllProcesses.xaml**
    
    - Force-closes remaining apps
        

---

### 💥 Faulted Job Handling

- Controlled by `ShouldMarkJobAsFaulted` (from Config.xlsx)
    
    - If `True`, the job is marked as **Failed**
        
    - Useful when stopping due to too many system exceptions
        

---

## 🧠 Final Recap

### 🔂 **Process Transaction Outcomes**

|Outcome|Trigger|Next State|
|---|---|---|
|**Success**|No error in Process.xaml|Get Transaction Data|
|**Business Rule**|Thrown `BusinessRuleException`|Get Transaction Data|
|**System**|Unexpected error / crash|Initialization|

---

### 🔄 **Retry Summary**

|Item Type|Retry Logic Controlled By|
|---|---|
|**Queue Item**|Orchestrator (built-in)|
|**Non-Queue Item**|`MaxRetryNumber` in Config|

---

### 🧩 **Workflows Involved**

- `Process.xaml`: business logic
    
- `SetTransactionStatus.xaml`: sets status + logs
    
- `RetryCurrentTransaction.xaml`: custom retry logic
    
- `CloseAllApplications.xaml`: graceful shutdown
    
- `KillAllProcesses.xaml`: force close (fallback)
    
---

## 🧠 **Purpose of Logging in REFramework**

The REFramework is designed to provide **comprehensive, structured logging** that supports:

- **Real-time debugging**
    
- **Post-execution diagnostics**
    
- **Audit trails and insights** using platforms like **UiPath Insights**, **Elasticsearch**, or **Kibana**
    

---

## 🧾 **Log Message Levels**

REFramework uses different log levels strategically:

- **Trace** – for deep-level details (e.g., internal variable values)
    
- **Info** – for standard execution messages (e.g., starting a transaction)
    
- **Warning** – for recoverable issues (e.g., missing data, retry warnings)
    
- **Error** – for serious problems (e.g., application crashes)
    
- **Fatal** – for critical failures that stop the automation (e.g., config not found)
    

---

## 🧩 **Custom Log Fields**

Custom fields are attached to log messages using **Add Log Fields** activity. These help enrich logs with transaction-specific metadata.

### 🔧 Custom Fields Defined in REFramework:

|Log Field|Where It’s Set|Purpose|
|---|---|---|
|`BusinessProcessName`|Init state (`Config.xlsx`)|Identifies the process|
|`TransactionNumber`|SetTransactionStatus.xaml|Tracks current transaction|
|`TransactionID`|GetTransactionData.xaml|Timestamp or unique ID|
|`TransactionField1`|GetTransactionData.xaml|Transaction-specific info (e.g., combined cash values)|
|`TransactionField2`|GetTransactionData.xaml (optional)|Optional – not used in demo|

✅ These fields are:

- Added before logging
    
- Removed **after** the relevant message is logged using **Remove Log Fields**
    

---

## 🖥️ **Execution Notes**

- Running in **Debug mode** lets you follow logs in the Output panel.
    
- Each message appears in color-coded format based on log level.
    
- Double-clicking a log shows **all attached fields**.
    

---

## 🧪 **Input Method Optimization**

By default, REFramework demos use **Hardware Events**, which causes the robot to control the keyboard/mouse (can interrupt user workflow).

**Recommended setting**:

- Switch to **Simulate** in `Use Application/Browser` activities:
    
    - Smoother
        
    - Faster
        
    - Works in background
        
    - More reliable in unattended mode
        
- Turn off **Click Before Typing** when using Simulate (not needed)
    

Also recommended:

- Reduce **UI timeout** in `Project Settings > UI Automation Modern > Timeout` (e.g., to 5 seconds) to accelerate error detection.
    

---

## 📊 **Log Behavior Per Transaction Outcome**

|Outcome|Log Behavior|
|---|---|
|**Success**|Adds Transaction Number, ID, Field1/Field2, Status → Logs "Transaction Successful"|
|**Business Exception**|Logs business error message + same fields as above|
|**System Exception**|Logs application error, exception details, path of screenshot → Invokes retry logic|

---

## 🗂️ **Helpful Integration**

Logs can be exported or integrated into:

- **UiPath Insights** (analytics dashboard)
    
- **Kibana / Elasticsearch** (for log visualization)
    
- **Custom monitoring tools**
    

These integrations allow you to create **custom dashboards**, alerts, and **reporting for business or tech stakeholders**.

---

## ✅ **Key Takeaways**

- **REFramework logging** is powerful and customizable, supporting transparency and maintainability.
    
- **Add Log Fields** only where needed, and always **remove** them afterward.
    
- Use **Simulate Input** to optimize execution.
    
- **Log levels** and messages follow a clear structure across all REFramework states.
    
- All logging is designed to support debugging, retries, and exception tracing.
    

---
## ⚠️ **Why Exception Handling Matters**

REFramework is designed to **keep automations running** reliably in production—even when errors occur. It ensures that:

- Transactions are processed correctly or flagged appropriately.
    
- The automation continues or stops based on rules.
    
- All issues are logged and visible to developers and operations.
    

---

## 🚨 **Types of Exceptions in REFramework**

### 1. **System Exceptions**

Triggered by:

- Unexpected errors (e.g., application crash, selector not found, network errors)
    
- Occur **during execution** without being explicitly coded
    

**Key Behavior:**

- Retry logic is activated (handled by Orchestrator or Config, depending on transaction type)
    
- Application is restarted (Init state is re-invoked)
    
- A screenshot is taken and logged
    
- `ConsecutiveSystemExceptions` counter increases
    

If this counter reaches the limit defined in `Config.xlsx` (e.g., 3), **the job stops**.

---

### 2. **Business Rule Exceptions**

Triggered when:

- Data is **invalid for business logic**
    
- Example: Sum of transaction fields exceeds a defined threshold
    

**Key Behavior:**

- Must be thrown **manually** using a `Throw` activity
    
- Marked as **Failed – Business** in Orchestrator
    
- **Not retried**
    
- No crash or restart happens
    
- Process continues with the **next transaction**
    

---

## 🧩 **Configuration File (Config.xlsx) Parameters for Exception Handling**

|Parameter|Purpose|
|---|---|
|`MaxRetryNumber`|Retries for **non-queue** transactions (set to 0 if using queues)|
|`MaxConsecutiveSystemExceptions`|Stops job after this many consecutive system exceptions|
|`ShouldMarkJobAsFaulted`|If TRUE, job is marked as **Faulted** in Orchestrator when stopped by max system exceptions|

---

## 🔁 **How REFramework Handles Exceptions**

### System Exception:

- In **Process state**:
    
    1. Try to process transaction.
        
    2. If a system exception occurs:
        
        - Log the error and take a screenshot.
            
        - Set transaction to **Failed - Application**.
            
        - Retry if allowed.
            
        - Reinitialize apps (Init state).
            
        - Increment `ConsecutiveSystemExceptions`.
            
- In **Init state**:
    
    - If a crash happens here and `ShouldMarkJobAsFaulted` is TRUE, the **job is marked as Faulted**.
        

---

### Business Exception:

- In **Process state**:
    
    1. Developer uses a `Throw` activity to raise a `BusinessRuleException`.
        
    2. Set transaction status to **Failed - Business**.
        
    3. Log the reason.
        
    4. Reset retry and exception counters.
        
    5. Proceed to the next transaction.
        

---

## 📈 **Viewing Exceptions in Orchestrator**

Go to:

> **Orchestrator → Queues → View Transactions**

There you can:

- View status: **Successful**, **Failed - Application**, **Failed - Business**
    
- Click **"More Actions → View Details"** to see:
    
    - Exception Type
        
    - Reason
        
    - Screenshot (for System Exceptions)
        
    - Specific Data
        
    - Retry status
        

---

## 🧪 **Real-Time Demo Scenarios Covered**

### ✅ **System Exception Test**

- Enabled crash simulation in UiDemo.
    
- Simulated crashes during multiple transactions.
    
- Confirmed:
    
    - Retry behavior.
        
    - Screenshot logging.
        
    - Incrementing of `ConsecutiveSystemExceptions`.
        
    - Job stopped when counter hit 3.
        

### ✅ **Business Rule Exception Test**

- Set threshold to 10,000 in Config.
    
- When a transaction exceeded this value:
    
    - A `Throw` activity raised a `BusinessRuleException`.
        
    - It was caught and logged.
        
    - Transaction was marked **Failed - Business** (no retry).
        
    - The exception counter was **reset**.
        

---

## 🧠 **Reflection Questions You Should Be Able to Answer**

1. ✅ What happens after a **Business Rule Exception** is thrown?
    
    - It is caught, logged, not retried, and the robot moves to the next transaction.
        
2. ✅ How does REFramework handle **System Exceptions**?
    
    - Retries, resets apps, logs error, and counts failures.
        
3. ✅ Where do you find queue item statuses?
    
    - **Orchestrator → Queues → View Transactions**
        
4. ✅ How can you find **why** a queue item failed?
    
    - Click **"View Details"** on a transaction to see Exception Type, Message, and Screenshot.
        

---

## 🏁 **Main Takeaways**

- **System Exceptions** → Retry if allowed, restart app, log and capture screenshot
    
- **Business Exceptions** → Not retried, flagged for human review
    
- All exceptions are **logged with context and custom fields**
    
- **REFramework is fault-tolerant** and built to self-recover unless critical thresholds are reached
    

---
## ⚙️ **What is Concurrent Queue Consumption?**

**Concurrent queue consumption** means multiple robots working **in parallel** on the same **Orchestrator queue**, each pulling and processing different transaction items simultaneously.

---

### ✅ **Benefits**

- **Speeds up processing** by splitting the workload
    
- **Scales effortlessly** as more robots are added
    
- Perfect for **large data sets** and **time-sensitive processes**
    

---

## 🚀 **How to Execute a Job with Multiple Robots**

1. **Prepare Your Robots**:
    
    - Ensure each robot is connected to **Orchestrator**
        
    - Robots can run on different machines (e.g., local + VM)
        
2. **Go to Orchestrator → Automations → Start Job**
    
3. **Key Settings**:
    
    - **User/Robot Account**: Let Orchestrator pick or choose specific ones.
        
    - **Machine**: Pick a specific host or let it allocate dynamically.
        
    - **Allocate Dynamically**: Run the job multiple times (e.g., 2-3) to allow Orchestrator to distribute across available robots.
        

> For example, if you start the process twice with 2 robots connected, each will pick different queue items and process in parallel.

---

## 📊 **Monitor Workload Distribution**

- Go to **Orchestrator → Monitoring → Queues**
    
- Observe processing rates (e.g., from 17 to 26 transactions per minute with 2 robots)
    

---

## 🛑 **Stopping a Job Gracefully**

### ✋ **Why Stop Instead of Kill?**

- **Stop** → Allows the robot to finish its current transaction and exit safely
    
- **Kill** → Immediately terminates the job (unsafe for transactions)
    

### 🛠️ **How the Stop Signal Works**

- In REFramework, the **Should Stop** activity checks if a stop command has been issued.
    
- It's placed at the beginning of the **Get Transaction Data** state.
    
- If `ShouldStop = True`:
    
    - `TransactionItem` is set to `Nothing`
        
    - Transitions to **End Process**
        
    - Logs the stop request
        

### 🔍 Where to See Stop Results

- Go to **Orchestrator → Jobs → View Logs**
    
- You’ll see a message like: **"Stop process was requested"**
    

---

## ⚡ **Dynamic Allocation Options**

|Option|Behavior|
|---|---|
|**User only**|Orchestrator dynamically assigns machine|
|**Machine only**|Orchestrator dynamically assigns user|
|**Neither**|Orchestrator assigns both|
|**Both**|Runs on specific user-machine pair|

---

## ✅ **Main Takeaways**

- REFramework with Orchestrator supports **scalable, distributed processing**.
    
- **Dynamic allocation** helps maximize resource utilization.
    
- **Should Stop** enables graceful termination, preventing data loss.
    
- This model supports **high availability** and **efficiency** in production.
    

---