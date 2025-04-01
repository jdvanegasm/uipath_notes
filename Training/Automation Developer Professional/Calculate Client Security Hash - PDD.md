### ACME Credentials
## ✅ Checklist

- [x] Refer to the provided PDD/SDD and thoroughly understand its content and requirements for the process.  
- [x] Develop the automation as specified in the document.  
- [ ] Refer to the Calculate Client Security Hash - Exercise Hints if needed.  
- [x] Upload the developed solution. Please ensure that you use the same email you used for the Academy in the ACME system while uploading.  
- [x] After submitting your work, you will gain access to the walkthrough. Please wait for the results. If necessary, refer to the walkthrough to refine your solution, and then upload it again. 
### 🧩 **State Machine Structure**

| Estado               | Descripción                                          |
| -------------------- | ---------------------------------------------------- |
| `Init`               | Opens the web browser, goes to ACME page and logs in |
| `GetTransactionData` | Filters the WI5 and prepares the actual transaction  |
| `Process`            | Generates the hash and updates the work item         |
| `End`                | Close the web browser and ends the process           |
