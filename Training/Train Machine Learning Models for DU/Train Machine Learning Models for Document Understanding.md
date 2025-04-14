## Course Overview

The course focuses on training **Machine Learning (ML) models** for document understanding using UiPath's platform, enabling automation professionals to train and deploy high-performing ML models for document processing without needing in-depth knowledge of data science. The course covers how to prepare, deploy, and use **model-based extraction** for processing documents such as invoices and receipts.

## Key Learning Objectives

By the end of this course, you should be able to:

1. Describe how **model-based extraction** works in comparison to **rule-based extraction**.
    
2. List the steps of preparing and deploying a custom ML extractor.
    
3. Gather requirements for an ML extractor.
    
4. Use UiPath Document Understanding components like **Document Manager** and **AI Center**.
    
5. Select the right documents for labeling and training the ML model.
    
6. Train an ML model in **AI Center** and deploy it as an **ML skill** in **UiPath Studio**.
    

---

## Introduction to Model-Based Extraction

### **Types of Data Extractors**:

1. **RegEx-based Extractor**: Ideal for structured documents with fixed fields.
    
2. **Form Extractor**: Used for documents with a fixed format, like tax forms.
    
3. **Forms AI**: Aimed at semi-structured or unstructured documents that are similar in information but have varying formats.
    
4. **Machine Learning Extractor (ML Extractor)**: Best for documents with varying layouts, such as invoices or receipts, using deep learning.
    

### **Data Extraction Methods**:

There are three types of extraction methods:

1. **Rule-based Extraction**:
    
    - Used for fixed format documents, such as forms and licenses.
        
    - Relies on templates and predefined rules for extraction.
        
2. **Model-based Extraction**:
    
    - Used for semi-structured or unstructured documents that vary in format (e.g., invoices, receipts).
        
    - Uses **Machine Learning (ML) models** that learn from labeled examples to extract information flexibly, without the need for templates.
        
    - Preferred for documents with varying layouts as it can handle new formats without the need for constant updates to rules.
        
3. **Hybrid Extraction**:
    
    - Combines both **rule-based** and **model-based** methods for more complex documents that require a mix of both approaches.
        

### **Model-Based Extraction** vs. **Rule-Based Extraction**:

|**Model-Based Extraction** (Template-less)|**Rule-Based Extraction** (Template-based)|
|---|---|
|Relies on ML models for deep learning-based extraction|Relies on predefined rules or templates|
|Processes less structured documents, e.g., invoices, receipts|Best for fixed format documents (e.g., forms)|
|Flexible, can handle new document types/layouts|Requires constant updates and maintenance of templates|
|Requires pre-trained models and retraining capabilities|High accuracy for already known documents|
|More suitable for handling varying layouts|Struggles with unknown document types|
|Does not need templates for new formats|Templates need to be created and updated|

### **When and Why Model-Based Extraction is Preferred**:

- **Model-based extractors** are preferred for documents like invoices and receipts, where the layout can vary widely. Rule-based extraction methods would require continuous updating of templates for each new document format, which can be cumbersome and inefficient.
    
- ML models trained on labeled data provide a flexible and scalable solution for document processing, especially when handling large volumes of varied documents.
    

---

## Key Takeaways

1. **Data Extraction Methods**:
    
    - **Rule-based** is best for structured documents with fixed layouts.
        
    - **Model-based** is more flexible and scalable for unstructured or semi-structured documents.
        
    - **Hybrid** combines both approaches for more complex document types.
        
2. **Model-Based Extraction**:
    
    - Relies on **Machine Learning models** that are trained on labeled examples.
        
    - More **flexible** and **scalable** than rule-based extraction, especially when dealing with documents that have varying formats.
        
    - Does not require constant updating and maintenance like template-based extraction.
        
3. **Benefits of Model-Based Over Rule-Based**:
    
    - Handles new document types effectively without the need for constant rule updates.
        
    - Ideal for semi-structured and unstructured documents, like invoices, which have varying layouts.
        

