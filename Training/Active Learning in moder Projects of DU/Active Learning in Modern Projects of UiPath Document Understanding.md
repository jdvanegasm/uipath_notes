**Course Overview:**

- **Target Audience:**  
    Technical users interested in the Active Learning feature in the 2024.4 version of UiPath Document Understanding.
    
- **Key Topics:**
    
    - Using Active Learning within the Modern Projects experience.
        
    - Creating and managing Modern Projects.
        
    - Leveraging AI for robust, self-improving models.
        
    - Performance analysis, project versioning, and monitoring.
        

---

## What is Active Learning?

- **Definition:**  
    Active Learning is an AI-powered, iterative training approach that minimizes the number of samples needed to train a machine learning model. It enables the model to query the user for annotations and continuously improve its performance.
    
- **Modern Experience:**  
    Available exclusively in Automation Cloud, Active Learning provides a unified interface for training, deploying, and monitoring Document Understanding projects.
    

---

## Benefits of Active Learning

- **No Coding Required:**  
    Users do not need advanced Machine Learning or coding skills.
    
- **Faster Model Training:**  
    Training time is reduced from a week to just a day (up to 80% faster).
    
- **Collaborative Optimization:**  
    Combines human expertise with AI recommendations for model optimization.
    
- **Instant Model Evaluation:**  
    Built-in performance analytics provide real-time feedback on model accuracy and effectiveness.
    
- **Simplified Workflow:**  
    Removes the need for manual tasks like dataset export, pipeline initiation, ML Package creation, and skill deployment.
    

---

## How Active Learning Works – The Process Flow

1. **Project Creation:**
    
    - Upload documents into a Modern Project.
        
    - Automatic classification into document types (e.g., Invoices, Receipts) using ML Classifiers.
        
2. **Schema and Annotation:**
    
    - Create or import a schema.
        
    - Pre-annotation of documents is performed automatically.
        
    - Annotators review and correct pre-annotations, reducing manual labeling effort.
        
3. **Model Training:**
    
    - Once a minimum threshold of annotations is met (e.g., 5 documents and 40 annotations), model training initiates automatically.
        
    - The model continues to re-train as more documents are annotated.
        
4. **Performance Measurement:**
    
    - The system provides real-time recommendations and metrics (e.g., AI Unit consumption, estimated time saved, cost, and detailed document processing breakdown).
        
    - Non-technical insights help guide model optimization.
        
5. **Publishing and Consumption:**
    
    - After reaching a satisfactory performance level, models are published.
        
    - Published skills can be consumed via Studio Desktop, Studio Web, or API integration.
        
    - New licensing model charges only on model consumption—not for underlying infrastructure or training.
        

---

## Key Takeaways

- **Interactive Model Training:**  
    Active Learning reduces the amount of data and time required to train robust models.
    
- **User-Friendly Interface:**  
    The Modern Experience provides an intuitive, guided process for building, measuring, publishing, and monitoring models.
    
- **Cost Efficiency:**  
    With the new licensing model, customers are charged only for skill consumption.
    
- **Continuous Improvement:**  
    The system automatically re-trains as more data is provided, ensuring continuous performance enhancement.
    

---

This summary encapsulates the technical and practical aspects of the Active Learning feature in UiPath Document Understanding, outlining its benefits, workflow, and impact on model training and deployment.
### **How the Active Learning Loop Works**
![[Pasted image 20250413184720.png]]

---
# Getting Started with Modern Projects in Document Understanding – Technical Summary

## Lesson Overview

This lesson introduces the new Modern Projects experience in UiPath Document Understanding. It covers how to create a Modern project, navigate the updated User Interface, and manage project permissions.

---

## Learning Objectives

By the end of this lesson, you will be able to:

1. **Create a Modern Document Understanding Project:**
    
    - Choose between the Classic and Modern project options.
        
    - Configure OCR settings during project creation.
        
