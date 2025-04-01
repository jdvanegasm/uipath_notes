## 🔁 **Triggers Overview**  
Triggers control when and how automations run. They are defined at the folder level, allowing fine-grained access. Three types:

1. Time Triggers
    
    - Schedule jobs at fixed times (e.g. every Wed 8:00 AM).
        
    - Useful for periodic tasks.
        
2. Queue Triggers
    
    - Start jobs based on new queue items.
        
    - Ideal for unpredictable workloads or processes with SLAs.
        
    - Configurable parameters:
        
        - Minimum items to trigger
            
        - Max concurrent jobs
            
        - Jobs per N new items
            
    - Example: 3 jobs processing items as they enter the queue to meet performance targets.
        
3. Event Triggers
    
    - Start automation based on external events (e.g. new Outlook email).
        
    - Created via Integration Service or Studio.
        
    - Requires configured connections (e.g. Outlook, Google Drive).
        
    - Set filters (e.g. process only “Paychecks” folder emails).
        
    - Events are added to Orchestrator from Package Requirements.
        

## ⚙️ **Connected Triggers (Studio ↔ Orchestrator)**

- When a project with trigger activities is published to Orchestrator:
    
    - It creates a process in the personal workspace.
        
    - Trigger configuration (e.g. interval, queue name) is auto-imported.
        
    - Reduces manual work for admins and misconfigurations.
        

Steps to Create a Connected Trigger:

1. In Studio: Add Time Trigger or Queue Trigger activity.
    
2. In Orchestrator:
    
    - Go to Automations > Triggers.
        
    - Create trigger (values from Studio pre-filled).
        
    - Adjust or edit if needed.
        

## 📊 **SLA (Service Level Agreements)**

- Define the maximum time allowed for processing a queue item (e.g. 2 days).
    
- Risk SLA: Preemptive indicator when nearing SLA breach.
    
- Helps ensure robots meet processing targets even under unexpected load.
    
- Avoids late discovery of SLA violations.
    

Enable SLA:

1. Go to Queue → Edit.
    
2. Enable SLA and define duration.
    
3. Save/Update.
    

## 📘 **Guided Practice Highlights**

- Dispatcher process populates the queue.
    
- Performer process consumes items from queue.
    
- Create a Queue Trigger:
    
    - Name it.
        
    - Select Performer process.
        
    - Job priority: Inherited.
        
    - Runtime: Production.
        
    - Job termination: Stop or Kill.
        
    - Enable alerts for incomplete jobs.
        
- Enable SLA from the Queue Edit page.
    
- Monitor job execution & SLA compliance in:
    
    - Automations > Jobs
        
    - Monitoring > SLA (Avg. Handling Time)
        

### 📝 **Summary Recap**

- Triggers automate job execution (time, queue, event).
    
- SLAs ensure items are processed within agreed time.
    
- Connected triggers simplify dev-admin collaboration.
    
- SLA breaches can be costly—configure risk SLAs to detect issues early.

---
# 📊 Monitoring and Alerts – Technical Summary

🎯 Goal: Learn how to monitor and prioritize job execution, interpret alerts, and navigate the built-in dashboards in Orchestrator.

---

## ✅ Learning Objectives

By the end of this lesson, you will be able to:

1. Explain how job priorities influence execution order.
    
2. Differentiate between the 4 Orchestrator monitoring dashboards.
    
3. Select the right dashboard for specific system metrics or alerts.
    

---

## 🔍 What is Monitoring?

Monitoring in UiPath Orchestrator provides real-time visibility into the system’s performance and health. You can monitor four key entities:

- 🖥️ **Machines** – robot utilization & status
    
- ⚙️ **Processes** – current executions, job performance
    
- 📦 **Queues** – items processed, failed, successful
    
- ⏱ **Queues SLA** – how well queue items meet SLA targets
    

Accessible via: `Monitoring` tab in Orchestrator (folder-level dashboards).

---

## 🚨 What are Alerts?

Alerts are real-time system notifications that inform you of system events. They can be:

- Severity-based:
    
    - ℹ️ Info – low importance, no impact
        
    - ✅ Success – completed as expected
        
    - ⚠️ Warn – may interrupt execution
        
    - ❌ Error – prevents successful execution
        
    - 💥 Fatal – force-stops execution
        
- Triggered by:
    
    - Robots, Triggers, Actions, Queue Items, etc.
        
    - Alerts are visible via the Notification Panel or the Alerts Page.
        

