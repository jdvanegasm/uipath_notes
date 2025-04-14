## **UiPath Document Understanding - Technical Summary**

### **Course Overview**

This course provides an introduction to **UiPath Document Understanding**, an AI-powered tool aimed at intelligently processing various document types. It covers key concepts, challenges, stages, and UiPath components involved in document automation, which is particularly valuable for companies dealing with large volumes of documents.

**Duration**: 1h 45min  
**Requirements**:

- Complete Knowledge Check with 80% score
    
- Fill in Feedback Survey
    

---

### **Learning Outcomes**

By the end of the course, you should be able to:

1. **Define Document Understanding**: Understand the concept and importance of intelligent document processing in business automation.
    
2. **Explain the Document Understanding Framework**: Learn the key stages of document processing (digitization, classification, extraction, validation) and how they are implemented in automation projects.
    
3. **Identify UiPath Components**: Understand the various UiPath tools and services that enable Document Understanding.
    
4. **Understand Key Document Types**: Differentiate between structured, semi-structured, and unstructured documents.
    
5. **Learn UiPath Studio Activities**: Get familiar with the Studio activities and wizards specific to Document Understanding.
    
6. **Handle Document Processing Challenges**: Learn how Document Understanding tackles common challenges in document automation, such as variability in document formats.
    
7. **Explain Licensing and Consumption**: Understand how licensing works for Document Understanding processes.
    

---

### **Key Concepts**

#### **What is Document Understanding?**

Document Understanding is a **document automation** solution that extracts and interprets information from various document types, including images, PDFs, handwritten text, and signatures. It utilizes **AI and rules-based approaches** to automate data extraction, especially from **unstructured** documents, significantly reducing manual effort.

#### **Document Types**

1. **Structured Documents (Forms)**:
    
    - Fixed format with well-defined fields (e.g., surveys, questionnaires, tax forms).
        
    - Contains key-value pairs and tables.
        
2. **Semi-structured Documents**:
    
    - Slight variation in format but follows a general structure (e.g., invoices, receipts, purchase orders, bank statements).
        
3. **Unstructured Documents**:
    
    - No fixed structure, making it challenging for automation (e.g., contracts, reports, agreements).
        

#### **Document Understanding Stages**

1. **Digitization**: Conversion of physical documents (e.g., images, PDFs) into digital format for processing.
    
2. **Classification**: Identifying the type of document (invoice, purchase order, etc.) for further processing.
    
3. **Extraction**: Extracting relevant data (text, tables, key-value pairs) from the document.
    
4. **Validation and Human in the Loop**: Validating extracted data and involving humans if necessary to ensure accuracy.
    

#### **Challenges Addressed by Document Understanding**

- **Manual effort**: Traditionally, document processing requires significant manual data extraction, especially with unstructured or poor-quality documents.
    
- **Document variability**: Managing documents in multiple formats and layouts is complex for traditional automation tools.
    

#### **Key UiPath Components for Document Understanding**

1. **UiPath Document Understanding Service**: The core AI service for intelligent document processing.
    
2. **UiPath Studio**: Provides specific activities and wizards for implementing document automation workflows.
    
3. **UiPath Orchestrator**: Manages robots and integrates Document Understanding processes with other automation workflows.
    

---

### **Typical Document Understanding Workflow**

1. **Digitization**: Scan and convert documents into a usable format (image, PDF, etc.).
    
2. **Classification**: Identify the document type (invoice, receipt, etc.).
    
3. **Extraction**: Extract key information such as text, tables, and values.
    
4. **Validation**: Human validation is required in cases of uncertainty or error detection.
    

---

### **Licensing and Consumption**

- **Licensing**: Understand the UiPath licensing model for Document Understanding, including the allocation of licenses for specific tasks such as AI model training and document processing.
    
- **Consumption**: Learn how the processes consume computational resources and scale within an enterprise environment.
    

---

### **Key Takeaways**

- **Document Understanding** is essential for automating document-related processes efficiently, reducing human intervention, and handling diverse document types.
    
- **Types of Documents**: Structured, semi-structured, and unstructured—each with its own challenges and solutions.
    
- **Four Stages**: The key stages—digitization, classification, extraction, and validation—are essential for processing documents effectively.
    
- **UIPath Components**: UiPath Studio and Orchestrator work together with Document Understanding services to automate these processes.
    

---
## **UiPath Document Understanding - Detailed Technical Summary**

### **Learning Objectives**

By the end of this lesson, you should be able to:

1. **Identify UiPath Platform Components**: Understand the key UiPath components that make up the **Document Understanding** capability and their functionalities.
    
2. **Explain the Document Understanding Framework**: Learn how the stages of Document Understanding are configured in an automation project.
    

---

### **Overview of UiPath Document Understanding**

UiPath Document Understanding is a complex automation capability that processes documents by combining multiple UiPath Platform components. Originally launched as a separate product, it now integrates into the UiPath Business Automation Platform. The framework includes **Studio**, **Robots**, and **AI Center** for building, executing, and training models for intelligent document processing.

### **Key UiPath Components in Document Understanding**

1. **UiPath Studio**: Used to design the automation workflows for document processing. It provides templates for ease of implementation.
    