2. **Understand the Modern Projects User Interface:**
    
    - Familiarize yourself with the guided, user-friendly UI.
        
    - Explore the various panels and navigation elements designed for an intuitive experience.
        
3. **Grant Project Permissions:**
    
    - Manage overall access and assign roles using the “Manage Access” functionality.
        
    - Understand the default Document Understanding roles and how organization roles are mapped:
        
        - **DU Administrator:** Full permissions for service-level administration.
            
        - **DU Developer:** Project-level administrator with full permissions.
            
        - **DU Model Trainer:** Can modify document type settings and manage documents.
            
        - **DU Viewer:** Read-only access.
            
    - Note: Organization roles (e.g., Tenant Administrators, Automation Developers, Automation Users) are automatically mapped to these DU roles, and manual adjustments to these mappings are not currently available.
        

---

## Key Points

- **Project Type Selection:**
    
    - **Classic:** A comprehensive model-building experience ideal for consuming projects from various tenants or exporting datasets and models.
        
    - **Modern:** A guided experience focused on simplicity and rapid deployment, with some limitations detailed in the documentation.
        
- **User Interface:**
    
    - Designed for ease of use, the Modern UI streamlines the project creation and management process.
        
    - Key elements include the project dashboard and dedicated access management sections.
        
- **Access Management:**
    
    - Use the “Manage Access” button (located in the upper right corner or bottom left of the project screen) to assign and review project permissions.
        
    - Default role mappings ensure that users with organization-level roles automatically receive corresponding DU permissions.
        

---

# Build Pillar in Active Learning – Technical Summary

## Lesson Overview

This lesson covers the "Build" pillar in Active Learning, focusing on the creation and refinement of machine learning models for Document Understanding. The process involves uploading documents, automatic classification, annotation, and leveraging recommendations to improve model performance.

---

## Learning Objectives

By the end of this lesson, you will be able to:

1. **Upload and Classify Documents:**
    
    - Add documents to your project using both manual and automatic methods.
        
    - Utilize automatic classification to pre-assign document types.
        
    - Adjust classifications if the automatic results are incorrect.
        
2. **Manage Project Files:**
    
    - Organize documents by document type.
        
    - Understand the process of batch uploads for different document types.
        
3. **Annotate Documents:**
    
    - Annotate documents to confirm or correct pre-annotations.
        
    - Handle various cases:
        
        - Pre-annotation is correct: simply confirm.
            
        - Pre-annotation is incorrect: select correct text and confirm.
            
        - Field is missing: mark as "missing."
            
        - No pre-annotation: annotate manually.
            
    - Use hotkeys and UI tools to speed up the confirmation process.
        
4. **Leverage Recommendations to Improve the Model:**
    
    - Follow the system's recommendations on the number of additional samples required.
        
    - Monitor and validate pre-labelled data.
        
    - Adjust document type settings (e.g., base model, number of layouts, languages) to tailor the model to your dataset.
        
    - Review project and model scores to measure performance and identify areas for improvement.
        

---

## Detailed Process Flow

### 1. Uploading Documents

- **Project Setup:**
    
    - Create a Modern Project and select the appropriate OCR settings.
        
    - Choose document type creation method:
        
        - **Sorted Upload:** Manually add document types and upload samples.
            
        - **Automatic Upload:** Drag and drop documents for automatic classification.
            
- **Automatic Classification:**
    
    - Review results by expanding each document type section.
        
    - Adjust the document type via a dropdown if the classification is incorrect.
        
    - Receive dataset recommendations based on model performance.
        

### 2. Annotating Documents

- **Pre-Annotation Process:**
    
    - Documents are automatically pre-annotated based on the schema defined for each document type.
        
    - Pre-annotations appear as underlines that can be confirmed or corrected.
        
