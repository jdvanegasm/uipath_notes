## Core components
### Studio
- Tool for building automation processes.

### Robot
- The robot executes the processes built in studio (Locally/Orchestrator).

### Orchestrator
- Web Application that acts as the Interface between studio and robot, and manages controls and monitors automation task.

### Workflow

1. A new version of a project change the package in orchestrator.
2. Published packages in orchestrator need to be associated with folders.
3. If a published package is paired with a folder, it becomes a process and can be run by robots.
4. Human users can trigger robots through the UiPath Assistant tool on their machines.
5. This robots triggered by humans, are attended robots.
6. Robots deploy on separate machines working without direct human intervention are called unnattended robots.
7. Orchestrator manage the execution of this unnatended robots.
8. The execution in both kinds of robots it's done through jobs.
9. Communication between robots and the orchestrator is always trigger by the robots.
10. The robots send heartbeats every thirty seconds and waits for the orchestrator to respond.
11. When there is a job to be done, the orchestrator sends a heartbeat with the job info to the robot.
12. When there is more than one Orchestrator, the job info, and packages are storaged in a external server, the robot ask the orchestrator for the job info, and the orchestrator send the query to the external server, the external server respond to orchestrator, and after it orchestrator respond to the robot.

#### Note: Packages in Orchestrator are saved as NuGet Packages

### **Automation Cloud Robots (ACRs)**

**Automation Cloud Robots (ACRs)** are **SaaS-based UiPath robots** that run automations without requiring users to manage infrastructure. They come in two types:

1. **VM Automation Cloud Robots** – Provide a **customizable Windows virtual machine**, enabling quick deployment of unattended automation.
2. **Serverless Automation Cloud Robots** – **Linux-based, cross-platform bots** that run in the background, with UiPath handling infrastructure and scaling.
### Compatibility
1. Windows use dotnet 6 with windows support
2. Cross-Platform use dotnet 6
3. Legacy uses 4.5.1

#### PDD: Process Definition Document
#### SDD: Solution Design Document

## Variables
- **We can imagine variables as containers that hold data (Values) of a certain type**
- **We should write variables name in PascalCase**
- **Most common data types:**
	- Boolean
	- Int32
	- String
	- Object
	- System.Data.DataTable
	- Array of [type]
- **Scope: Defines the context of the variable**
- **Default values depends of the variable type**

### **Type Conversion Methods in C# – Summary**

#### **Convert a Value to a String**

- **`Convert.ToString(value)`** → Converts a value to a string.
- **Example:**
    
    ```csharp
    StrVar = Convert.ToString(IntVar);
    ```
    
- **Alternative for Floating-Point Numbers:**
    
    ```csharp
    StrVar = DblVar.ToString();
    ```
    

#### **Convert a Value to an Integer**

- **`Convert.ToInt32(value)`** → Converts a string or floating-point number to an integer.
- **Examples:**
    
    ```csharp
    IntVar = Convert.ToInt32(StrVar);
    IntVar = Convert.ToInt32(DblVar);
    ```
    
- **Alternative Method:**
    
    - `CInt(StringVar)` (Only in VB.NET)
    
    ```csharp
    IntVar = CInt(StrVar);
    ```
    

#### **Convert a String to a Double (Floating-Point Number)**

- **`Double.Parse(value)`** → Converts a string representation of a number to a `double`.
- **Example:**
    
    ```csharp
    DblVar = Double.Parse(StrVar);
    ```
    

#### **Convert a Boolean to a String**

- **`Boolean.ToString()`** → Converts a `bool` to `"True"` or `"False"`.
- **Example:**
    
    ```csharp
    StrVar = BoolVar.ToString();
    ```
    

#### **Convert a Value to a Boolean**

- **`Convert.ToBoolean(value)`** → Converts an integer or other value to a Boolean.
- **Example:**
    
    ```csharp
    BoolVar = Convert.ToBoolean(IntVar);
    ```
    

#### **Convert Date and Time to a String**

- **`DateTimeVar.ToString("format")`** → Converts a `DateTime` to a formatted string.
- **Example (DD-MM-YYYY format):**
    
    ```csharp
    DateStr = DateTimeVar.ToString("dd-MM-yyyy");
    ```
    

