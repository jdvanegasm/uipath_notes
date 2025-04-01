# 🎯 Trigger-Based Attended Automation Framework

### 🔍 What Is It?

The **Trigger-Based Attended Automation Framework** is a new way to build attended automations based on **application and user events**.

Instead of following a sequential flow, automations are designed to **react asynchronously** to events—like:

- A user clicking a button
    
- A UI element appearing on the screen
    

When such events occur, specific **XAML files** are triggered.

> 🧠 **Key advantage:** You can react to multiple triggers simultaneously (e.g. opening multiple forms, or responding to multiple instances of the same form).

---

### 💡 Why Is It Useful?

Traditional UiPath workflows are sequential. While they allow parallelism and isolated invocations, they still follow a linear logic.

In contrast, **attended automations** in dynamic environments (like contact centers) require **event-driven, reactive behavior**. This is where the trigger-based architecture shines.

Triggers should be treated as **first-class citizens**—both during **design (Studio)** and at **run-time (Robot)**.

> A **trigger = Event + Action**

- **Event**: Button click, text field value change, application state change
    
- **Action**: A specific XAML file to execute
    

---

### 🚀 Getting Started with the Template

You can access the new framework template via:

- **Studio:** `Start > Templates > Attended Automation Framework Template`
    
- **UiPath Marketplace**
    

---

# 🖱 UI Automation Triggers

**⏱ Duration: 10 minutes**

### ✅ Learning Objective

1. Use UI automation triggers effectively.
    

---

### 🔍 What Is It?

By using the **Application Event Trigger** activity as the first activity in a XAML file, developers can initiate workflows **when specific UI events occur**.

> ⚠️ For events to be captured, ensure `Run Local Triggers` is included in `Main.xaml`.

Each XAML triggered this way receives a `TriggerEventArgs` input, which includes a reference to the **UI Element** that triggered it.

You can block or allow event propagation with:

- `Click Event Trigger`
    
- `Keypress Event Trigger`  
    (Use `Block event = True` to prevent the event from reaching the target app.)
    

Replay blocked events using:

- `Replay User Event` activity with `TriggerEventArgs.Event`
    

---

# 🧾 Forms and Form Triggers

**⏱ Duration: 40 minutes**

### 🧱 What Are Forms?

Forms in UiPath are similar to workflows and come with their own **set of triggers**. They respond to:

- Being opened/closed/minimized
    
- Element value changes
    
- Button clicks
    

Create forms via:

> `Project Panel > Right-click > Add > Form`

---

### 💡 Why Are Forms Useful?

- **Open forms programmatically** using `Show Form` (with input arguments).
    
- **Control form behavior** with `Change Form Properties`.
    
- **Retrieve or set form data** using `Set Form Values` / `Get Form Values`.
    
- **Support multiple forms at once** using `Show Form` with "Continue Workflow Execution" enabled.
    
- **Add custom JavaScript** using `Run Form Script`.
    

> 🧠 Use a unique **Instance Name** (e.g. customer email) when displaying the same form multiple times for different use cases.

---

# 🧩 Common Trigger Functionalities

**⏱ Duration: 10 minutes**

### 💡 Why Is This Useful?

- Exit triggers gracefully using `Stop Local Triggers`.
    
- Schedule workflows using `Repeat Trigger`.
    
- Triggers can run:
    
    - **Concurrently**
        
    - **Sequentially**
        
    - **Once**
        

Use these options depending on whether your trigger is inside or outside a `Trigger Scope`.

---

# 💬 Callouts

**⏱ Duration: 15 minutes**

### 🔍 What Are Callouts?

With **UiPath 2023.4**, the `UiPath.Callouts.Activities` package integrates with the new trigger/forms infrastructure.

A **Callout** is a form rendered next to a **specific UI element** and follows that element’s position.

Use `Show Callout` to display it. This activity is **non-blocking**.

---

### 💡 Why Are Callouts Useful?

- **Attached to a target element** — will move with it.
    
- **Automatically hide/show** depending on app state.
    
- **Can be closed** with `Close Form`.
    
- **Contain input elements** that trigger events like a regular form.
    

---

### 🛠 How It Works

Each section includes hands-on examples to demonstrate:

- Trigger-based automation design
    
- UI automation trigger setup
    
- Form creation and interaction
    
- Callout usage and customization