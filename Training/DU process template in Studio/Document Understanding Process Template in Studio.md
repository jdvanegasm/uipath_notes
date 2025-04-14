## Overview

- **Purpose:**  
    Provides a best-practice, production-ready UiPath Studio project template for automating document processing. It is designed for both large-scale enterprise implementations and quick demo or proof-of-concept projects.
    
- **Key Update – IXP:**  
    The introduction of UiPath Intelligent Xtraction & Processing (IXP) enhances capabilities by handling unstructured and high-complexity documents while retaining core functionalities.
    

---

## Core Features & Design

- **Built-In Capabilities:**
    
    - **Logging & Exception Handling:**  
        Integrated mechanisms ensure robust error management.
        
    - **Retry Mechanisms:**  
        Automatically reattempt failed operations to increase reliability.
        
    - **Preconfigured Components:**  
        Includes a taxonomy of basic document types, a classifier for categorization, and extractors for data extraction.
        
- **Architecture Flexibility:**
    
    - Supports both attended and unattended modes (e.g., via UiPath Action Center).
        
    - Simplifies development, testing, deployment, debugging, and scaling.
        
- **Key Principle – Single Input File per Job:**  
    Each job is designed to process one file at a time. This approach simplifies error handling and resource management by avoiding batch processing.
    

---

## Integration in End-to-End Automation

- **Upstream Automation:**
    
    - Manages business logic prior to document processing.
        
    - Dispatches files to the Document Understanding process.
        
- **Document Understanding Process:**
    
    - Acts as the core processor performing classification and extraction.
        
    - Dispatches processed data to subsequent automation steps.
        
- **Downstream Automation:**
    
    - Consumes the extracted data to drive further business processes.
        

---

## Course Details & Learning Objectives

- **Course Requirements:**
    
    - Pass a knowledge check with a minimum score of 80%.
        
    - Complete a feedback survey upon module exit.
        
    - Total course duration: **3 hours**.
        
- **Key Learning Outcomes:**
    
    1. **Definition & Key Principle:**  
        Understand the Document Understanding template and its one-file-per-job approach.
        
    2. **Process Integration:**  
        Learn where the template fits within an end-to-end automation process.
        
    3. **Generic Processing Flow:**  
        Describe the logical flow of document processing.
        
    4. **Component Identification:**  
        Recognize key components and their specific roles.
        
    5. **Configuration:**  
        Configure the template for attended/unattended modes and implement custom success logic.
        
    6. **Handling Challenges:**  
        Address orchestration, queuing, locking mechanisms, and other limitations.
        
    7. **Real-Life Applications:**  
        Analyze case studies where the template was successfully implemented.
        
    8. **Architecture Overview:**  
        Explain the overall architecture of UiPath’s Document Understanding capabilities.
        
    9. **Licensing:**  
        Understand how licensing applies to different components involved in document processing.
        

---

## Key Technical Takeaways

- **Rapid Project Initiation:**  
    The template enables quick setup of new Document Understanding projects.
    
- **Versatile Architecture:**  
    Provides a common framework that easily adapts to various deployment scenarios (attended vs. unattended).
    
- **Robust, Production-Ready Design:**  
    Equipped with essential features for error handling, logging, and retries, making it ideal for real-world enterprise applications.
    
- **Modular Process Flow:**  
    The detailed, module-based process flow can be tailored—merging or omitting parts—to fit specific use cases.
    

![[Pasted image 20250412221207.png]]
![[Pasted image 20250412221200.png]]

# Architecture of the Document Understanding Process Template – Technical Summary

## Lesson Overview

This lesson provides an in-depth look at the architecture of the Document Understanding process template. It covers the components, configuration for attended or unattended modes, custom success logic for classification/extraction, built-in error handling, and integrated testing features.

---

## Learning Objectives

At the end of this lesson, you should be able to:

1. **Identify Components:**  
    Understand each workflow and its purpose within the process template.
    
2. **Configuration Modes:**  
    Set up the template for both attended and unattended implementations.
    
3. **Custom Success Logic:**  
    Enable and customize the business rules for classification and extraction validations.
    
4. **Error Handling:**  
    Explain how exceptions are managed within the main sequence and individual document processing.
    
