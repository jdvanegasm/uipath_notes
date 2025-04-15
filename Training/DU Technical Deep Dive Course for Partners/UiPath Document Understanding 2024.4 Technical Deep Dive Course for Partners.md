
This summary captures the essential updates and technical details from the 2024.4 version of UiPath Document Understanding. Use these notes as a quick refresher before referring to the full documentation.

---

## Course Overview

- **Target Audience:** Technical professionals interested in the latest DU features.
        
- **Key Learning Objectives:**
    
    - Leverage **Active Learning** in the Modern Experience.
        
    - Utilize **Generative Validation** in IntelligentOCR and DU Activities.
        
    - Apply **Classification Validation** for DU Activities (cross-platform).
        
    - Use **Validator Notes** in IntelligentOCR.
        
    - Experiment with **Extraction, Classification & Validation** using DU Cloud APIs.
        
    - Understand updates on **OOTB models**, **ML & OCR**, and other DU enhancements.
        

---

## New Features & Updates

### Main Document Understanding Features

1. **Modern Projects with Active Learning**
    
2. **Validator Notes in IntelligentOCR**
    
3. **Language Expansion OCR**
    
4. **Arabic Language Support**
    

### Feature Updates

1. **Updates on OOTB Models**
    
2. **Classification Validation for DU Activities (Cross-platform)**
    
3. **Generative Validation in IntelligentOCR & DU Activities**
    
4. **Generative Extraction, Classification & Validation via APIs**
    

---

## Active Learning (Modern Experience)

### Overview

- **Definition:** An AI-powered, iterative model training approach that minimizes data requirements.
    
- **Availability:** Currently available in Automation Cloud.
    
- **Purpose:** Reduce manual annotation efforts and training time (up to 80% faster).
    

### Benefits

- **No Coding/ML Skills Needed:** Simplifies model training for non-experts.
    
- **Rapid Model Training:** Reduces training time from a week to about a day.
    
- **Human-AI Collaboration:** Provides guidance on model optimization.
    
- **Instant Evaluation:** Built-in analytics deliver real-time performance insights.
    
- **Simplified Process:** Eliminates the need for exporting datasets, pipeline creation, and manual ML package management.
    

### Core Workflow

1. **Project Creation:** Start a DU project to handle multiple document types (e.g., Invoices and Receipts).
    
2. **Auto-Classification:** Upload documents and let the system automatically classify them.
    
3. **Schema Setup:** Create or import a schema for document annotation.
    
4. **Annotation Process:** Benefit from pre-annotated documents, requiring only review and correction.
    
5. **Automated Training:** The model begins training automatically after annotating a minimal number of documents (e.g., 5).
    
6. **Continuous Improvement:** Model re-trains automatically as more documents are annotated.
    
7. **Recommendations & Metrics:** Receive easy-to-understand recommendations and real-time performance metrics.
    
8. **Deployment:** Use the Publish tab to deploy project versions and access integration snippets for Studio Desktop, Studio Web, or via API.
    
9. **Monitoring & Insights:** Track AI Unit consumption, time saved, cost estimates, and detailed document processing insights.
    
10. **New Licensing Model:** Charges apply only for skill consumption—not for underlying infrastructure or training.
    

---

## Conclusion

The 2024.4 release of UiPath Document Understanding introduces a modern, streamlined approach with Active Learning at its core. This update significantly reduces the barrier to entry for AI model training by automating key processes, providing real-time analytics, and simplifying deployment. These enhancements are designed to boost efficiency and model performance, making Document Understanding more accessible and effective for technical users.

Use these notes as a quick technical refresher before diving deeper into the full documentation when executing tasks related to DU projects.

---
# Technical Summary: Document Understanding – Getting Started & Build

## 1. Getting Started

### Learning Objectives

- **Project Creation:** Learn to create a Modern Document Understanding project.
    
- **User Interface:** Understand the new Modern Projects UI.
    
- **Permissions:** Grant and manage project user permissions.
    

### Key Components

#### A. Creating a Modern Project

- **Project Options:**
    
    - **Classic:** Full-featured model-building; suitable for multi-tenant projects and data/model export.
        
    - **Modern:** Guided model-building experience with streamlined processes; note current limitations (refer to official docs for details).
        
- **OCR Settings:** Option to select specific OCR configurations during project creation.
    

#### B. Understanding the User Interface

- **Modern Experience:**
    
    - A redesigned UI tailored for guided project creation.
        
    - Provides an intuitive layout for managing and monitoring project tasks.
        

