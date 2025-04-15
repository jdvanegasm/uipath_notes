# Technical Summary: IDP 2024.10 Release

This summary captures the key technical enhancements and learning objectives for the latest IDP release, focusing on UiPath Document Understanding and Communications Mining features.

---

## Course Overview

- **Target Audience:** Technical professionals
    
- **Purpose:** To provide an in-depth exploration of new features in the IDP 2024.10 release and prepare users for real-world implementation.
        
- **Credit Requirement:** Must view at least 80% of the course content

---

## Key Enhancements in UiPath Document Understanding

1. **Exporting Datasets**
    
    - _Status:_ General Availability
        
    - Enables exporting datasets from modern projects for improved data handling.
        
2. **Active Learning Integration**
    
    - Now available in the UiPath Automation Suite.
        
    - _Note:_ DocPath is available in the US region only.
        
3. **Cross-Tenant/Organization Project Support**
    
    - Seamless migration of modern projects between tenants and organizations.
        
4. **Advanced Metrics & Model Insights**
    
    - Provides detailed metrics and extraction performance insights for each batch in modern projects.
        
5. **Custom Validation Tasks**
    
    - Allows development of tailored validation applications to meet specific customer needs.
        
6. **AI Trust Layer Governance**
    
    - Enhances control over access to AI-powered features in Document Understanding.
        

---

## Enhancements in Communications Mining

- **UiPath Autopilot Feature**
    
    - Introduces conversational filters for improved dataset filtering and communication analysis.
        

---

## Learning Objectives

By the end of the course, participants will be able to:

1. Describe the new features introduced in Document Understanding for the 2024.10 release.
    
2. Migrate modern projects seamlessly across different tenants or organizations.
    
3. Obtain and analyze detailed metrics and model results for each batch in modern projects.
    
4. Develop custom validation applications to better address customer requirements.
    
5. Effectively control access to AI-powered features within Document Understanding.
    
6. Utilize natural language prompts to filter datasets in Communications Mining.
    

---

## Additional Information

- **Documentation & Release Notes:** For a comprehensive understanding and further details on additional updates, refer to the official documentation and release notes.
    

This summary serves as a quick refresher to refresh critical concepts before diving deeper into the detailed documentation as needed.

# Technical Summary: Active Learning in Automation Suite

This lesson introduces the integration of Document Understanding active learning into the UiPath Automation Suite, highlighting its features, benefits, deployment nuances, and limitations.

---

## Key Learning Objectives

- **Enable Active Learning:**  
    Learn how to activate the UiPath Document Understanding active learning feature in Automation Suite.
    

---

## What's New

- **Feature Availability:**  
    Document Understanding active learning is now fully available in the 2024.10 Automation Suite release.
    
- **Enhanced Model Training:**
    
    - Uses AI to guide the training process.
        
    - Provides automatic annotation and expert recommendations to improve model accuracy.
        
    - Leverages the most informative datasets to optimize learning.
        

---

## Problem Solved

Active learning addresses several challenges in data-driven decision-making by:

- **Efficiency Improvement:**  
    Selects the most informative data points for labeling, reducing the need for exhaustive data annotation.
    
- **Cost Reduction:**  
    Minimizes expenses by focusing on valuable examples, crucial when labeled data is limited or expensive.
    
- **Enhanced Model Accuracy:**  
    Improves performance especially in cases of data imbalances, limited labeled data, or concept drift.
    

---

## Business Scenarios

Active learning is beneficial in various industries, including:

- **Customer Support Automation:**  
    Improves chatbots and virtual assistants by focusing on complex or ambiguous customer queries.
    
- **Fraud Detection:**  
    Prioritizes unusual cases for review, helping financial institutions identify evolving patterns of fraud.
    
- **Medical Diagnosis:**  
    Assists in early and accurate diagnosis by highlighting rare or unusual cases for expert review.
    

---

## Deployment and Configuration

### How to Get Started

1. **Activation Steps:**
    
    - Log in to your Automation Suite account.
        
    - Navigate to the Admin page.
        
    - Select the desired tenant.
        
    - Go to Services, locate the Document Understanding card.
        
    - Click the three-dot icon (⋮) and select **Enable**.
        

### Deployment Types and Feature Availability

- **Automation Suite Online Deployment:**
    
    - Pre-defined projects: _Planned_
        
    - Generative Annotation: _Planned_
        
    - Document Understanding APIs: _Available_ (with some restrictions)
        
- **Automation Suite Offline Deployment:**
    
    - Pre-defined projects: _Planned_
        
    - Generative Annotation: _Not Available_
        
- **Hybrid Deployment (Document Understanding on Automation Cloud™, robot on Automation Suite):**
    
    - Pre-defined projects: _Available_ via Document Understanding Cloud APIs
        
    - Generative Annotation: _Available_
        