![[Pasted image 20250408144449.png]]

---
# Technical Summary: The Out-of-the-Box UiPath ML Models for Document Understanding

## Course Overview

This lesson introduces the **out-of-the-box ML extractors** provided by **UiPath** and explains how they can be utilized to automate document processing without the need for creating custom models. Additionally, the lesson provides an overview of the steps to prepare and deploy custom ML extractors when needed.

## Key Learning Objectives

By the end of this lesson, you should be able to:

1. Describe the **three scenarios** of using ML extractors with the **UiPath Platform**.
    
2. Explain what **out-of-the-box ML extractors** are and how to use them.
    
3. List the steps of preparing and deploying a **custom ML extractor**.
    

---

## Three Scenarios of Using ML Extractors with UiPath

1. **Using an Out-of-the-Box ML Model**:
    
    - You can use **UiPath's pre-trained ML models** directly from **AI Center** without further training. These models are based on real-world scenarios prepared by UiPath engineers. However, it is recommended to train the models with your own data for better accuracy.
        
2. **Training a UiPath ML Model with Your Own Data**:
    
    - You can start with a pre-trained UiPath model and then **train it using your own labeled data**. After training, deploy the model for your specific use case.
        
3. **Building Your Own Model from Scratch**:
    
    - If your team has expertise in **Machine Learning**, you can **develop your own custom ML model** from scratch. The UiPath Platform provides an environment for training, deploying, and retraining the model.
        

---

## What Are Out-of-the-Box ML Extractors?

- **Out-of-the-box ML extractors** are models pre-trained by **UiPath engineers** to extract data from documents without requiring custom templates or additional training.
    
- These extractors can process documents immediately and support formats such as **PDF, PNG, JPEG, and TIFF**.
    
- **Predefined Entities**: Each extractor is configured to look for specific **data points** or entities within documents. For example, an invoice extractor will look for fields like:
    
    - **Invoice number**, **vendor address**, **billing name**, **net amount**, **tax**, **line items**, **unit price**, and more.
        

### Example Fields for Invoice Extraction:

- **Name**, **vendor address**, **billing address**, **invoice number**, **date**, **total**, **net amount**, **items**, **line amount**, **quantity**, etc.
    

### The Generic Model:

- A **generic document understanding model** is also available. You can **train this model** on your own to extract commonly occurring data points in both **semi-structured** and **structured documents** (like invoices, receipts, etc.).
    

---

## Preparing and Deploying a Custom ML Extractor

### 4 Key Steps to Deploying a Custom ML Extractor:

1. **Gather Requirements**:
    
    - Identify the types of **fields** you need to extract and understand their **format** within the documents.
        
2. **Select and Label Documents**:
    
    - Annotate (label) a **set of documents** that represent the variety of data you want to extract. The more variable the document type, the more examples you need to annotate.
        
3. **Train the ML Model**:
    
    - Using the labeled data, **train the custom ML model** in **AI Center**. The model will learn to extract the fields you’ve defined.
        
4. **Deploy the Custom ML Extractor**:
    
    - After training, **deploy the model** as an **ML skill** within your automation. Optionally, set up **retraining** to continually improve the model’s performance.
        

---

## Key Takeaways

- **Out-of-the-Box ML Extractors**: UiPath provides pre-trained ML models that are ready to use for document processing, supporting various formats and predefined field extractions. While you can use these models directly, training them with your own data will enhance their accuracy.
    
- **Custom ML Extractors**: If the out-of-the-box models don’t fit your specific needs, you can **train a custom ML extractor** by annotating documents, training the model, and then deploying it for use in your automations.
    

---
# Technical Summary: Gathering the Requirements for the ML Extractor

## Course Overview

This lesson focuses on the **requirements gathering process** necessary to build a **custom ML extractor**. It covers the importance of understanding the goals of the automation project, analyzing sample documents, identifying fields to be extracted, and addressing potential challenges to ensure the machine learning model performs well.