2. **UiPath Robots**: Executes the automation workflows designed in Studio.
    
3. **AI Center**: Provides machine learning model training and deployment for advanced extraction and classification tasks.
    
4. **UiPath Platform (DU capability)**: Central to this capability, it integrates the above components and allows seamless execution and scaling.
    

---

### **Building and Running a Document Understanding Process**

#### **Document Understanding Framework Stages**

1. **Digitization**: Converts physical documents into digital format for processing. For example, an OCR engine like UiPath Document OCR extracts text and its location from the document.
    
2. **Classification**: Identifies the document type (e.g., invoice, receipt). If the classification confidence is below a certain threshold, human intervention may be needed.
    
3. **Extraction**: Uses pre-defined extractors (like Machine Learning Extractor, Regex, or Form Extractors) to pull specific data fields from the document.
    
4. **Validation**: Human users review and validate the extracted data, ensuring accuracy before moving forward.
    

#### **Workflow Execution in UiPath Studio**

- **Document Understanding Process Template**: A pre-built workflow template in UiPath Studio that guides the automation of document processing from start to finish.
    
- **Human in the Loop (HITL)**: In cases where classification or extraction is uncertain, human validation can be triggered for further review.
    

---

### **Using the Document Understanding Template in UiPath Studio**

1. **Start a Project**: In UiPath Studio, create a project using the **Document Understanding Process** template. This template provides a ready-made flowchart for document processing.
    
2. **Main Workflows**:
    
    - **Attended Mode**: A human is involved in the automation for tasks like classification and validation.
        
    - **Action Center Mode (Unattended)**: Tasks are processed automatically, with intervention if needed.
        
3. **Digitization Workflow**: Uses the **Digitize Document** activity to recognize and locate text within the document.
    
4. **Classification Workflow**: Uses a **Keyword Classifier** (or Machine Learning Classifier) to determine the document's type. If the robot is uncertain, human intervention can confirm the classification.
    
5. **Extraction Workflow**: Extracts data using multiple extractors like **Machine Learning Extractor**, **Form Extractor**, or **Regex Extractor**.
    
6. **Validation Workflow**: After data extraction, human users verify the extracted data, which can then be exported for further use.
    

---

### **Pre-configured Packages and Activities**

1. **Intelligent OCR Activities**: A set of core activities for taxonomy definition, digitization, classification, extraction, and training classifiers/extractors.
    
2. **Document Understanding ML Activities**: Machine learning activities for document classification and extraction, including pre-trained models for common document types like receipts and invoices.
    

### **Taxonomy Setup**

- **Taxonomy Manager**: Defines the document structure, specifying fields and their expected types. The template includes pre-configured taxonomies for various document types like **Receipts**, **Invoices**, and **W-9 Forms**.
    
- **Custom Taxonomy**: You can create or modify taxonomies for specific document types.
    

---

### **OCR Engines**

- **UiPath Document OCR**: Default OCR engine optimized for document images.
    
- **External OCRs (Google Cloud Vision)**: You can switch OCR engines and provide API keys for external services like Google Cloud Vision OCR.
    

---

### **Classifier and Extractor Configuration**

- **Intelligent Keyword Classifier**: Pre-configured to classify documents like receipts.
    
- **Machine Learning Classifier**: Trained on a set of documents, can be retrained with additional data.
    
- **Extractor Configuration**: Configured to use the appropriate extractor based on the document type (e.g., **Machine Learning Extractor** for receipts).
    

---

### **Human-in-the-Loop (HITL) Process**

- During classification or extraction, if the system's confidence is low, the task can be handed to a human for validation.
    
- **Action Center**: When operating in unattended mode, the Action Center is used to present tasks to human users for intervention.
    

---

### **Exporting Data**

- The extracted data is saved in a designated folder (e.g., **Data\Exports**), and can be consumed by other automations or applications.
    
- Exported data includes fields and line items in structured formats like Excel.
    

---

### **Summary**

- **UiPath Document Understanding** is an AI-powered framework integrated into the UiPath platform, utilizing components like **Studio**, **Robots**, and **AI Center** for intelligent document processing.
    
- The process follows a structured workflow: **Digitization → Classification → Extraction → Validation**.
    
- The **Document Understanding Process Template** simplifies the creation of automation workflows, including pre-configured classifiers, extractors, and OCR engines.
    
- **Human in the Loop** allows for manual validation in cases of uncertainty, ensuring the quality and accuracy of extracted data.
    

---

### **Next Steps**

Explore the **Document Understanding framework** in UiPath Studio by applying the knowledge gained from this lesson, experimenting with different document types, classifiers, and extractors to tailor solutions to specific business needs.

![[Pasted image 20250407184136.png]]
![[Pasted image 20250407184910.png]]

## **UiPath Document Understanding - Digitization Overview**

### **Learning Objectives**

By the end of this lesson, you should be able to:

1. **Describe what digitization is and how it works.**
    
2. **Explain how Optical Character Recognition (OCR) is deployed as a key component of digitization.**
    
3. **Explore the capabilities of various available OCR engines.**
    

---

### **What is Digitization?**