---

### 🔹 **Summary**

These conversion methods are essential for handling different data types in C#. Use:

- `Convert.ToString()` for string conversion.
- `Convert.ToInt32()` or `CInt()` for integers.
- `Double.Parse()` for floating-point numbers.
- `Convert.ToBoolean()` for Boolean values.
- `DateTime.ToString("format")` for date formatting.

#### **🔹 What is a Workflow?**

- A **workflow** is a small, reusable part of an automation project.
- It **executes a specific task** and can be used across multiple projects.
- Composed of **Studio activities**, interconnected through **variables**.
- Typically has an **input** and an **output**, defining the **flow of automation**.

#### **🔹 Workflow Layouts in UiPath Studio**

UiPath provides predefined workflow structures to optimize automation:

1. **Sequences**
    
    - Best for linear, simple processes.
    - Executes steps **sequentially**.
2. **Flowcharts**
    
    - Useful for complex decision-making.
    - Allows for **branching logic**.
3. **State Machines**
    
    - Ideal for processes with **multiple states and transitions**.
    - Efficient for **event-driven automation**.

#### **🔹 Benefits of Using Workflows**

- **Faster & More Reliable Automation**  
    Breaking processes into smaller workflows improves efficiency.
- **Independent Testing**  
    Each workflow can be tested separately for debugging.
- **Team Collaboration**
    Multiple developers can work on different workflows simultaneously.
- **Reusability** 
    Workflows can be reused in different projects, reducing redundancy.

#### **🔹 Key Takeaway**

The best approach to automation is **dividing a large process into smaller workflows**, making the project **modular, scalable, and easier to maintain**.


### **Arguments in UiPath – Summary**

#### **🔹 What are Arguments?**

- **Arguments** are used to pass data **between workflows**, unlike variables that pass data **between activities** within the same workflow.
- Essential for **complex automation** where multiple workflows interact.

#### **🔹 Argument Directions**

Arguments have **three specific directions** that define data flow:

1. **In (`In`)**
    
    - Passes data **into** a workflow.
    - The value is **read-only** inside the workflow.
    - Example: Supplying a **username** or **order ID** to a process.
2. **Out (`Out`)**
    
    - Passes data **out** of a workflow.
    - Used when the workflow **processes data** and returns a result.
    - Example: Extracting **processed data** to be used in another workflow.
3. **In/Out (`In/Out`)**
    
    - Allows data to be **both received and modified** within the workflow.
    - Used when the workflow needs to **update a value** and pass it back.
    - Example: **Updating a status** within a loop.

#### **🔹 Why Use Arguments?**

- **Enable modular workflows**
    Workflows can function independently and exchange data.
- **Enhance reusability**
    A workflow can be used in different projects with different input values.
- **Improve automation structure**
    Makes automation **scalable** and **easy to maintain**.

#### **🔹 Key Takeaway**

Arguments are **critical for multi-workflow automation**, ensuring smooth data transfer between workflows. Proper use of **In, Out, and In/Out** directions optimizes workflow interaction and execution.

### Control Flow
Its the order in wich activires are executed or evaluated in a software project, In UiPath the control flow is determinated by:
1. Workflow layouts:
	1. Sequence
	2. Flowchart
	3. State Machine
	4. Global Handler
2. Control Flow Statements:
	1. Conditionals: If, Else If and Switch.
	2. Loops: While, Do While and For Each

**Note: When using nested conditional logic, its generally best practice to use the Flow Decision activity in a flowchart rather tan nesting multiple If activities.**

**Note: There is a Browse For Folder and Browse For File activities very useful when we work with Folders and Files, another useful activities are: **
1. **Move File**
2. **Move Folder**
3. **For Each for File in a Folder incluiding Sub Folders**
4. **For each Row in Data Table**

## Excel Automation
**We can access and manipulate workbooks/excel with:**
1. Workbook or File Acces Level: Doesn't need excel installed, and works only with xls and xlsx files. Cannot open files in excel at runtime.
2. Excel or Excel App Integration: Needs excel installed on the computer, and works with xls, xlsx, xlsm and csv. Can Open Files in excel at runtime.