#### C. Granting Project Permissions

- **Manage Access:**
    
    - Use the "Manage access" button (top right or bottom left, depending on overall access vs. specific project access) to configure roles.
        
- **Default Roles:**
    
    - **DU Administrator:** Service-level administrator with full permissions.
        
    - **DU Developer:** Project-level administrator with full control within a project.
        
    - **DU Model Trainer:** Permission to modify document type settings, upload or delete documents.
        
    - **DU Viewer:** Read-only access.
        
- **Role Inheritance:**
    
    - Organization roles are automatically mapped to Document Understanding roles (e.g., Tenant Administrators become DU Administrators).
        
    - Removal of automatically assigned roles is not currently supported.
        

### Lesson Summary

- You can now create Modern Projects with guided steps.
    
- Organization roles are automatically mapped to DU roles, simplifying access management.
    

---

## 2. Build Pillar
### Learning Objectives

- **Document Management:** Upload, classify, and manage project files.
    
- **Annotation:** Annotate documents and validate pre-labels.
    
- **Model Improvement:** Leverage recommendations to enhance model performance.
    

### Process Overview

#### A. Uploading Documents

- **Initiation:**
    
    - Open your project and upload sample documents.
        
    - Choose between manual document type creation (for sorted documents) or using automatic classification.
        
- **Automatic Classification:**
    
    - Uploaded documents are digitized, classified, and pre-annotated automatically.
        
    - Review and adjust the classification if needed via dropdown options.
        
- **Dataset Recommendations:**
    
    - The system suggests the number of additional samples needed based on model performance.
        

#### B. Annotating Documents

- **Annotation Interface:**
    
    - Start annotating by selecting the document type or via the options menu.
        
- **Pre-Annotations:**
    
    - Documents are pre-annotated using a combination of generative and specialized models based on an existing schema.
        
    - **Review Process:**
        
        - Confirm correct pre-annotations (using hotkeys or confirmation options).
            
        - For incorrect annotations:
            
            - Adjust by selecting the correct text.
                
            - Mark missing fields when necessary.
                
- **Status Indicators:**
    
    - **Confirmed Documents:** Marked with a green shield.
        
    - **Partially Confirmed:** Indicated by an empty shield, meaning further annotation is required.
        

#### C. Document Type & Field Settings

- **Document Type Settings:**
    
    - Modify settings such as base model, number of layouts, and language support via the Document Type Manager.
        
    - **Note:** Changing the base model is recommended for advanced users.
        
- **Editing Field Settings:**
    
    - Configure field properties such as name, content type (String, Number, Date, Phone, ID Number), and assign shortcut keys.
        
    - Adjust advanced settings based on the selected content type.
        

#### D. Project and Model Score

- **Performance Metrics:**
    
    - The overall project score reflects both classifier and extractor performance.
        
    - Individual document type scores and model ratings (Poor to Excellent) help visualize model performance.
        
- **Requirements:**
    
    - At least 10 documents are needed to generate a project score.
        
    - Each document type requires a minimum of 10 documents.
        

#### E. Best Practices

- **Data Requirements:**
    
    - Upload a minimum of 30 representative documents per document type.
        
- **Validation:**
    
    - Ensure to validate all classifications and pre-annotations.
        
    - Mark fields as ‘missing’ where applicable.
        
- **OCR Usage:**
    
    - Use default OCR for Latin, Hebrew, or Arabic.
        
    - Use Extended Languages OCR for Chinese, Japanese, Korean, etc.
        
- **Follow Recommendations:**
    
    - Adhere to system-provided recommendations for optimizing model training and performance.
        

### Lesson Summary

- The Build process covers the end-to-end workflow from document upload and automatic classification to detailed annotation and configuration.
    
- It includes managing document types, editing fields, and monitoring project performance through detailed scores.
    
- Best practices and system recommendations are essential for creating effective and high-performing models.
    

---

# Technical Summary: Measure & Publish

This summary consolidates the key information from the "Measure" and "Publish" lessons in Document Understanding, providing a quick reference guide for assessing model performance and deploying projects.

---

## Measure

### Learning Objectives

- Interpret the overall **Project Score**.
    
- Analyze the **Classification Score**.
    
- Evaluate the **Extraction Scores**.
    

### Key Components

#### 1. Project Score

- **Overview:**
    
    - Combines classifier and extractor performance across all document types.
        
    - Visible at the top-right corner of the platform.
        
