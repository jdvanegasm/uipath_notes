## Course Overview

This course provides a concise overview of the most important updates introduced in the 2024 April snapshot of the UiPath Business Automation Platform. It covers both enhancements to existing components and the introduction of new ones, offering guidance on how to leverage these changes to optimize your automation initiatives.

---

## Learning Objectives

By the end of this course, you will be able to:

1. **Describe the Updates:**
    
    - Understand the key changes and new features for each component of the UiPath Platform.
        
2. **Position New Components:**
    
    - Identify where the new capabilities fit within the overall platform ecosystem.
        
3. **Access Additional Resources:**
    
    - Locate further documentation, release notes, and training materials for deep dives into each new feature.
        

---

## How to Get the Most Out of This Course

- **Tailored Learning:**
    
    - If you’re focused on a specific product (e.g., Test Suite), you can navigate directly to that lesson.
        
- **Prerequisites:**
    
    - This course assumes you are already familiar with the existing UiPath products. It focuses solely on new features.
        
- **Additional Learning:**
    
    - Each lesson provides quick overviews, short videos, GIFs, screenshots, or text explanations followed by links to detailed resources and documentation.
        
- **Level:**
    
    - The course is introductory in nature, offering an overview of the updates with pointers to more in-depth courses for further study.
        

---

## Course Structure & Content

### 1. Overview of the UiPath Business Automation Platform

- **Integration of RPA and AI:**
    
    - Combines robust RPA capabilities with advanced AI/ML technologies.
        
- **Automation Spectrum:**
    
    - From identifying automation opportunities to building, deploying, and managing enterprise-grade automation solutions.
        

### 2. Key Components Covered

- **Discover Capabilities:**
    
    - Data mining techniques including process mining, task mining, and communications mining.
        
    - Automation idea lifecycle management to identify high-ROI opportunities.
        
- **Automate Components:**
    
    - Low-code development and UI/API automation.
        
    - Intelligent Document Processing and integrated NLP/AI capabilities.
        
    - Process orchestration and rapid automation development.
        
- **Operate Tools:**
    
    - Analytics, continuous testing, unified management, and flexible deployment options for running and optimizing automation programs.
        

### 3. Learning Resources Provided

- **Lesson Structure:**
    
    - Each lesson starts with a list of new features by product.
        
    - Followed by in-depth explanations using multimedia (videos, GIFs, screenshots).
        
    - Additional resources and direct links to release notes and official documentation.
        

---

## Conclusion

This course offers a high-level snapshot of the new features in the 2024 April release of the UiPath Business Automation Platform. It is designed to help you quickly grasp the key updates, understand their placement within the overall platform, and find resources for deeper technical exploration. Whether you're enhancing existing automation workflows or exploring new opportunities, this course is your guide to navigating the latest innovations in UiPath.

![[Pasted image 20250413195133.png]]

# What's New in the Discover Phase – Technical Summary

## Process Mining Updates

- **New Process Models:**
    
    - Two new process models enable users to uncover exclusive choices, parallel activities, and complex loops within business processes.
        
    - Import BPMN models as reference models directly into the application.
        
- **Autopilot™:**
    
    - An AI-powered helper now available to assist Process Mining users, offering intelligent insights and recommendations to streamline process discovery.
        

## Task Mining Updates

- **Assisted Task Mining for Japanese Applications:**
    
    - Now supports capturing processes executed in Japanese-language applications, broadening its global applicability.
        

## Communications Mining Updates

- **Dispatcher Framework Template:**
    
    - Provides a ready-to-use template for initiating automation projects in Studio, simplifying the transition from discovery to automation.
        
- **Customizable Roles and Permissions:**
    
    - Enhanced capabilities for defining and managing user roles and permissions within the Communications Mining component.
        

![[Pasted image 20250413195234.png]]

---

# What's New in UiPath Process Mining – 2024.4 Update

## New Features