---

## 🤖 What are Jobs?

A job = the execution instance of a process on a robot.  
Types of jobs:

- 🎛 **Attended** – started manually via Assistant or CLI
    
- 🕹 **Unattended** – triggered automatically from Orchestrator
    

💡 Job execution modes:

- Start jobs immediately (via Jobs tab)
    
- Schedule jobs with Triggers
    

🔁 Jobs can be:

- Stopped
    
- Killed
    
- Resumed
    
- Restarted
    

---

## ⚖️ What is Job Priority?

Job Priority determines which jobs take precedence when robot capacity is limited.

Priority levels:

- Low
    
- Medium (Default)
    
- High
    

📌 Priority can be configured:

- When deploying the process
    
- While creating/editing a job or trigger
    

---

## 🧪 Guided Practice Overview

You’ll use the following workflows:

- ACME Demo (Medium Priority)
    
- Performer (Medium Priority)
    
- RaiseAlert (High Priority)
    

### Steps:

1. Open UiPath Studio and load `RaiseAlert.zip`.
    
2. Login to [cloud.uipath.com](https://cloud.uipath.com/) and access your Orchestrator tenant.
    
3. Set Job Priorities:
    
    - ACME Demo → Medium
        
    - Performer → Medium
        
    - Raise Alert → High
        
4. Run `Raise Alert` from Studio.
    
5. Set input argument `in_Severity = Info`, start job.
    
6. In Automations, run job again with `in_Severity = Warning`.
    
7. Navigate to Alerts Page:
    
    - Apply filters by severity/time.
        
    - Observe alerts: Info, Warn, Error, Fatal.
        
8. Review Job History:
    
    - Successful
        
    - Faulted
        
    - Stopped
        
9. Navigate to Monitoring Dashboards:
    
    - 🖥 Machines
        
    - ⚙ Processes
        
    - 📦 Queues
        
    - ⏱ Queues SLA
        

---

## 📌 Lesson Recap

- 🧭 Monitoring: Track real-time metrics across Machines, Queues, Processes & SLAs.
    
- ⚠ Alerts: Notifications on events; help identify and troubleshoot issues quickly.
    
- 🧩 Job Priorities: Define which job runs first under limited capacity.
    
- 📊 Dashboards: Centralized views help admins track system health efficiently.
    

---
# Best Practices – Technical Summary

**Duration**: ~10 min  
**Objective**: Apply best practices to ensure smooth, efficient, and reliable use of UiPath Orchestrator.

---

## ✅ Learning Outcome

By the end of this lesson, you will be able to:

- Identify key best practices that improve orchestration reliability and maintainability.
    

---

## 🔧 Recommended Best Practices

### 1. Trigger Time Zone = Tenant Time Zone

- When using non-working days or calendar restrictions, the trigger time zone must match the tenant’s time zone.
    
- Location: `Tenant > Settings > General`
    
- A tenant without an explicit time zone inherits the host's time zone.
    
- Mismatches lead to incorrect or skipped schedule executions.
    

---

### 2. Runtime License Configuration

- Only **Unattended runtimes** are valid for job execution.
    
- Make sure the machine template has the required **runtime licenses** allocated.
    
- Missing licenses = failed job assignments.
    

---

### 3. Handle Default 30-Minute Check Wisely

- Orchestrator checks for resource availability every 30 minutes.
    
- During off-hours, jobs with unprocessed items may block resources.
    
- To prevent this:
    
    - Ensure queues are emptied before end-of-day.
        
    - Or use only **fully unattended** processes that don't require user input.
        

---

### 4. Keep Automations Clean

To improve performance, readability, and reduce errors:

- Close all target applications (browsers, desktop apps) after use.
    
- Remove:
    
    - Unreferenced variables
        
    - Temporary `Write Line` outputs
        
    - Disabled code
        
    - Unused or unnecessary containers
        

---

### 5. RDP Session Management

- Always sign out from **RDP sessions** on Robot machines before executing jobs.
    
- Left-open sessions can interfere with execution or cause conflicts.
    

---

### 6. Enable Proactive Monitoring and Alerts

- Leverage Orchestrator's built-in monitoring and alerting tools.
    
- Detect and resolve issues early—before they impact production.
    

---

## 📌 Summary

Applying these best practices ensures:

- Better job scheduling accuracy
    
- Optimal use of robot resources
    
- Clean, maintainable workflows
    
- Fewer execution failures or delays
    
- Improved system observability and troubleshooting
    

---
# Solutions Management – Technical Summary

**Objective**: Understand what a solution is in UiPath and how Solutions Management simplifies deployment and lifecycle management across environments.

---

## ✅ Learning Outcomes

By the end of this lesson, you will be able to:

1. Describe what a solution is in the UiPath ecosystem.
    
2. Explain why centralized Solutions Management is critical for scaling automation projects.
    

---

## 📦 What is a Solution?

A **solution** in UiPath is a bundle of components that together automate a business use case.

A solution can include:

- One or more Studio workflows/processes
    
- Apps
    
- Assets
    
- Queues
    
- Storage Buckets
    
- Data Service entities
    
- Other resources required for execution
    

📝 A solution can range from simple (single workflow) to complex (multi-component, multi-environment business automations).

---

## 🚀 Why Solutions Management Matters

### Pre-Solutions Management:

- Developers managed each component (e.g., workflows, queues, credentials) independently.
    
- Manual handling of dependencies between environments (Dev, Test, Prod).
    
- Synchronization was time-consuming and error-prone.
    

### With Solutions Management:

- Centralized control over the full lifecycle of an automation solution.
    
- Enables bundling of all required components into a single **solution package**.
    
- Simplifies:
    
    - Cross-environment deployment
        
    - Version control
        
    - Dependency management
        
    - Environment-specific configuration
        

---

## 📁 What is a Solution Package?

A **solution package** is a deployable bundle containing:

- All relevant components and configurations
    
- Metadata required for transfer and deployment
    
- Environment-specific parameters that can be adapted during deployment
    

Ideal for moving solutions from Development → Testing → Production seamlessly.

---

## 🔐 Access Requirements

To use Solutions Management, ensure:

- You have a UiPath Automation Cloud account.
    
- You have access to **Automation Ops**.
    
- You are assigned one of the default Orchestrator roles:
    
    - Solutions Contributor
        
    - Solutions Administrator
        

---

## 🧭 Accessing the Solutions Management UI

1. Open the Automation Cloud App Launcher.
    
2. Navigate to **Automation Ops**.
    
3. In the left-side menu, select **Solutions Management**.
    

---

## 📌 Summary

Solutions Management in UiPath:

- Enables centralized, scalable automation project management
    
- Reduces deployment errors and increases maintainability
    
- Supports easy packaging and transport across environments
    
- Requires Automation Cloud and proper roles for access
    

---
# Introduction to Automation Cloud Robots – Technical Summary

**Objective**: Understand what Automation Cloud Robots are and distinguish between their two types.

---

## ✅ Learning Outcomes

By the end of this lesson, you will be able to:

1. Explain the role and benefits of Automation Cloud Robots (ACRs).
    
2. Identify and differentiate between the two types of ACRs: Serverless and VM.
    

---

## 🤖 What are Automation Cloud Robots?

**Automation Cloud Robots (ACRs)** are SaaS-based robots hosted in the UiPath Automation Cloud platform.  
They allow you to execute unattended jobs without setting up or maintaining any local infrastructure.

- Hosted and fully managed by UiPath
    
- Can be provisioned, scaled, and managed directly from the Automation Cloud
    
- Ideal for users who want quick setup and scalability without infrastructure overhead
    

---

## 🧱 Background Context

UiPath supports multiple robot deployment types:

- Standard Robots (on-prem)
    
- Cloud-Orchestrated Robots (using VM or hybrid setup)
    
- **Automation Cloud Robots (SaaS-native solution)**
    

---

## 🧩 Types of Automation Cloud Robots

1. **Serverless Cloud Robots**
    
    - Run background and cross-platform jobs
        
    - No infrastructure management required
        
    - Best for fast, scalable task execution
        
2. **VM Cloud Robots**
    
    - Full Windows virtual machines
        
    - Customizable environment
        
    - Suitable for jobs requiring a desktop experience or UI interaction
        

---

## 💡 Additional Note

- **Test Automation Cloud Robots** are available for both Serverless and VM types
    
- They support running test cases and non-production workloads at reduced cost
    

---

## 📌 Summary

- ACRs let you run unattended jobs from the cloud—no infrastructure setup needed
    
- Two types:
    
    - Serverless (lightweight, background jobs)
        
    - VM (customizable, desktop-style execution)
        
- All provisioning, scaling, and maintenance are managed by UiPath
    
- Test ACRs are available for efficient testing workflows
    

---

![[Pasted image 20250331091436.png]]