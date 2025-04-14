## Overview

This course is designed for AI professionals aiming to build enterprise automation projects, focusing on **Document Understanding** within the UiPath platform. It covers essential tools, techniques, and best practices for gathering requirements, development walkthroughs, and configuring a document automation workflow. By the end of the course, you'll have practical knowledge and hands-on experience in building a Document Understanding solution.

## Course Details

- **Course Duration**: 2h 30min
    
- **Completion Requirements**:
    
    - Pass the Knowledge Check with at least an 80% score.
        
    - Complete the Feedback Survey.
        

## Learning Objectives

By the end of this course, you will be able to:

1. **Set up your development environment** for Document Understanding using UiPath Studio and required activity packages.
    
2. **Gather data for business cases and technical validation** using targeted questions during the Process Analysis stage.
    
3. **Design Document Understanding automation solutions** by understanding core principles.
    
4. **Configure each stage of the Document Understanding framework**, including:
    
    - Taxonomy
        
    - Digitize
        
    - Classify
        
    - Extract
        
    - Validate
        
5. **Configure the main activities** within the Document Understanding framework.
    
6. **Understand the concept of confidence** in the Document Understanding framework.
    

## Document Understanding Framework

### Key Stages of the Workflow:

1. **Digitization**: Converting documents (scanned or in other formats) into machine-readable text.
    
2. **Classification**: Identifying the type of document (e.g., invoice, purchase order).
    
3. **Extraction**: Extracting relevant data (e.g., invoice number, dates, amounts).
    
4. **Validation**: Validating extracted data for accuracy.
    

### UiPath Document Understanding Components:

- **UiPath Studio**: The development environment for creating automation workflows.
    
- **Document Understanding Activities**: Predefined components to facilitate document processing (e.g., Digitize, Classify).
    
- **Taxonomy**: A classification schema that defines document types and their data fields.
    
- **Customizable Components**: You can define your workflows and templates for specific document types and processes.
    

### Workflow Summary

1. **Load Taxonomy**: Define the document types and relevant fields.
    
2. **Digitize**: Use OCR (Optical Character Recognition) to extract text from scanned documents.
    
3. **Classify**: Categorize documents based on predefined taxonomy.
    
4. **Extract**: Retrieve specific data from the classified documents.
    
5. **Validate**: Review extracted data to ensure accuracy.
    
6. **Post-processing**: Pass the validated data for further actions.
    

## Practical Approach

- **Template-Based Setup**: While UiPath Studio provides ready-made templates for Document Understanding, this course will focus on manually building the workflow from scratch to deepen your understanding of each component.
    
- **Automation Decisions**: Emphasis on making development decisions and understanding the mechanics of the framework.
    

## Key Concepts

- **Confidence in Document Understanding**: Understanding the confidence levels of extracted data and how to handle low-confidence results.
    

---
## Setting Up UiPath Studio for Document Understanding

## Overview

In this section, you'll learn how to set up your development environment in **UiPath Studio** for Document Understanding. This involves creating a project, installing required activity packages, and testing the setup.

## Key Steps

### 1. **Create a Blank Process in UiPath Studio**

- Open **UiPath Studio**.
    
- Create a new blank process.
    

### 2. **Install Required Activity Packages**

Ensure that the following activity packages are installed and up to date:

- **UiPath.IntelligentOCR.Activities** (min. version 6.5.0)
    
- **UiPath.DocumentUnderstanding.ML.Activities** (min. version 1.17.0)
    
- **UiPath.System.Activities** (min. version 22.10.3)
    
- **UiPath.UIAutomation.Activities** (min. version 22.10.3)
    
- **UiPath.Excel.Activities** (min. version 2.16.0)
    

Once installed, these packages will enable relevant activities under the **Activities Panel** in UiPath Studio. For example, the **UiPath.IntelligentOCR.Activities** will appear in **Available-Default Activities-App Integration-Document Understanding**.

### 3. **Test the Setup**

To verify the installation:

- From the **Activities Panel**, go to **Available-Default Activities-App Integration-Document Understanding-Extractors**.
    
- Drag **Data Extraction Scope** and drop it into your workflow.
    
- Use the search field to find **Form Extractor** and **Machine Learning Extractor**.
    
- If the activities don't appear, double-check the installation steps.  

## Conclusion