- **Annotation Workflow:**
    
    - **Confirming Correct Pre-Annotations:**
        
        - Use hotkeys or UI options to validate underlined fields.
            
    - **Correcting Incorrect Pre-Annotations:**
        
        - Select and confirm the correct text for fields that were pre-annotated incorrectly.
            
    - **Handling Missing Annotations:**
        
        - Mark fields as missing using the provided options when the pre-annotation is not present.
            
    - **Status Indicators:**
        
        - Confirmed documents show a green shield.
            
        - Partially confirmed documents display an empty shield, indicating further annotation is required.
            

### 3. Document Type and Field Settings

- **Document Type Manager:**
    
    - Access settings by clicking the three-dot icon (⁝) next to the document name.
        
    - Adjust settings like:
        
        - **Base Model:** Select the most suitable model to reduce annotation work.
            
        - **Number of Layouts & Languages:** Influence dataset size recommendations.
            
- **Editing Field Settings:**
    
    - Modify field properties:
        
        - **Field Name**
            
        - **Content Type:** (String, Number, Date, Phone, ID Number)
            
        - **Shortcut Key**
            
        - **Advanced Settings:** Vary based on content type.
            
    - Add or remove fields to customize extraction based on your requirements.
        

### 4. Project and Model Score

- **Scoring Metrics:**
    
    - The overall project score is visible in the top-right corner.
        
    - Scores factor in classifier and extractor performance for each document type.
        
    - Detailed model scores are accessible via the Measure section.
        
    - Minimum sample requirements:
        
        - At least 10 documents per project and per document type are needed to generate scores.
            
- **Model Rating Scale:**
    
    - Poor (0–49)
        
    - Average (50–69)
        
    - Good (70–89)
        
    - Excellent (90–100)
        

### 5. Best Practices

- **Document Uploads:**
    
    - Upload at least 30 representative documents per document type.
        
- **Validation:**
    
    - Validate all classifications and pre-annotations.
        
    - Mark fields not present in documents as ‘missing’ instead of attempting to modify OCR outputs.
        
- **OCR Recommendations:**
    
    - Use the default UiPath Document OCR for Latin, Hebrew, or Arabic scripts.
        
    - Use Extended Languages OCR for Chinese, Japanese, Korean, etc.
        
- **Follow System Recommendations:**
    
    - Act on suggested actions to optimize model performance and efficiency.
        

---

## Summary

The Build pillar in Active Learning guides you through:

- **Uploading & Classifying:** Efficiently import and auto-classify documents.
    
- **Annotating:** Validate and correct pre-annotations to train your model.
    
- **Customization:** Adjust document type and field settings to suit your data.
    
- **Performance Monitoring:** Use project and model scores to track and improve model accuracy.
    
- **Best Practices:** Ensure quality by following recommended guidelines for document uploads and annotations.

---

# Measure Pillar in Active Learning – Technical Summary

## Lesson Overview

The Measure tab in Modern Projects provides detailed insights into the performance of your Document Understanding model. It helps you assess overall project health, evaluate classification and extraction performance, and receive actionable recommendations to optimize your dataset and training process.

---

## Learning Objectives

By the end of this lesson, you should be able to:

1. **Interpret the Project Score:**
    
    - Understand how the overall performance score is calculated.
        
    - Identify key metrics influencing the project score.
        
2. **Interpret the Classification Score:**
    
    - Analyze performance factors and metrics for the classification model.
        
    - Review recommendations and dataset statistics to enhance classification accuracy.
        
3. **Interpret the Extraction Scores:**
    
    - Assess performance for each document type’s extraction model.
        
    - Utilize provided metrics and recommendations to fine-tune extraction processes.
        

---

## Key Components of the Measure Tab

### 1. Project Score

- **Overall Performance:**
    
    - Combines both classification and extraction scores from all document types.
        
    - Located in the top-right corner of the platform.
        
- **Model Rating:**
    
    - Expressed as a score from 0 to 100.
        
    - Users determine when to stop training based on their specific project needs and desired model performance.
        

### 2. Classification Score

- **Performance Factors:**
    
    - Considers both the model performance and the quality/size of the training dataset.
        