5. **Testing Features:**  
    Utilize the built-in testing capabilities to automatically validate each step of the process.
    

---

## Key Architectural Components

### 1. Process Structure

- **Modular Workflows:**  
    The template is built from multiple integrated workflows, each addressing a specific part of the document processing lifecycle.   

### 2. Attended vs. Unattended Modes

- **Attended Mode:**
    
    - Use `Main-Attended.xaml` as the main workflow.
        
    - **Project Settings:**  
        Disable _Background Running_ and _Persistence Support_.
        
- **Unattended Mode:**
    
    - Use `Main-ActionCenter.xaml` as the main workflow.
        
    - **Project Settings:**  
        Enable _Persistence Support_ to facilitate long-running and background processes.
        

### 3. Custom Success Logic for Classification & Extraction

- **Validation Workflows:**  
    Custom workflows allow you to implement business rule validations after classification and extraction steps.
    
- **Business Rules Example:**
    
    - **Classification Validation:**  
        Use a flowchart to define conditions such as "Always use Action Center," handling multiple documents, and flagging low confidence levels.
        
    - **Invoice Post-Processing:**  
        Validate critical financial fields with specific business rules (e.g., mandatory fields, arithmetic checks on quantities, unit prices, and totals).
        

### 4. Error Handling

- **Global Exception Handling (Main Sequence):**
    
    - Capture and manage errors via a configured `ERR_AbortProcess` activity.
        
    - Customize handling for various exception types.
        
- **Document-Level Error Handling:**
    
    - Implement error handling within the Try/Catch blocks of individual document processing.
        
    - **Best Practice:**  
        Avoid rethrowing errors within the document processing loop to ensure that processing continues for subsequent documents.
        
    - **Custom Logic Example:**  
        Log error details, set error flags, and, if necessary, throw a summary error after processing all documents.
        

### 5. Built-in Testing Features

- **Automated Workflow Testing:**
    
    - Each step of the process (e.g., Digitize, Classify, etc.) has at least one automated test.
        
    - **Default Testing Data:**  
        Tests are based on the default input file saved in the Cache folder.
        
- **Batch Testing Utilities:**
    
    - Tools to facilitate batch testing during development, including data caching.
        
    - **Data Variation Support:**  
        Some tests can handle variations in input data, although not set up by default.
        

---

## Additional Resources