**Digitization** is the process of converting non-machine-readable document content (like scanned images) into machine-readable text. This is achieved using **Optical Character Recognition (OCR)**. In UiPath, the **Digitize Document** activity performs this operation, detecting all the words and their coordinates on the document, whether it’s a scanned image or a native PDF.

#### **Key Features of Digitization**:

- **Text Detection**: Detects words and their positions (x-y coordinates).
    
- **PDF Types**:
    
    - **Native PDFs** (text-based): No OCR required.
        
    - **Scanned PDFs**: OCR is used to extract text.
        
- **Detection of Other Elements**: Can detect **handwritten text**, **checkboxes**, **signatures**, and **barcodes/QR codes** depending on the OCR engine used.
    
- **Metadata Extraction**: OCR can extract not only the text but also metadata like positions and formats.
    

---

### **How OCR is Deployed in Digitization**

OCR is the most compute-intensive process in document automation. It involves reading both printed and handwritten text, as well as additional elements like checkboxes, signatures, or barcodes. There are different OCR engines available, which you can choose based on document type and performance requirements.

#### **Available OCR Engines**:

1. **UiPath Document OCR**:
    
    - **Use**: Standard for most documents (printed text, handwriting, signatures, barcodes, etc.).
        
    - **Languages Supported**: Latin-based languages (e.g., English, French, German).
        
2. **UiPath Chinese-Japanese-Korean OCR**:
    
    - **Use**: Specially designed for text in Chinese, Japanese, and Korean.
        
3. **Kofax Omnipage OCR**:
    
    - **Use**: For printed text (requires an activity package in UiPath Studio).
        
4. **Google Cloud Vision OCR**:
    
    - **Use**: Detects printed and handwritten text.
        
    - **Languages Supported**: Multiple languages (not suitable for checkboxes or signatures).
        
5. **Microsoft Azure Computer Vision OCR**:
    
    - **Use**: Detects printed and handwritten text.
        
    - **Languages Supported**: Multiple languages (not suitable for checkboxes or signatures).
        
6. **Tesseract OCR**:
    
    - **Use**: Open-source OCR for general use.
        

---

### **Is Digitization the Same as OCR?**

**No, digitization and OCR are not the same.**

- **Digitization** refers to the broader process of converting documents into a machine-readable format, which may involve OCR and other processing steps (e.g., text extraction from native PDFs).
    
- **OCR** is specifically the technology used to convert scanned images into text.
    

In the case of PDF documents:

- If the document is **native** (text-based), OCR is not necessary.
    
- If the document is **scanned** or **hybrid** (native text with scanned elements), OCR is applied selectively to read the scanned parts.
    

#### **Example Process**:

- **ApplyOCRonPDF = Auto**: Automatically applies OCR if needed (for scanned PDFs).
    
- **ApplyOCRonPDF = Yes**: Applies OCR to all PDF pages.
    
- **ApplyOCRonPDF = No**: Skips OCR for native PDFs, directly extracting text.
    

---

### **Capabilities of Available OCR Engines**

|**Engine**|**Print**|**Handwriting**|**Checkboxes**|**Signature**|**Barcode**|**Languages**|
|---|---|---|---|---|---|---|
|**UiPath Document OCR Cloud**|✔|✔|✔|✔|✔|Latin-based (EN, FR, DE), Handwriting (EN, FR, DE)|
|**UiPath Document OCR LocalServer**|✔|✔|✔|✔|✔|Latin-based (EN, FR, DE), Handwriting (EN, FR, DE)|
|**UiPath Chinese-Japanese-Korean OCR**|✔|✔|✘|✘|✘|Chinese, Japanese, Korean|
|**Kofax Omnipage**|✔|✘|✘|✘|✘|-|
|**Google Cloud Vision OCR**|✔|✔|✘|✘|✘|Multiple languages|
|**Microsoft Azure Computer Vision**|✔|✔|✘|✘|✘|Multiple languages|
|**Tesseract OCR**|✔|✔|✘|✘|✘|Multiple languages|

---

### **Lesson Summary**

- **Digitization** is a crucial step in document processing, where OCR is deployed to convert scanned or image-based documents into machine-readable text.
    
- Different OCR engines offer various capabilities to detect text, handwriting, signatures, and other document elements, with each engine having its own strengths depending on the document type and language.
    
- OCR is the most compute-intensive operation, and optimizing its deployment (e.g., choosing the right OCR engine) can help balance cost and performance in automation processes.

![[Pasted image 20250407185205.png]]

## **UiPath Document Understanding - Classification Overview**

### **Learning Objectives**

By the end of this lesson, you should be able to:

1. **Describe classification** and its role in document processing.
    
2. **Differentiate between various classification methods** available in UiPath.
    

---

### **What is Classification?**

After **digitization**, the next step is **classification**, which involves identifying the type of document you are working with. This step is crucial in projects involving multiple document types because accurate classification ensures the correct data extraction strategy is applied.

#### **Why Classification is Important:**

- **Document Segmentation**: In scenarios where multiple document types are scanned into a single file, classification allows the automation system to identify each document type (e.g., invoices, receipts, purchase orders) and process them accordingly.
    
- **Improved Data Extraction**: By identifying the document type, you can apply the appropriate extraction strategy, ensuring accurate data extraction for each document type.
    

---