**Excel Design Experiences:**
1. UseGlobalSetting:
	- This option applies the default design experience set at the studio level. If the studio-level design experience is set to Modern, then this option selects Modern for Excel activities in the project. If the studio-level design experience is set to Classic, then this option selects Classic for Excel activities in the project.
2. UseClassic:
	- This option selects the Classic design experience for Excel activities in the project, irrespective of the studio-level design experience.
3. UseMordern:
	- This option selects the Modern design experience for Excel activities in the project, regardless of the studio-level design experience.

### Useful Activities
1. Read Range Workbook: Opens some Excel files
2. Add Data Column: Literally adds a column with the selected configs

```
Convert.ToDouble(CurrentRow["Quantity"].ToString()) * Convert.ToDouble(CurrentRow["Price per Kg"].ToString().Replace(",", "."));
```

**Note: Don't forget to initialize the dt_variables with new DataTable()**
**Note: Don't forget to set the output dt while reading the workbook**

### **UI Automation: Key Concepts**

**UI Automation Activities** → Predefined actions to interact with UI elements.  
**Activity Properties** → Configurable settings to control activity behavior.  
**Targeting Methods** → Ways to identify UI elements (selectors, anchors, fuzzy search).  
**Input & Output Methods** → Sending keystrokes, clicks, and extracting data from UI.  
**Recorders** → Tools to capture user interactions for automation.  
**Extraction Wizard** → Extracts structured data from UI elements.  
**Object Repository** → Centralized storage for UI elements, improving reusability.  
**AI Computer Vision** → Uses AI to interact with UI elements visually.

**Essential for building robust UI automation in UiPath!**

![[User_Interface_Automation.gif]]
**Targeting methods**: determine which elements in the UI to interact with.
**UI Automation activities**: perform the required actions on the targeted UI elements.
**Activity properties**: configure the behavior of the UI Automation activities.
**Input and output methods**: provide data to and receive data from the UI elements.

### **Overview of UI Automation Activities**

UI automation activities allow robots to interact with application interfaces. They are categorized into four main types:

### **Containers** 

- Define the browsers or applications the process will interact with.
- Ensure all activities inside them run in the same app.
- **Examples:** Open Browser, Attach Browser, Open Application, Use Application/Browser.

### **Activities for Synchronization** 

- Trigger actions based on UI events or behaviors.
- Help the Robot wait for specific conditions before proceeding.

### **Input Activities** 

- Used to send data or actions to UI elements.
- **Examples:** Click, Type Into, Check, Send Hotkeys.

### **Output Activities**

- Extract data from UI elements.
- **Examples:** Get Text, Get Structured Data, Retrieve UI Elements with Images.

### **Activity Properties in UI Automation**

Each UI Automation activity has specific properties that control its behavior.

| **Property**               | **Function**                                                         |
| -------------------------- | -------------------------------------------------------------------- |
| **DelayAfter/DelayBefore** | Sets the waiting time (in milliseconds) before/after execution.      |
| **ContinueOnError**        | Defines whether the automation should proceed despite errors.        |
| **Target**                 | Specifies properties to identify the target UI element.              |
| **Timeout (seconds)**      | Determines how long the Robot will attempt an action before failing. |
| **Input Mode**             | Selects the method for sending input actions to UI elements.         |
| **Output**                 | Stores the result of the activity in a variable.                     |
### **Input Methods in UiPath UI Automation**

When inserting data or triggering system actions, UiPath provides different input methods that impact execution speed, background processing, and user interference.

Here are the four **input methods** available in the modern design experience:

| **Input Method**         | **Description**                                                                                                                         | **Best Use Case**                                                                                  |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| **Hardware Events**      | Uses physical mouse/keyboard signals to interact with the UI. Works with all applications but requires focus (no background execution). | Automating tasks that need direct keyboard/mouse interaction (e.g., data entry, clicking buttons). |
| **Send Window Messages** | Sends system messages directly to applications, mimicking user interactions without using physical hardware. Works in the background.   | Automating applications requiring precise timing or those unresponsive to other methods.           |
| **Simulate**             | Directly interacts with UI elements without relying on hardware or system messages. Faster and runs in the background.                  | Automating fast and accurate GUI interactions like typing and clicking.                            |
| **ChromiumAPI**          | Uses **DevTools Protocol** for direct browser communication. Works with Chrome, Edge, and other Chromium-based browsers.                | Automating web applications, web scraping, or background browser automation.                       |