Once you've installed the necessary packages and tested your setup, you're ready to start developing Document Understanding automations in UiPath Studio.

--- 
# Technical Summary: Project Requirements and Solution Design for Document Understanding

## Overview

In this lesson, you will learn how to gather requirements for a Document Understanding project and design the solution based on the gathered data. The process involves asking the right questions during the **Business Case**, **Technical Validation**, and **Process Analysis** stages. The solution design is broken into distinct workflows, making use of **automation technologies** and AI components to process documents efficiently.

## Key Learning Objectives

By the end of this lesson, you will be able to:

1. **Gather Requirements**:
    
    - Use focused questions to collect data for the Business Case, Technical Validation, and Process Analysis stages.
        
2. **Design the Automation Solution**:
    
    - Understand principles for designing a document understanding solution based on the gathered data.
        

---

## Business Case: Invoice Processing Automation

### Scenario Overview

The **Account Payable team** of a large organization processes daily invoices received from vendors. These invoices come in various formats (email, shared drives, scanned, computer-generated), and their layouts differ. Currently, employees spend about **15 minutes per invoice** manually extracting information and submitting it to the internal **ERP system**. This is a time-consuming and manual process, ideal for automation.

---

## Gathering Requirements: Key Areas

### 1. **Document Source**:

- **Where do the documents come from?** (e.g., email, shared drives, physical post).
    
- **How are new documents captured?** (e.g., uploaded to shared drive, email).
    

### 2. **File Structure**:

- **What file formats are involved?** (e.g., PDF, images, scanned documents).
    
- **Are the files computer-generated, scanned, or handwritten?**
    
- **How many files are processed daily?**
    

### 3. **Classification**:

- **Is document classification required?** (e.g., invoices, receipts).
    
- **Do you need to split documents if they contain multiple types?**
    

### 4. **Data Extraction**:

- **What method will you use to extract data?**
    
    - **Regex** for structured data.
        
    - **Form Extractor** for structured documents.
        
    - **Machine Learning Extractor** for semi-structured documents (common for invoices).
        

### 5. **Validation**:

- **What validation methods are needed?** (e.g., verifying extracted data against predefined rules).
    

### 6. **Post-Processing**:

- **Where will the extracted data be used?** (e.g., uploaded to an ERP system).
    

---

## Solution Design: Architecture and Workflow

### **Solution Overview**:

The automation solution is divided into **3 functional workflows**:

1. **Dispatcher**:
    
    - Reads invoices from the shared drive and uploads them into an Orchestrator queue for processing.
        
2. **Performer 1 (Document Understanding Workflow)**:
    
    - Retrieves documents from the queue and performs **digitization**, **classification**, **extraction**, and **validation**.
        
3. **Performer 2 (ERP Update)**:
    
    - Uses the validated data to update the **ERP system** (e.g., entering invoice details into the system).
        

### **Performer 1 Workflow**:

This is the focus of the lesson and will implement the **Document Understanding Framework** to handle:

- **Digitization**: Converting documents into machine-readable text.
    
- **Classification**: Identifying the document type (e.g., invoice).
    
- **Extraction**: Extracting relevant data fields (e.g., invoice number, date, total).
    
- **Validation**: Verifying the extracted data for accuracy.
    

### **Performer 2 Workflow**:

- Updates the ERP system using the data processed by **Performer 1**.
    

---

## Solution Architecture Breakdown

### Key Principles

- **Functional Separation**: Each workflow focuses on a specific task, which ensures modularity and scalability.
    
    - **Dispatcher**: Handles document retrieval.
        
    - **Performer 1**: Manages document processing.
        
    - **Performer 2**: Handles ERP integration.
        

### **Scalability**:

- Since **Document Understanding** jobs process one document at a time, multiple robots can run in parallel for scalability. This allows for greater throughput when dealing with multiple invoices.
    

---

## Requirements Gathering Guide

- For in-depth requirement gathering, download the **Capturing-the-Document-Understanding-project-requirements-guide** (PDF), which includes essential questions for stakeholders during the **Business Case** and **Technical Validation** stages.
    

---

## Conclusion

By gathering the right information and breaking down the solution into separate workflows, you can effectively automate complex document processing tasks like **invoice handling**. The **Document Understanding Framework** and AI-driven extractors make it possible to handle different document layouts and formats with minimal manual intervention. The result is a **scalable, efficient, and reliable automation solution**.