- **Model Rating:**
    
    - Ranges from 0 to 100, classified as Poor (0-49), Average (50-69), Good (70-89), Excellent (90-100).
        
- **Usage:**
    
    - Helps decide when to stop training based on project needs.
        

#### 2. Classification Score

- **Overview:**
    
    - Assesses the performance of the classification model and dataset quality.
        
- **Tabs Provided:**
    
    - **Factors:** Offers recommendations on dataset size and model performance improvements.
        
    - **Metrics:** Displays key statistics per document type, including:
        
        - **Train:** Number of documents used for training.
            
        - **Test:** Number of documents used for evaluation.
            
        - **Precision:** Accuracy of positive predictions.
            
        - **Accuracy:** Overall correct predictions.
            
        - **Recall:** Proportion of true positives identified.
            
        - **F1 Score:** Harmonic mean of precision and recall.
            
- **Note:** Available only when more than one document type is created.
    

#### 3. Extraction Score

- **Overview:**
    
    - Evaluates extractor performance and dataset quality per document type.
        
- **Detailed Views:**
    
    - **Factors:** Provides actionable recommendations (e.g., increase dataset size or improve field accuracy).
        
    - **Dataset:** Offers feedback on training data, such as the number of pages and labeled content.
        
    - **Metrics:** Lists detailed performance stats, including:
        
        - **Training Pages:** Total pages used for training.
            
        - **Rating:** Similar to the project score rating.
            
        - **Accuracy:** Correct prediction frequency.
            
- **Navigation:**
    
    - Access detailed insights by clicking on individual document types, which directs you to the Annotate view.
        

#### 4. Best Practices

- **Document Count:**
    
    - Minimum of 10 documents required for a project score and per document type score.
        
- **Training Cessation:**
    
    - Stop training when the desired performance is reached, based on project objectives.
        
- **Follow Recommendations:**
    
    - Utilize system recommendations to optimize model performance.
        

---

## Publish

**Duration:** 10 min

### Learning Objectives

- Create a **Project Version**.
    
- Deploy a **Project Version**.
    
- Integrate with **Studio Web/Desktop** or via **APIs** for automation.
    

### Key Components

#### 1. Creating a Project Version

- **Purpose:**
    
    - Freeze the current state of the classifier and extractor models.
        
    - Provides a stable snapshot that can be consumed in workflows.
        
- **Steps:**
    
    - Navigate to the **Publish** section.
        
    - Click **Create a project version**.
        
    - Enter a name (and optionally a description).
        
    - Choose which models to include and the deployment type.
        
- **Note:**
    
    - Classification is automatically enabled when multiple document types are present.
        

#### 2. Deploying a Project Version

- **Deployment Stages:**
    
    - **Training:** Models are actively training (transitory state).
        
    - **Trained:** Models have finished training.
        
    - **Undeployed:** Models are idle and not consuming resources; not available for workflows.
        
    - **Deployed:** Models are active, consuming hardware resources, and accessible in workflows.
        
- **Action:**
    
    - Toggle the deployment status to move from undeployed to deployed.
        

#### 3. Automating Your Process

- **Integration Options:**
    
    - **Studio Web/Desktop:**
        
        - Click **Open Studio Web** or **Open Studio Desktop** to generate workflows.
            
    - **API Integration:**
        
        - Use the **Integrate via API** button to obtain code snippets in your preferred programming language.
            
        - The snippet includes necessary configurations like Platform URL, Organization Name, Tenant Name, and Project ID.
            
- **Outcome:**
    
    - Use the deployed project version in automations by referencing it in your workflows.
        

#### 4. Best Practices

- **Version Consistency:**
    
    - Ensure published versions referenced in automations are updated as needed.
        
- **Resource Selection:**
    
    - Choose the appropriate resources (classifier, document types) when creating a project version.
        

---
# Technical Summary: Monitor

This summary provides an overview of the "Monitor" pillar in Document Understanding. It covers how to track automation performance, review processed documents, and drill down into document-specific details, helping you maintain and optimize your DU projects.

---

## Learning Objectives

- **Access and interpret the Project Performance Dashboard (Preview).**
    
- **Review the list of Processed Documents.**
    
- **Obtain detailed insights about individual document processing.**
    

---

## 1. Project Performance (Preview)

- **Dashboard Overview:**
    
    - Displays key performance metrics such as estimated time saved, number of processed documents, and time spent on extraction.
        
    - Presented as an Insights dashboard, requiring UiPath Insights to be enabled (no active license needed).
        