**Choosing the right input method enhances automation speed, accuracy, and stability!**

### Lesson 7: Using Input Activities & Input Methods (Part 1)

#### **Foreground vs Background Processes**

🔹 **Foreground Process** → **Visible & interactive** (e.g., typing a document, browsing).  
🔹 **Background Process** → **Runs without user involvement** (e.g., antivirus scans, backups).

|**Characteristic**|**Foreground Process** 🖥️|**Background Process** ⚙️|
|---|---|---|
|**Example**|Typing, browsing|Antivirus, backups|
|**Visibility**|Visible & interactive|Runs in the background|
|**Resource Usage**|Uses more resources|Lower priority usage|
|**Interruptions**|Can be paused|Runs continuously|
|**User Attention**|Requires focus|No user input needed|

---

### **Background Mode in UiPath**

✅ **Allows automation to run in the background without user interaction.**  
✅ **Enabled via:** `Properties Panel → Input Mode → Background Mode`.  
✅ **Works only in** `Use Application/Browser Activity`.

---

### **Limitations of Background Mode**

🚫 Activities **not** compatible with Background Mode:

- **Image-based targeting** 📷.
- **Native text automation** ✍️.
- **Keyboard shortcuts** ⌨️.
- **Minimized applications** 📉.
- **Take Screenshot Activity** 🖼️.

🔹 **If incompatible actions are included?**

- **Automation still runs**, but **those activities execute in the foreground** before resuming in the background.
- **Solution:** Use **Picture-in-Picture (PIP)** for multitasking.

---
### **Lesson Summary**

✔ **Foreground processes** require user interaction, while **background processes** do not.  
✔ **Background Mode** in **Use Application/Browser** allows UiPath to run automation **without active user input**.  
✔ Uses **Simulate** or **ChromiumAPI** input methods.  
✔ **Certain UI actions are not compatible**, but automation still runs smoothly.

🔹 **💡 Pro Tip:** Use **PIP mode** to handle attended automation while multitasking! 🚀

### 📌 Input Methods & Activities (Part 2) - Notes

---

## **🖊️ Overview of Automation in Double UI Application**

We automate a **deposit transaction** using:  
✅ **Type Into** – Entering values in "Cash in" & "On Us Check" fields.  
✅ **Click** – Submitting the transaction.

The automation runs inside **Use Application/Browser** activity.

---

## **🖋️ Type Into Activity - Key Concepts**

### **1️⃣ Adding Text**

- **Directly** or via **Open Editor** (Right-click).
- **Standard vs Secure String**:
    - **Standard** → Normal text input.
    - **Secure String** → Used for passwords.

---

### **2️⃣ Options & Properties**

|**Property**|**What It Does**|
|---|---|
|**Empty Field** 🗑️|Deletes existing text before typing. Options: `None`, `SingleLine`, `MultiLine`|
|**Click Before Typing** 🖱️|Clicks the field before typing. Options: `None`, `Single`, `Double`|
|**Delay Before/After** ⏳|Wait time before or after execution.|
|**Input Mode** 🎯|Inherits from `Use Application/Browser` OR set separately.|
|**Auto Set Correct Input Method** 🛠️|Tests **ChromiumAPI → Simulate → Windows Messages → Hardware Events** until one works.|
|**Activate** 🔥|Brings UI element to **foreground** before typing. Works with **Hardware Events & Chromium API**.|

💡 **Important:**

- `"Empty Field"` **does not apply** when using **Simulate Input Mode** (it always replaces text).
- `"Click Before Typing"` **only works** with **Hardware Events & Chromium API**.

---

## **🖋️ Click Activity - Key Concepts**