#### Components Comparison

- **Building Models:**
    
    - **IntelligentOCR.Activities:** Available in both Automation Suite and Hybrid.
        
    - **DocumentUnderstanding.Activities:** _Planned_ for both.
        
    - **Generative Capabilities:**
        
        - Not planned via DocumentUnderstanding.Activities;
            
        - Not planned for IntelligentOCR.Activities.
            
- **Consuming Models:**
    
    - **Document Understanding Insights Dashboards:** Not available in both deployments.
        
    - **AI Units Consumption Dashboards:** Available in both.
        
    - **Project Performance Dashboard:** Available in Automation Suite Monitor; planned for Hybrid.
        

---

## Current Limitations

Active learning in Automation Suite has some deployment restrictions:

- **Unsupported Configurations:**
    
    - **Openshift:** No support available.
        
    - **Linux:** Offline deployments and Azure Government environments are unsupported.
        
    - **EKS/AKS:** Offline deployments and Azure Government environments are unsupported.
        

---

## Lesson Summary

- The lesson demonstrates that the UiPath Document Understanding active learning experience is now part of the UiPath Automation Suite.
    
- It provides a guided approach to model training with enhanced AI-driven annotations and recommendations.
    
- Active learning is strategically implemented to solve data labeling challenges and improve overall model performance in real-world business applications.
    
---

# Technical Summary: Cross-Tenant/Cross-Organization Consumption of Modern Projects

## Key Learning Objectives

- **Cross-Tenant/Organization Consumption:**  
    Learn how to configure and consume modern projects that span multiple tenants or organizations.
    

---

## What's New

- **Feature Availability:**
    
    - **IOCR.Activities Package:**  
        GA (General Availability) for cross-tenant/cross-organization support.
        
    - **DU.Activities Package:**  
        Public Preview in Automation Cloud.
        
- **Benefit:**  
    Improves flexibility and collaboration by allowing projects to leverage resources and functionalities across organizational boundaries.
    

---

## Problem Statement

Modern projects, unlike classic projects, face challenges such as:

- **Limited Deployment Options:**  
    Incompatibility with on-premises robots.
    
- **Restricted Sharing:**  
    Inability to share projects across different tenants or organizations.
    

**Proposed Solutions:**

- **Cross-Environment Compatibility:**  
    Enable modern projects to work with on-premises robots by configuring external applications.
    
- **Multi-Tenant & Multi-Organization Support:**  
    Allow seamless sharing and consumption of projects across various organizational setups.
    
- **Unified Project Structure:**  
    Facilitate a smooth transition from classic to modern projects, future-proofing investments.
    

---

## How to Get Started

### Configuring External Application & Authentication

1. **Add External Application:**
    
    - In your Automation Cloud organization, add an external application with Document Understanding as a resource.
        
    - Include necessary User and Application scopes.
        
    - Save the provided **App ID** and **App Secret**.
        
2. **Store External Application Credentials:**
    
    - In the local Orchestrator where your robot is registered, store these credentials as a Credential Asset:
        
        - **Username:** App ID.
            
        - **Password:** App Secret.
            
3. **Configure Activity Authentication:**
    
    - In the activity’s **Authentication** section:
        
        - **Runtime Credentials Asset:**  
            Select or manually enter the path (format: `<OrchestratorFolderName>/<AssetName>`) to the Credential Asset containing the external app credentials.
            
        - **Runtime Tenant URL:**  
            Enter the URL of the cloud tenant in the format: `https://<baseURL>/<OrganizationName>/<TenantName>`.
            

---

## Business Impact

- **Enhanced Flexibility:**  
    Modern projects can now be consumed by on-premises robots, removing previous limitations.
    
- **Improved Collaboration:**  
    Cross-tenant/organization support facilitates shared resources and expertise across different teams and regions.
    
- **Future-Proofing:**  
    Provides a clear migration path from classic to modern projects, ensuring long-term adoption and scalability.
    

---

## Lesson Summary

This lesson covers the configuration required to enable cross-tenant/cross-organization consumption of Document Understanding modern projects. By setting up an external application, storing credentials in the local Orchestrator, and configuring the activity’s authentication properties, users can overcome the limitations of modern projects and fully leverage cloud resources across organizational boundaries.

This summary provides a quick refresher on the essential steps and business rationale, serving as a reference before consulting the detailed documentation or watching the instructional video.

---

# Technical Summary: AI Trust Layer Governance Policy

**Duration:** 15 minutes

This lesson details the governance and control mechanisms for AI-powered features within Document Understanding, focusing on centralized management of GenAI functionalities across UiPath Cloud accounts.

---

## Key Learning Objectives

- **Control Access:**  
    Learn how to manage and restrict access to AI-powered features in Document Understanding.
    

---

## What's New

