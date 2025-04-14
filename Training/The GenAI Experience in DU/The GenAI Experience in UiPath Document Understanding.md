## Course Overview

This course covers the significant updates in UiPath Document Understanding, focusing on advanced generative features for annotation, classification, extraction, and validation. In addition, it introduces a new experience in Document Understanding with a UX overhaul and one-click functionalities for classifier and extractor training.

### Learning Objectives

By the end of this course, you will be able to:

1. Leverage Generative Annotation to speed up ML model training.
    
2. Use Generative Classification and Extraction activities/models in your workflows.
    
3. Utilize the Extraction Automation Builder to create Studio Web workflows based on single documents.
    
4. Implement Generative Validation using IntelligentOCR & DU.Activities.
    

---

## Lesson 1: A New Experience in Document Understanding (Duration: 10 min)

### Key Updates & Features

- **UX Overhaul:**
    
    - Redesigned DU center with a scalable and flexible layout that displays more artifact details.
        
- **One-Click Classification (Public Preview):**
    
    - **What It Is:** Train document classifiers directly from the DU center without manually creating datasets, pipelines, or ML skills in AI Center.
        
    - **How It Works:**
        
        1. Create a new project in the DU center.
            
        2. Use “Classify - Automated Training” after uploading at least 10 documents.
            
        3. Monitor classifier training in the Classifiers tab.
            
        4. Copy the public endpoint URL for integration in Studio.
            
        5. Configure the Classification Scope activity with the API Key and classifier details.
            
- **One-Click Extraction (Public Preview):**
    
    - **What It Is:** Create extractors directly from the DU app for semi-structured document types, bypassing AI Center.
        
    - **How It Works:**
        
        1. Ensure a document type is set up (Semi-Structured AI).
            
        2. Navigate to the “Extractors” tab and select “New Extractor” → “Automated Training.”
            
        3. Enter extractor name, select document type, base model, version, and GPU option.
            
        4. Once training is complete, copy the public endpoint URL.
            
        5. Integrate in Studio via the Data Extraction Scope activity.
            

---

## Lesson 2: Generative Annotation (Prelabeling) (Duration: 10 min)

### Key Updates & Features

- **Generative Annotation Overview:**
    
    - Utilizes Generative AI to prelabel (annotate) documents, significantly accelerating the annotation process. This can reduce training time from a week to days or even minutes for simpler forms.
        
- **How It Works:**
    
    - When opening a Semi-Structured AI document type in the DU product, a new, enhanced "Predict" button is available.
        
    - **Predict Options:**
        
        - **Model Predict:** Uses your configured Prelabeling Endpoint (if available).
            
        - **Generative Predict:** Invokes a Generative AI model regardless of pre-trained models.
            
        - **Predict (Recommended):** Combines both approaches for optimal annotation results.
            
- **Benefits:**
    
    - Faster model training and reduced manual annotation effort.
        
    - Accelerates time-to-value even for document types without pre-trained out-of-the-box models.
        

---

## Lesson Summary

- **New UX Experience:**  
    The DU center’s scalable and flexible design improves usability and displays more detailed artifact information.
    
- **One-Click Training:**  
    One-Click Classification and One-Click Extraction allow seamless, end-to-end model training from the DU interface—eliminating the need for manual dataset and pipeline creation in AI Center.
    
- **Generative Annotation:**  
    Leveraging Generative AI to prelabel documents dramatically speeds up the annotation process, enabling faster ML model training and improved efficiency.
    
- **Overall Impact:**  
    These enhancements collectively simplify and accelerate the Document Understanding workflow, providing a more intuitive and efficient model-building and deployment process.
    

---

# Generative Classification & Extraction – Technical Summary

## Generative Classification

### What It Is

- **Overview:**
    
    - Generative Classification leverages Generative AI to classify documents without the need to train a custom ML model.
        
    - Users only need to define document types via descriptive prompts, and the system automatically categorizes documents accordingly.
        

### Why You Need It

- **Efficiency:**
    
    - Streamlines the classification process by eliminating manual rule creation and extensive ML model training.
        
- **Ease of Use:**
    
    - Simplifies document classification using a descriptive approach, saving time and effort.
        

### How It Works

- **Platforms Supported:**
    
    - Available in Studio Web, Windows projects (via UiPath.DocumentUnderstanding.ML.Activities), and Cross-Platform projects (using the UiPath.DocumentUnderstanding.Activities package).
        
- **Implementation Details:**
    
    - **Studio Web & Cross-Platform:**
        
        - Use the "Classify Document" activity.
            
        - Choose "Generative Classifier" from the predefined project and configure prompts describing each document type.
            
    - **Windows Projects:**
        
        - Add the "Generative Classifier" activity in the "Classify Document Scope" and configure the prompt for each document type.
            
- **Version Requirements:**
    
    - Upgrade to UiPath.DocumentUnderstanding.Activities package v2.3.0-preview (for Cross-Platform) or UiPath.DocumentUnderstanding.ML.Activities v1.24.0-preview (for Windows projects).
        