![[Pasted image 20250407201107.png]]

---

# Technical Summary: Developing Using the Document Understanding Framework

---
## Overview

This lesson walks you through the process of configuring the **Document Understanding framework** using UiPath Studio, applying the concepts to a real-world **invoice processing** scenario. The focus is on configuring the stages of the framework, including taxonomy creation, OCR digitization, classification, data extraction, and human validation stages. Additionally, it covers retraining features for classifiers and extractors.

## Key Learning Objectives

By the end of this lesson, you will be able to:

1. **Create and modify a taxonomy** and load it into your automation project.
    
2. **Digitize documents** by selecting and configuring the appropriate OCR engine.
    
3. **Use classifiers** to categorize documents.
    
4. **Configure extractors** to retrieve data from the classified documents.
    
5. **Set up human validation stages** and implement retraining features for classifiers and extractors.
    

---

## Workflow Overview

### **1. Taxonomy Creation and Configuration**

- **Taxonomy Manager**: Define the classification schema for the documents you want to process.
    
    - Example: In the **Financial** category, create a subcategory **incoming** for invoices.
        
    - Define the fields to extract (e.g., invoice number, date, total amount) and their data types.
        
- Use **Load Taxonomy activity** to load this taxonomy into the workflow.
    

### **2. Document Digitization**

- **Digitize Document Activity**: Convert documents into machine-readable formats using OCR engines.
    
    - **OCR Engine**: By default, UiPath Document OCR is used, but you can configure other engines like **Google OCR** or **Microsoft OCR** depending on document quality and layout.
        

### **3. Document Classification**

- **Classify Document Scope**: Configure the classification of documents based on the taxonomy.
    
    - Example: For invoices, use **Intelligent Keyword Classifier** to identify and split documents.
        
    - Train the classifier to improve its accuracy by providing examples of invoices.
        
    - The **Present Classification Station** activity can be used to manually review classification results.
        

### **4. Data Extraction**

- **Data Extraction Scope**: Once the document is classified, extract the relevant data using the configured extractors.
    
    - **Machine Learning Extractor**: For semi-structured documents like invoices where layouts vary, use the **Machine Learning Extractor**.
        
    - **Form Extractor**: Use this for structured documents with consistent layouts.
        
    - The **Present Validation Station** activity can be used for manual validation of the extracted data.
        

### **5. Human Validation Stages**

- **Validation Station**: Review the extracted data and manually correct or confirm the fields.
    
    - Example: If the invoice data is missing certain fields, manually highlight and add them in the validation station.
        

### **6. Exporting Results**

- Use the **Export Extraction Results** activity to save the extracted data into a **dataset**.
    
    - You can include confidence levels for both extraction and OCR results.
        
    - Save the results into an **Excel file** for further processing.
        

### **7. Retraining Classifiers and Extractors**

- **Train Classifier Scope**: Use this activity to retrain the classifier based on validated data.
    
    - Input the document path, taxonomy, and validated classification results.
        
- **Train Extractor Scope**: Similarly, retrain the extractor using validated extraction results.
    
    - Map the extractor’s output to the required fields, and store retrained data locally for future use.
        

---

## Demo Walkthrough

The demo video showcases a real-world **invoice processing use case** and highlights each of the activities and configurations:

1. **Dispatcher Process**:
    
    - A queue is populated with documents (invoices) from a shared drive.
        
    - The dispatcher uses a modified **RE Framework** to process documents linearly and add them to the queue.
        
2. **Document Understanding Workflow**:
    
    - The workflow begins by retrieving transaction items (documents) from the queue.
        
    - It checks if the transaction has a value, then proceeds with digitizing, classifying, and extracting data from the invoice.
        
3. **Taxonomy Configuration**:
    
    - A schema is created with fields such as **invoice number**, **date**, and **line items**.
        
4. **Document Classification**:
    
    - The **Intelligent Keyword Classifier** is used to identify and classify the invoice.
        
    - If the document includes multiple types of information (e.g., invoice and other forms), it is split using the classifier.
        
5. **Data Extraction**:
    
    - The **Machine Learning Extractor** is used to extract data from semi-structured invoices.
        
    - The results are validated and can be manually corrected if necessary.
        