## Key Learning Objectives

By the end of this lesson, you should be able to:

1. Understand the **project goals** for a custom ML extractor.
    
2. Request and analyze **sample documents** to assess the document types and quality.
    
3. Identify the **fields to extract** and recognize any potential challenges.
    

---

## Steps Involved in Gathering Requirements for the Custom ML Extractor

### Step 1: **Understanding the Goals of the Automation Project**

- Understand the document types you are processing (e.g., invoices, receipts, tax forms).
    
- Clarify the **fields** you need to extract from each document.
    
- Consider the **formats/layouts/templates** these documents come in, their **volume**, and **languages**.
    
- Identify whether the documents are **digital or scanned** and whether multiple documents are part of a single file.
    
- Understand if there are **irrelevant documents** that need to be filtered out.
    
- Address any **handwriting** or **OCR quality** issues, and identify any **variations** in the document formats or languages.
    

### Step 2: **Requesting Sample Documents**

- Obtain real-world documents or examples that represent the documents you will process.
    
- Review the documents for:
    
    - **Proportions** (e.g., how many documents come in each format).
        
    - **Document quality** (e.g., clarity, legibility).
        
    - **OCR performance**, especially if documents are scanned or contain handwriting.
        
    - **Consistency** and variations across different samples.
        

### Step 3: **Identifying the Fields to Extract**

- Work with stakeholders to **define** which fields need to be extracted from the documents.
    
- Consider:
    
    - **Field types**: Are they numbers, strings, dates, etc.?
        
    - **Location**: Where do these fields appear (e.g., header, footer, or item level)?
        
    - **Uniqueness**: Are any fields unique to a specific customer or document type?
        
    - **Existing Models**: Are these fields covered by UiPath's out-of-the-box models?
        

### Step 4: **Deciding the Approach**

- With the sample documents and field requirements in hand, create the **taxonomy** for the custom model. This includes:
    
    - Defining **regular fields** (commonly extracted fields).
        
    - Identifying **column fields** (fields within tables).
        
    - Specifying **classification fields** (fields used to categorize the document).
        

### Key Challenges Identified:

- **Ambiguity in Field Data**: Multiple addresses or data points with similar names could cause confusion.
    
    - For instance, the **vendor address** and **payment address** might appear in different sections of the document but need to be treated separately.
        
- **Repeated Fields**: Some fields like the **account number** may appear in multiple places within the same document. All instances should be correctly labeled.
    
- **Document Variations**: Different layouts, free text, or missing information in certain sections of the document need careful handling during training to improve model accuracy.
    

---

## Key Takeaways

- A **custom ML extractor** is trained using a **custom set of documents** that the automation system will process.
    
- **Understanding requirements** early is crucial. You need to know the **document types**, **fields to be extracted**, and any **variations** in the documents to ensure accurate training.
    
- **Sample documents** should be carefully analyzed to identify **inconsistencies** and potential issues, as ML models work similarly to humans in recognizing patterns and learning from experience.
    
- **Clear and consistent labeling** of fields is essential for training the ML model to accurately recognize and extract the required data.
    

By taking the time to **gather requirements**, you ensure that the ML model will perform efficiently and reliably in production, minimizing errors and maximizing the accuracy of extracted data.

### Technical Summary: Selecting, Labeling, and Categorizing Documents for ML Training in UiPath Document Manager

---

### Course Overview:

In this lesson, you will learn how to prepare documents for training an ML model in UiPath's **Document Manager**, and the importance of labeling documents accurately for effective model training. You will explore the process of selecting the right documents, setting up Document Manager, performing data labeling, and checking the health of your dataset.

### Key Learning Objectives:

By the end of this lesson, you should be able to:

1. Select the right documents for labeling and training the ML model.
    
2. Set up and use **Document Manager** for pre-labeling and labeling.
    