|**Property**|**What It Does**|
|---|---|
|**Click Type** 🖱️|Choose `Single`, `Double`, `Down`, or `Up`. (Default: `Single`).|
|**Mouse Button** 🖱️|Choose `Left`, `Middle`, or `Right`. (Default: `Left`).|

---

## **🖥️ Running in Background Mode**

✅ Allows automation to **run without user interaction**.  
✅ Works with **Simulate Input & Chromium API**.

### **🚨 Incompatible Actions for Background Mode**

❌ Image-based targeting.  
❌ Native text automation.  
❌ Keyboard shortcuts.  
❌ Minimized applications.  
❌ Take Screenshot activity.

---

## **Summary**

✔ **"Type Into"** enters data in UI fields with multiple configuration options.  
✔ **"Click"** is configurable with different click types & buttons.  
✔ **Foreground & Background execution affects automation behavior.**  
✔ **Background Mode works with Simulate Input & Chromium API but has limitations.**


### **📌 Output Methods in UI Automation - Notes**

---

## **🖊️ Overview of Output Methods**

Output actions **extract data** (usually text) from **UI elements**.  
Modern UI automation design uses **three main output methods**:

|**Output Method**|**Key Features**|
|---|---|
|**Full Text** ✅|🔹 Fastest method 🚀 🔹 Extracts **hidden text** 👀 🔹 **100% accuracy** 🎯 🔹 Works in the **background** ✅|
|**Native** 🏛️|🔹 Works with **GDI-based apps** 🖼️ 🔹 **Does NOT extract hidden text** ❌ 🔹 **Cannot run in the background** ❌ 🔹 Captures **text position & formatting** 🎨|
|**OCR (Optical Character Recognition)** 🏆|🔹 Works in **virtual environments** 🖥️ 🔹 **Extracts text from images** 📸 🔹 **Slowest method** 🐢 🔹 Accuracy **varies** depending on settings ⚙️|

---

## **📋 Choosing the Right Output Method**

### Ask yourself:

🔹 How **fast** does it need to be?  
🔹 Should it run **in the background**?  
🔹 Does it need to extract **hidden text**?  
🔹 Is it running in a **virtual environment**?

---

## **⚡ Detailed Comparison of Output Methods**

| **Criteria**                         | **Full Text** ✅ | **Native** 🏛️             | **OCR** 🏆     |
| ------------------------------------ | --------------- | -------------------------- | -------------- |
| **Speed** ⏩                          | **Fastest** 🚀  | Slower ⚡                   | **Slowest** 🐢 |
| **Accuracy** 🎯                      | **100%** ✅      | **100%** ✅ (GDI apps only) | **Varies** ⚠️  |
| **Works in Background** 🎭           | **Yes** ✅       | **No** ❌                   | **No** ❌       |
| **Extracts Hidden Text** 👀          | **Yes** ✅       | **No** ❌                   | **No** ❌       |
| **Works in Virtual Environments** 🌐 | **No** ❌        | **No** ❌                   | **Yes** ✅      |
| **Captures Text Formatting** 🎨      | **No** ❌        | **Yes** ✅                  | **Yes** ✅      |

---

## **🔍 Additional Notes on OCR**

🟢 Supports multiple OCR engines:

- **Google Tesseract** 🔍
- **Microsoft MODI** 🏛️
- **Omnipage & Abbyy Embedded (Free)** 🎁
- **Abbyy IntelligentOCR (Paid)** 💰

💡 **OCR should only be used when Full Text & Native are not an option** (e.g., text inside images or remote desktops).

---

## **📌 Lesson Summary**

✔ **Output methods** extract data from UI elements.  
✔ **Three main methods**: Full Text, Native, OCR.  
✔ **Full Text is the fastest & extracts hidden text**.  
✔ **Native works with GDI apps & extracts formatting**.  
✔ **OCR is the only method for images & virtual environments but is slow & less accurate**.

---

### 📌 Summary: Using Output Activities and Output Methods - Part 3

---

## **🔹 Key Learnings**

By the end of this session, you should be able to:  
✔ Identify and configure **output activities** in UI automation.  
✔ Apply different **scraping methods** to extract data effectively.  
✔ Use **Get Text** activity to capture and process UI data.