### **Classification Methods in UiPath**

UiPath offers several **classification methods** ranging from **keyword-based** to **machine learning (ML)-based** approaches. These methods help automate the identification of document types within a workflow.

#### **Classification Methods**:

1. **Keyword Classifier**:
    
    - **Where to Find**: Studio (IntelligentOCR.Activities package)
        
    - **What It Does**: Classifies documents based on specific, predefined words known in advance.
        
    - **Splitting Capabilities**: Does not split document packs.
        
    - **Retrainability**: Yes, it can be retrained with additional data.
        
2. **Intelligent Keyword Classifier**:
    
    - **Where to Find**: Studio (IntelligentOCR.Activities package)
        
    - **What It Does**: Classifies documents of different types (e.g., invoices vs. passports).
        
    - **Splitting Capabilities**: Can split document packs (i.e., multi-page documents).
        
    - **Retrainability**: Yes, it can be retrained.
        
3. **Document Classifier/ML Classifier**:
    
    - **Where to Find**: Document Understanding in **Automation Cloud/Suite** (AI Center must be enabled).
        
    - **What It Does**: Classifies documents based on machine learning models, useful for a wide range of document types (e.g., invoices, receipts).
        
    - **Splitting Capabilities**: Does not split document packs.
        
    - **Retrainability**: Yes, it can be retrained.
        

#### **Pre-trained Classifiers**:

- **Pre-trained Extractors**: UiPath offers classifiers trained on common document types, available as a Machine Learning (ML) package. These classifiers can be deployed in **Automation Cloud** or **Automation Suite** (on-premises).
    