- **Centralized GenAI Control:**
    
    - A unified setting in the Automation Ops section allows customers to disable all GenAI features across their Cloud accounts.
        
    - This consolidated switch streamlines management and ensures uniform compliance with security and operational policies.
        
- **Benefits:**
    
    - **Simplified Management:**  
        Centralized control removes the need to adjust multiple settings.
        
    - **Enhanced Security & Compliance:**  
        Quickly adhere to internal and external regulations regarding AI usage.
        
    - **Risk Management:**  
        Mitigate risks related to data privacy and unintended AI behaviors.
        
    - **Operational Flexibility:**  
        Easily enable or disable GenAI features to adapt to changing business requirements.
        

---

## Problem Statement

The centralized GenAI control addresses several challenges:

- **Security and Compliance:**  
    Ensures organizations meet regulatory requirements by controlling AI interactions with sensitive data.
    
- **Risk Management:**  
    Provides a mechanism to prevent potential AI-related risks by disabling features when necessary.
    
- **Operational Control:**  
    Simplifies administrative tasks by allowing a single point of control over AI capabilities.
    
- **Flexibility:**  
    Adapts to evolving operational needs by allowing dynamic toggling of AI features.
    

---

## How to Get Started

1. **Add a New AI Trust Layer Policy:**
    
    - Initiate the process by adding a new policy within the Automation Ops section.
        
2. **Configure Product Toggles:**
    
    - Under the **Product Toggles** section, locate the **Enable Document Understanding features** option.
        
    - By default, this toggle is set to **Yes**.
        
    - Disabling this option will remove all generative features across Document Understanding products (e.g., generative annotation in modern projects).
        

---

## Lesson Summary

- The lesson demonstrates a streamlined approach to managing GenAI functionality across UiPath Cloud accounts.
    
- By leveraging a unified control, organizations can improve security, manage risks, and maintain operational flexibility.
    
- This centralized setting simplifies the governance of AI-powered features, ensuring that Document Understanding products comply with organizational policies.
    
---
# Technical Summary: Revamped Validation Station in Apps

This lesson focuses on creating a custom validation application by leveraging the enhanced Validation Station, now integrated with UiPath Apps, to streamline and optimize Document Understanding processes.

---

## Key Learning Objectives

- **Custom Validation Application:**  
    Develop and implement a tailored validation solution for Document Understanding workflows.
    

---

## What's New

- **Integrated Experience:**
    
    - The Validation Station has been revamped and now seamlessly integrated with UiPath Apps.
        
    - It extends functionality to include Communications Mining, delivering a unified experience across IDP automations.
        
- **Enhanced User Interface & Features:**
    
    - A streamlined, sophisticated interface enables more effective human validation of extracted data.
        
    - **Advanced Data Lookups:**  
        Provides enriched contextual information during the validation process.
        
    - **Customizable Interactive Components:**  
        Facilitates end-to-end task processing with workflows that can be tailored to specific business needs and document types.
        

---

## Problems Solved

- **Fragmented User Experience:**  
    Consolidates disparate workflows into a unified validation station, reducing complexity.
    
- **Inefficient Human Validation:**  
    Enhances accuracy and productivity by simplifying manual validation tasks.
    
- **Limited Data Context:**  
    Data lookup features offer additional context, leading to more informed decision-making.
    
- **Inflexible Task Processing:**  
    Customizable components allow for adaptable workflows suited to various operational scenarios.
    

---

## How to Get Started

- **Demo Walkthrough:**  
    Follow the demo provided in the lesson to understand the revamped validation experience.
    
- **Local Implementation:**  
    Resources such as the _ForwardDUAppDemoPackage.zip_ and the _Homeowners Insurance Policy Review - Forward Keynote FINAL.uiapp_ are available to implement the process locally.
    

---

## Lesson Summary

- The lesson demonstrates how to create a custom validation application within the revamped Validation Station.
    
- It covers the benefits of an integrated and customizable approach to Document Understanding, addressing issues like fragmented workflows and limited data context.
    
- This solution improves overall efficiency, accuracy, and adaptability in processing complex document tasks.
    

---

# Technical Summary: Feature Updates in Document Understanding

This lesson explores the latest feature updates introduced in the 2024.10 release of Document Understanding, focusing on enhanced capabilities and new offerings that improve model training, performance, and scalability.

---

## What's New

1. **UiPath DocPath LLM for Custom Document Types (Public Preview):**
    
    - **Purpose:**
        
        - Train models for custom document types.
            
        - Monitor and continuously improve model performance.
            
    - **Benefits:**
        
        - Higher accuracy, especially with complex tables.
            
        - Reduced training effort through active learning.
            
        - Significant time savings for better ROI.
            