- **Data Ingestion:**
    
    - **Orchestrator Data:** Updated approximately every 20 minutes.
        
    - **Robot Logs:** Typically ingested every 10–15 minutes, but may take up to 2 hours to reflect due to latency.
        
- **Key Business Metrics:**
    
    - **Estimated Time Saved:** Calculated as the difference between manual processing time and actual validation time.
        
    - **Estimated Cost:** Based on the consumed AI Units.
        
    - **Processed Documents Trend:** Monthly breakdown by consumer type (APIs, RPA processes, etc.).
        
    - **Validation Metrics:** Includes validation time per document, per validator, and average handling time.
        
    - **Straight-through vs. Manual Processing:** Compares fully automated document processing to those that required human intervention.
        
- **Additional Metrics:**
    
    - **Consumption Metrics:** Overview and detailed view of AI Units consumption, including for model hosting.
        
    - **Runtime Metrics:** Analysis of document types requiring validation, field corrections, extraction accuracy, and classification confusion.
        
- **Filtering and Scheduling:**
    
    - Offers extensive filtering options (process name, period, handling time, etc.) and the ability to schedule email delivery of the dashboard data.
        

---

## 2. Processed Documents

- **Overview:**
    
    - Provides a list of documents processed via APIs or UiPath.DocumentUnderstanding.Activities.
        
    - Ensures that any document that has been digitized or processed appears in the list.
        
- **Key Information Displayed:**
    
    - **File Name:** Clickable to access detailed document view.
        
    - **Document Type:** Categorization based on processing rules.
        
    - **Consumer:** Identifies whether the document was processed via API or an RPA process.
        
    - **Modified Date:** Last operation timestamp.
        
    - **Validator:** User who performed the validation, if applicable.
        
    - **AI Units Consumption:** Number of AI Units used for processing.
        
- **Search Capability:**
    
    - Users can quickly search for specific documents by file name.
        

---

## 3. Document Details

- **Detailed View Metrics:**
    
    - **General Information:** Total AI Units consumed, creation and completion times, consumer details, file type, etc.
        
    - **Classification Data:** Includes project version, pre- and post-validation document types, and confidence levels.
        
    - **Extraction Data:** Displays model used, extracted fields with predicted values, extraction and OCR confidence, and any post-validation modifications.
        
    - **Validation Details:** Lists task-specific information such as task name, type, assignee, status, creation/completion dates, idle and validation time, and modification details.
        
- **Purpose:**
    
    - Offers granular insights into each document’s processing lifecycle, enabling detailed analysis and troubleshooting.
        

---

## 4. Best Practices & Considerations

- **Data Ingestion Timings:**
    
    - Orchestrator data updates every 20 minutes.
        
    - Robot logs may take up to 2 hours to appear in Insights.
        
- **Metrics Variability:**
    
    - Consumption metrics can change, reflecting the dynamic nature of project usage.
        
- **RBAC Policies:**
    
    - **Full Access:** Document Understanding Administrator and Contributor roles.
        
    - **Limited Access:** Document Understanding Viewer (only dashboard access).
        
    - **No Monitor Access:** Document Understanding Data Labeler.
        
- **Monitoring Settings:**
    
    - Adjust data monitoring settings in the Tenant Profile if necessary.
        

---
# Technical Summary: Modern Projects – Consumption, Environment, and Limitations

## 1. New Consumption Model for Modern Projects

**Key Concept:**

- **Unified Charging:**
    
    - **Standard Operations:** Regardless of whether you perform digitization, classification, or extraction, **1 AI Unit per page** is charged.
        
    - **Generative Validation:**
        
        - When using generative validation, an **additional 1 AI Unit per page** is charged (total: 2 AI Units/page).
            

**Examples:**

- **OCR Only:** 1 AI Unit/page
    
- **OCR + Classification:** 1 AI Unit/page
    
- **OCR, Classification & Extraction:** 1 AI Unit/page
    
- **OCR, Classification, Extraction & Generative Validation:** 2 AI Units/page
    

**Additional Points:**

- **Model Training & Serving:** No AI units are charged for training or serving models.
    
- **Multiple Digitizations:** If the same document is digitized multiple times, each instance is charged separately.
    
- **Hybrid Use:**
    
    - When both Classic and Modern experiences are used in a project, each follows its own metering logic.
        

---