---

## **📌 Overview of 'Get Text' Activity**

🟢 **Extracts and copies text** from a UI element.  
🟢 **Must be placed inside** a **Use Application/Browser** activity.  
🟢 Supports **various output methods**:

|**Scraping Method**|**Functionality**|
|---|---|
|**Default** ✅|Tries all methods and uses the first one that returns text.|
|**Text Attribute** 📄|Extracts text from a specific attribute (e.g., `value`).|
|**Full Text** 🔍|Captures **all text**, including hidden elements.|
|**Native** 🎨|Extracts text with **formatting & screen coordinates**.|

📌 **Use Case Considerations:**  
✔ Extracting **single input fields** → Use **Text Attribute**.  
✔ Extracting **structured text (e.g., tables)** → Use **Full Text**.

---

## **⚡ Implementing 'Get Text' in the Automation**

### **🛠 Steps to Extract & Store Transaction Numbers**

1️⃣ **Add a Get Text Activity** → Select the UI element to extract text from (e.g., Transaction Number label).  
2️⃣ **Store the extracted text** in a **variable**.  
3️⃣ **Use a Message Box** to verify the extracted data.

### **📌 Automating Data Entry & Storage**

✔ **Read Excel Data** → Use **Read Range Workbook** activity to load transaction details into a **Data Table**.  
✔ **Loop through entries** → Use **For Each Row in Data Table** to process each transaction.  
✔ **Enter Data** → Use **Type Into & Click Activities** to input data into the UI.  
✔ **Extract Transaction Number** → Use **Get Text Activity**.  
✔ **Write Data Back to Excel** → Use **Write Cell Workbook** to store the extracted transaction number.

---

## **📌 Handling Row Numbering in Excel**

✔ **Create a Variable** (`RowNumber`) to track the row index.  
✔ **Increment RowNumber** after each transaction using an **Assign Activity**.  
✔ **Use the updated RowNumber** in **Write Cell** to store values correctly.

---

## **🔍 Key Takeaways**

✔ **Get Text Activity** extracts UI text efficiently using different **scraping methods**.  
✔ **Output methods** (Full Text, Native, OCR) help extract data from UI elements.  
✔ **Looping & writing data** to Excel ensures an automated workflow.  
✔ **Adjust variable scope** for `RowNumber` to **DO container** for proper execution.

### 📌 Summary: Using App/Web Recorder in UiPath

---

## **🔹 Key Learnings**

By the end of this session, you should be able to:  
✔ **Use the App/Web Recorder** to capture user interactions.  
✔ **Understand recorded actions & manually selected actions.**  
✔ **Edit, modify, and optimize recorded workflows.**

---

## **📌 Overview of App/Web Recorder**

🟢 Captures **on-screen user actions** and converts them into **UiPath activities**.  
🟢 Supports **both Web & Desktop applications**.  
🟢 Generates a **Use Application/Browser** activity, organizing all recorded actions inside.

---

## **⚡ Automatically Recorded vs Manually Selected Actions**

|**Automatically Recorded Actions** ✅|**Manually Selected Actions** ✋|
|---|---|
|**Clicking** buttons, links, icons, images → **Click Activity** 🖱️|**Copying text** → **Get Text Activity**|
|**Typing text** → **Type Into Activity** ⌨️|**Hovering over an element** → **Hover Activity** 🏹|
|**Selecting/Deselecting checkboxes** → **Check/Uncheck Activity** ☑️|**Highlighting elements** → **Highlight Activity** 🔦|
|**Keyboard shortcuts** → **Keyboard Shortcuts Activity** ⌨️||
|**Selecting dropdown items** → **Select Item Activity** 🔽||

---

## **📌 Recorder Settings & Features**

### **1️⃣ Input Method Options** 🎯

✔ **Auto Mode (Default)** → Selects the best input method automatically.  
✔ **Other Methods:** Chromium API, Window Messages, Simulate, Hardware Events.

### **2️⃣ Full Configuration of Targets & Saved Values** 🏹