3. Import, store, and categorize documents in Document Manager.
    
4. Check the health of a dataset.
    
5. Use pre-labeling in Document Manager.
    
6. Perform data labeling in Document Manager.
    

---

### Key Steps in Document Preparation and Labeling

#### **1. Selecting the Documents for Training**

- **Variety in Samples**: For effective training, ensure that documents represent the different variations you expect in real-world use (e.g., different layouts, languages, and number of pages).
    
- **Training and Evaluation Sets**: Documents should be categorized into **training sets** (used for model learning) and **evaluation sets** (used to test the trained model's performance).
    
- **Representing Variations**: Select samples with varied document types (e.g., different invoice layouts) to ensure your model can handle multiple formats.
    
- **Document Count**: It’s recommended to have 10-20 samples per layout, with a few extra for evaluation. The more varied the dataset, the better the model will generalize.
    

#### **2. Setting Up Document Manager**

- **Project Creation**: Create a new project in **AI Center**, and then establish a **data labeling session** for the documents.
    
- **OCR Configuration**: Set up the **OCR engine** that will be used to digitize the documents before they are labeled. You can choose from various OCR engines such as **UiPath Document OCR**, **Google Cloud Vision OCR**, etc.
    
- **Schema Configuration**: Predefine the fields (e.g., invoice number, date) that need to be labeled and extracted. This will guide the labeling process.
    
- **Pre-labeling**: Use pre-labeling for faster labeling using an out-of-the-box model, which will predict fields for labeling. However, this step consumes **AI units**.
    

#### **3. Labeling the Documents**

- **Pre-labeling with ML Models**: Pre-labeling utilizes existing models to predict data fields. This step can speed up the labeling process, but it may require manual corrections.
    
- **Human Labeling**: After pre-labeling, human intervention is necessary to ensure that fields are accurately labeled, especially when the model hasn't seen those fields before.
    
- **Rubber-banding**: To label fields, select the relevant text in the document and assign it to a field using the hotkeys. For example, select the vendor name and press a designated key to label it.
    
- **Table Handling**: For tables, select and group rows or columns together, and use the **/ hotkey** to mark them accordingly.
    

#### **4. Health Check of the Dataset**

- **Dataset Size Check**: Make sure that the dataset size aligns with the **recommended dataset size** for the chosen document type and layout.
    
- **Validation Set**: Ensure that the evaluation dataset is distinct from the training set and consists of documents the model has never seen before.
    

---

### **Best Practices for Dataset Labeling and Model Training**

- **Balanced Dataset**: Aim for a balanced dataset that includes a variety of document layouts, and don't overuse one particular layout. A well-balanced dataset improves the model’s ability to generalize across document types.
    
- **Model Performance with Larger Datasets**: Training on a larger dataset (with more layouts and variations) helps the model perform better across a wide variety of scenarios. A dataset that includes more than just a few layouts ensures the model will better understand unseen document types.
    

---

### **Post-Labeling and Exporting Documents**

Once labeling is complete, you can export the labeled data for further training and evaluation.

1. **Export Options**:
    
    - **Excel Download**: For local review and further processing.
        
    - **Export to AI Center**: If further retraining is required, export the data back to **AI Center**.
        
2. **Data Categories**:
    
    - **Train-validate set**: This is the set used for model training and evaluation.
        
    - **Evaluation set**: A separate set used to test the model’s performance.
        

---

### **Conclusion:**

This lesson emphasizes the importance of selecting the right documents and accurately labeling the data for machine learning model training. The use of **Document Manager** simplifies the labeling process, and following best practices for dataset creation and health checks ensures that the model can be trained effectively.

## **Training and Deploying the ML Model in AI Center**

---

### **Course Overview**

In this lesson, you will learn how to:

1. **Train** an ML package in **AI Center** using an uploaded dataset.
    
2. **Evaluate** the trained model.
    
3. **Deploy** the model as an **ML skill** for use in automation workflows.
    

---

### **Training the Model in AI Center**

#### **Step-by-Step Process:**

To train a model using **AI Center**, the following components are involved:

1. **Project**: Organizes datasets, ML packages, pipelines, logs, and skills.
    
2. **Dataset**: Stores the labeled data that the model will be trained on.
    
3. **ML Package**: Contains the model that will be trained and deployed.
    
4. **Pipeline**: Describes the ML workflow, including functions to run and their execution order.
    
5. **ML Skill**: A trained model that can be used in UiPath automation workflows.
    
6. **ML Log**: Tracks and records events related to ML processes.
    

---

### **Steps to Train the Model:**

1. **Create a Project**:
    
    - Navigate to the **Projects** page in AI Center and click **Create Project**.
        
    - Optionally, provide a description for the project.
        
2. **Upload a Dataset**:
    
    - Open the created project and navigate to the **Datasets** section.
        
    - Click **Upload folder** to upload the labeled documents.
        
    - If the dataset is already labeled, you can skip the data labeling step.
        
3. **Choose an ML Package**:
    
    - Select an existing **out-of-the-box Document Understanding package** (e.g., Invoice model).
        
    - Choose the latest version of the ML package to train on your data.
        
4. **Create a Training Pipeline**:
    
    - Navigate to the **ML Package details** and click **Create new** under the **PIPELINE RUNS** tab.
        
    - Choose the dataset and the ML package version to train on.
        
    - Set up the training pipeline using both training and evaluation data.
        
5. **Evaluate the Model**:
    
    - After the model is trained, create an **evaluation pipeline** to assess the performance of the trained model.
        
    - Evaluate the model's accuracy using a separate evaluation dataset, which consists of documents the model has never seen before.
        
6. **Enable GPU for Faster Training** (optional):
    
    - Enable GPU for faster training of the model, especially if working with large datasets.
        
7. **Create a New Version**:
    
    - After training, a new version of the model is generated. Ensure the training is done on the **base version** (minor version 0), and avoid partial training.
        

---

### **Evaluating the Model**

- **Evaluation Pipeline**:
    
    - Once the training pipeline is complete, create an evaluation pipeline using the model's trained version.
        
    - Evaluate how the model performs against the evaluation dataset.
        
- **Performance Metrics**:
    
    - Check the **F1 Score** and **Accuracy** metrics. Anything above **0.9** is considered excellent.
        
    - Review the evaluation results in **Excel** or **text files** to understand how well the model performed on individual fields.
        

---

### **Deploying the Model as an ML Skill**

1. **Create a New ML Skill**:
    
    - Go to the **ML Skills** page in AI Center and click **Create New**.
        
    - Name your new skill (e.g., "Invoice Model").
        
    - Select the trained model's **major and minor versions**.
        
    - Provide a description for the ML skill (optional).
        
2. **Deploy the Model**:
    
    - Click **Create** to deploy the model as an ML skill.
        
    - Once the model is deployed, it becomes available to be used in UiPath Studio.
        
    - Choose whether to make the ML skill **public** and whether to enable **auto-update** for the skill.
        
3. **Usage**:
    
    - After deployment, the **ML skill** can be invoked from UiPath Studio workflows by using the **ML Skill activity**.
        
    - Ensure that the **API key** for the deployed model is available for authentication.
        

---

### **Best Practices for Model Training and Deployment**

- **Training Dataset**: Ensure that your training dataset covers a broad variety of document layouts to help the model generalize better.
    
- **Evaluation Dataset**: Include unseen documents in the evaluation dataset to accurately test the model's performance in real-world scenarios.
    
- **Model Versioning**: Always train the model on the base version (minor version 0) and avoid partial trainings, as they can reduce the model's effectiveness.
    
- **Deployment Considerations**: Make sure that the model is deployed as an **ML skill** for integration with UiPath automation.
    

---

### **Conclusion:**

By following the steps outlined above, you will be able to train, evaluate, and deploy an ML model for document understanding in UiPath. Once the model is deployed as an ML skill, it can be easily integrated into automation workflows, enabling efficient document processing in real-world applications.

**![[Pasted image 20250408173823.png]]**

### **Using the ML Skill in UiPath Studio**

---

### **Course Overview**

By the end of this lesson, you'll be able to:

1. **Integrate** the deployed **ML skill** in an **automation project** built with **UiPath Studio**.
    

---

### **How to Use the ML Skill in Studio**

In this section, you'll learn how to use your trained **ML model** as an **ML skill** in a Studio automation project, utilizing the **Document Understanding Process Template** for ease of implementation.

---

### **Steps to Use the ML Skill in Studio:**

1. **Create a New Project in UiPath Studio:**
    
    - Open **UiPath Studio**.
        
    - Go to **New Project** and select **Document Understanding Process**.
        
    - If you can't find it directly, click the **More Templates** button to access additional templates and download the **Document Understanding Process** template.
        
2. **Remove Unneeded Document Types:**
    
    - In the **Document Understanding** template, remove any document types that aren't relevant to your project.
        
    - Keep the **Invoice** document type and update it to match your ML model's schema.
        
    - Ensure the schema includes all fields, such as **Vendor Email**, **Phone Number**, and **Instructions**.
        
3. **Update the Configuration File:**
    
    - In the **config file**, update the **Invoices Endpoint URL** to point to the URL of your deployed ML skill.
        
    - Ensure that the **API key** is set correctly, pointing to the **Orchestrator Asset** containing the API key for the ML skill.
        
4. **Configure Classifiers and Extractors:**
    
    - **Configure the Classifiers**: Make sure the classifier is set up to recognize invoices. You can update the classifier’s settings under **Configure Classifiers** in the workflow.
        
    - **Configure Extractors**: Under the **Configure Extractors** section, update the extractor to use your deployed **ML skill** instead of any default extractors.
        
5. **Run the Process:**
    
    - Compile the project and run the **Main.xaml** workflow.
        
    - If no input file is provided, it will prompt you to select one. You can use documents not included in the training dataset for testing.
        

---

### **Testing the ML Skill**

1. **Classification Station:**
    
    - During runtime, the **Classification Station** will recognize the document type (Invoice).
        
    - The ML model may require manual adjustments in some cases, such as when documents are split across multiple pages.
        
2. **Extraction Process:**
    
    - In the **Extraction Station**, the model will extract the relevant fields such as **Vendor Name**, **Invoice Number**, **Amount**, and **Vendor Phone Number**.
        
    - If the model misses some fields or makes an error (e.g., incorrect extraction of phone numbers), you can manually correct them during validation.
        
3. **Human Validation:**
    
    - By default, **Document Understanding** directs all documents to **Human Validation**. This is useful for checking the results and making any necessary adjustments.
        

---

### **Fine-Tuning the Model**

- **Adding More Training Data**:
    
    - If the ML model isn't performing perfectly, you can improve its accuracy by adding more labeled data to the training set and retraining the model.
        
- **Handling Complex Data:**
    
    - Some issues, like merging rows in tables or capturing fields that span multiple pages, might require manual corrections or adjustments in the RPA workflow.
        

---

### **Best Practices for Using the ML Skill:**

1. **Maintain a Balanced Dataset**: Ensure that your training data covers a variety of document layouts and edge cases.
    
2. **Monitor the Model's Performance**: Continuously assess the model's accuracy during human validation and use the feedback to refine the dataset.
    
3. **Retrain the Model Regularly**: Periodically retrain the model to improve accuracy and handle new document types.
    

---

### **Conclusion:**

Now that you've successfully integrated your **ML skill** in an **automation project** in **UiPath Studio**, you can process invoices, extract data, and handle edge cases. You should regularly evaluate and improve the model for better accuracy and efficiency.

---

### **Next Steps:**

Explore how **Forms AI** can be leveraged for even more accurate document classification and extraction in your automation workflows!

## **Build a Model with Forms AI**

---

### **Lesson Overview**

By the end of this lesson, you should be able to:

- **Use Forms AI** for efficient document processing and automation.
    

---

### **What is Forms AI?**

**Forms AI** is a powerful tool within the **UiPath Document Understanding** framework. It’s designed to streamline the extraction process for structured documents by leveraging AI. Forms AI allows for **template-based** document extraction while continuously improving its accuracy, providing a **no-code solution** for efficient document processing.

Forms AI is particularly useful for creating extractors that handle **structured** documents, such as invoices, purchase orders, or any fixed-layout form. It eliminates the need for manually creating templates for each document type and allows for automation in extracting relevant fields from various layouts of the same document type.

---

### **Steps to Implement Forms AI for Document Processing**

---

### **Step 1: Creating a Forms AI Project**

To start using **Forms AI**, follow these steps:

1. **Navigate to the UiPath Document Understanding Overview** page in **Automation Cloud**.
    
2. Select **+ New Project** to create a new Forms AI project.
    
3. Provide a **Project Name**.
    
4. From the **OCR Method** drop-down list, select an appropriate **OCR engine** (e.g., UiPath Document OCR, Google OCR, etc.).
    
5. Enter the **OCR URL** based on your OCR engine.
    
6. Click **Create**.
    

---

### **Step 2: Defining a New Document Type**

Once your project is created:

1. Open the newly created project in **UiPath**.
    
2. Ensure that the **Document Types** tab is selected.
    
3. Select **+ New** > **Using Forms AI (Fixed Layout Forms)** to define a new document type.
    

---

### **Step 3: Uploading Documents**

Once a new document type is created, you need to upload at least two documents for Forms AI to process:

1. Click **Import Data** to open the upload dialog.
    
2. Select **2-5 documents** that match the layout of the document type you want to process.
    
3. Click **Save** to upload the documents.
    

---

### **Step 4: Defining Fields for One Document**

After uploading documents:

1. Forms AI will automatically detect **fields** from the uploaded documents.
    
2. Review the detected fields and modify them as necessary, especially if any fields are missing or incorrectly detected.
    
3. You can edit the field names, values, or layout as required.
    

---

### **Step 5: Publishing the Extractor**

Once you are satisfied with the field detection:

1. In the top-right corner of the screen, click **Publish**.
    
2. In the **Extractor Name** field, provide a **suitable model name**.
    
3. Click **Publish** to make your extractor available.
    

---

### **Step 6: Using the Extractor**

After publishing the extractor:

1. The extractor is now available in **Automation Cloud** under **Document Understanding** > **[Your Project]** > **Extractors**.
    
2. You can use the extractor via its **URL (endpoint)** in your automation workflows, just like any other ML model within the UiPath ecosystem.
    

---

### **Frequently Asked Questions**

1. **Why Use Forms AI Instead of Form Extractor?**
    
    Forms AI is preferred because it creates extractors that work on **multiple layouts** of structured and semi-structured documents, whereas **Form Extractor** creates templates for **specific document layouts**. If a document layout changes, the Form Extractor may fail, but Forms AI is more flexible and adaptable to changes.
    
2. **What is the Difference Between Forms AI and Document Manager?**
    
    - **Forms AI**: Used for uploading, processing forms, and publishing extractors for fixed-form documents.
        
    - **Document Manager**: Allows you to prepare, review, and make corrections to datasets for **training** and **evaluation** of Document Understanding models. It is more suited for **semi-structured documents**.
        

---

### **Next Steps:**

Now that you understand the steps involved in creating and using a model with **Forms AI**, you can proceed to implement it in your automation projects. Whether it's for invoice processing, receipts, or any other fixed-form document, Forms AI will help you streamline the extraction process.

---

For a more in-depth look, visit the **Forms AI Official Documentation** to dive deeper into its features and usage.