## 2. Training Modern Projects in Development vs. Production

**Current Approach & Recommendations:**

- **Traditional Practice:**
    
    - Development environments are used for testing and feature exploration.
        
    - Production environments are tightly controlled to protect live operations.
        
- **Challenges:**
    
    - Segregation can limit flexibility and lead to underutilization of resources.
        

**Modern Projects Strategy:**

- **Single-Project Usage:**
    
    - With proper Role-Based Access Control (RBAC), training and development can occur within the same project without needing separate environments.
        
- **Infrastructure & Model Training:**
    
    - **New Active Learning:**
        
        - Automated training triggers for a quicker feedback loop.
            
        - Faster training times due to optimized algorithms.
            
    - **Deployment Enhancements:**
        
        - Model deployments run on GPUs that scale automatically, eliminating manual replica configuration.
            
        - Models are loaded/unloaded as needed to optimize resource usage.
            
- **Performance Benchmark:**
    
    - Each account can process up to **10,000 pages per hour** (scalable if required).
        

---

## 3. Current Limitations, Limits & Quotas

**Limitations of Modern Projects:**

- Not yet at parity with Classic Projects. Missing features include:
    
    - Consuming projects across different tenants or organizations.
        
    - Moving projects or datasets between tenants.
        
    - Support for Windows-based IntelligentOCR activities.
        
    - Document splitting and auto-fine-tuning.
        
    - Tags for project versions and document batches.
        
    - Business Rules implementation.
        

**Key Limits & Quotas:**

- **File Formats & Image Sizes:**
    
    - **Supported Formats:** PNG, JPG/JPEG, PDF, TIF/TIFF
        
    - **Image Dimensions:**
        
        - Minimum: 50 x 50px
            
        - Maximum: 10,000 x 10,000px
            
- **Document & Dataset Limits:**
    
    - **Max Document Types:** 50 per project
        
    - **Max Pages per Document Type:** 3,000
        
    - **Max Pages per Document:** 500
        
    - **Max Pages per Project:** 30,000
        
    - **Pre-labeling Limit:** 30 pages per document
        
    - **Max Number of Fields:** 300
        
    - **Max Dataset Size:** 3.9 GB
        
- **Processing & API Constraints:**
    
    - **Parallel Requests:** Up to 10 processed concurrently
        
    - **OOTB Model Processing:** Up to 30 pages
        
    - **Generative Extraction/Classification:** Limited to 50 pages/document types in activities
        
    - **Digitization Limits:**
        
        - Max file size: 160 MB
            
        - Max pages per digitization document: 500
            
- **Throughput:**
    
    - **Processing Rate:** Up to 10,000 pages per hour (adjustable if needed)
        

**Usage Note:**

- These specifications ensure optimal utilization and performance for Document Understanding Modern Projects. Always refer to the official documentation for any updates or further details.
    

---

# Technical Summary: Choosing the Right Automation Type

This summary outlines the advantages and disadvantages of the three main ways to automate Document Understanding (DU) processes—**DocumentUnderstanding.Activities** package, **IntelligentOCR** activities package, and **Document Understanding Cloud APIs**—so you can select the best approach for your project.

---

## 1. DocumentUnderstanding.Activities Package

**Advantages**

- **Ease of Adoption**
    
    - Cloud-based, minimal setup required for using pre-trained models.
        
    - Available via the “Create Automation” option in DU and the Marketplace.
        
    - Suggested by Autopilot in workflows, reducing guesswork for developers.
        
- **Seamless Integration with Modern Projects**
    
    - Configuration is isolated in a DU project, promoting reusability.
        
    - Relies on DU Cloud APIs, benefiting from quicker bug fixes and updates.
        
- **Single In/Out Object**
    
    - Uses `Document Data` as the central data structure, simplifying data flow.
        

**Disadvantages**

- **Missing Advanced Features**
    
    - No splitting, business rules, or model fine-tuning within the activity set.
        
    - Limited support for multi-tenant or on-prem Automation Suite.
        
    - Does not support multiple extraction methods per document type in a single workflow.
        

---

## 2. IntelligentOCR Activities Package

**Advantages**

- **High Flexibility**
    
    - Allows mixing and matching multiple extraction and classification models (including fallback scenarios).
        
    - Runtime modifications to taxonomy, DOM, and `ExtractionResults` in the RPA code.
        
- **Extensible & Open Framework**
    
    - Users can bring their own classifier, extractor, or OCR engine by implementing custom interfaces.
        
    - The DU Process Template is based on the REFramework, providing a robust starting point.
        