6. **Exporting and Final Output**:
    
    - The extracted data is exported into an **Excel file**, including all the fields from the taxonomy.
        

---

# Technical Summary: Zooming In on UiPath Studio Activity Packages for Document Understanding

## Overview

This lesson focuses on the essential **UiPath Studio activities** for implementing the **Document Understanding framework**. You'll learn how to configure key activities for taxonomy management, document digitization, classification, data extraction, validation, and retraining of classifiers and extractors. The goal is to guide you through best practices for each activity and how to effectively use them for efficient document processing.

## Key Learning Objectives

By the end of this lesson, you should be able to:

1. **Configure the Load Taxonomy wizard**.
    
2. **Digitize documents using OCR**.
    
3. **Configure the Classify Document Scope** activity.
    
4. **Set up the Data Extraction Scope** activity.
    
5. **Use the Classification Station and Validation Station**.
    
6. **Train Classifiers and Extractors** using the respective scopes.
    
7. **Export Extraction Results** efficiently.
    

---

## Core Activities for Document Understanding

### **1. Load Taxonomy Wizard**

- **Purpose**: The Taxonomy Manager helps define document types and the associated fields to extract.
    
- **Configuration**:
    
    - Create a taxonomy structure that specifies the document types (e.g., invoices) and their fields (e.g., invoice number, amount).
        
    - Available after installing **UiPath.IntelligentOCR.Activities** version 1.6.0 or higher.
        
    - The wizard helps define the schema and fields for your documents.
        

**Pro-tips**:

- Plan your taxonomy before starting the document processing.
    
- Make sure to define appropriate field data types while creating them, which can be updated later.
    

### **2. Digitize Document Activity Using OCR**

- **Purpose**: This activity converts documents into machine-readable text.
    
- **Outputs**:
    
    - **Text**: The readable content from the document.
        
    - **Document Object Model (DOM)**: JSON object containing details about the document, such as text length, pages, and coordinates of identified words.
        

**Pro-tips**:

- Choose the appropriate OCR engine (e.g., **UiPath Document OCR**, **OmniPage OCR**, **Google Cloud Vision OCR**) based on document quality.
    
- Use **Retry Scope** and **Try Catch** activities for better error handling and retries during the OCR process.
    
- Perform **OCR Benchmark testing** to evaluate OCR engines on sample documents for accuracy.
    

### **3. Classify Document Scope Activity**

- **Purpose**: This activity is used for document classification, categorizing documents into specific types.
    
- **Classification Methods**:
    
    - **Keyword-based Classifier**: Uses keywords to classify documents with repeatable entities.
        
    - **Intelligent Keyword Classifier**: Supports document splitting and is based on learned word vectors.
        
    - **Machine Learning Classifier**: Uses pre-trained ML models to classify documents.
        

**Pro-tips**:

- Choose classifiers based on document variations (e.g., use **Machine Learning Classifier** for unstructured documents and **Intelligent Keyword Classifier** for splitting).
    
- **Train** classifiers with real document variations for better results.
    

### **4. Data Extraction Scope Activity**

- **Purpose**: Extracts data from documents using different extraction algorithms.
    
- **Available Extractors**:
    
    - **RegEx-based Extractor**: Ideal for fixed-format documents.
        
    - **Form Extractor**: Works well with structured documents, such as tax forms.
        
    - **Machine Learning Extractor**: Best for semi-structured documents like invoices and receipts.
        

**Pro-tips**:

- Use **RegEx** for documents with fixed patterns and **Machine Learning Extractor** for semi-structured documents.
    
- Mix and match extractors for better results, and check extraction confidence to validate accuracy.
    
- Use **Try Catch** to handle extraction errors, especially when dealing with scanned documents.
    

### **5. Classification Station and Validation Station**

- **Purpose**: These stations are used for manual validation of classification and data extraction.
    
    - **Classification Station**: Used for checking and correcting classification results.
        
    - **Validation Station**: Used for reviewing and correcting extracted data.
        

**Pro-tips**:

- Use **Classification Station** only when manual classification is necessary.
    
- Wrap these activities in **Try Catch** to handle unexpected errors and exceptions during validation.
    

### **6. Train Classifiers and Train Extractors Scope Activities**

