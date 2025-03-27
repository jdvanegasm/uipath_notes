## 🔧 **Workflow Design Layouts in UiPath Studio**

UiPath offers **three main layout diagrams** for structuring automation workflows:

### 1. **Sequence**

- **Best for:** Simple, linear workflows (e.g., data entry, UI navigation).
    
- **Characteristics:**
    
    - Executes top to bottom.
        
    - Easy to assemble and understand.
        
    - Ideal for straightforward, step-by-step tasks.
        
    - Allows local error handling without affecting the entire process.
        

---

### 2. **Flowchart**

- **Best for:** Medium to complex processes with multiple decisions.
    
- **Characteristics:**
    
    - 2D visual logic with conditional branching.
        
    - More flexible and visually clear than sequences.
        
    - Allows multiple entry/exit points via arrows (use carefully to avoid messy logic).
        
    - Suitable for processes that require validation, checks, or repeated decisions.
        

---

### 3. **State Machine**

- **Best for:** Complex, event-driven or cyclic processes.
    
- **Characteristics:**
    
    - Built from **States** and **Transitions**.
        
    - States perform activities; transitions control flow based on conditions.
        
    - Designed for **finite state control** and high-level process structuring.
        
    - Typically used in `Main.xaml` in REFramework.
        

---

## 🔄 **State Machine: Concepts & Structure**

### 🧩 **Components**

- **State**:
    
    - Has **Entry**, **Exit**, and **Transitions**.
        
    - Entry = actions when state starts.
        
    - Exit = actions before leaving the state.
        
    - Transitions = outgoing paths based on conditions.
        
- **Transition**:
    
    - Links between states.
        
    - Conditions must be met to trigger a transition.
        
    - May include actions before switching states.
        
- **Final State**:
    
    - Represents process termination.
        
    - A State Machine can have **one initial state** and **multiple final states**.
        

---

### ❄️ **Real-World Example: Air Conditioner State Machine**

#### **States**:

- `Idle State`: Default/initial.
    
- `Heat State`: Heats if desired > current temp.
    
- `Cold State`: Cools if desired < current temp.
    
- `Turning OFF`: Final state when input is “OFF” or empty.
    

#### **Transitions**:

- Idle → Idle: temp matches.
    
- Idle → Heat/Cold: temp is lower/higher.
    
- Heat/Cold → Idle: desired temp reached.
    
- Idle → Turning OFF: user input = "Turn OFF".
    

---

### 🏢 **Use Cases for State Machines**

#### ✅ Inventory Management

- States: Receive Order → Process Order → Generate Purchase Order → Receive Items → Update Inventory → Complete Order.
    
- Transitions based on stock availability.
    

#### ✅ Employee Leave Management

- States: Submit Request → Check Balance → Approve → Update Records → Notify.
    
- Handles exceptions and notifies employee if balance is insufficient.
    

#### ✅ Customer Onboarding

- States: Collect Info → Perform KYC → Create Account → Issue Card → Activate → Notify.
    
- Ensures regulatory compliance and smooth flow.
    

---

## 📌 Summary of Layout Choice Guidelines

|Layout|Use When…|Complexity|
|---|---|---|
|**Sequence**|Steps are strictly linear and simple|Low|
|**Flowchart**|Logic branches out or converges frequently|Medium|
|**State Machine**|Workflow is cyclic, event-driven, or has well-defined states|High|

---

## 🧠 **State Machine Process: Payment Workflow**

### 🎯 **Objective**

Build a State Machine that:

- Gets an initial account balance.
    
- Accepts payment values from the user.
    
- Handles valid/invalid inputs.
    
- Makes or denies payments based on balance.
    
- Loops until the user decides to stop.
    

---

## 🏗️ **Workflow Architecture**

### 🔷 **States**

1. **Get Initial Balance**
    
    - **Entry:** Prompt user input via `Input Dialog → InputValue (String)`
        
    - **Validation:** `Double.TryParse(InputValue)`
        
        - If valid → `CurrentBalance ← Double.Parse(InputValue)`
            
        - If invalid → `Message Box` + `IsValidInput ← False`
            
    - **Transitions:**
        
        - To `Get Payment Value` if `IsValidInput = True`
            
        - To `Final State` if `IsValidInput = False`
            