**Disadvantages**

- **Complex Configuration**
    
    - Higher learning curve with multiple objects and activities.
        
    - Configuration is mostly stored in the workflow, reducing reusability (e.g., repeated passing of taxonomy, classification results, etc.).
        
    - More moving parts lead to heavier overhead when building or maintaining solutions.
        

---

## 3. Document Understanding Cloud APIs

**Advantages**

- **Technology-Agnostic**
    
    - Can be consumed from cloud or on-prem environments.
        
    - Works without requiring a UiPath Robot in some scenarios.
        
- **Flexible Integration**
    
    - Ideal for non-RPA contexts (e.g., integrating DU in a custom web application).
        
    - Offers programmatic access to DU features (digitization, classification, extraction, validation).
        

**Disadvantages**

- **Requires Programming Expertise**
    
    - Not as straightforward as using RPA activities in Studio.
        
    - Lacks built-in access to certain platform capabilities that come “out of the box” with UiPath activities.
        

---

## Key Takeaways

1. **DocumentUnderstanding.Activities** – Best for quick adoption, minimal setup, and a simplified in/out data structure, though it lacks certain advanced or highly customizable features.
    
2. **IntelligentOCR Activities** – Offers extensive customization and extensibility, but at the cost of increased complexity and heavier configuration overhead.
    
3. **DU Cloud APIs** – Ideal for advanced developers or non-RPA scenarios where direct programmatic access to DU features is desired. Requires more coding and lacks the convenience of Studio-based workflows.
    

Use these comparisons to select the most appropriate automation approach based on your project’s complexity, required flexibility, and team’s skill set.

---

# Technical Summary: Choosing the Right Project Type

## Learning Objectives

- **Understand Advantages & Disadvantages:**
    
    - Compare Modern, Classic, and AI Center-based projects.
        
- **Compatibility & Deployment:**
    
    - Identify which deployment methods and activities packages work with each project type.
        
    - Know available ML model versions for each option.
        

---

## Project Type Comparison

### Modern Projects

- **Advantages:**
    
    - ✅ **Faster model development time.**
        
    - ✅ **Guided model training experience.**
        
    - ✅ **No infrastructure costs.**
        
    - ✅ **No need for AI Center & manual deployment to multiple instances.**
        
- **Disadvantages:**
    
    - ❌ **Not available on Automation Suite.**
        
    - ❌ **No auto-fine-tuning support.**
        

### Classic Projects

- **Advantages:**
    
    - ✅ **Can be consumed from different tenants or organizations.**
        
    - ✅ **Models and datasets can be exported.**
        
- **Disadvantages:**
    
    - ❌ **Not available on Automation Suite.**
        
    - ❌ **No auto-fine-tuning support.**
        

### AI Center-Based Projects

- **Advantages:**
    
    - ✅ **Can be consumed from different tenants or organizations.**
        
    - ✅ **Models and datasets can be exported.**
        
    - ✅ **Auto-fine-tuning support.**
        
    - ✅ **Available on Automation Suite and Standalone deployments.**
        
- **Disadvantages:**
    
    - ❌ **Requires advanced knowledge.**
        
    - ❌ **Slower model development time.**
        
    - ❌ **No model training guidance.**
        

---

## Compatibility Overview

|**Project Type**|**Deployment Method**|**Activities Compatibility**|**DU Public APIs**|**Available ML Model Version**|
|---|---|---|---|---|
|**Modern Projects**|Automation Cloud|DocumentUnderstanding Activities|Yes|24.4|
|**Classic Projects**|Automation Cloud|IntelligentOCR & DocumentUnderstanding Activities|Yes|24.4 + all older versions|
|**AI Center-Based Projects**|Automation Cloud, Automation Suite, Standalone|IntelligentOCR Activities only|No|24.4 + all older versions|

---

## Key Takeaways

- **Modern Projects** offer the most advanced and user-friendly experience but may lack certain advanced features (e.g., auto-fine-tuning).
    
- **Classic Projects** provide multi-tenant consumption and export capabilities, making them suitable when such features are required.
    
- **AI Center-Based Projects** support auto-fine-tuning and are available in diverse deployment scenarios but demand deeper technical expertise and have slower development cycles.
    

---

# Technical Summary: Migrating Classic Projects to the Modern Experience