- **Purpose**: These activities are used to retrain classifiers and extractors based on manually verified data.
    
    - **Train Classifier Scope**: Retrains classifiers with corrected classification results.
        
    - **Train Extractor Scope**: Retrains extractors with verified extraction results.
        

**Pro-tips**:

- Train classifiers and extractors only on documents that have been manually verified.
    
- Store retrained data in a local folder or AI Center dataset for future use.
    

### **7. Export Extraction Result Activity**

- **Purpose**: This activity is used to export the results of the document processing workflow for further automation or storage (e.g., to Excel, SAP, email).
    

**Pro-tips**:

- Always store extracted data in a persistent storage location to avoid reprocessing the documents.
    
- Use **Export Extraction Results** to integrate Document Understanding workflows with other automation components.
    

---

## Best Practices and Tips for Using UiPath Document Understanding Activities

### **General Tips**:

- **Define taxonomy carefully** to ensure all necessary data fields are included for extraction.
    
- **Select OCR engine based on document quality**: Each engine has strengths for different document types.
    
- **Use multiple classifiers** if needed to handle complex document types or those with multiple variations.
    
- **Configure extractors based on document type**: Use rule-based methods for structured documents and machine learning-based extractors for semi-structured ones.
    
- **Perform thorough testing**: Especially when selecting OCR and extractors, test them with various document formats to ensure the best results.
    
- **Human validation** should be used only when necessary: Try to automate as much as possible and use the validation stations for exceptional cases.
    

---

# Technical Summary: Confidence Explained in the Document Understanding Framework

## Overview

This lesson explains the **concept of confidence** in the **Document Understanding framework**, focusing on its role in assessing the performance of OCR, classification, and extraction processes. Understanding confidence helps in determining whether a document's data requires human validation or not. The lesson also covers the **types of confidence scores** and how they are used in various stages of document processing.

## Key Learning Objectives

By the end of this lesson, you should be able to:

1. **Describe the concept of confidence** in the Document Understanding framework.
    
2. **Identify the types of confidence scores** used in different stages of document processing.
    

---

## What is Confidence in Document Understanding?

- **Confidence** is a numerical value used by the Document Understanding framework to estimate how well a certain task was performed by an algorithm.
    
- It helps detect potential errors in document processing, triggering **human validation** when the confidence score falls below a certain threshold.
    
- **Confidence** is a probabilistic value and can sometimes be unreliable. To improve accuracy, it is advised to use consistency rules (e.g., "Net Amount + Tax Amount = Total Amount") to verify extracted data.
    
- Each activity in the Document Understanding framework computes its own confidence score based on its specific algorithm.
    

---

## Types of Confidence Scores

There are three main types of confidence scores used in Document Understanding:

### 1. **OCR Confidence**

- **Definition**: This score is provided by the OCR engine, reflecting its ability to accurately recognize characters in the document.
    
- **Usage**: OCR confidence helps in evaluating the success of character recognition and can be used to flag documents where text extraction may be less accurate.
    

### 2. **Classification Confidence**

- **Definition**: This score indicates how well the classifier can identify the type of document (e.g., invoice, purchase order).
    
- **Usage**: Classification confidence is particularly useful for routing documents to the appropriate processing flow.
    
- **Validation Impact**: Once a document classification is validated (e.g., through the Classification Station), the classification confidence becomes **100%**.
    

### 3. **Extraction Confidence**

- **Definition**: This score reflects the ability of an extractor to correctly identify and extract the relevant fields (e.g., invoice number, date, total amount).
    
- **Field Confidence**: Represents how accurately a particular field was extracted. After validation, the field confidence score becomes **100%**.
    
- **Table Confidence**: Calculated by taking the **minimum extraction confidence** value of all cells in a table. Missing table cells are not considered in this calculation.
    
- **Table Cell Confidence**: Confidence scores are also generated for each table cell, although these are not shown individually in the validation interface. They can be accessed in the extraction results.
    

---

## Key Takeaways

- **Confidence Scores** provide insights into the quality of document processing and help route documents for human validation if needed.
    
- **Field, Table, and Table Cell Confidence** are important for understanding how well the extraction algorithms performed at different levels of the document.
    
- After **manual validation**, classification and extraction confidence scores can become **100%**, indicating perfect accuracy.
    
- **Consistency rules** should always be used in conjunction with confidence scores to ensure the accuracy of extracted data.
    