1. **Discover Process Model**
    
    - **What It Is:**
        
        - A new option among three process models that automatically identifies activities in parallel, decision points, and complex loops.
            
    - **Why It's Useful:**
        
        - Captures non-linear process flows better than the previous linear "Directly Follows" model, providing deeper insights into real-world processes.
            
    - **More Info:**
        
        - [Discover Process Model - Official documentation](https://docs.uipath.com/)
            
2. **Import BPMN Model**
    
    - **What It Is:**
        
        - Enables users to import their own BPMN 2.0 process models (supporting start/end events, tasks, exclusive and parallel gateways, and sequence flows) to serve as reference models in Process Mining apps.
            
    - **Why It's Useful:**
        
        - Facilitates cross-team collaboration and process optimization by allowing comparisons between as-is processes and intended to-be models.
            
    - **More Info:**
        
        - [Import BPMN Model - Official documentation](https://docs.uipath.com/)
            
3. **Conformance Checking Dashboard**
    
    - **What It Is:**
        
        - A new dashboard feature that lets users assess whether the actual process conforms to the Discover or Import BPMN models.
            
    - **Why It's Useful:**
        
        - Helps identify compliance issues, deviations from the standard process, and opportunities for process improvement.
            
    - **More Info:**
        
        - [Conformance Checking - Official documentation](https://docs.uipath.com/)
            
4. **Flexible Data Model**
    
    - **What It Is:**
        
        - A customizable data model feature that allows developers to add or remove tables and create unlimited custom fields within Process Mining apps.
            
    - **Why It's Useful:**
        
        - Enables tailored data structures that fit specific business needs, ensuring only relevant data is used in analysis and visualization.
            
    - **More Info:**
        
        - [Adding Tables - Official documentation](https://docs.uipath.com/)
            
        - [Adding Fields - Official documentation](https://docs.uipath.com/)
            
5. **Autopilot™ for Process Mining**
    
    - **What It Is:**
        
        - An AI-powered assistant that leverages conversational AI to help business users with filter selection, interpreting process graphs by highlighting inefficiencies, and recommending tailored charts.
            
    - **Why It's Useful:**
        
        - Accelerates data interpretation, reduces manual filtering, and simplifies dashboard navigation, making it easier for users to derive actionable insights.
            
    - **More Info:**
        
        - [Autopilot for Process Mining - Official documentation](https://docs.uipath.com/)
            

---

# What's New in Task Mining & Communications Mining – 2024.4 Updates

### New Feature: Assisted Task Mining in Japanese

- **What It Is:**
    
    - Assisted Task Mining now supports Japanese, allowing users to record tasks in applications displayed in Japanese.
        
    - By default, the recording language is English; however, you can select Japanese when creating a new Assisted Task Mining project.
        
- **Why It’s Useful:**
    
    - Expands the usability of Task Mining to non-English environments, supporting global and localized automation initiatives.
        
- **More Details:**
    
    - For technical guidance, refer to the [Changing the Recording Language (ATM) - Official documentation](https://docs.uipath.com/).
        

---

## Communications Mining (Duration: 5 minutes)

### New Feature 1: Communications Mining Dispatcher Framework in UiPath Studio

- **What It Is:**
    
    - An officially supported template within UiPath Studio designed to kick-start projects that leverage Communications Mining.
        
    - The Dispatcher Framework simplifies the process by handling stream consumption and queue item creation.
        
- **Why It’s Useful:**
    
    - It provides a ready-to-use starting point, reducing setup time and complexity, and enabling developers to focus on configuring specific business logic.
        
- **More Details:**
    
    - For further technical details, check the [Dispatcher Framework - Official documentation](https://docs.uipath.com/).
        

### New Feature 2: Assignable User Roles

- **What It Is:**
    
    - Enhancements in the Manage Access page now allow assigning both global and project-specific user roles in Communications Mining.
        
    - Users can have different roles across multiple projects, and current users are automatically assigned roles based on their existing permissions.
        
- **Why It’s Useful:**
    
    - Enables tighter data access control, essential for organizations handling sensitive information.
        
    - Simplifies the management of user permissions and enhances governance over project structures.
        
- **More Details:**
    
    - For more information, refer to the [Manage Access - Official documentation](https://docs.uipath.com/).
        
These updates in Task Mining and Communications Mining for the 2024.4 release enhance language support, streamline workflow development, and improve access control—empowering organizations to leverage automation more effectively in diverse environments.

---
![[Pasted image 20250413195445.png]]

# What's New in the Automate Phase – 2024.4 Update

The 2024.4 release brings several exciting updates in the Automate phase of the UiPath Business Automation Platform. These updates span across multiple components such as Studio, Studio Web, Apps, Integration Service, Document Understanding, and more. Below is a technical summary of the key new features:

---

## UiPath Studio Updates (Duration: 10 minutes)

### 1. **UiPath Autopilot™ for Studio**

- **What It Is:**
    
    - An AI-powered feature that assists in building workflows using natural language.
        
- **How It Works:**
    
    - **Expression Editor:** Generate expressions from natural language descriptions.
        
    - **Coded Workflows:** Automatically write code by simply describing desired methods.
        
    - **Command Palette/Annotation:** Add activities to workflows by describing the automation steps.
        
- **Why It’s Useful:**
    
    - Simplifies development for both citizen developers and seasoned RPA developers by reducing the need for extensive coding.
        
- **Additional Resources:**
    
    - Refer to the official UiPath blog post "Announcing UiPath Autopilot™" for in-depth insights.
        

### 2. **Edit Activities During Debug**

- **What It Is:**
    
    - A debugging enhancement that allows you to modify workflows on the fly.
        
- **How It Works:**
    
    - Changes can be applied and tested immediately without halting the debugging session.
        
- **Why It’s Useful:**
    
    - Increases debugging efficiency, enabling real-time corrections and faster development cycles.
        
- **Additional Resources:**
    
    - Visit the UiPath Forum for discussions and tips on editing during debug.
        

### 3. **Indicate Target in Runtime Errors**

- **What It Is:**
    
    - A feature that prompts users to specify a new UI element when the target element is not found.
        
- **How It Works:**
    
    - Applicable to key UI activities (e.g., Click, Type Into, Use Application/Browser).
        
    - Enable via the "Ask user on runtime error" option in Project Settings under UI Automation Modern.
        
- **Why It’s Useful:**
    
    - Allows the automation to continue in real-time by resolving element identification issues during both debugging and attended executions.
        

---

## UiPath Studio Web Updates

- **Enhanced Enterprise Capabilities:**
    
    - **Real-Time Property and Output Value Visualization:**
        
        - View detailed properties and output values during trigger testing.
            
    - **Workflow Linking:**
        
        - Easily connect and link multiple workflows within a project.
            
    - **Simplified Backstage View:**
        
        - A new, streamlined interface that improves navigation and project management.
            

---

## Additional Automate Phase Updates

### UiPath Apps

- **New Features:**
    
    - **Autopilot™ for Apps:**
        
        - Integrates AI-powered capabilities to streamline app development.
            
    - **Action Center Integration:**
        
        - Enhanced features that allow apps to trigger actions and receive insights directly in Action Center.
            

### Integration Service Enhancements

- **New Connectors:**
    
    - Connectors for cutting-edge applications like UiPath Gen AI, Pinecone, and IBM WatsonX enhance API automation capabilities.
        

### Assistant & Automation Cloud Robots

- **Bring-Your-Own-Image for VMs:**
    
    - Customize VMs for Automation Cloud Robots with your own images, improving consistency and control in deployment.
        

### Document Understanding Modernization

- **Generative & Specialized AI Integration:**
    
    - A revamped approach that combines generative AI with specialized AI, streamlining model creation through active learning.
        
- **New OCR Engine:**
    
    - Now supports 200+ languages for enhanced digitization.
        
- **API Availability:**
    
    - The new Document Understanding experience is fully accessible via APIs for more flexible integrations.
        

### Action Center Enhancements

- **Integration with Insights:**
    
    - Better linkage between Action Center and UiPath Insights, allowing for improved monitoring and decision-making.
        

---

## Summary

The 2024.4 update to the Automate phase significantly boosts developer productivity and simplifies the automation process:

- **Studio Enhancements:**
    
    - Autopilot for Studio, real-time debug editing, and UI element targeting during runtime errors streamline development and debugging.
        
- **Studio Web Improvements:**
    
    - Enhanced visibility and workflow connectivity in Studio Web make it a powerful enterprise automation tool.
        
- **Broad Ecosystem Upgrades:**
    
    - New capabilities in Apps, Integration Service, Document Understanding, and Action Center provide comprehensive enhancements across the platform.
        

These updates collectively enable faster, more efficient, and more flexible automation, ensuring that your organization can leverage cutting-edge technology to transform business processes.

For further details, consult the official documentation and training resources provided with each component.

--- 

# What's New in the Automate Phase – 2024.4 Update

The 2024.4 release brings a wide range of new features across the Automate phase, significantly enhancing productivity and developer experience. These updates span across several key components, including UiPath Studio, Studio Web, Apps, and Integration Service. Below is an organized technical summary of the major updates:

---

## 1. UiPath Studio Updates (Duration: 10 minutes)

### **UiPath Autopilot™ for Studio**

- **What It Is:**
    
    - An AI-powered assistant that generates workflow components from natural language descriptions.
        
    - Functions in three ways:
        
        - In the Expression Editor: Generates expressions from plain language.
            
        - In coded workflows: Writes code by describing desired methods.
            
        - Via the command palette or annotations: Automatically adds activities to a sequence.
            
- **Why It’s Useful:**
    
    - Simplifies development for both citizen and professional developers.
        
    - Reduces coding complexity and accelerates workflow creation.
        

### **Edit Activities During Debug**

- **What It Is:**
    
    - An enhancement that allows modifications to activities on-the-fly while debugging.
        
- **Why It’s Useful:**
    
    - Improves debugging efficiency by enabling real-time changes without halting execution.
        

### **Indicate Target in Runtime Errors**

- **What It Is:**
    
    - A feature that lets users specify a new target element when the original element is not found during runtime.
        
- **Why It’s Useful:**
    
    - Enhances error recovery in UI automation by allowing seamless user intervention during both debugging and live runs.
        

---

## 2. UiPath Studio Web Updates (Duration: 5 minutes)

### **Improved Trigger Testing**

- **What It Is:**
    
    - The Output panel now displays properties and returned test values for matching trigger items.
        
- **Why It’s Useful:**
    
    - Increases efficiency and debugging capability by making trigger outputs and test values readily available.
        

### **Linking Multiple Workflow Files**

- **What It Is:**
    
    - New options to link workflows via drag-and-drop or an ‘Invoke in current workflow’ option.
        
- **Why It’s Useful:**
    
    - Simplifies project organization and improves workflow modularity.
        

### **AI Computer Vision in Unified Target**

- **What It Is:**
    
    - Integration of AI Computer Vision as a targeting method for Studio Web.
        
- **Why It’s Useful:**
    
    - Enhances cross-platform automation where traditional selectors are not available.
        

### **Simplified Backstage View**

- **What It Is:**
    
    - A redesigned backstage interface with fewer tabs, enhanced ordering, filtering options, and a customizable default view.
        
- **Why It’s Useful:**
    
    - Improves the overall user experience and streamlines project management.
        

---

## 3. UiPath Apps Updates (Duration: 10 minutes)

### **Apps for Action Center (Preview)**

- **What It Is:**
    
    - Allows users to design the UI for Action Center tasks directly in UiPath Apps.
        
- **Why It’s Useful:**
    
    - Enables real-time data retrieval, integrated automation, and streamlined data management through dynamic app interfaces.
        

### **Autopilot™ for Apps**

- **What It Is:**
    
    - A generative AI-powered feature that converts various data sources (text, images, PDFs) into fully functional apps.
        
- **Why It’s Useful:**
    
    - Accelerates app creation by automatically incorporating controls and Data Service entities, reducing manual work.
        

### **Integration Service Connections in Apps**

- **What It Is:**
    
    - Directly add connectors from UiPath Integration Service as controls in your apps.
        
- **Why It’s Useful:**
    
    - Extends app functionality by seamlessly binding API data to UI elements.
        

### **Custom HTML Control**

- **What It Is:**
    
    - Enables creation of custom, interactive controls using HTML, CSS, and JavaScript.
        
- **Why It’s Useful:**
    
    - Offers developers enhanced flexibility to extend app capabilities beyond standard controls.
        

### **Custom List Control**

- **What It Is:**
    
    - A control for displaying lists of records with customizable templates, utilizing the ThisRow keyword for data retrieval.
        
- **Why It’s Useful:**
    
    - Improves data presentation and user experience by allowing tailored list views.
        

---

## 4. Integration Service Updates (Duration: 5 minutes)

### **New Connectors**

- **What It Is:**
    
    - Additional connectors for:
        
        - **UiPath GenAI:** Directly work with foundational AI models.
            
        - **Pinecone:** Utilize a vector database for generative AI applications.
            
        - **IBM WatsonX:** Access IBM’s generative AI tools and large language models.
            
        - **Shopify:** Automate e-commerce processes like order sync, inventory updates, and marketing automation.
            
- **Why It’s Useful:**
    
    - Expands integration capabilities, allowing automation of diverse and complex processes with industry-leading services.
        

### **Activity Designer (Preview)**

- **What It Is:**
    
    - A new tool that previews how custom Integration Service activities will appear in UiPath Studio.
        
    - Allows visualization of layout, parameter settings, and request/response fields.
        
- **Why It’s Useful:**
    
    - Provides immediate feedback on activity configuration, ensuring that custom activities are correctly designed before deployment.
        

---

## 5. Additional Highlights

- **Bring-Your-Own-Image for VMs:**
    
    - Allows users to use custom images for Automation Cloud Robots, enhancing deployment consistency and control.
        
- **Document Understanding Modernization:**
    
    - Integration of Generative AI with Specialized AI for active learning, plus a new OCR engine supporting 200+ languages and full API availability.
        
- **Action Center Integration with Insights:**
    
    - Better linkage between Action Center and UiPath Insights, streamlining performance monitoring and decision-making.
        

---

## Summary

The 2024.4 release significantly enhances the Automate phase by:

- **Improving Developer Productivity:**
    
    - Through advanced features in Studio and Studio Web (Autopilot, real-time debug editing, and UI element targeting).
        
- **Enhancing App Development:**
    
    - Via new features in UiPath Apps such as Autopilot for Apps, custom controls, and integration with Action Center.
        
- **Expanding API Automation:**
    
    - With new connectors and the Activity Designer in Integration Service, enabling more robust integrations.
        
- **Optimizing Deployment:**
    
    - With options for custom VM images and improved Document Understanding capabilities.
        

These updates collectively empower developers and business users to build, deploy, and manage automation solutions more efficiently and effectively. For more detailed information, refer to the official documentation and training resources provided by UiPath.

---

# What's New in the Automate Phase – 2024.4 Update: Technical Summary


The 2024.4 release brings a host of powerful updates that streamline automation development, enhance productivity, and broaden integration capabilities across the UiPath platform. Here’s a high-level overview of the key enhancements:

---

## UiPath Studio

- **UiPath Autopilot™ for Studio:**
    
    - **Features:**
        
        - Generate expressions, code, and complete workflow activities from natural language descriptions.
            
        - Works in the Expression Editor, coded workflows, and via command palette annotations.
            
    - **Benefits:**
        
        - Reduces coding complexity and accelerates development, making it accessible for citizen developers and experts alike.
            
- **Edit Activities During Debug:**
    
    - **Features:**
        
        - Modify and test workflow changes in real-time during debugging without halting the session.
            
    - **Benefits:**
        
        - Enhances debugging efficiency and reduces downtime during development.
            
- **Indicate Target in Runtime Errors:**
    
    - **Features:**
        
        - Prompts users to specify an alternative UI element when the intended target isn’t found.
            
    - **Benefits:**
        
        - Minimizes workflow interruptions and improves error recovery in both debug and attended scenarios.
            

---

## UiPath Studio Web

- **Improved Trigger Testing:**
    
    - **Features:**
        
        - Displays detailed properties and test output values for triggers, including suggestions if no match is found.
            
    - **Benefits:**
        
        - Facilitates faster troubleshooting and more accurate trigger-based automation.
            
- **Enhanced Workflow Linking:**
    
    - **Features:**
        
        - Drag-and-drop linking and an ‘Invoke in current workflow’ option for connecting multiple workflows.
            
    - **Benefits:**
        
        - Simplifies project organization and improves modularity.
            
- **AI Computer Vision in Unified Target:**
    
    - **Features:**
        
        - Incorporates AI Computer Vision as a targeting method for projects.
            
    - **Benefits:**
        
        - Enables automation in scenarios where traditional selectors are ineffective.
            
- **Simplified Backstage View:**
    
    - **Features:**
        
        - Redesigned backstage interface with streamlined tabs, improved ordering, and filtering options.
            
    - **Benefits:**
        
        - Enhances overall user experience and simplifies project management.
            

---

## UiPath Apps

- **Apps for Action Center (Preview):**
    
    - **Features:**
        
        - Develop apps that serve as the primary interface for interacting with Action Center tasks.
            
        - Supports dynamic data retrieval through web service calls.
            
    - **Benefits:**
        
        - Offers real-time insights and integrated automation, streamlining human-in-the-loop processes.
            
- **Autopilot™ for Apps:**
    
    - **Features:**
        
        - Automatically converts various data sources (text, images, PDFs) into fully functional apps.
            
    - **Benefits:**
        
        - Reduces manual app development effort and accelerates time-to-market.
            
- **Integration Service Connections in Apps:**
    
    - **Features:**
        
        - Directly add Integration Service connectors as controls to bind API data to UI elements.
            
    - **Benefits:**
        
        - Enhances app functionality and simplifies data integration.
            
- **Custom HTML & Custom List Controls:**
    
    - **Features:**
        
        - Custom HTML control enables interactive controls using HTML/CSS/JavaScript.
            
        - Custom List control allows for tailored list templates using the ThisRow keyword.
            
    - **Benefits:**
        
        - Expands the flexibility and customization options for app development.
            

---

## Integration Service

- **New Connectors:**
    
    - **Features:**
        
        - Added connectors for UiPath GenAI, Pinecone, IBM WatsonX, and Shopify.
            
    - **Benefits:**
        
        - Broadens the scope for API automation and enhances the integration with leading external services.
            
- **Activity Designer (Preview):**
    
    - **Features:**
        
        - Preview custom Integration Service activities before deployment, including parameter configuration and layout visualization.
            
    - **Benefits:**
        
        - Provides immediate feedback and ensures activities are properly configured prior to use.
            

---

## UiPath Assistant

- **Autopilot™ for Assistant (Preview):**
    
    - **Features:**
        
        - Leverages Generative AI to assist with daily automation tasks within the Assistant interface.
            
    - **Benefits:**
        
        - Increases productivity by automating routine tasks and aiding in brainstorming new automation ideas.
            
- **Diagnostic Reports for Assistant Errors:**
    
    - **Features:**
        
        - Generates detailed diagnostic reports when errors occur, allowing users to share insights with technical support.
            
    - **Benefits:**
        
        - Streamlines support processes and accelerates problem resolution.
            

---

## Automation Cloud Robots

- **Delayed Auto-Update Option:**
    
    - **Features:**
        
        - Allows postponing updates by one Enterprise version, while critical security updates are still pushed immediately.
            
    - **Benefits:**
        
        - Provides greater control over software updates, reducing potential disruptions.
            
- **Bring Your Own Image (BYOI):**
    
    - **Features:**
        
        - Provision VMs using custom images from your cloud subscription.
            
    - **Benefits:**
        
        - Simplifies deployment and software installation, saving time and enabling customized robot accounts.
            

---

## UiPath Document Understanding

- **Active Learning:**
    
    - **Features:**
        
        - Interactive model training that reduces data and time requirements by up to 80%, with guided annotation and expert recommendations.
            
    - **Benefits:**
        
        - Empowers users to train models without coding, with real-time analytics and continuous improvement.
            
- **UiPath Extended Languages OCR:**
    
    - **Features:**
        
        - Supports over 200 languages, including complex scripts and right-to-left languages.
            
    - **Benefits:**
        
        - Ensures accurate digitization in multilingual environments.
            
- **Generative Validation:**
    
    - **Features:**
        
        - Uses Generative AI to automatically validate extracted data against predefined rules.
            
    - **Benefits:**
        
        - Enhances data extraction accuracy and reduces manual intervention.
            
- **Generative Extraction, Classification & Validation via APIs:**
    
    - **Features:**
        
        - Offers advanced, generative-based document processing capabilities accessible through APIs.
            
    - **Benefits:**
        
        - Enables developers to integrate state-of-the-art AI capabilities into custom automation solutions.
            

---

## Next Steps: Action Center

- **Coming Up:**
    
    - After exploring the Automate phase, the next module will cover the latest updates in Action Center, further enhancing task management and human-in-the-loop processes.
        

---

# What's New in UiPath Action Center – 2024.4 Update
## New Features

### 1. Apps in Action Center (Preview)

- **What It Is:**
    
    - Develop apps in UiPath Apps to serve as the primary user interface for managing and interacting with human actions within Action Center.
        
    - Supports dynamic data retrieval through web service calls and provides a more customer-centric task experience.
        
- **Key Benefits:**
    
    - **Real-Time Data Access:** Ensures users receive up-to-date information when making decisions.
        
    - **Integrated Automation:** Enables automated processes to be triggered directly within action tasks.
        
    - **Streamlined Data Management:** Centralizes data handling with capabilities like queue item creation and storage buckets.
        
    - **Enhanced Data Persistence:** Leverages UiPath Data Service entities to maintain data integrity throughout task lifecycles.
        
- **Additional Resources:**
    
    - [Creating Action Definitions - Official Documentation](https://docs.uipath.com/)
        
    - [Create App Task - Official Documentation](https://docs.uipath.com/)
        
    - [Leveraging Actions in Your App - Official Documentation](https://docs.uipath.com/)
        

---

### 2. Action Center-Insights Integration

- **What It Is:**
    
    - Integrates Action Center with UiPath Insights, allowing you to visualize and analyze key business metrics related to human tasks.
        
    - Includes a dedicated Actions dashboard template in Insights and the option to build custom dashboards.
        
- **Key Benefits:**
    
    - **Enhanced Visibility:** Monitor how human actions impact overall process performance.
        
    - **Operational Reporting:** Provides detailed insights into task handling and productivity.
        
    - **Data-Driven Improvement:** Helps optimize task management processes with actionable metrics.
        
- **Additional Resources:**
    
    - [Enabling Actions Dashboard - Official Documentation](https://docs.uipath.com/)
        
    - [The Actions Dashboard - Official Documentation](https://docs.uipath.com/)
        
    - [Action Center Data Model - Official Documentation](https://docs.uipath.com/)
        

---
![[Pasted image 20250413200245.png]]

# What's New in the Operate Phase – 2024.4 Update

The 2024.4 release enhances the Operate phase with powerful new features to monitor, manage, and deploy your automation at scale. These updates help you measure impact, manage environments more effectively, and simplify licensing and solution deployment across the UiPath Platform.

---

## 1. UiPath Insights Updates

- **Real-Time Monitoring (Preview):**
    
    - **What It Is:**
        
        - Offers three dashboard templates—Real-time processes, Real-time queues, and Real-time machines—providing in-progress views with approximately 1-minute latency.
            
    - **Benefits:**
        
        - Enables near real-time visibility into job, queue, and machine performance, aiding quick operational decisions.
            
- **Actions Dashboard Template:**
    
    - **What It Is:**
        
        - A pre-built dashboard template for UiPath Action Center, offering a summary of pending actions, actions nearing SLA, and breached SLAs per user.
            
    - **Benefits:**
        
        - Increases productivity by providing an at-a-glance view of task statuses and operational efficiency in Action Center.
            
- **Document Understanding Dashboard Templates:**
    
    - **What It Is:**
        
        - Dashboard templates to monitor Document Understanding projects, tracking workflow runs, time saved, processed projects, and performance metrics (e.g., classification, extraction, training, and validation).
            
    - **Benefits:**
        
        - Provides actionable insights into your document processing performance, helping to optimize workflows and improve accuracy.
            
- **Insights for All:**
    
    - **What It Is:**
        
        - A read-only version of Insights that allows your entire organization to view dashboards and data without making modifications.
            
    - **Benefits:**
        
        - Promotes data transparency and informed decision-making across the company.
            

---

## 2. UiPath Orchestrator Updates

- **Checking Assigned Roles and Permissions:**
    
    - **What It Is:**
        
        - New capability to easily verify permissions assigned at both tenant and folder levels.
            
    - **Benefits:**
        
        - Simplifies administration and reduces operational risks by enabling on-the-fly adjustments.
            
- **Historical Monitoring:**
    
    - **What It Is:**
        
        - In addition to real-time views, historical monitoring now provides data from the past two years.
            
    - **Benefits:**
        
        - Allows for trend analysis and verification of past events, supporting long-term performance evaluation.
            
- **Video Timeline:**
    
    - **What It Is:**
        
        - A new feature that displays video recordings of job executions alongside text logs.
            
    - **Benefits:**
        
        - Enhances troubleshooting by combining visual context with detailed log data.
            

---

## 3. Introducing Solutions Management

- **What It Is:**
    
    - A new concept that bundles all components of an automation—code, data, APIs, versioning, and configuration—into a comprehensive package called a UiPath solution.
        
- **Solutions Management Features:**
    
    - Helps manage the entire lifecycle of your automation solutions.
        
    - Facilitates the transfer of solutions between environments and simplifies deployment with environment-specific configurations.
        
- **Access Requirements:**
    
    - Available to Automation Cloud users with access to Automation Ops and assigned roles such as Solutions Contributor or Solutions Administrator.
        
- **Benefits:**
    
    - Streamlines solution deployment, versioning, and lifecycle management across the enterprise.
        

---

## 4. Licensing Updates

- **Deprecation of Legacy License Management:**
    
    - **What It Is:**
        
        - Legacy license management will be deprecated in October 2025, transitioning fully to user license management.
            
    - **Benefits:**
        
        - Enables better visibility and management of user licenses at the organizational level.
            
- **Introduction of SAP Transport Units:**
    
    - **What It Is:**
        
        - A new service consumption unit for licensing the SAP Change Impact Analysis feature in UiPath Test Manager.
            
    - **Benefits:**
        
        - Ensures that only the initial analysis of each unique SAP transport consumes units, avoiding redundant charges.
            
- **Simplified Consumption Model for Document Understanding:**
    
    - **What It Is:**
        
        - A new charging logic for Document Understanding modern projects where each page is charged as follows:
            
            - OCR only → 1 AI unit/page
                
            - OCR + classification → 1 AI unit/page
                
            - OCR + classification + extraction → 1 AI unit/page
                
            - OCR + classification + extraction + generative validation → 2 AI units/page
                
    - **Benefits:**
        
        - Simplifies cost calculations and allows for free training and experimentation without incurring extra AI unit charges.
            

---

## Summary

The 2024.4 updates in the Operate phase provide enhanced visibility and control over your automation environment with:

- **Insights:** Real-time monitoring, comprehensive dashboards for Action Center and Document Understanding, and a read-only version for the entire company.
    
- **Orchestrator:** Improved role and permission management, historical data monitoring, and a video timeline for enhanced troubleshooting.
    
- **Solutions Management:** A new unified approach for packaging and deploying complete automation solutions.
    
- **Licensing:** A streamlined licensing model with the deprecation of legacy management, new SAP Transport Units, and a simplified consumption model for Document Understanding.
    

These features empower organizations to monitor, manage, and optimize their automation initiatives effectively, ensuring robust performance and streamlined operations across the UiPath Platform.

For more detailed technical information, refer to the official documentation and additional learning resources provided by UiPath.