✔ If **enabled**, requires confirmation for UI elements before recording.  
✔ Allows **adding/deleting anchors** for better accuracy.  
✔ If **disabled**, actions are recorded instantly without confirmation.

### **3️⃣ Recording Multiple Applications in One Session** 🔄

✔ If **Use Application/Browser Activity is selected** → Can **only record actions** within that app/window.  
✔ If **No Use Application/Browser is selected** → Can **record across multiple applications** seamlessly.

---

## **📌 Implementing App/Web Recorder: Loan Application Workflow**

### **Steps:**

1️⃣ **Start Recording** → Select "Apply for Loan" button (Click Activity).  
2️⃣ **Enter Details** → Fill in email, loan amount, income (Type Into Activity).  
3️⃣ **Select Loan Term** → Dropdown selection (Select Item Activity).  
4️⃣ **Submit Application** → Click on "Submit" button.  
5️⃣ **Extract Loan ID** → Use **Get Text** activity.  
6️⃣ **Store Loan ID** in a **variable** and display it using a **Message Box**.

---

## **📌 Lesson Summary**

✔ The **App/Web Recorder** captures and automates UI interactions efficiently.  
✔ It generates a **Use Application/Browser** activity containing all recorded steps.  
✔ Supports **automatic & manual** actions.  
✔ Allows **customization & editing** after recording.  
✔ Can record across **multiple applications** if no specific app/browser is selected.

---
### 📌 Summary: Using Table Extraction in UiPath

## **🔹 Key Learnings**

By the end of this session, you should be able to:  
✔ **Use the Table Extraction wizard** to extract structured data.  
✔ **Define columns, refine selection, and edit extracted data.**  
✔ **Extract multi-page data efficiently using navigation.**

---

## **📌 Overview of Table Extraction**

🟢 Automates structured data extraction from web pages & applications.  
🟢 Converts extracted data into a **Data Table object** for further processing.  
🟢 Useful for **data entry, web scraping, and business intelligence.**

### **🚀 Example Use Case**:

Extracting **video titles, URLs, and upload dates** from Google search results and saving them into an **Excel file**.

---

## **📌 Key Features & Options in Table Extraction Wizard**

|**Feature** 🔧|**Functionality**|
|---|---|
|**Add New Column** ➕|Select similar elements to be extracted as a table column.|
|**Extract Text or URL** 🌐|Extract either **visible text** or associated **URL** of elements.|
|**Refine Selection** 🎯|Improve accuracy by selecting similar missing elements.|
|**Column Settings ⚙️**|Modify column properties like name, type, sorting, and format.|
|**Parse Data As** 🔄|Convert extracted data to **Text, Numbers, or Date & Time**.|
|**Sort Data** 📊|Arrange data in **Ascending or Descending order**.|
|**Preview Extracted Data 👁️**|Check extracted data before finalizing extraction.|

---

## **📌 Extracting Data from Multiple Pages**

✔ Toggle **"Extract data from multiple pages"** to `Yes`.  
✔ Indicate the **"Next Page"** button or link.  
✔ Set a **limit** (Max Pages / Max Rows) in **Settings Section**.

---

## **📌 Implementing Table Extraction: UiPath Academy Videos Use Case**

### **Steps:**

1️⃣ **Open Browser** → Navigate to Google search page (`Use Application Browser`).  
2️⃣ **Search "UiPath Academy"** → Use **Type Into** & **Click** activities.  
3️⃣ **Navigate to Videos Tab** → Use **Click Activity**.  
4️⃣ **Start Table Extraction** → Select video **titles**, **URLs**, and **upload dates**.  
5️⃣ **Customize Data** → Edit columns, refine selection, and sort results.  
6️⃣ **Enable Multi-Page Extraction** → Extract from the first **3 pages**.  
7️⃣ **Save Extracted Data to Excel** → Use **Write Range Workbook**.

---

## **📌 Lesson Summary**

✔ **Table Extraction** converts structured UI data into **Data Tables**.  
✔ Supports **text, URLs, and multi-page extraction**.  
✔ Allows **customization (column settings, sorting, parsing)**.  
✔ Can be used for **data entry, business intelligence, and web scraping**.