- **Official Documentation:**  
    [Document Understanding Process Studio Template](https://docs.uipath.com/)
    
- **Classification Validation:**  
    [Document Classification Validation Documentation](https://docs.uipath.com/)
    
- **UiPath Test Suite:**  
    [Test Suite Course](https://academy.uipath.com/)
    
- **RPA Testing with Studio:**  
    [RPA Testing Course](https://academy.uipath.com/)
    
- **User Guide:**  
    [Document Understanding Process Template User Guide on GitHub](https://github.com/)

---
# Known Limitations & Challenges of the Document Understanding Process Template

## Learning Objectives

By the end of this lesson, we should be able to:

1. **Orchestration Processes:**
    
    - Describe the limitations when using orchestration processes with the DU template.
        
2. **Queue Limitations:**
    
    - Understand the constraints related to Orchestrator queues.
        
3. **DU-Specific Challenges:**
    
    - Identify challenges arising from the document understanding project specifications.
        
4. **Architecture Restrictions:**
    
    - Explain restrictions in the solution architecture, including risks with the locking mechanism.
        

---

## 1. Limitations with Orchestration Processes

- **Persistence Points:**
    
    - Can only be placed in _Main.xaml_ (e.g., during Wait for Classification/Validation Action and Resume activities).
        
- **Supported Orchestrator Versions:**
    
    - Queue support for persistence is available only from Orchestrator version 2020.10.8 onward.
        
- **Loop Restrictions:**
    
    - Only the _Parallel For Each_ loop may contain persistence points.
        
- **Activity Restrictions:**
    
    - Avoid using Delay or Retry Scope activities in _Main.xaml_, as embedded Delays can suspend the process.
        
- **Resource Management:**
    
    - Robots in environments or modern folders must share or make resources available after a suspension.
        
    - Proper lock mechanisms are necessary when editing shared resources (e.g., while training the Intelligent Keyword Classifier).
        
- **Serialization:**
    
    - All variables in long-running activities must be serializable.
        
- **Suspension Point Limit:**
    
    - A single job can have up to 1000 suspension points.
        

---

## 2. Queue Limitations

- **Version Dependency:**
    
    - Queues for persistence activities are supported only in Orchestrator v2020.10.8 or later.
        
- **Abandonment Issue:**
    
    - In unsupported versions, if items wait for human validation longer than 24 hours, they are marked as Abandoned.
        

---

## 3. Challenges Specific to Document Understanding

- **Exception Handling:**
    
    - On application exceptions, only the failed step(s) should be retried instead of restarting the whole process (unlike the REFramework).
        
- **Input File Variability:**
    
    - A single input file may contain multiple documents of varying types.
        
    - Documents or files might need independent processing without waiting for other actions.
        
- **Exception Considerations:**
    
    - Exceptions within a file or document’s flow require careful handling.
        
- **Job Outcome:**
    
    - Even if a job fails, it does not delete or invalidate the actions created by that job.
        

---

## 4. Restrictions in the Solution Architecture

- **Single Input File per Job:**
    
    - The DU process template is designed to process one input file at a time—batch processing is not supported.
        
- **Dispatcher Requirement:**
    
    - A separate dispatcher mechanism is needed to trigger DU jobs.
        
- **Temporary Files:**
    
    - The template does not clean up its Temp folder (which stores split or downloaded files).
        
- **Locking Mechanism Concerns:**
    
    - **Purpose:**
        
        - Synchronizes updates to the learning (training) file among multiple robots.
            
    - **Mechanism:**
        
        - Uses _LockFile.xaml_ and _UnlockFile.xaml_ to create a copy of the learning file, update it, and then overwrite the original.
            
    - **Risk:**
        
        - If multiple robots update simultaneously, the last update may overwrite previous data, potentially causing data loss.
            

---

# Document Understanding Process Template in Action – Technical Summary

## Lesson Overview

This lesson demonstrates a real-life use case where the Document Understanding process template is applied to automate invoice processing for an Accounts Payable team. The focus is on showing how the template streamlines development and enhances reliability compared to a custom-built solution.

---

## Business Scenario Recap

- **Context:**  
    A large organization’s Accounts Payable team handles daily invoices from various vendors. These invoices are received via email, physical mail, or scanned images, and vary in layout (computer-generated vs. scanned).
    
- **Current Manual Process:**
    
    - Invoices are downloaded or scanned into a local drive.
        
    - Relevant information is manually extracted.
        
    - Data is then entered into the internal ERP system.
        
    - Processing each invoice takes around 15 minutes, making it time-consuming and error-prone.
        

---

## Architectural Approach

### Functional Separation Principle

The end-to-end automation is divided into three key workflows:

1. **Dispatcher:**
    
    - **Function:** Reads invoices from a shared drive and uploads them to an Orchestrator queue.
        
    - **Configuration:** Utilizes RE Framework principles (adapted to a linear process) with configuration parameters for source folder and destination queue.
        
2. **Performer 1 – Document Understanding Workflow:**
    
    - **Function:** Retrieves documents from the queue and processes each invoice using the Document Understanding template.
        
    - **Configuration Steps:**
        
        - Update configuration file settings (e.g., target file key, queue name).
            
        - Create necessary assets in Orchestrator.
            
        - Select the attended workflow for quick testing and demonstration.
            
3. **Performer 2 – ERP Integration:**
    
    - **Function:** Takes the extracted data and inputs it into the ERP application for further processing.
        

---

## Detailed Process Flow

### Initialization

- **Taxonomy Loading:**
    
    - The Taxonomy Manager loads the defined document types (e.g., invoice) and required extraction fields.
        
    - The configuration file is read to determine settings controlling flow execution, such as skipping training steps if not needed.
        

### Digitization

- **OCR Implementation:**
    
    - The digitization step is mandatory. For invoices, UiPath Document OCR is selected after comparing multiple OCR engines.
        
    - **Outputs:**
        
        - Document Object Model (DOM)
            
        - Document text
            
    - These outputs feed into subsequent classification and extraction processes.
        

### Classification

- **Classifier Configuration:**
    
    - Utilizes the Intelligent Keyword Classifier, which is capable of splitting documents if multiple invoices are found within a single file.
        
    - **Business Rule Validation:**
        
        - Classification results are validated using predefined business rules to decide whether manual verification is required.
            
        - If manual verification is needed, the present classification station is invoked.
            
- **Training Component:**
    
    - When manual verification occurs, the trained classifier scope captures the verified data to enhance future classification accuracy.
        

### Extraction

- **Data Extraction Scope:**
    
    - Implements a Machine Learning Extractor using an out-of-the-box invoice model from AI Center.
        
    - **Validation:**
        
        - Extracted data is subjected to a series of business rules.
            
        - Manual validation (present validation screen) is triggered if confidence levels fall below acceptable thresholds.
            
- **Training for Extractor:**
    
    - Similar to classification, verified extraction data is used to train the extractor via the trained extractor scope.
        
    - Training data is stored locally and later uploaded to AI Center.
        

### Export

- **Formatting and Export:**
    
    - Extracted and validated data is formatted into a tabular format.
        
    - An Excel file is generated containing structured data:
        
        - Regular fields on one sheet.
            
        - Detailed line items on another sheet.
            
    - This file serves as input for further processing in the ERP system.
        

---

## Demo & Supporting Artifacts

- **Live Demonstration:**
    
    - The attended workflow is executed, reading taxonomy, digitizing documents, classifying, extracting, and validating data.
        
    - Logs display each step, and the user is prompted to manually verify data when required.
        
    - Once verified, training data is captured and exported to an Excel file.
        
- **Resources Provided:**
    
    - **Sample Document:** _SampleDocument.pdf_
        
    - **Dispatcher Workflow Package:** _Dispatcher_Invoice_Processing.zip_
        
    - **Performer Workflow Package:** _Performer_DU_Invoice.zip_
        
    - **Best Practices Guide:** _BestPracticesGuide_DUPT.pdf_
        

---

## Summary

This lesson illustrates how the Document Understanding process template simplifies a real-world automation scenario by:

- **Streamlining the workflow:**  
    Dividing the process into clear, modular components (Dispatcher, Document Understanding, ERP integration).
    
- **Enhancing reliability:**  
    Through built-in mechanisms for digitization, classification, extraction, validation, and training.
    
- **Reducing manual effort:**  
    Automating repetitive tasks like data extraction and validation, while still enabling manual intervention when necessary.
    

This structured approach significantly cuts down processing time and improves the accuracy and scalability of invoice processing in enterprise environments.

---
# UiPath Document Understanding Architecture & Licensing – Technical Summary

## Lesson Overview

This lesson covers the overall architecture of the UiPath Document Understanding capability and explains the licensing mechanisms for its various components. It focuses on how the solution is deployed—whether in cloud, on-premises, or hybrid modes—and how licensing, including AI unit consumption, is managed.

---

## 1. Architecture of Document Understanding

### In Cloud

- **Using Public Services:**
    
    - **Deployment:**  
        All services are hosted in the UiPath cloud.
        
    - **ML Models:**  
        Available as public SaaS endpoints.
        
    - **Licensing:**  
        Licensing servers in the UiPath cloud track usage and consumption.
        
    - **Overview:**  
        A simplified public services architecture diagram illustrates this setup.
        
- **Using a Cloud Tenant:**
    
    - **Deployment:**  
        All services remain hosted in the UiPath cloud.
        
    - **ML Models:**  
        Deployed in cloud AI Center.
        
    - **Licensing:**  
        Consumption is tracked by UiPath cloud licensing servers.
        
    - **Overview:**  
        A diagram illustrates the cloud tenant architecture.
        

### On-Premises

- **Online Mode:**
    
    - **Deployment:**  
        Orchestrator and AI Center are deployed on-premises.
        
    - **ML Models:**  
        Deployed on-premises in AI Center.
        
    - **Licensing:**  
        Metering data is sent to UiPath cloud licensing servers.
        
    - **Key Point:**  
        This is the default, recommended on-premises installation—it is easier to install, manage, and update, with no customer data leaving the premises.
        
- **Air-Gapped Mode:**
    
    - **Deployment:**  
        Orchestrator and AI Center are on-premises.
        
    - **Licensing:**  
        Managed internally in the Orchestrator instance (requires v20.10 or later).
        
    - **Key Point:**  
        This mode is more challenging to install and update but ensures that no customer data leaves the premises.
        

### Hybrid Deployment

- **Hybrid Mode (for DU Models Only):**
    
    - **Configuration:**  
        Orchestrator and robots remain on-premises, while AI Center is hosted in the cloud.
        
    - **ML Models:**  
        Exposed as public endpoints from AI Center.
        
    - **Licensing:**  
        Usage is tracked by UiPath cloud licensing servers.
        

---

## 2. Licensing Overview

### Licensing Components

- **Automation Developer Licenses:**  
    Required to build automation projects in UiPath Studio.
    
- **Robot Licenses (Attended/Unattended):**  
    Necessary for running automations.
    
- **Enterprise/Trial Licenses for Automation Cloud/Automation Suite:**  
    Must include access to Document Understanding, AI Center, and Action Center third-party services.
    
- **AI Units:**  
    The licensing unit consumed by AI-driven capabilities such as document classification and extraction.
    

### AI Unit Licensing & Consumption

- **General Concept:**  
    AI Units are used when executing machine learning tasks (e.g., classification and extraction) and are sold in packages.
    
- **On-Premises:**
    
    - A typical machine-learning extractor consumes **1 AI unit per page**.
        
- **Cloud:**
    
    - **Unit Cost:**  
        1 AI unit per page for the ML Extractor.
        
    - **Additional Consideration:**  
        Approximately 20% extra AI units are recommended to cover compute charges, hosting, GPU-intensive training, and support for production/development environments.
        

### Pricing Details

#### Classification Pricing (Intelligent Keyword Classifier & ML Classifier)

- **Document Pages vs. AI Unit Consumption:**
    
    - 1–24 pages: 0 AI units
        
    - 25–49 pages: 1 AI unit
        
    - 50–74 pages: 2 AI units
        
    - 75–99 pages: 3 AI units
        
    - 100–124 pages: 4 AI units
        
    - 125+ pages: 5 AI units
        
- **Key Points:**
    
    - Most classification scenarios are free.
        
    - Classification charges are capped at **5 AI units per document**.
        
    - Classification fees are separate from extraction fees.
        
    - Document splitting does not incur additional charges.
        

#### Extraction Pricing

- **AI Unit Charge Per Document Page:**
    
    - **Form Extractor:** 0.2 AI units
        
    - **Intelligent Form Extractor:** 1 AI unit
        
    - **Forms AI:** 1 AI unit
        
    - **ML Extractor:** 1 AI unit
        
- **Recommendations:**
    
    - Most extraction operations cost **1 AI unit per page**.
        
    - Use classification/document splitting to minimize extraction charges.
        
    - “Predict” usage inside Document Manager is charged as an extraction call.
        

---

## Key Takeaways

- **Deployment Flexibility:**  
    Document Understanding is accessible in cloud (public services and cloud tenant), on-premises (online and air-gapped), and hybrid modes.
    
- **Licensing Management:**  
    Licensing for Document Understanding includes Developer, Robot, Enterprise licenses, and consumption of AI Units.
    
- **Cost Considerations:**  
    AI unit consumption varies between on-premises and cloud environments, with clear pricing structures for classification and extraction tasks.
    

---

## Additional Resources

- **AI Units – Official Documentation:**  
    [Learn more about AI Units here](https://docs.uipath.com/).
    

---

This technical summary provides a clear reference for understanding the architecture and licensing aspects of UiPath Document Understanding, serving as a quick guide for deployment, cost management, and strategic planning in enterprise automation projects.****
### **The architecture of the Document Understanding capability**

**In cloud Using public Services:**
![[Pasted image 20250413150136.png]]
**In Cloud using a Cloud tenant: **
![[Pasted image 20250413150204.png]]
**Onpremises Online:**
![[Pasted image 20250413150224.png]]
**On premises: air-gapped**
![[Pasted image 20250413150248.png]]