- **Two Main Sections:**
    
    - **Factors:**
        
        - Provides recommendations on improving dataset size and model performance for each document type.
            
    - **Metrics:**
        
        - Displays key statistics including:
            
            - **Train:** Number of training documents.
                
            - **Test:** Number of evaluation documents.
                
            - **Precision:** Accuracy of positive predictions.
                
            - **Accuracy:** Overall correctness of predictions.
                
            - **Recall:** Ability to identify all true positives.
                
            - **F1 Score:** Harmonic mean of precision and recall.
                
- **Availability:**
    
    - The classification score becomes available once you have created more than one document type.
        

### 3. Extraction Score

- **Performance Evaluation by Document Type:**
    
    - Provides insights specific to each document type’s extraction process.
        
- **Three Main Tabs for Each Document Type:**
    
    - **Factors:**
        
        - Recommends actions based on dataset size (number of uploaded/annotated documents) and model performance (field accuracy).
            
        - Double-clicking recommendations navigates you to the corresponding training step in the Build pillar.
            
    - **Dataset:**
        
        - Shows details on the documents used for training, total imported pages, and labelled pages.
            
    - **Metrics:**
        
        - Includes field-level metrics such as:
            
            - **Training Pages:** Number of pages used for training.
                
            - **Rating:** Model performance (poor, average, good, excellent).
                
            - **Accuracy:** Percentage of correct predictions from the training pipeline.
                

### 4. Dataset Diagnostics and Management Bar

- **Dataset Diagnostics:**
    
    - Offers feedback for constructing effective datasets.
        
- **Management Bar:**
    
    - Indicates the status of your dataset and guides decisions on when to stop further training.
        

---

## Best Practices

- **Minimum Document Requirements:**
    
    - Upload at least 10 documents to generate a project score.
        
    - For a document type-specific score, a minimum of 10 documents under that type is required.
        
- **Training Cessation:**
    
    - Stop training when your model reaches the desired performance level, which varies by use case.
        
- **Actionable Recommendations:**
    
    - Follow system recommendations to improve dataset quality and model performance.
        

---

# Publish Pillar in Active Learning – Technical Summary

## Lesson Overview

The Publish phase is focused on creating and deploying new project versions that freeze the current state of your models. Once published and deployed, these models can be integrated into workflows via Studio Web, Studio Desktop, or APIs, allowing you to automate your document processing tasks.

---

## Learning Objectives

By the end of this lesson, you will be able to:

1. **Create a Project Version:**
    
    - Freeze the current state of your continuously trained models (Classifier and Extractor) into a stable snapshot.
        
2. **Deploy a Project Version:**
    
    - Transition the project version through various states—from training, to trained, to undeployed, and finally to deployed—making it available for automation.
        
3. **Start Automating Your Process:**
    
    - Consume the deployed project version in UiPath Studio (Web/Desktop) or via APIs to integrate Document Understanding into your automation workflows.
        

---

## Detailed Process Flow

### 1. Creating a Project Version

- **Snapshot Creation:**
    
    - A project version captures the current state of your models, ensuring consistent behavior when used in automation.
        
- **Steps to Create a Version:**
    
    - Navigate to the **Publish** section of your project.
        
    - Click **Create a project version**.
        
    - Enter a name and an optional description.
        
    - Select the models to include from the provided dropdown.
        
    - Choose the desired deployment type.
        
    - Click **Create** to start the process.
        
- **Model Training:**
    
    - Upon creation, training is automatically triggered on all uploaded data for the selected Classifier and Extractors. Training duration varies based on model type and dataset size.
        

### 2. Deploying a Project Version

- **Deployment States:**
    
    - **Training:** Models are actively being trained.
        
    - **Trained:** Training is complete, but models are idle.
        
    - **Undeployed:** Models are not consuming resources and cannot be referenced in workflows.
        
    - **Deployed:** Models are live, consuming hardware resources, and available for integration.
        