2. **Get Payment Value**
    
    - **Entry:** Prompt `PaymentValue (Double)`
        
    - **Validation:** Same as above using `Double.TryParse(InputValue)`
        
    - **Transitions:**
        
        - To `Deny Payment` if `IsValidInput = True && CurrentBalance < PaymentValue`
            
        - To `Make Payment` if `IsValidInput = True && CurrentBalance >= PaymentValue`
            
        - To `Final State` if `IsValidInput = False`
            
3. **Deny Payment**
    
    - **Entry:** Message Box → Inform insufficient funds + Show `CurrentBalance`
        
        - Prompt: "Do you want to continue?" → store in `ContinueAnswer (String)`
            
    - **Transitions:**
        
        - To `Get Payment Value` if `ContinueAnswer = Yes`
            
        - To `Final State` if `ContinueAnswer = No`
            
4. **Make Payment**
    
    - **Entry:**
        
        - Assign: `CurrentBalance ← CurrentBalance - PaymentValue`
            
        - Message Box → Show success + new `CurrentBalance`
            
        - Prompt: "Do you want to continue?" → store in `ContinueAnswer`
            
    - **Transitions:**
        
        - To `Get Payment Value` if `ContinueAnswer = Yes`
            
        - To `Final State` if `ContinueAnswer = No`
            
5. **Final State**
    
    - **Entry:** Message Box → "Process finished."
        

---

## 🔁 **Transition Summary**

|From|To|Condition|
|---|---|---|
|Get Initial Balance|Get Payment Value|`IsValidInput = True`|
|Get Initial Balance|Final State|`IsValidInput = False`|
|Get Payment Value|Deny Payment|`IsValidInput = True && CurrentBalance < PaymentValue`|
|Get Payment Value|Make Payment|`IsValidInput = True && CurrentBalance >= PaymentValue`|
|Get Payment Value|Final State|`IsValidInput = False`|
|Deny Payment|Get Payment Value|`ContinueAnswer.Equals("Yes")`|
|Deny Payment|Final State|`ContinueAnswer.Equals("No")`|
|Make Payment|Get Payment Value|`ContinueAnswer.Equals("Yes")`|
|Make Payment|Final State|`ContinueAnswer.Equals("No")`|

---

## 📋 **Variable Overview**

|Variable|Type|Scope|Purpose|
|---|---|---|---|
|InputValue|String|State Machine|Raw user input for amounts|
|IsValidInput|Boolean|State Machine|Flag for input validity|
|CurrentBalance|Double|State Machine|Stores and updates account balance|
|PaymentValue|Double|State Machine|User-supplied payment amount|
|ContinueAnswer|String|State Machine|Stores Yes/No to continue or not|

---

## 🧠 **State Machine Components Recap**

|Component|Description|
|---|---|
|**State**|Contains: `Entry`, `Exit`, and `Transitions`. Represents a logical step.|
|**Final State**|Only has `Entry`. Represents termination of the process.|
|**Transition**|Connects states based on conditions. May have actions before switching.|

---

## ✅ **Best Practices for State Machines**

1. **Use for Complex Flows**  
    Ideal for processes with repeated decisions, branching, and loops.
    
2. **Simplify Transitions**  
    Keep logic in transitions readable and non-redundant.
    
3. **Robust Error Handling**  
    Use `Try-Catch` inside states or create dedicated error states.
    
4. **Naming Conventions**  
    Descriptive names for States and Transitions improve readability.
    
5. **Logging and Debugging**  
    Use `Log Message` and `Write Line` to trace state entries and variable values.
    
6. **Testing**  
    Validate behavior across all input scenarios (valid, invalid, edge cases).
    
7. **Documentation**  
    Annotate states and provide external documentation for maintainability.
    

---

## ⚠️ Key Takeaways

- **Always** include a **Final State**.
    
- **Only one initial state** is allowed.
    
- Each **state** has `Entry`, `Exit`, and `Transitions`.
    
- **Final State** only has `Entry`.
    
- **Avoid overlapping transitions** with the same conditions.
    

---