### Lesson Summary

Generative Classification simplifies document classification by allowing you to define document types through descriptive prompts—eliminating the need for manual dataset creation or extensive model training.

---

## Generative Extraction

### What It Is

- **Overview:**
    
    - Generative Extraction uses Generative AI to extract data by answering questions and summarizing content from documents.
        
    - It works for free-form unstructured documents as well as structured and semi-structured documents without training a dedicated ML model.
        

### Why You Need It

- **Speed and Flexibility:**
    
    - Accelerates the extraction process, reducing the time-to-value by avoiding the custom training of extractors.
        
- **Versatility:**
    
    - Suitable for various document types, from semi-structured forms to unstructured text, by using descriptive prompts to specify which fields to extract.
        

### How It Works

- **Platforms Supported:**
    
    - Available in Studio Web, Windows projects, and Cross-Platform projects.
        
- **Implementation Details:**
    
    - **Studio Web & Cross-Platform:**
        
        - Use the "Extract Document Data" activity, select "Generative" from the predefined project, and configure prompts to describe each field you wish to extract.
            
    - **Windows Projects:**
        
        - Add the "Generative Extractor" activity in the "Data Extraction Scope" and set up the prompts for the desired fields.
            
- **Version Requirements:**
    
    - Upgrade to UiPath.DocumentUnderstanding.Activities package v2.3.0-preview (for Cross-Platform) or UiPath.DocumentUnderstanding.ML.Activities v1.24.0-preview (for Windows projects).
        
- **Note:**
    
    - Table processing might require improvements in future updates.
        

### Lesson Summary

Generative Extraction empowers you to extract data from a wide range of documents without the need for pre-training custom models. It uses generative AI to answer specific questions about document content, delivering an efficient and flexible extraction solution.

---

# Extraction Automation Builder – Technical Summary

## What It Is

- **Overview:**
    
    - The Extraction Automation Builder lets you generate a Studio Web workflow automatically from a single document.
        
    - The workflow is pre-configured to classify the document, upload it to Orchestrator, and extract data using a pre-configured extractor.
        

## Why You Need It

- **Accessibility:**
    
    - Empowers business users without deep DU skills to create a fully functional, low-code workflow.
        
- **Simplicity:**
    
    - Provides a ready-to-run automation that processes one document (using only out-of-the-box document types).
        

## How It Works

1. **Create Automation:**
    
    - In Automation Cloud, click "Create Automation" within the Document Understanding center.
        
2. **Upload Document:**
    
    - Upload a document (.jpg, .pdf, or .png) with a maximum size of 14MB and 20 pages.
        
    - Document type is auto-detected with a confidence score; manually override if needed.
        
3. **Optional Configurations:**
    
    - Configure advanced settings such as custom project name, description, and whether data validation is required.
        
4. **Generate Workflow:**
    
    - Click "Create Workflow" to generate and be redirected to Studio Web where you can further customize or run the workflow.
        
5. **Run & Validate:**
    
    - Run the project, complete any Action Center tasks, and view extraction results in the console.
        

## Limitations

- Only predefined (OOTB) document types are supported.
    
- No digitization settings available.
    
- Designed to work with one document type per file.
    

---

# Generative Validation in IntelligentOCR & DU.Activities – Technical Summary

## What It Is

- **Overview:**
    
    - Generative Validation leverages both Generative AI and Specialized AI within the Data Extraction Scope activity to cross-check and fine-tune confidence levels for extracted data.
        
    - It uses properties like **ApplyAutoValidation** and **AutoValidationConfidenceThreshold** to enhance extraction accuracy.
        

## Why You Need It

- **Enhanced Accuracy:**
    
    - Cross-checks extracted data to reduce errors and inconsistencies.
        
- **Improved Learning:**
    
    - Accelerates system learning by integrating Generative AI for continuous performance improvements.
        
- **Flexibility & Efficiency:**
    
    - Applicable across various document types and languages, resulting in faster processing and reliable data extraction.
        

## How It Works

1. **Integration in Data Extraction Scope:**
    
    - Use the Generative Validation feature within the Data Extraction Scope activity.
        
2. **Configuration:**
    
    - Set **ApplyAutoValidation** to enable automatic cross-checking.
        
    - Configure **AutoValidationConfidenceThreshold** to define when to trigger validation.
        
3. **Combined Approach:**
    
    - The Specialized AI component understands content intricately, while the Generative AI component enhances learning and speeds up validation.
        
4. **Deployment:**
    
    - Generative Validation is available when installing the UiPath.IntelligentOCR.Activities package, which automatically includes the necessary DU.ML.Activities package.
        

## Benefits

- **Reduced Errors:**
    
    - Minimizes data extraction errors through effective cross-checking.
        
- **Time Efficiency:**
    
    - Automates the validation process, significantly reducing manual intervention.
        
- **Versatility:**
    
    - Can be applied to a wide range of document processing tasks.
        

---

