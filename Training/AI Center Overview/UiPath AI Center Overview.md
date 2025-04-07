## Welcome

This course showcases how **AI Center** enables the deployment and management of machine learning models in automation workflows developed with **UiPath Studio**.

> **Important Update:**  
> Cloud AI Center Open-Source packages, UiPath OOB non-DU Models, and BYOM are being deprecated as part of our product evolution strategy.      

---
## What To Learn

By the end of this course, you should be able to:

1. **Describe** how AI Center works and the types of ML models it can manage.
    
2. **Differentiate** between the available deployment options of AI Center.
    
3. **Recognize** the types of problems that can be solved by deploying machine learning models in automated processes.
    

---

## Prerequisites

This course is designed for certified Automation Developers experienced with production scenarios. Before starting, ensure you have completed the following UiPath Academy learning plans:

### 1. Automation Explorer Learning Plan

- Explore Automation Development with UiPath Studio
    
- Build Your First Process with Studio
    
- Variables, Constants, and Arguments in Studio
    
- Control Flow in Studio
    
- Excel Automation with the Modern Experience in Studio
    
- User Interface Automation with the Modern Experience in Studio

### 2. Automation Developer Associate Learning Plan

- Data Manipulation with Strings in Studio
    
- Data Manipulation with Lists and Dictionaries in Studio
    
- UI Automation Synchronization with Studio
    
- UI Automation Descriptors in Studio
    
- Selectors in Studio: Deep Dive
    
- Debugging in Studio
    
- Error and Exception Handling in Studio
    
- Working with Local Files and Folders in Studio
    
- Email Automation in Studio
    
- PDF Automation with Studio
    
- Data Manipulation with DataTables in Studio
    
- Introduction to Logging in Studio
    
- Orchestrator Overview for Automation Developers
    
- Working with Orchestrator Resources
    
- Object Repository in Studio
    
- UiPath Integration Service Overview
    
- Version Control Systems Integration in Studio
    
- Workflow Analyzer in Studio
    
- RPA Testing with Studio
    
- Project Organization in Studio
    
- Automation Implementation Methodology Fundamentals.

---

## Technical Setup Requirements

To complete this course, you must have access to a **UiPath Platform enterprise environment** which includes:

- **UiPath Document Understanding** (first-party service)
    
- **UiPath AI Center**
    
- **UiPath Action Center**
    
- **AI units** for extraction, retraining, and additional capabilities

---
# What is AI Center?

## What To Learn

By the end of this lesson, you should be able to:

1. **Define AI Center** and position it relative to other UiPath Platform components.
    
2. **Describe how AI Center works** and identify who uses it for automating tasks.
    
3. **List the four types of machine learning models** that can be managed in AI Center.
    

---

## 1. Definition & Positioning

- **AI Center** is a component of the **UiPath Platform** that enables:
    
    - **Deploying**
        
    - **Consuming**
        
    - **Managing**
        
    - **Improving** machine learning models.
        
- It supports models built by:
    
    - In-house data scientists
        
    - UiPath and UiPath partners
        
    - The open-source community
        
- **Role in Automation:**  
    AI Center integrates with UiPath Studio, making it simple to infuse specialized AI into automation workflows. This empowers robots to:
    
    - Process unstructured data
        
    - Handle uncertainty in decision-making
        
    - Work with scenarios that involve numerous variables
        

---

## 2. How AI Center Works

- **Deployment of ML Models:**  
    AI Center allows you to deploy machine learning models directly into automation workflows built with UiPath Studio.
    
- **Infusing Specialized AI:**  
    It makes it extremely easy to add specialized AI capabilities to your automation solutions, enhancing decision-making and data processing.
    

---

## 3. Types of Machine Learning Models Managed in AI Center

- **Bring Your Own Model:**  
    Models built by your own data science team.
    
- **Open-Source Model:**  
    Models created by the data scientist community; these can be managed, trained, and deployed directly within RPA workflows.
    
- **Pick a Model:**  
    Models developed by UiPath technology partners.
    
- **Out-of-the-Box Models:**  
    Pre-built models provided and supported by UiPath.
    

---

## 4. Who Uses AI Center?

The main roles that can benefit from AI Center in your company include:

- **Model Builders:**
    
    - Build and upload ML models to AI Center.
        
- **ROI Improvement Specialists:**
    
    - Deploy models (either developed in-house or provided by UiPath) into ML skills to enhance the ROI of automations.
        
- **Automation Developers:**
    
    - Consume available ML skills within customized RPA workflows where decisions are made by robots.
        

---
# Deployment and Installation

---

## What To Learn

- **Differentiate** between AI Center deployment options.
    
- **Identify** the AI Center installation options available.
    

---

## Deployment Options for AI Center

### 1. In Cloud, as Part of the UiPath Platform