- **Deployment Action:**
    
    - Toggle the deployment status in the **Deployed** column to make a project version available for use.
        

### 3. Automating Your Process

- **Integration Options:**
    
    - **Studio Web/Desktop:**
        
        - Open the project version in Studio to generate a workflow that leverages ML Skills.
            
    - **APIs:**
        
        - Use the **Integrate via API** button to generate code snippets in your preferred programming language.
            
        - The generated snippet includes hardcoded values for Platform URL, Organization Name, Tenant Name, and Project ID.
            
        - Configure your App ID and App Secret, and then implement your process logic.
            
- **Best Practices:**
    
    - Each published version is referenced in your automation workflows. When updating your model, ensure that your automation references the latest project version.
        
    - Verify that the required resources (such as classifiers or document types) are correctly selected during project version creation.
        

---

## Summary

The Publish pillar enables you to:

- **Freeze Model State:**  
    Create project versions that capture the current performance of your models.
    
- **Deploy for Consumption:**  
    Move project versions through different states until they are deployed and ready to be integrated.
    
- **Integrate Seamlessly:**  
    Start automating processes by consuming the deployed project version via Studio Web, Studio Desktop, or APIs.
    

---

# Monitor Pillar in Active Learning – Technical Summary

## Lesson Overview

The Monitor phase provides comprehensive insights into the performance of your Document Understanding automations. It helps you evaluate key metrics, assess process efficiency, and identify areas for improvement using three main views:

- **Project Performance (Preview)**
    
- **Processed Documents**
    
- **Document Details**
    

---

## Learning Objectives

By the end of this lesson, you will be able to:

1. **Access and Interpret the Project Performance Dashboard:**
    
    - Understand high-level metrics such as estimated time saved, number of processed documents, and extraction processing times.
        
    - Use the Insights dashboard to visualize business performance metrics and process success.
        
2. **Access and Interpret the Processed Documents Section:**
    
    - View a list of all documents processed via APIs or Document Understanding activities.
        
    - Filter and search for specific documents using file name, document type, consumer details, and validation status.
        
3. **Obtain Details About the Processing of a Document:**
    
    - Drill down into the Document Details view to see metrics like total consumption, classification and extraction information, and validation details.
        
    - Review detailed performance metrics and timestamps to understand processing and validation durations.
        

---

## Key Components

### 1. Project Performance (Preview)

- **Dashboard Overview:**
    
    - Displays performance metrics (e.g., estimated time saved, number of processed documents, cost estimation in AI Units).
        
    - Requires UiPath Insights (data ingestion from Orchestrator and Robot logs).
        
- **Key Metrics Include:**
    
    - **Estimated Time Saved:** Calculated based on the number of documents processed minus validation time.
        
    - **Estimated Cost:** Based on AI Unit consumption.
        
    - **Processed Documents Trends:** Monthly processing volumes per consumer.
        
    - **Validation Metrics:** Total and per-validator validation times, straight-through processing vs. manual validations.
        
- **Filtering & Customization:**
    
    - Options include filtering by process name, time period, document handling time, and scheduling email delivery of dashboard data.
        

### 2. Processed Documents

- **Document List View:**
    
    - Shows processed documents with details such as file name, document type, consumer (API or RPA), modified date, validator, and AI Unit consumption.
        
    - Allows users to search for documents by file name.
        
- **Usage:**
    
    - Provides an overview of how documents are processed within your automation, serving as a quick reference to track individual document processing outcomes.
        

### 3. Document Details

- **Detailed Metrics for Individual Documents:**
    
    - **General Information:** File name, creation and completion times, consumer details.
        
    - **Classification Data:** Model version, pre- and post-validation document types, confidence levels.
        
    - **Extraction Data:** Extracted fields along with OCR and extraction confidence, and any modifications made during validation.
        
    - **Validation Details:** Task name, type, assignee, status, criticality, and timestamps for task creation and completion.
        