2. **DocPath in Active Learning:**
    
    - **Availability:**
        
        - General Availability in the US region.
            
        - Private Preview for regions excluding Invoices China, Japan, and Hebrew until January 2025.
            
3. **Additional General Availability Features:**
    
    - **IntelligentOCR Support for Modern Projects:**  
        Enhances efficiency, scalability, and cost-effectiveness.
        
    - **Generative Features in FedRAMP:**  
        Expands compliance and security in regulated environments.
        
    - **New Document Types in ML Packages:**  
        Adds support for previously previewed document types (e.g., 1040x, 3949a, 709, 941x, 9465, Invoices Hebrew).
        

---

## Why These Updates?

- **Enhanced Accuracy & Efficiency:**  
    Improved models and active learning reduce training effort while increasing overall extraction accuracy.
    
- **Scalability & Cost-effectiveness:**  
    New features support more efficient processing at scale, ensuring a higher ROI.
    
- **Broader Compliance:**  
    Features like generative capabilities in FedRAMP expand the solution’s applicability in regulated industries.
    
- **Expanded Document Support:**  
    Additional document types in ML Packages provide greater versatility in document processing.
    

---

## Lesson Summary

- This lesson covers the key feature updates in the Document Understanding 2024.10 release.
    
- It highlights the introduction of the DocPath LLM, active learning enhancements, and expanded support in IntelligentOCR and ML Packages.
    
- The updates focus on improving model performance, reducing training efforts, and increasing operational efficiency while ensuring regulatory compliance.
    

---
# Technical Summary: Export Dataset from Modern Projects

This lesson demonstrates how to export annotated datasets from modern Document Understanding projects, facilitating data portability between Modern and Classic environments.

---

## Key Learning Objectives

- **Dataset Export:**  
    Learn how to export datasets from modern projects to enable seamless data transfer and model retraining.
    

---

## What's New

- **Data Portability Across Environments:**
    
    - Export annotated datasets from modern projects.
        
    - Import datasets into other modern projects or classic projects (AI Center).
        
- **General Availability Update:**
    
    - The export dataset functionality is now in General Availability.
        

---

## Problems Solved

- **Data Silos:**  
    Enables the transfer of datasets across different project types, breaking down data silos.
    
- **Consistency in Model Performance:**  
    The imported dataset is retrained to deliver model performance nearly identical to the original project.
    
- **Streamlined Migration:**  
    Facilitates smooth transitions between Modern and Classic projects without data loss.
    
- **Resource Efficiency:**  
    Maximizes the value of annotated data, reducing redundant work and saving resources.
    

---

## How to Get Started

1. **Navigate to Export Tab:**
    
    - In the Publish window of your project, access the Export tab.
        
2. **Select Document Type and Version:**
    
    - Choose the relevant document type and version for export.
        
    - **Note:** Only annotated datasets are exported. For classic project imports, the model version must be higher than 2023.4.
        
3. **Download the Dataset:**
    
    - Once the export is configured and prepared, download the dataset to import into another project.
        

---

## Lesson Summary

- The lesson covers the steps to export annotated datasets, addressing data portability, consistency, streamlined migration, and efficient resource utilization in Document Understanding projects.
    

---

# Technical Summary: Advanced Detailed Metrics

**Duration:** 15 minutes

This lesson introduces an advanced metrics feature for modern Document Understanding projects, providing comprehensive insights into model performance at a batch level.

---

## Key Learning Objectives

- **Advanced Metrics Retrieval:**  
    Learn to obtain detailed metrics and model results per batch from modern projects.
    

---

## What's New

- **Enhanced Metrics Feature:**
    
    - In addition to existing metrics (field names, training status counts, accuracy), a new "Download advanced metrics" button is introduced.
        
- **Download Capability:**
    
    - Users can export an Excel file containing detailed batch-specific model results for deeper analysis.
        

---

## Problems Solved

- **Consistency Across Project Types:**  
    Provides a similar level of performance analysis that was previously available in Classic projects via the evaluation_du.xlsx file.
    
- **Detailed Performance Analysis:**  
    Offers granular insights into model performance, enabling better troubleshooting and optimization.
    
- **Familiar Workflow for Classic Users:**  
    Helps users transitioning from Classic to Modern Projects by maintaining a familiar reporting mechanism.
    
- **Data-Driven Decision Making:**  
    Enhances the ability to monitor and improve extraction models through detailed batch analysis.
    

---

## How to Get Started

- **Access Advanced Metrics:**
    
    - In the Measure window, under the Metrics tab, locate and use the "Download advanced metrics" button.
        
    - This function downloads an Excel file with detailed performance metrics per batch, facilitating comprehensive model evaluation.
        

---

## Lesson Summary

- The lesson equips users with the capability to download and analyze advanced metrics for modern Document Understanding projects, ensuring consistency, improved troubleshooting, and informed decision-making.