- **Description:**
    
    - Hosted in UiPath Automation Cloud.
        
    - UiPath manages all product infrastructure (including ML models).
        
- **Features:**
    
    - Deploy, manage, and improve ML models on UiPath Automation Cloud.
        
    - No infrastructure or maintenance required.
        
    - Enterprise version comes with an uptime guarantee.
        
    - Frequent patches under the Automation Cloud release cadence.
        
    - Document Understanding metering is done in UiPath cloud.
        
    - **Requirement:** Internet access is required.
        

---

### 2. In Automation Suite, as Part of the UiPath Platform

- **Description:**
    
    - Deploy all server-side products in a single package.
        
    - Can be installed on bare metal, on-premises VMs, or cloud subscriptions.
        
- **Features:**
    
    - Multi-node deployment with automatic scaling and built-in High Availability (HA).
        
    - Monitor, configure, and upgrade within a unified package.
        
    - Deployment profiles must be selected accurately.
        
    - For more details, refer to the deployment architecture documentation.
        

---

### 3. On-Premises Air-Gapped

- **Description:**
    
    - Designed for environments with no internet connection.
        
    - Ideal for highly secure sectors (e.g., public, financial services).
        
- **Features:**
    
    - Deploy, manage, and improve ML models locally.
        
    - Customer-managed infrastructure.
        
    - Fully integrated with on-premises Orchestrator.
        
    - All resources must be manually downloaded and loaded.
        
    - Document Understanding metering is done in Orchestrator.
        
    - **No internet access is required.**
        

---

### 4. On-Premises Online

- **Description:**
    
    - Deployed on the customer’s infrastructure (local server or private cloud).
        
    - Provides control over hosting ML models.
        
- **Features:**
    
    - Deploy, manage, and improve ML models locally.
        
    - Customer-managed infrastructure with automatic retrieval of installer and updates.
        
    - Fully integrated with on-premises Orchestrator.
        
    - Releases patches at a slower cadence.
        
    - Document Understanding metering is done in UiPath cloud.
        

#### Installation Types for On-Premises Online

- **Single-Node Installation:**
    
    - Can be deployed on any physical or virtual machine.
        
    - Includes Kubernetes installation.
        
    - Recommended on fresh cloud VMs (Azure, AWS, or GCP) or bare metal.
        
- **Multi-Node Installation:**
    
    - Enables running many ML Skills and training pipelines with high availability and scalability.
        
    - Bundled Kubernetes deployment for multi-node configuration.
        
    - Recommended on fresh cloud VMs (Azure, AWS, or GCP) and supports Azure Kubernetes Service, as well as bare-metal installations.
        

---

### 5. Hybrid Mode (Cloud AI Center + Orchestrator On-Premises)

- **Description:**
    
    - AI Center is hosted in UiPath Automation Cloud while keeping the existing on-premises Orchestrator.
        
- **Features:**
    
    - Robots remain connected to the on-premises Orchestrator.
        
    - Robots can call ML Skills to upload data to a dataset.
        
    - New ML Services activities enable use of Public ML Skills and Public datasets.
        
    - Benefit from cloud advantages without migrating Orchestrator.
        
    - Frequent patches following the cloud platform release cadence.
        
    - No installation or management required on the AI Center.
        
    - Document Understanding metering is done in UiPath cloud.
        
    - **Requirement:** Internet access is required.
        

---

## Important Notes

- **Deployment Profiles:**  
    Once the deployment starts, you **cannot switch/upgrade** from one deployment profile to another.

---
# Identifying Use Cases

---

## What You'll Learn

1. **Recognize the types of problems** that can be solved by deploying machine learning models in automated processes.
    
2. **Present applications** of the out-of-the-box ML packages available in AI Center.
    

---

## Use Cases for AI Center

With AI Center, the universe of automation opportunities expands tremendously. Organizations can now identify and prioritize a wide range of new opportunities by deploying machine learning models to automate tasks. This enables robots to process complex data such as documents, language, images, and tabular information.

---

## Applications of the Out-of-the-Box Packages

- **Pre-built ML Models:**
    
    - Over 25 pre-built models are available.
        
    - Models are designed to handle various data types:
        
        - **Documents:** Allow robots to understand and process document data.
            
        - **Language:** Enable natural language processing for text comprehension and generation.
            
        - **Images:** Facilitate image analysis and processing.
            
        - **Tabular Data:** Extract insights from structured data.
            
- **Industry-Specific Solutions:**
    
    - A variety of verticals are supported, each with specialized form types and corresponding models.
        
    - Choose a pre-built model that best fits your business needs—with no advanced data science background required.
        

![[Pasted image 20250406192537.png]]
![[Pasted image 20250406192540.png]]
![[Pasted image 20250406192544.png]]

