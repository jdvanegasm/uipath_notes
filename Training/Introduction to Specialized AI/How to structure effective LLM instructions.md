This summary outlines how to structure effective LLM instructions with XML. It is designed to help you create clear, organized, and machine-readable prompts that guide language models precisely.

---

## 1. Why Use XML?

- **Clear Organization:**
    
    - Use tags like `<instructions>`, `<search_instructions>`, `<synthesizing_response>`, `<response_formatting>`, and `<response_instructions>` to separate and organize different types of guidance.
        
- **Information Hierarchy:**
    
    - The nested structure reflects priority and relationships among instruction sets.
        
- **Machine-Readable:**
    
    - Standardized XML makes it easy for the model to parse and apply instructions.
        
- **Explicit Boundaries:**
    
    - Opening and closing tags ensure unambiguous instruction segments.
        
- **Easy Referencing:**
    
    - Structured format allows the AI to quickly locate specific sections when needed.
        

---

## 2. Core Components

### A. Core Task / Focus

- **Definition:**
    
    - Specify the overall role and objective (e.g., assisting a clinician with plasma donor assessments).
        
- **Example:**
    
    - _"You are an AI assistant supporting a clinician at [COMPANY] for plasma donor eligibility intake and assessments."_
        

### B. Document Descriptions

- **Purpose:**
    
    - Describe which documents to reference for specific clinical scenarios.
        
- **Documents Include:**
    
    - **Medical Review of Donor Results:** Procedures for evaluating donor test results.
        
    - **Managing the MSM Program:** Guidelines for managing plasma donations from male donors with specific histories.
        
    - **Health Assessment:** Detailed protocols for health assessments in plasma donation.
        
    - **Applicant Donor:** Work instructions for managing new or lapsed donor intake.
        
    - **Medical Review of Donor Suitability:** Guidelines for assessing donor eligibility.
        
    - **Medical Staff References:** Eligibility criteria and deferral periods.
        
    - **Medication List:** Medications impacting donation eligibility.
        
    - **Screening Test Trending Review Actions Table:** Procedures for reviewing donor screening test results.
        
    - **Talking Points Indeterminate Gender Donation:** Guidelines for indeterminate gender donation.
        

---

## 3. Detailed XML Instruction Structure

### XML Example

```xml
<instructions>
  <search_instructions>
    <!-- Provide step-by-step rules for performing multiple searches. -->
    <!-- Example: Context Grounding and specific document searches based on conditions. -->
  </search_instructions>
  
  <synthesizing_response>
    <!-- Rules for compiling a complete response: -->
    <!-- - Ensure response is concise and only includes relevant text. -->
    <!-- - Use exact text from search results without personal interpretation. -->
    <!-- - Clearly state if no relevant information is found. -->
  </synthesizing_response>
  
  <response_formatting>
    <!-- Guidelines for output formatting: -->
    <!-- - Use line breaks and bold formatting for readability. -->
    <!-- - Use structured tables for 'if...then...' formats. -->
    <!-- - Display all text exactly as found, without rephrasing. -->
  </response_formatting>
  
  <response_instructions>
    <!-- Provide the ideal structure for responses based on search results: -->
    <!-- - When information is found: include an introduction, cited sections, and follow-up questions (in bold). -->
    <!-- - When not found: clearly indicate, list potentially relevant sections, and provide reasoning. -->
  </response_instructions>
</instructions>
```

---

## 4. Key Guidelines and Best Practices

- **Follow All Instructions Exactly:**
    
    - The AI must adhere to every detail of the XML instructions without deviation.
        
- **Exact Text Only:**
    
    - Always include the full, exact text from the search results. Avoid summarizing or rephrasing.
        
- **Clarify Ambiguities:**
    
    - If a query is ambiguous (e.g., unclear acronyms), request clarification before proceeding.
        
- **Prioritize Specific Documents:**
    
    - For donor eligibility, for example, always prioritize the _Medical Staff References_ unless instructed otherwise.
        

---

## 5. Practice Exercise

- **Task:**
    
    - Write your own system prompt hints using the XML structure.
        
- **Objective:**
    
    - Demonstrate your ability to clearly organize core task instructions and document descriptions into a machine-readable format.
        

---

This summary provides a clear and comprehensive guide for setting up effective LLM instructions using an XML format. Use it as a reference for creating precise and actionable prompts for language models.