- **Purpose:**
    
    - Offers granular visibility into each document’s processing lifecycle, enabling troubleshooting and performance optimization.
        

---

## Best Practices & Additional Considerations

- **Data Ingestion Latency:**
    
    - Orchestrator data updates every 20 minutes; Robot logs may take up to 2 hours.
        
- **Role-Based Access Control (RBAC):**
    
    - Different access levels are available based on user roles (e.g., DU Administrator, Contributor, Viewer, Data Labeler).
        
- **Customizability:**
    
    - Utilize dashboard filters and schedule regular reports to stay informed about your automation’s performance.
        
- **Platform Monitoring:**
    
    - Continuously monitor consumption metrics and validation performance to optimize resource allocation and improve overall automation efficiency.
        

---

# Generative Extraction, Classification & Validation via APIs – Technical Summary
## Lesson Overview

This lesson introduces the new generative capabilities now available on Public Preview in the Document Understanding API. These capabilities enable advanced machine learning methods for both document classification and extraction tasks.

---

## Learning Objectives

By the end of this lesson, you will be able to:

- **Utilize Generative Classification:**
    
    - Use the API to classify documents using advanced generative models.
        
- **Leverage Generative Extraction:**
    
    - Extract fields from documents with generative techniques via the API.
        

---

## Generative Classification via APIs

- **Capability Overview:**
    
    - The Document Understanding API now supports generative classification, which employs advanced ML methods to determine the document type.
        
- **How It Works:**
    
    - A POST request is made to the generative classifier endpoint.
        
    - The request includes:
        
        - **Document ID:** Identifies the document to be classified.
            
        - **Prompts:** A list of prompts with names and descriptions (e.g., "Invoice" and "Receipt") that guide the classification.
            
- **Sample cURL Command:**
    
    ```bash
    curl -X 'POST' \
      'https://cloud.uipath.com/uipathstgss/UiPathDefault/du_/api/framework/projects/<ProjectID>/classifiers/generative_classifier/classification?api-version=1' \
      -H 'accept: text/plain' \
      -H 'Authorization: Bearer <YourBearerToken>' \
      -H 'Content-Type: application/json' \
      -d '{
        "documentId": "<DocumentID>",
        "prompts": [
          {
            "name": "Invoice",
            "description": "A detailed statement of goods or services provided, with individual prices, the total charge, and payment terms."
          },
          {
            "name": "Receipt",
            "description": "A written acknowledgment of having received a specified amount of money, goods, or services."
          }
        ]
      }'
    ```
    
- **Response Sample:**
    
    - Returns a JSON object with `classificationResults` including:
        
        - **DocumentTypeId:** E.g., "Invoice"
            
        - **Confidence:** A numerical value indicating the confidence level.
            
        - **ClassifierName:** "Generative Classifier"
            

---

## Generative Extraction via APIs

- **Capability Overview:**
    
    - The API now allows generative extraction, leveraging advanced ML to extract specific fields from documents.
        
- **How It Works:**
    
    - A POST request is sent to the generative extractor endpoint.
        
    - The request includes:
        
        - **Document ID:** The unique identifier for the document.
            
        - **Prompts:** A set of prompts (e.g., "Invoice Number", "Date", "Total") to specify what information to extract.
            
- **Sample cURL Command:**
    
    ```bash
    curl -X 'POST' \
      'https://cloud.uipath.com/uipathstgss/UiPathDefault/du_/api/framework/projects/<ProjectID>/extractors/generative_extractor/extraction?api-version=1' \
      -H 'accept: text/plain' \
      -H 'Authorization: Bearer <YourBearerToken>' \
      -H 'Content-Type: application/json' \
      -d '{
        "documentId": "<DocumentID>",
        "prompts": [
          {
             "id": "Invoice Number",
             "question": "Extract the invoice number from the provided document."
          },
          {
             "id": "Date",
             "question": "What is the invoice date mentioned in the document?"
          },
          {
             "id": "Total",
             "question": "Extract the total amount from the invoice."
          }
        ]
      }'
    ```
    
