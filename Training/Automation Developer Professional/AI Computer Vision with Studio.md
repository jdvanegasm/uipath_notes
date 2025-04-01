## 🧠 **Basics of AI Computer Vision**

### ✅ What is Computer Vision?

- It allows robots to **"see"** the UI visually instead of relying only on selectors.
    
- Uses **AI (Object Detection, OCR, Fuzzy Matching, Icon Detection)** + **Anchoring System** to locate and interact with elements reliably.
    

### ✅ Why is it needed?

- Traditional OCR/Image Matching often fails in **Virtual Desktop Environments (VDIs)** like Citrix, VMware, RDP.
    
- CV offers **human-like recognition** to handle **dynamic UI changes** more robustly.
    

### ✅ Real-World Applications:

- **Invoice Processing:** Reads data from varied invoice formats.
    
- **Document Classification:** Sorts and routes emails/contracts intelligently.
    
- **Automated Data Entry:** Extracts info from forms into databases.
    

### ✅ How it improves automation:

- Enhances **accuracy**, **resilience**, and **adaptability** in automation.
    
- Works well with **scrollable, dynamic content**, even when elements change position or style.
    

### ✅ Key Benefits:

1. Works beyond selectors (PDFs, images).
    
2. Intelligent interaction using **multi-anchoring system**.
    
3. Compatible with **VDIs and hybrid interfaces**.
    
4. Supports **tables, dropdowns, checkboxes**.
    
5. **Auto-scroll** feature for long content.
    

---

## 🛠 **Computer Vision Activities**

**⏱ Duration: 10 min**

### ✅ All CV activities must be placed **inside `CV Screen Scope`**, which starts the neural network and allows screen interaction.

### 📌 **Key CV Activities:**

- **CV Screen Scope** – Starts the Computer Vision engine.
    
- **CV Click** – Clicks on visual UI elements.
    
- **CV Get Text** – Extracts text using OCR.
    
- **CV Extract Table** – Extracts visible tables to DataTable.
    
- **CV Element Exists** – Checks if an element is present.
    
- **CV Check** – Toggles checkboxes.
    
- **CV Dropdown Select** – Selects an option from dropdowns.
    
- **CV Highlight** – Highlights elements visually.
    

---

## 🔍 **Computer Vision vs. UI Automation**

**⏱ Duration: 10 min**

|Feature|UI Automation|Computer Vision|
|---|---|---|
|**Element Detection**|Uses **selectors**|Uses **neural network + AI**|
|**Scrolling Support**|Limited, struggles with infinite scroll|**Auto-scroll** support|
|**Table Extraction**|Works on structured tables|**Flexible**, works even when structure is unclear|
|**Targeting**|Selectors, anchor base, image automation|Uses **visual cues** and **anchors**|

### ✅ When to Use:

- Use **UI Automation** when dealing with stable, modern apps (with good selectors).
    
- Use **Computer Vision** for **remote environments**, **scanned docs**, and **dynamic UIs**.
    
- Best practice: **Combine both** based on context for reliable automation.
    

---

## 🧾 Final Summary:

- **AI Computer Vision** empowers robots to interact visually like humans.
    
- It excels in **unstructured**, **dynamic**, and **remote environments**.
    
- UiPath's CV activities and features provide a powerful toolset for automation where selectors fall short.

---
## 🎥 **Computer Vision Recorder**

### ✅ What is it?

The **Computer Vision Recorder** is a tool in UiPath Studio (Design Ribbon) that **automatically generates workflows** using **CV activities** by recording user interactions on screen.

### 🎬 How to use it:

1. Open Studio and click **Computer Vision Recorder**.
    
2. Click **Record** and select the application window to automate.
    
3. The selected app is sent to the CV server and screen enters **recording mode**.
    
4. Perform UI interactions – they are recorded as **CV Click, CV GetText**, etc.
    
5. Use:
    
    - **Refresh** if the app content changes.
        
    - **Change Application** to switch windows.
        
6. When done, click **Save & Quit** – all actions are inserted into your workflow.
    

### 🔐 API Key / Licensing:

- Needed only if using UiPath Automation Cloud.
    