This summary details the process for migrating existing Classic Document Understanding projects to the Modern Experience, focusing on exporting datasets and importing them into Modern Projects.

---

## Learning Objectives

- **Dataset Migration:**
    
    - Understand how to export datasets from Classic projects.
        
    - Learn how to import these datasets (and schemas) into Modern Projects.
        

---

## Migration Steps

### 1. Exporting the Dataset from Classic Projects

- **Navigate & Open:**
    
    - Open the Classic project and select the desired document type.
        
- **Filter Documents:**
    
    - Use the “Training and Validation Set” filter to narrow down the dataset.
        
- **Export Process:**
    
    - Click **Export**, select **Current search results** (or other export types as needed), provide a job name, and then click **Download**.
        

**Export Types Overview:**

|**Export Type**|**Exported Data**|**Usage in Modern Project**|
|---|---|---|
|**Current Search Results**|Exports the filtered dataset using the training and validation filter.|Training documents train the model; validation documents are used to measure model performance.|
|**All Labeled**|Exports all annotated documents (Train, Validation, Evaluation).|Training uses Train set; Validation uses Validation set; Evaluation set is ignored.|
|**All**|Exports all annotated and unannotated documents.|Training uses Training set; Validation uses Validation set; unannotated documents are pre-annotated as unconfirmed.|

### 2. Importing the Dataset into Modern Projects

- **Create Document Type:**
    
    - In your Modern project, select **Add Document Type** and create a new custom document type.
        
- **Upload Dataset:**
    
    - Use the **Upload** option to import the ZIP file exported from the Classic project.
        
- **Processing:**
    
    - Once the upload is complete, all documents will be marked as "Confirmed" (if annotated) and model training will be automatically triggered.
        

### 3. Importing Schemas

- **Schema Import Process:**
    
    - Create a custom document type in the **Build** section.
        
    - Import the ZIP file containing the schema.
        
- **Important Note:**
    
    - Schema import works only if no schema exists; if one is already defined, the import will fail.
        

---

## Key Takeaways

- Migrating to the Modern Experience involves exporting datasets (and schemas) from Classic projects and importing them into a Modern Project.
    
- Ensure that you select the correct export type (preferably "Train and Validation") to maintain data consistency for training and evaluation.
    
- Schema imports require a custom document type with no pre-existing schema.
    

---

# Technical Summary: OOTB Models Updates & Language Expansion OCR

## 1. Updates on OOTB Models

### New OOTB Models (Preview)

- **1040 Schedule C**
    
- **1040 Schedule D**
    
- **1040 Schedule E**
    
- **UB04**
    
- **941X**
    
- **709**
    
- **3949a**
    
- **9465**
    
- **Invoices Hebrew**
    

### Performance Improvements

- **Turkish (TUR):**
    
    - Improved accuracy for characters with diacritics (e.g., Ç, ç, Ğ, ğ, I, ı, İ, i, Ş, ş, Ö, ö, Ü, ü).
        
- **Eastern-Arabic Numerals:**
    
    - Enhanced accuracy for numerals (٠, ١, ٢, ٣, ٤, ٥, ٦, ٧, ٨, ٩).
        

---

## 2. Language Expansion OCR

### What It Is

- **Extended Language Support:**
    
    - Supports over 200 languages including Chinese, Japanese, Korean, Thai, Vietnamese, major Indian languages, Cyrillic, Greek, and right-to-left languages (Arabic, Hebrew, Persian).
        
- **Enhanced Digitization:**
    
    - Delivers superior performance for diverse languages compared to the default Document OCR.
        

### How to Use It in Studio

- **Installation:**
    
    - Install the **IntelligentOCR package version 6.18.0-preview**.
        
- **Implementation Steps:**
    
    - Search for **Extended Languages OCR** in the Activities pane.
        
    - Drag and drop it into the **Digitize Document** activity.
        
    - Run your DU workflow to test the digitization process.
        
    - The endpoint and API key are automatically configured in Project Settings.
        

### How to Use for Document Annotation

- **Project Settings:**
    
    - In both Classic and Modern projects, click **Advanced Options** when creating a project to select the Extended Languages OCR.
        
- **Within AI Center:**
    
    - Available in the Document Manager for digitizing documents.
        

### Current Limitation

- **Re-digitization Constraint:**
    
    - Once a document is imported into Document Manager/Document Type sessions, it cannot be re-digitized without losing annotation data. To re-digitize, you must export and reimport the document.
        
- **Automation Suite Availability:**
    
    - Not yet available on Automation Suite; no timeline provided.
        

