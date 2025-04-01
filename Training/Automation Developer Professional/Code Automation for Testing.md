### Overview

- **Coded Automations** let you create automation solutions using code rather than a visual design interface.
    
- They are integrated within Studio via a built-in code editor, enabling you to develop automations in a familiar coding environment.
    

---

### Core Concepts

- **Definition:**  
    Coded automations are analogous to standard (low-code) automations but leverage the flexibility and extensibility of coding. They allow you to call activity packages as services and use activities as APIs, enabling seamless integration with external systems, databases, and APIs.
    
- **Programming Language:**  
    The code is written in **C#**, chosen for its popularity and strong integration with the .NET ecosystem. Future support for additional languages is possible.
    

---

### Key Benefits

- **Enhanced Productivity:**  
    Developers leverage existing coding skills, speeding up the creation and maintenance of automations.
    
- **Complexity Management:**  
    Custom logic, exception handling, and reusable functions can be implemented to manage intricate automation scenarios.
    
- **Hybrid Automation:**  
    Coded and low-code automations can coexist in the same project, facilitating collaboration between developers and business users.
    
- **Improved Performance:**  
    Fine-tuned code can optimize workflows, making execution faster—especially for tasks that can be parallelized.
    
- **Readability & Maintainability:**  
    Well-structured, documented code enhances clarity and simplifies collaborative maintenance.
    

---

### Types of Coded Automations

- **Coded Workflows:**
    
    - Serve as the entry points for automations (similar to sequences in low-code).
        
    - Can be set as the main entry (akin to Main.xaml) and invoked using the standard "Invoke Workflow File" activity.
        
- **Coded Test Cases:**
    
    - Equivalent to traditional test cases, enabling testing within the coded automation framework.
        
- **Code Source Files:**
    
    - These contain source code (e.g., utility functions or portions of business logic) and act similarly to non-entry point XAML files.
        

---

### Integration & Use Cases

- **Seamless Integration:**  
    Coded automations fully integrate with existing low-code XAML-based automations, supporting the use of custom classes and data types.
    
- **Performance-Critical Scenarios:**  
    Ideal for:
    
    - Designing test automations (e.g., Selenium, Appium, Playwright) where a low learning curve and improved review process are essential.
        
    - Complex operations or libraries that require performance optimization.
        
    - Scenarios where standard activities are insufficient (e.g., vendor-specific serialization using NuGet packages).
        
- **Collaboration:**  
    Allows cross-team collaboration—enabling experienced developers to handle complex logic while business users contribute with low-code designs in the same project.
    

---
## 🔧 **Coded Automation – Structure**

### ✅ **Namespaces**

- Automatically generated using the Studio **project name**.
    
    - Example: Project “My project” → Namespace: `Myproject`
        
- If placed inside folders:
    
    - Example: Folder “place” → Namespace: `Myproject.place`
        
- **Tip:** Leave namespaces as-is unless necessary to change.
    

---

### ✅ **Base Class**

- All coded workflows/test cases inherit from `CodedWorkflow` (from `UiPath.CodedWorkflows` package).
    
- This class provides interfaces for working with activity packages (a.k.a. services).
    
- Package is **included automatically** with packages like `UiPath.System.Activities v23.8.0-preview` or higher.
    

---

### ✅ **Entry Point: `Execute()` Method**

- Acts as the **starting point** of the automation (like `Main.xaml`).
    
- Attributed as `[Workflow]` or `[TestCase]` (depending on its purpose).
    
- You can **rename** the method as long as it remains properly attributed.
    
- Supports **input/output arguments**, equivalent to In/Out/InOut in low-code.
    

---

### ✅ **File Compatibility**

- Coded automations are supported in:
    
    - **Windows Projects**
        
    - **Cross-platform Projects**
        

---

## 📦 **Using Activity Packages**

- Activity packages (like `System.Activities`) are used as **services** in coded automations.
    
- Activities within them expose **APIs** that can be called from C#.
    
- Example:
    
    ```csharp
    var result = UiPath.System.Activities.SomeService.DoSomething();
    ```
    

---

## 🧠 **Best Practices for Coded Automations**

### ✅ **Coded Workflow Inheritance**

- Enables **modularity** and **code reuse** through class inheritance.
    
- Changes in a **parent class** apply automatically to **child classes**.
    
- Helps avoid code duplication and makes updates easier.
    
- Example:
    
    - `Login.cs` inherits from `BaseLogin.cs` where common functionality is centralized.
        

---

### ✅ **Tips & Tricks**

- Avoid unnecessary modification of **auto-generated namespaces**.
    
- Encapsulate **reusable actions inside helper classes**.
    
- Clean up **unused `using` directives** to reduce clutter.
    
- For **multi-source data retrieval**, keep each phase clearly separated to avoid mixing data from different sources.
    

---

## 📌 **Lesson Summary**

Coded automations use a structured C#-based model featuring:

- **Namespaces**
    
- **Helper Classes**
    
- **Entry Points (`Execute()` methods)**
    

By following best practices (inheritance, modular code, separation of concerns), you ensure that your automations are:

- Efficient
    
- Maintainable
    
- Scalable
    

Use this structure and practice guide to design better-coded automations and prepare for more complex scenarios.

---