- **Public Endpoint**: A public endpoint is available for direct use in automation workflows:
    
    - [ML Classification Endpoint](https://du.uipath.com/classify/MLclassification)
        

---

### **Lesson Summary**

- **Document Classification** is vital for accurately identifying and processing different document types.
    
- Various **classification methods** in UiPath, including **keyword-based** and **ML-based** classifiers, provide flexibility in classifying documents.
    
- **Retrainability** is a key feature, allowing you to adapt the classifiers to specific document types or workflows.

![[Pasted image 20250407185626.png]]

## **UiPath Document Understanding - Extraction Overview**
### **Learning Objectives**

By the end of this lesson, you should be able to:

1. **Describe what extraction is** in the context of Document Understanding.
    
2. **Differentiate between the different extraction methods** available in UiPath.
    
3. **Explain the pre-trained out-of-the-box extractors** and their advantages.
    

---

### **What is Extraction?**

**Extraction** is the process of capturing specific data from a document. Unlike manually extracting data from lengthy documents, extraction in the **Document Understanding** framework uses various extractors to automate the task, enabling efficient and accurate data retrieval.

Once the data is extracted, it is passed to the validation stage for further processing.

---

### **Extraction Methods in UiPath**

There are four primary extraction methods, each suited for different types of documents and data:

1. **RegEx Extractor**:
    
    - **Where to Find**: Studio (IntelligentOCR.Activities package)
        
    - **What It Does**: Extracts single values from the document using **regular expressions**. Ideal for fixed-format data such as dates or invoice numbers.
        
    - **Flexibility**: Requires knowledge of regular expressions.
        
2. **Form Extractor**:
    
    - **Where to Find**: Studio (IntelligentOCR.Activities package)
        
    - **What It Does**: Extracts values or simple tables from fixed forms (e.g., tax forms, structured documents).
        
    - **Flexibility**: Requires some training to be effective.
        
3. **Forms AI**:
    
    - **Where to Find**: Document Understanding in **Automation Cloud/Suite** (AI Center required)
        
    - **What It Does**: Extracts values or tables from fixed forms. It’s easier to use than Form Extractor as no special training is required.
        
    - **Flexibility**: Designed for regular forms like tax forms or ACORD forms.
        
4. **Semi-structured AI**:
    
    - **Where to Find**: Document Understanding in **Automation Cloud/Suite** (AI Center required)
        
    - **What It Does**: Extracts data from more complex, semi-structured documents. It works well for both fixed forms and high-diversity documents.
        
    - **Flexibility**: Best for complex or varied documents.
        

---

### **Pre-trained Out-of-the-Box Extractors**

UiPath provides **pre-trained ML extractors** that have been trained on common document types, so you can start processing documents right away without needing custom training.

#### **Advantages of Pre-trained Models**:

1. **Immediate Use**: Start processing documents immediately without the need for setup or training.
    
2. **Wide Document Support**: The models support formats such as **PDF**, **PNG**, **JPEG**, and **TIFF**. They can automatically locate and extract critical data, even if document formats change.
    
3. **No Templates Needed**: The extractors automatically identify and extract relevant information, even from noisy documents.
    

#### **Example Pre-trained Extractors**:

1. **Invoices ML Extractor**:
    
    - **Languages Supported**: English, Spanish, Portuguese, German, and Romanian.
        
    - **Purpose**: Extracts data from invoices, particularly for these languages but applicable to other documents using Latin, Cyrillic, or Greek alphabets.
        
2. **Receipts ML Extractor**:
    
    - **Languages Supported**: English, Spanish, German, French, Norwegian, Finnish, and Romanian.
        
    - **Purpose**: Extracts data from receipts, suitable for multiple European languages.
        

These extractors are available in **ML Packages** deployed in **Automation Cloud** or **Automation Suite** or as **public endpoints** for direct integration into RPA workflows.

For an updated list of available pre-trained extractors, refer to UiPath’s official documentation.

---

### **Lesson Summary**

- **Extraction** involves capturing valuable data from documents, which is then used in automation.
    
- There are various **extraction methods**—**RegEx**, **Form Extractor**, **Forms AI**, and **Semi-structured AI**—each suitable for different document types and complexity.
    
- **Pre-trained extractors** provide ready-to-use solutions for common tasks like invoice and receipt data extraction, enabling faster automation without the need for additional training or setup.

![[Pasted image 20250407192757.png]]

## **UiPath Document Understanding - Validation and Human-in-the-loop**

### **Learning Objectives**

By the end of this lesson, you should be able to:

1. **Describe the processes of manual validation** for document processing.
    
2. **Explain the process of retraining classifiers and extractors** to improve accuracy.
    

---

### **What is Human Validation?**

Despite the advanced capabilities of UiPath’s **extraction** and **classification** technologies, robots may encounter documents that are hard to classify or contain difficult-to-read fields. In such cases, **human validation** is necessary to ensure data accuracy and reliability.

The **Document Understanding framework** allows documents that might contain errors to be flagged for human review.

#### **Types of User Interfaces for Manual Validation**:

1. **Classification Station**:
    
    - **Use**: To validate document classification (e.g., invoice, receipt, etc.).
        
    - **How**: The robot invokes the **Present Classification Station activity** for attended robots, or the **Create Document Classification Action activity** for Action Center.
        
2. **Validation Station**:
    
    - **Use**: To validate the data extracted from documents (e.g., values from invoices, receipts, etc.).
        
    - **How**: Similar to the Classification Station but focused on validating data extraction rather than document classification.
        
3. **Forms**:
    
    - **Use**: Allows the creation of custom validation forms with **pdf viewers**.
        
    - **How**: These forms can be created using the **UiPath.Form.Activities** package for attended robots or the **UiPath.Persistence.Activities.FormTask.CreateFormTask** for Action Center management.
        
4. **UiPath Apps**:
    
    - **Use**: For highly customizable validation interfaces.
        
    - **How**: Requires more development but provides a flexible solution for creating unique validation experiences.
        

---

### **Error Detection Methods**

Potential errors are detected in two ways:

1. **Business Rules**: Ensures that extracted data follows logical business rules. For example:
    
    - Net amount + tax must equal the total.
        
    - Quantity * unit price must equal the line amount.
        
    - Due date must come after the invoice date.
        
2. **Confidence Level Thresholds**: Each extractor (except Forms AI) provides a confidence level for the data it extracts. If the confidence is low or the data doesn’t match the defined business rules, the document is flagged for human review.
    

**Pre-built rules** are available through the **IntelligentOCR.Activities** package, helping with common checks like tax amounts, net amounts, etc.

---

### **How to Retrain Classifiers and Extractors**

Retraining classifiers and extractors is an essential part of improving the accuracy of document processing. Not all classifiers and extractors support retraining, but some can be improved by training on corrected data.

#### **Available Training Methods**:

|**Component**|**Training Activity**|**Other Components Required**|
|---|---|---|
|**Keyword Based Classifier**|**Keyword-Based Classifier Trainer**|-|
|**Intelligent Keyword Classifier**|**Intelligent Keyword Classifier Trainer**|-|
|**Document Classifier**|**Machine Learning Classifier Trainer**|**AI Center** scheduled Pipeline|
|**Regex Extractor**|Not Available|-|
|**Form Extractor**|Not Available|-|
|**Forms AI**|Not Available|-|
|**Semi-structured AI**|**Machine Learning Extractor Trainer**|**AI Center** scheduled Pipeline, **Document Manager**|

Retraining classifiers and extractors helps adapt the automation system to specific document types or improve its performance based on feedback from human validation.

---

### **Lesson Summary**

- **Human validation** ensures the accuracy of extracted data and is essential when documents are difficult to classify or extract data from.
    
- **User interfaces** like **Classification Station**, **Validation Station**, **Forms**, and **Apps** provide flexible options for manual review and validation.
    
- **Error detection** can be done using business rules or confidence levels.
    
- **Retraining classifiers and extractors** allows the system to improve over time by learning from human corrections, which can be done using UiPath’s **training activities** and **AI Center**.

---
## **UiPath Document Understanding First-party Service Overview**

### **Learning Objectives**

By the end of this lesson, you should be able to:

1. **Describe the purpose** of the **UiPath Document Understanding first-party service**.
    
2. **Present the main functionalities** of the Document Understanding service and its relation to other UiPath Platform components.
    

---

### **What Does the UiPath Document Understanding Service Do?**

The **UiPath Document Understanding first-party service** acts as a central hub that integrates with the other UiPath components to provide a comprehensive document understanding solution. It is designed to simplify and streamline the process of document classification, extraction, and validation.

#### **Key Capabilities**:

- **Building Classifiers and Extractors**: Train machine learning models to classify documents and extract relevant data.
    
- **Pre-labeling and Labeling**: Provides functionalities for annotating and labeling document data to train the models.
    

This service integrates seamlessly with other components in the UiPath Platform, enabling end-to-end automation for document processing.

---

### **Relation with Other UiPath Platform Components**

1. **UiPath Studio**:
    
    - **Role**: Develop document understanding automation projects.
        
    - **Integration**: Uses the classifiers and extractors built through the **UiPath Document Understanding service** to automate document processing.
        
2. **UiPath AI Center**:
    
    - **Role**: Create, train, and deploy machine learning models.
        
    - **Integration**: AI Center is deeply integrated with the **Document Understanding service** for training and deploying models specifically tailored for document understanding tasks. It also allows for retraining based on human validation input.
        
    - **Difference**: While **AI Center** is more suited for technical roles (data scientists, developers), the **Document Understanding service** is designed for ease of use by business users.
        
3. **UiPath Action Center**:
    
    - **Role**: Manage human validation tasks for document processing (e.g., using Validation Station or Forms).
        
    - **Integration**: Works closely with the **Document Understanding service** to route documents for human review when necessary.
        

---

### **Features Overlapping Between Document Understanding Service and AI Center**

- Some features, such as the ability to **train semi-structured AI extractors**, are available in both the **AI Center** and **Document Understanding service**.
    
- **Key Difference**: The **Document Understanding service** is more user-friendly, catering to business users, while **AI Center** is more technical, designed for data scientists and developers working on broader automation projects.
    
- **Recommendation**: When in doubt, always start with the **Document Understanding service**.
    

---

### **Automated Training Capability**

The **UiPath Document Understanding first-party service** offers **automated training**, also known as **one-click training**. This feature allows you to start training machine learning models without manual setup:

- **How It Works**: Behind the scenes, **Document Understanding** handles the training process, and once completed, the classifier or extractor is automatically populated in the **extractor/classifier view** for use.
    

---

### **Lesson Summary**

- The **Document Understanding first-party service** is integral to UiPath’s document processing capabilities, enabling the efficient classification and extraction of data from documents.
    
- **Deep integration** with other UiPath components, like **AI Center**, **Studio**, and **Action Center**, ensures a seamless document automation experience.
    
- **Automated training** with the **one-click training** feature simplifies the process of training classifiers and extractors, enhancing automation efficiency.

## **UiPath Studio Document Understanding Components**

### **Learning Objectives**

By the end of this lesson, you should be able to:

1. **Identify the various Studio activities** and wizards in the Document Understanding framework.
    
2. **Describe the Document Understanding Process Template**.
    

---

### **The Document Understanding Features in UiPath Studio**

To build document understanding automations, Automation Developers leverage various Studio components, which include activity packages, wizards, and pre-configured templates. The key components involved are:

1. **UiPath.IntelligentOCR activity package**: This package contains the main activities for the Document Understanding framework.
    
2. **DocumentUnderstanding.ML activity package**: Enables the use of machine learning (ML) extractors and their retraining.
    
3. **UiPath.OCR activity package**: Provides the OCR engines used for digitization.
    
4. **Document Understanding Process Template**: A ready-to-use process structure with built-in configurations and exception handling, designed for enterprise-level automation projects.
    

---

### **UiPath.IntelligentOCR Activity Package**

The **UiPath.IntelligentOCR activity package** provides the essential activities required to build document understanding workflows.

#### **Key Activities**:

- **Taxonomy Manager**:
    
    - **Purpose**: Configure the document types and business rules for your automation.
        
    - **How**: Accessible from the ribbon in Studio, it allows you to define the document types that need to be processed.
        
- **Digitize Document**:
    
    - **Purpose**: Extracts text and structure from a document by using OCR or by scraping native text from PDFs.
        
    - **How**: Multiple OCR engines are available for this activity, including **UiPath Document OCR**, **Google Cloud Vision OCR**, **Microsoft Azure OCR**, and more.
        
- **Classify Document Scope**:
    
    - **Purpose**: Classifies documents into specific types (e.g., invoice, receipt, etc.).
        
    - **How**: Supports multiple classifiers like **Keyword Classifier**, **Intelligent Keyword Classifier**, and **Machine Learning Classifier**.
        
- **Data Extraction Scope**:
    
    - **Purpose**: Extracts data from documents using defined extractors.
        
    - **How**: Includes extractors such as **Regular Expression Extractor**, **Form Extractor**, and **Machine Learning Extractor**.
        
- **Classification and Validation Stations**:
    
    - **Purpose**: These stations allow manual validation of document classification and data extraction when automatic confidence levels are low.
        

---

### **DocumentUnderstanding.ML Activity Package**

The **DocumentUnderstanding.ML activity package** is used to integrate machine learning-based extractors and classifiers into your workflows.

#### **Key Activities**:

- **ML Extractor**:
    
    - **Purpose**: Drop this activity inside the **Data Extraction Scope** to use machine learning-based extractors.
        
- **ML Extractor Trainer**:
    
    - **Purpose**: Used in the **Train Extractors Scope** to save human-validated data for retraining extractors, either in a local folder or directly into an AI Center dataset for further fine-tuning.
        

---

### **UiPath.OCR Activity Package**

The **UiPath.OCR activity package** provides the various OCR engines required for document digitization.

#### **Key Activities**:

- **UiPath Document OCR**:
    
    - **Purpose**: Used in the **Digitize Document** activity to perform OCR using the default UiPath OCR engine.
        
- **OCR-Japanese Chinese Korean**:
    
    - **Purpose**: This is the OCR engine specifically designed for text recognition in Asian languages and can be used in the **Digitize Document** activity.
        

---

### **Document Understanding Process Template**

The **Document Understanding Process Template** is a pre-configured UiPath Studio template designed to facilitate Document Understanding projects.

#### **Key Features**:

- **Fully Functional**: It is a ready-to-use template with built-in logic, logging, exception handling, and retry mechanisms.
    
- **Pre-configured Taxonomy**: Comes with basic document types and classifiers configured for those types.
    
- **Best Practice Example**: It serves as a best practice guide, showcasing how to configure various components of the Document Understanding framework.
    
- **Dependencies**: Includes **UiPath.IntelligentOCR.Activities**, **UiPath.DocumentUnderstanding.ML.Activities**, and other required components.
    

You can find the **Document Understanding Process Template** in the **Official Template Feed** by navigating to the **Templates tab** and selecting the **Document Understanding Process card**.

---

### **Lesson Summary**

- To leverage the Document Understanding framework in UiPath Studio, you need to install various activity packages, including **UiPath.IntelligentOCR.Activities**, **DocumentUnderstanding.ML**, and **UiPath.OCR** activities.
    
- The **Document Understanding Process Template** provides a complete, ready-to-use automation structure, complete with logging, exception handling, and pre-configured components to simplify document processing automation.

## **The Lifecycle of a Document Understanding Project**

### **Learning Objectives**

By the end of this lesson, you should be able to:

1. **Explain the particular aspects** in each stage of the lifecycle of a Document Understanding automation project.
    
2. **Identify the roles and responsibilities** of the people involved throughout the implementation of a Document Understanding project.
    

---

### **Recap: The Automation Project Lifecycle**

The project lifecycle in automation refers to the series of phases a project goes through from initiation to closure. Each phase has specific objectives and deliverables. The UiPath implementation model includes **eight stages**, ensuring the project meets stakeholders' expectations and is completed on time and within budget.

---

### **Roles and Responsibilities in a Document Understanding Project**

The team involved in a Document Understanding project typically consists of several roles, each with specific responsibilities:

|**Role**|**Responsibilities**|
|---|---|
|**Automation Project Manager**|Overall project planning, execution, and delivery.|
|**Automation Business Analyst**|Gathering and analyzing business requirements, identifying use cases.|
|**Automation Solution Architect**|Designing the solution, reviewing code, ensuring best practices are followed.|
|**Automation Developer**|Developing the UiPath automation solution, selecting activities, and building workflows.|
|**Subject Matter Expert (SME)**|Providing domain knowledge, especially about the documents being used.|
|**End-User/s**|Providing feedback on usability and user-experience.|
|**IT/Operations**|Managing deployment, maintenance, and infrastructure (UiPath Orchestrator, robots).|
|**Quality Assurance**|Testing and validation to ensure the solution meets requirements.|

---

### **Stages of a Document Understanding Project**

1. **Gathering Data**
    
    - **Key People**: Solution Architects, Project Managers.
        
    - **Key Tasks**: Collect business and technical requirements, understand document types, set expectations.
        
    - **Deliverables**: As-is process, metrics, target metrics, document properties.
        
2. **Business Case and Technical Validation**
    
    - **Key People**: Solution Architects, Project Managers, Business Analysts.
        
    - **Key Tasks**: Confirm use case alignment with contract expectations, identify complexity and dependencies.
        
    - **Deliverables**: Verified automation use case.
        
3. **Process Analysis**
    
    - **Key People**: Solution Architects, Project Managers, Business Analysts.
        
    - **Key Tasks**: Analyze the current process, define “to-be” processes, complete Process Design Document (PDD).
        
    - **Deliverables**: Approved PDD, UAT plan.
        
4. **Process Design**
    
    - **Key People**: Business Analysts, Solution Architects, Project Managers, Automation Developers.
        
    - **Key Tasks**: Design document types, business rules, taxonomies, classifiers/extractors, and data export methods.
        
    - **Deliverables**: Taxonomies, business rules, process designs.
        
5. **Implementation**
    
    - **Key People**: Solution Architects, Project Managers, Automation Developers.
        
    - **Key Tasks**: Build and test the first model, develop dispatcher, handle errors, integrate with Insights.
        
    - **Deliverables**: Built solution, tested models.
        
6. **Integration and User Acceptance Testing (UAT)**
    
    - **Key People**: Solution Architects, Business Analysts, Project Managers, Automation Developers.
        
    - **Key Tasks**: Test solution, conduct load testing, ensure all exceptions are handled.
        
    - **Deliverables**: UAT results, load testing results.
        
7. **Deployment and Hypercare**
    
    - **Key People**: Solution Architects, Project Managers, Automation Developers.
        
    - **Key Tasks**: Move to Production, handle migration, address critical issues.
        
    - **Deliverables**: Production-ready automation, migration documentation.
        
8. **Project Closure**
    
    - **Key People**: Solution Architects, Project Managers, Business Analysts.
        
    - **Key Tasks**: Finalize documentation, handover for long-term support, sign off the contract completion.
        
    - **Deliverables**: Final sign-off, production environment running.
        

---
### **Lesson Summary**

A Document Understanding project follows a structured lifecycle, with eight stages from **Gathering Data** to **Project Closure**. Throughout the lifecycle, key roles such as Project Managers, Solution Architects, Developers, and Business Analysts collaborate to ensure the project aligns with business goals and delivers the expected outcomes. Each stage involves gathering critical information, building solutions, testing, and deploying the system to production.

![[Pasted image 20250407194351.png]]

## **How Does Licensing Work for Document Understanding?**

### **Learning Objectives**

By the end of this lesson, you should be able to:

1. **Describe how licensing and consumption** work for document understanding processes.
    

---

### **Document Understanding Licensing Overview**

To set up and run **Document Understanding** automation projects, you need various licenses for different **UiPath Platform** components. These components are part of the complex architecture required for Document Understanding processes.

Licensing covers the following:

1. **Automation Developer Licenses**: Required to build automation projects in **UiPath Studio**.
    
2. **Robot Licenses**: Both **attended** and **unattended** robots are needed to run the automations.
    
3. **Enterprise (or Enterprise Trial/Pro Trial) License**: For **Automation Cloud/Automation Suite**, which includes third-party services like **Document Understanding**, **AI Center**, and **Action Center**.
    
4. **AI Units**: These are specific to the AI-based features used in Document Understanding processes, like machine learning, classification, and extraction.
    

While you're likely familiar with licenses for **Automation Developers**, **Robots**, and **Platform Services**, let's focus on **AI Unit Licensing**.

---

### **AI Unit Licensing**

**AI Units** are the licensing units consumed by Document Understanding projects that use machine learning and AI capabilities.

- **AI Units** are generally purchased in packages.
    
- **Consumption** happens primarily when doing **classification** and **data extraction** in a system that consumes **AI units per page**.
    

#### **AI Unit Consumption Breakdown**:

1. **Digitization**:
    
    - **OCR engines** don’t consume AI units, but using **UiPath proprietary OCR** engines (like **Document OCR**) or external engines (Google Cloud, Microsoft Azure) might require a Document Understanding license.
        
    - Free OCR engines (e.g., **Tesseract OCR**, **Omnipage OCR**) don’t incur charges.
        
2. **Classification**:
    
    - **AI unit consumption** applies when documents are **larger than 24 pages**.
        
    - For documents exceeding 24 pages, consumption increases incrementally, but will cap at **5 AI units** regardless of the number of pages.
        
    - **Keyword Classifier** is free for use.
        
3. **Extraction**:
    
    - **Extraction** typically results in **AI unit consumption** (usually **1 AI unit per page**).
        
    - Some extractors are free (e.g., **RegEx extractor**) or less expensive (**0.2 AI units per page** for **Form Extractor**).
        
4. **Validation and Human-in-the-Loop**:
    
    - **No AI unit consumption** is associated with validation and human input, such as reviewing classifications and extractions in **Action Center**.
        

#### **Additional Costs**:

If using **Automation Cloud** and first-party services, expect an additional **+20%** to cover costs for hosting, model training, and other cloud-related services.

---

### **AI Unit Consumption Examples**:

#### **Example 1**:

- **Document**: 3 pages
    
- **Extractors Used**: **RegEx-Based Extractor** (free), **Form Extractor** (0.2 AI units per page)
    
    - **AI Units Consumed**:
        
        - Form Extractor: 3 pages * 0.2 = **0.6 AI units**
            
    - **Total AI Units**: **0.6 AI units**
        

#### **Example 2**:

- **Document**: 10 pages
    
- **Extractors Used**: **Intelligent Keyword Classifier** (free for <24 pages), **Form Extractor** (0.2 AI units per page), **ML Extractor** (1 AI unit per page)
    
    - **AI Units Consumed**:
        
        - Form Extractor: 6 pages * 0.2 = **1.2 AI units**
            
        - ML Extractor: 4 pages * 1 = **4 AI units**
            
    - **Total AI Units**: **5.2 AI units**
        

#### **Example 3**:

- **Document**: 100 pages
    
- **Extractors Used**: **ML Classifier** (1 AI unit per 25 pages), **RegEx-Based Extractor** (free), **Intelligent Form Extractor** (1 AI unit per page), **ML Extractor** (1 AI unit per page)
    
    - **AI Units Consumed**:
        
        - ML Classifier: 4 AI units
            
        - Form Extractor: 23 pages * 1 = **23 AI units**
            
        - ML Extractor: 81 pages * 1 = **81 AI units**
            
    - **Total AI Units**: **108 AI units**
        

---

### **Lesson Summary**

- **AI Units** are the main licensing consumption for Document Understanding, especially for classification and extraction.
    
- **Digitization** and **Validation** don’t consume AI units, but extraction and classification, particularly for larger documents or complex models, do.
    
- Additional **cloud-related costs** may apply when using services like **AI Center** or **Automation Cloud**.