---

# Technical Summary: Advanced DU Activities & API Capabilities

This summary consolidates key updates related to classification validation, generative validation, validator notes, and generative extraction & classification capabilities available through DU activities and public APIs.

---

## 1. Classification Validation for DU.Activities (Cross-platform)

### New Activities

- **Create Classification Validation Task:**
    
    - Initiates validation tasks in Action Center.
        
- **Create Classification Validation Task and Wait:**
    
    - Pauses workflow execution until the validation task is completed.
        
- **Wait for Classification Validation Task and Resume:**
    
    - Suspends the workflow until a specific document validation action is finished.
        

### Enhancements & Improvements

- **Orchestrator Storage Options:**
    
    - Additional settings allow you to specify a storage bucket for validation tasks. A default bucket can be created if none exists.
        
- **Timeout Property:**
    
    - Optional Timeout for both Extract Document Data and Classify Document activities to control execution duration.
        
- **Extractor Overrides:**
    
    - In the Extract Document Data activity, the selected extractor now overrides the document type (excluding generative models).
        
- **Multi-value Fields Handling:**
    
    - All values for multi-value fields are returned under `DocumentData.Data.FieldName.MultiValues`.
        
- **Document Data Object Updates:**
    
    - The **Name** property is replaced by **DisplayName** for custom models and **ID** for OOTB models.
        
    - Two new properties are added: **ID** and **DisplayName** sourced from the DU framework.
        

### Limitations

- **Insights Dashboards:**
    
    - Existing DU Insights dashboards (in preview) no longer report data from cross-platform DU.Activities workflows.
        
    - A new, separate Insights dashboard now tracks this data.
        

---

## 2. Generative Validation in IntelligentOCR & DU.Activities

### Core Concept

- **Generative Validation:**
    
    - Leverages both Generative AI and Specialized AI to cross-check and validate data extracted within the Data Extraction Scope activity.
        

### Key Benefits

- **Enhanced Accuracy:**
    
    - Cross-validation between generative and specialized models improves overall data extraction precision.
        
- **Improved Learning:**
    
    - Accelerates model improvement through generative feedback.
        
- **Flexibility:**
    
    - Applicable across various document types and languages.
        
- **Reduced Errors & Time Efficiency:**
    
    - Minimizes extraction errors while streamlining the validation process.
        

### Implementation Note

- **Package Integration:**
    
    - Installing the _UiPath.IntelligentOCR.Activities_ package automatically includes the _UiPath.DocumentUnderstanding.ML.Activities_ package.
        

---

## 3. Validator Notes in IntelligentOCR

### Feature Overview

- **Purpose:**
    
    - Validator Notes enhance collaboration between automated processes and human validators by providing contextual notes on each field.
        

### Functionality

- **Configurable Display:**
    
    - Depending on settings in Taxonomy Manager, notes can be:
        
        - Editable text fields,
            
        - Read-only text,
            
        - Or selectable options via radio buttons.
            
- **Impact on Processing:**
    
    - Notes are integrated into the new ExtractionResult object property, improving validation accuracy and communication during document processing.
        

---

## 4. Generative Extraction, Classification & Validation via APIs

### Generative Classification (Public Preview)

- **Capabilities:**
    
    - Uses advanced machine learning to classify documents through generative methods.
        
- **API Example:**
    
    - A POST call to the DU API endpoint enables document classification by providing document IDs and prompt details.
        
- **Response Data:**
    
    - Returns classification results including DocumentTypeId, confidence scores, and other metadata.
        

### Generative Extraction (Public Preview)

- **Capabilities:**
    
    - Applies generative AI for document field extraction, enhancing the precision of extraction tasks.
        
- **API Example:**
    
    - A POST call to the DU API endpoint processes extraction prompts (e.g., invoice number, date, total) and returns detailed field data with confidence scores.
        

---

## Summary

- **Classification Validation Activities** streamline the validation workflow by creating, waiting, and resuming tasks in Action Center with improved control over storage, timeouts, and data handling.
    
- **Generative Validation** boosts extraction accuracy by combining the strengths of generative and specialized AI, while package integration ensures seamless deployment.
    
- **Validator Notes** empower human validators with context-rich feedback, enhancing overall processing quality.
    
- **Generative Extraction & Classification via APIs** extend DU capabilities to advanced ML scenarios, available in public preview, enabling high-accuracy, programmatic processing for diverse document types.