- **Response Sample:**
    
    - Provides an `extractionResult` JSON object containing:
        
        - **ResultsDocument:** With details like document bounds, language, and fields.
            
        - **Fields:** Each field includes:
            
            - **FieldId/FieldName:** E.g., "Invoice Number", "Date", "Total"
                
            - **Value:** The extracted value (e.g., "INV-3337", "January 25, 2016", "$93.50")
                
            - **Confidence Levels:** For both extraction and OCR.
                

---

## Summary

The Document Understanding API now offers generative capabilities for both classification and extraction, enabling:

- **Advanced Classification:**  
    Identify document types using generative models driven by customizable prompts.
    
- **Enhanced Extraction:**  
    Extract detailed field information from documents using state-of-the-art generative techniques.
---
# Other Updates in 23.10 – Technical Summary

## Lesson Overview

This lesson covers several important updates included in the 23.10 product version for Document Understanding. These updates expand API capabilities, enhance model training and deployment performance, and introduce new features for licensing and authentication.

---

## Key Updates

### 1. Document Understanding Cloud APIs GA

- **General Availability:**
    
    - DU Cloud APIs are now GA.
        
    - Consume Document Understanding via robots (RPA) or directly through Cloud APIs.
        
- **Capabilities:**
    
    - Digitize, classify, extract, and validate documents through HTTP requests.
        
- **Resources:**
    
    - Dedicated Academy course and official documentation available for more details.
        

### 2. Forms AI Updates

- **Field Detection Changes:**
    
    - Automatic field detection has been removed to streamline the process.
        
- **Prelabeling Adjustments:**
    
    - Prelabeling only becomes available after manually annotating the first document.
        
    - For subsequent documents, the "Predict" functionality is enabled.
        

### 3. One-Click Classifier & One-Click Extractor GA

- **Simplified Training:**
    
    - These features are now generally available.
        
    - Allow training of classifiers and extractors directly from the Document Understanding interface.
        
    - Bypass the need to manually create datasets, pipelines, and ML Skills in AI Center.
        

### 4. AI Units Consumed at Tenant Level

- **New Allocation Model:**
    
    - AI Units can now be allocated and consumed at the tenant level.
        
- **Management:**
    
    - Adjust allocation via the "Admin" panel in Automation Cloud under the Licenses section.
        
    - Monitor available and consumed AI Units at the organization or tenant level.
        

### 5. Frozen Backbone Model Architecture

- **Performance Enhancement:**
    
    - Frozen Backbone reduces training time by 3-4X by freezing part of the neural network.
        
- **Default Behavior & Overrides:**
    
    - Enabled by default for datasets smaller than 400 pages.
        
    - Options to override for full training (even on small datasets) or force Frozen Backbone on larger datasets (up to 3000 pages).
        
- **Trade-Off:**
    
    - Faster training may occasionally lead to slight accuracy loss.
        
- **Configuration:**
    
    - Override using environment variables:
        
        - `model.override_finetune_freeze_backbone_mode=True`
            
        - Force Frozen Backbone: `model.finetune_freeze_backbone_mode=True`
            
        - Force Full Training: `model.finetune_freeze_backbone_mode=False`
            

### 6. Token-Based Authentication

- **New Authentication Method:**
    
    - Instead of providing an API Key, users can now authenticate sessions using Robot Tokens.
        
- **Benefit:**
    
    - Simplifies authentication in automated workflows consuming DU features.
        

---

## Lesson Summary

- **GA Updates:**
    
    - Many features initially in Preview in 23.4, such as One-Click Classifier/Extractor, are now GA.
        
- **Enhanced Licensing & Performance:**
    
    - AI Units can be managed at tenant level, and the Frozen Backbone architecture significantly speeds up training.
        
- **Improved Security & Usability:**
    
    - Introduction of token-based authentication streamlines API consumption.
---