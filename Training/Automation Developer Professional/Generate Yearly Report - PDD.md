**Project Overview**

- **Objective:** Automate the generation of a yearly report for vendors, aimed at speeding up processing, reducing manual effort, and increasing the reliability and overall performance of the Finance and Accounting department.
    

**Scope and Process Details**

- **Full Automation:** The process is fully in scope for RPA; all steps are expected to be automated.
    
- **Input & Output:**
    
    - **Input:** Vendor Tax ID
        
    - **Output:** A consolidated Excel file named “Yearly-Report-[Year]-[Tax ID].xlsx” and a unique Upload ID after submission.
        
- **Frequency and Volume:**
    
    - Scheduled to run yearly, typically in mid-January
        
    - Process approximately 7–15 vendors per day, with an average handling time of 15 minutes per vendor
        
    - Typically managed by a single FTE with no peak periods.
        

**Detailed Process Steps**

1. **Accessing the System:**
    
    - Open the ACME System 1 Web Application and log in using provided credentials (email and password).
        
    - Navigate to the Dashboard and then to the Work Items listing.
        
2. **Processing WI4 Activities:**
    
    - For each task of type WI4, perform the following sub-steps:
        
        - **Retrieve Vendor Tax ID:** Open the activity details to capture the Tax ID.
            
        - **Download Monthly Reports:** Go to the “Download Monthly Report” section, enter the Vendor Tax ID, and download all monthly reports for the previous year.
            
        - **Merge Reports:** Combine the downloaded monthly reports into a single Excel file following the naming convention “Yearly-Report-[Year]-[Tax ID].xlsx”.
            
        - **Upload Report:** Navigate to the “Upload Yearly Report” section, fill in the required fields (Vendor Tax ID, year, and select the file), and capture the unique Upload ID returned by the system.
            
        - **Update Work Item:** Return to the Work Item details and update the task status to “Completed”, including a comment with the Upload ID.
            

**Exception and Error Handling**

- **Missing Monthly Reports:** If one or more monthly reports are missing (typically 1–3 per vendor), these months should be ignored.
    
- **Login Failures:** If the login fails due to an incorrect email or password, the process should handle the exception, for instance by sending an alert to [exceptions@acme-test.com](mailto:exceptions@acme-test.com).
    
- **No WI4 Tasks:** If no task of type WI4 exists, the process should halt accordingly.
    
- **Application Issues:** In case of the web application not loading or being unresponsive, the robot should retry a couple of times and then close and restart the application if needed.
    
- **General Exception Handling:** Any unexpected errors should trigger an email notification (with the original error message and screenshot) to [exceptions@acme-test.com](mailto:exceptions@acme-test.com).

**Development Environment and Tools**

- **Technologies:**
    
    - **UiPath RPA:** The process will be developed using UiPath.
        
    - **ACME System 1:** Web-based application accessed via a web browser.
        
    - **Microsoft Excel:** Used for merging and formatting the monthly reports into the yearly report file.
        
- **Credentials Management:** Use Windows Credential Manager or UiPath Orchestrator Assets to securely store login details.
    
- **Testing and Deployment:** Ensure that the development and testing environments mirror production exactly. After development, the process will be deployed and monitored via UiPath 

**Documentation and Approval Flow**

- **Design Document History:** The document includes a detailed history of changes, with approvals by Business Analysts, UiPath BA, and Dev/RPA Solution Architects.
    
- **Post-Deployment:** The appendix of the document will be filled out after process completion, covering automation overview, robot type (unattended), human intervention level, logging details, and lessons learned.

# REF Reminder
## Architecture and Execution of Dispatcher and Performer in UiPath

### Project Separation

- **Separate Projects:**  
    The best practice is to keep the **Dispatcher** and **Performer** as independent projects. This separation enhances scalability, maintenance, and clear responsibility management.
    
- **Dispatcher Project:**
    
    - **Responsibility:** Extracts data from the source (e.g., databases, Excel files) and adds work items to a Queue in Orchestrator.
        
    - **Output:** Populates the Queue with tasks that the Performer will later process.
        
- **Performer Project:**
    
    - **Responsibility:** Retrieves work items from the Queue (using activities like _Get Transaction Item_) and processes each item. This includes performing actions like logging in, downloading reports, merging files, and uploading the final report.
        
    - **Output:** Completes each task by updating the Queue with the status and any relevant output (e.g., an Upload ID).
        

### Orchestrator Setup and Integration

- **Queue Configuration:**  
    A central Queue (e.g., "VendorReportsQueue") is created in Orchestrator. Both projects must reference the same Queue name in their configuration files (typically in a config.xlsx).
    
- **Assets and Credentials:**  
    Use Orchestrator Assets to manage sensitive information such as credentials, file paths, and system configurations. This ensures both projects have access to consistent settings and security measures.
    
- **Permissions and Roles:**  
    Ensure that the robots assigned to the Dispatcher and Performer have the necessary permissions to add and retrieve items from the Queue. The environment settings must be consistent across both projects.
    

### Execution Flow

- **Sequential Unattended Execution:**  
    Although the Dispatcher and Performer are separate projects, they can be orchestrated to run sequentially:
    
    - **Step 1:** The Dispatcher job runs at a scheduled time or via a trigger, populating the Queue with work items.
        
    - **Step 2:** Once the Queue is populated, the Performer job, either scheduled immediately afterward or continuously monitoring the Queue, begins processing the items.
        
- **Triggering and Chaining:**  
    You can set up triggers in Orchestrator to automatically start the Performer once the Dispatcher completes its job. This chaining ensures a seamless unattended process.
    

### Best Practices Summary

- **Maintain Separation:** Keeping the Dispatcher and Performer as separate projects preserves clarity and modularity.
    
- **Centralized Configuration:** Use the same Queue and shared Assets in Orchestrator to ensure both projects work with the same settings.
    
- **Unattended Operation:** Schedule both processes as unattended jobs in Orchestrator. The Dispatcher populates the Queue, and the Performer consumes and processes the items automatically.
    
- **Scalability and Flexibility:** This approach allows you to add multiple Performer robots to consume the Queue concurrently if the volume increases, improving load distribution and processing speed.