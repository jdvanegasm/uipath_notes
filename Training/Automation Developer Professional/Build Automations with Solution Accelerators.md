## 🧩 **Solution Accelerators – Technical Summary**

### 🔹 **Definition**

**Solution Accelerators** are pre-built **modular automation frameworks** provided by UiPath.  
They:

- Are tailored to **common, high-impact use cases**
    
- Contain templates, reusable components, models, and connectors
    
- Follow **UiPath best practices**
    
- Are **meant to be customized**, not plug-and-play
    

> ✅ They act as a starting point to **design, develop, and deploy** automations faster.

---

### 🔹 **Scope**

- Target **Level 3 Business Use Cases** (complex, end-to-end business processes)
    
- Example: In **Finance**, a common use case is **Two-Way Match Invoice Processing**
    

---

### 📥 **How to Access Solution Accelerators**

1. Go to **[UiPath Marketplace](https://marketplace.uipath.com/)**
    
2. Click the **Solution Accelerators** tab
    
3. Select based on your business need
    
4. Click **Download Package** and choose one of the two methods:
    
    - **Manual Deployment** – config files and components for manual upload
        
    - **Solutions Management Deployment** – optimized for **Automation Ops** users:
        
        - Download Solutions Management Assets (.zip)
            
        - Download Templates (Studio templates and libraries)
            

---

### 📦 **Typical Package Contents**

|Category|Contents|Notes|
|---|---|---|
|**📄 Documentation**|Tech Docs, Deployment Guides, Design Specs, Best Practices|Helps understand and implement the solution|
|**🚀 Deployment**|Config files (.xlsx), schemas (.json), Solutions Management packages|Used for setting up queues, assets, data schemas|
|**📁 Processes**|Studio Projects (Dispatcher, Performer, Finalizer, etc.)|Main logic to be customized|
|**📚 Libraries**|Application UI reusables, custom components|Generic and app-specific logic|

> Some content like Forms AI/Document Understanding models only appears in accelerators using those features.

---

### ✅ **Key Benefits**

- 🔧 **Reduces design time by up to 70%**
    
- 🕵️‍♂️ Reduces discovery time — curated by UiPath **industry experts**
    
- 🏗️ Follows **best practices** and modular architecture
    
- 🔄 Easy to **swap applications** due to reusable components
    
- 🎯 Helps you **avoid starting from scratch**
    
- 🔐 Marketplace content is **certified for security, quality, and compliance**
    

---

### 🧠 Lesson Recap

- Solution Accelerators speed up automation development using **pre-built, modular frameworks**
    
- Available on **UiPath Marketplace**
    
- Contain: **Documentation, Deployment files, Processes, Libraries**
    
- Must be **customized** to fit your organization’s use case
    

---
![[Pasted image 20250331233943.png]]
![[Pasted image 20250331233958.png]]

---
## 🚀 **How to Use Solution Accelerators Effectively in Projects**

### 🎯 **Lesson Objectives**

- Adopt **Solution Accelerators** in implementation projects
    
- Understand how to **develop a process** using one
    

---

## 📊 **Where Accelerators Fit in the Project Lifecycle**

|**Stage**|**Accelerator Usage**|
|---|---|
|**Kickoff**|No accelerator usage at this stage|
|**Business Case & Validation**|No accelerator usage at this stage|
|**Process Analysis**|No accelerator usage at this stage|
|**Solution Design**|🔍 _Check UiPath Marketplace_ for relevant accelerators|

```
                            📄 *Review Technical Docs* (Overview, Architecture)
                            📝 Use diagrams & templates to **build SDD** (Solution Design Document)                                                  |
```

| **Development & Testing** | 🔧 _Set up Orchestrator Process Folder_  
📥 _Import schemas, assets, libraries_  
🧩 _Customize downloaded Solution Accelerator Projects_, filling in placeholders  
🧪 _Execute Technical Testing Plan_ | | **User Acceptance Testing** | No new accelerator actions—validate solution functionality | | **Deployment & Hypercare** | 🚀 Migrate final packages and components to **production Orchestrator** | | **Project Closure** | 📋 Confirm all deliverables and complete handover |

---

## 🧑‍💻 **Developer Workflow with Solution Accelerators**

To develop a process using a Solution Accelerator:

1. **Review Documentation:**
    
    - High Level Solution Design (HLSD)
        
    - Detailed Solution Diagram
        
    - Framework-specific notes (e.g., REFramework)
        
2. **Understand the Framework Used:**
    
    - Typically REFramework or similar modular architecture
        
3. **Set Up the Environment:**
    
    - 🗂️ Create process folder in **Orchestrator**
        
    - ⚙️ Import:
        
        - **Schemas** (`.json`)
            
        - **Assets** (`.xlsx`, Orchestrator assets)
            
        - **Queues**
            
        - **Libraries**
            
        - **Projects**
            
4. **Customize Components:**
    
    - Modify templates
        
    - Add business-specific logic
        
    - Fill in placeholders from technical docs
        

---

## 📦 **Solution Accelerator Package – Key Components**

|**Category**|**Contents**|
|---|---|
|**Technical Documentation**|HLSD, Detailed Diagram, Best Practices|
|**Solutions Management Package**|Bundled components for Automation Ops (Assets, Queues, etc.)|
|**Assets & Queues**|Found in config and schema files (`.xlsx`, `.json`)|
|**Processes**|Dispatcher, Performer, Finalizer — ready-to-edit Studio projects|
|**Libraries**|Generic and app-specific reusable components|

---

## ✅ **Benefits Recap**

- **Accelerates design** via prebuilt diagrams and best practices
    
- **Simplifies development** with ready-to-edit templates
    
- **Reduces errors and effort** with reusable components
    
- Encourages **structured automation delivery** across roles (PM, Architect, Dev)
    

---

![[Pasted image 20250331234056.png]]