- To get the key:
    
    1. Go to [cloud.uipath.com](https://cloud.uipath.com/)
        
    2. Admin → License → Robots & Services → Copy API Key.
        
    3. Paste into **Project Settings > Computer Vision > ApiKey**.
        

> Community users can use it **freely**, within specific limits.

### 🧪 Demo Recap:

- UI Demo app was used to record data entry in two tabs: **Deposit** and **Withdrawal**.
    
- Used anchors when elements had **duplicate matches**.
    
- Recorded **CV Click**, **CV GetText**, etc.
    
- Stored transaction numbers in variables.
    
- Added **Write Line** to display them.
    

### 📌 Key Takeaways:

- Fast, reliable creation of CV-based workflows.
    
- Reduces manual configuration of CV activities.
    
- Reusable in **local and virtual environments** (Citrix, RDP, etc.).
    

---

## 📊 **Tabular Data Extraction with Scrolling**

**⏱ Duration: 10 min**

### ✅ Purpose:

Extract data from **scrollable tables** (local or remote) using **CV Extract Table**, especially useful in **Citrix/RDP environments**.

### ⚙️ Main Properties of `CV Extract Table`:

|Property|Description|
|---|---|
|`DelayScreenshotAfterScroll`|Wait time (ms) before capturing screen after scroll.|
|`NumberOfScrolls`|Scrolls per capture (e.g., 1 = scroll once then capture).|
|`ScrollableTable`|Enables detection of tables that need scrolling.|
|`ScrollDirection`|Direction to scroll (e.g., Down).|
|`Add Headers`|If unchecked, assigns generic column names.|

### 🧪 Demo Recap:

1. Created a new process and added **CV Screen Scope**.
    
2. Indicated the webpage region containing the table.
    
3. Used **CV Extract Table** to select the full table area.
    
4. Configured properties:
    
    - `NumberOfScrolls = 1`
        
    - `ScrollableTable = True`
        
    - `ScrollDirection = Down`
        
    - `Add Headers = False`
        
5. Stored data in a **DataTable variable**.
    
6. Wrote output to Excel with **Write Range Workbook**.
    

### 📌 Key Takeaways:

- CV can **scroll and extract full tables** from webpages or apps.
    
- Works smoothly in **remote/virtual desktops**.
    
- Allows efficient automation of large data extractions with no selectors.
    

---

## 🧾 Combined Summary:

|Tool|Purpose|Key Benefit|
|---|---|---|
|**CV Recorder**|Automatically generate CV workflows|Faster development|
|**CV Extract Table**|Extract tables with auto-scroll|Handles long or hidden content|

---
## ✅ **AI Computer Vision Best Practices**

These tips help improve reliability and performance, especially in **Virtual Desktop Infrastructure (VDI)** environments like Citrix, RDP, or VMware.

### 🧩 Best Practices:

1. **Select specific UI areas**  
    Focus on **smaller, clear regions** when working with repeated or similar labels. This avoids ambiguity in field selection.
    
2. **Ensure a stable RDC**  
    A **stable Remote Desktop Connection** avoids disconnections, timeouts, and rendering issues.
    
3. **Secure credential management**  
    Use **Windows Credential Manager** and **Get Secure Credential** activity to protect sensitive data.
    
4. **Add the API Key in Project Settings**  
    Paste your **Computer Vision API key** in **Project Settings > Computer Vision > ApiKey**.
    
5. **Global API Key behavior**  
    Editing the `ApiKey` in one **CV Screen Scope** changes it for **all scopes** in that workflow.
    

---

## 🛠️ **Practice: Building a Full CV Automation Project**

**⏱ Duration: 20 min**  
**Use Case:** Automate ACME website — log in, extract & filter WI5 items with “Open” status, generate hash codes, update items, and log out.

---

### 🧩 **Project Structure:**

- `ACME_Open.xaml` → **Login and open Work Items**
    
- `ACME_Process.xaml` → **Extract and process WI5 items**
    
- `ACME_Close.xaml` → **Logout and close browser**
    

---

### 🔓 ACME_Open.xaml – Login Sequence

1. Create new process and rename default sequence to **login**.
    
2. Add **CV Screen Scope** for `https://acme-test.uipath.com/login`.
    
3. Use **Windows Credential Manager** to store credentials.
    
4. Use `Get Secure Credential` to retrieve username & password.
    
5. Use:
    
    - `CV Type Into` for Email + Password fields
        
    - `CV Check` for "Remember Me"
        
    - `CV Click` for Login and Work Items
        

---

### ⚙️ ACME_Process.xaml – Process WI5 Items

1. Add `CV Screen Scope` for **Work Items page**.
    
2. Use `CV Extract Table` to capture the list.
    
3. Use `Filter Data Table` for:
    
    - Type = **WI5**
        
    - Status = **Open**
        
4. Use `For Each Row` to loop through items:
    
    - `CV Click` to open each item.
        

#### 🔧 Sub-Workflows for Each Item:

|Workflow|Purpose|
|---|---|
|`ACME_GetWorkItemDetails.xaml`|Extract Client ID, Name, Country using `CV Get Text`|
|`ACME_GetHashCode.xaml`|Generate SHA-1 hash using `Invoke Code`|
|`ACME_UpdateWorkItem.xaml`|Update comment field, change status to “Completed”|

##### ➕ Extra Config in `ACME_UpdateWorkItem.xaml`:

- `CV Type Into` → comment with hash (uses `in_Comment` argument)
    
- `CV Dropdown Select` → set to "Completed"
    
- `CV Click` → Submit changes + close
    

---

### 🔚 ACME_Close.xaml – Close Sequence

1. Add `CV Screen Scope` and indicate dashboard.
    
2. Use `CV Click` to:
    
    - Click **Logout**
        
    - Close **browser window**
        

---

## 🧾 Final Summary:

|Section|Key Focus|
|---|---|
|**Best Practices**|UI targeting, secure credentials, API Key configuration|
|**ACME Project**|Full end-to-end automation using **Computer Vision activities** for login, table extraction, processing, and logout|

✅ **Computer Vision in UiPath** enables automation even in challenging environments (like Citrix), and this project ties together all key concepts in practice.

---
