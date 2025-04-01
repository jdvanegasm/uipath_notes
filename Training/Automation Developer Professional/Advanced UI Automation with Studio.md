# 🔧 **UiPath Extensions**

**Purpose:**  
Extensions expand automation capabilities in browsers and applications like Java, Silverlight, Citrix, and RDP environments. They allow native UI element detection so selectors work correctly.

**Installation Methods:**

1. **From Studio:**  
    `Home > Tools > UiPath Extensions`
    
2. **Using SetupExtensions.exe CLI:**
    
    - Per-machine install:  
        `C:\Program Files\UiPath\Studio\UiPath\SetupExtensions.exe`
        
    - Per-user install:  
        `%LocalAppData%\Programs\UiPath\Studio\UiPath\SetupExtensions.exe`
        
    - Custom install:  
        `<Studio_Install_Folder>\UiPath\SetupExtensions.exe`
        
    - Remote Runtime:  
        `C:\Program Files (x86)\UiPath\RemoteRuntime\SetupExtensions.exe`
        
3. **Via UiPathStudio.msi command line install**
    

---

## 🖥️ UiPath Remote Runtime

**Purpose:**  
Enables native selector generation for apps accessed via RDP (like Citrix, VMware), avoiding reliance on OCR or image recognition.

**How it works:**  
Remote Runtime runs on the **remote machine** and communicates with the **client-side extension**. It transfers UI element data to Studio, allowing it to build reliable selectors remotely.

**Installation Steps:**

#### A. Using `.msi Installer` on the remote machine:

1. Download from:
    
    - UiPath Customer Portal
        
    - Automation Cloud > Resource Center
        
    - Or request via Support
        
2. Run `UiPathRemoteRuntime.msi`
    
3. Log off and back in (to apply changes)
    
4. Install the matching extension on the client machine
    

#### B. Using Command Line:

1. Open Command Prompt as Administrator
    
2. Navigate to the installer folder
    
3. Run:  
    `UiPathRemoteRuntime.msi ADDLOCAL=RemoteRuntime,RemoteRuntimeTask`
    
4. Log off and back in
    
5. Install the extension on the client
    

---

### 🔗 Remote Runtime Dependencies

- **Important:** Compatibility depends on the version of `UiPath.UIAutomation.Activities`, not Studio.
    
- **Steps to match the dependency:**
    
    1. On **client machine**:  
        Go to `%UserProfile%\.nuget\packages\uipath`  
        Copy the folder matching your activity package version
        
    2. On **remote machine**:  
        Paste it into  
        `%ProgramFiles(x86)%\UiPath\RemoteRuntime\packages\uipath`
        

> ⚠️ If the package version doesn't match, selectors may not be built correctly.

---

### 🛠️ Common Issues & Fixes

- **Runtime not installed:**  
    Ensure `UiPathRemoteRuntime.msi` is properly installed on the remote machine.
    
- **Citrix 7 2109+:**  
    Citrix blocks custom virtual channels by default. Add UiPath to the allow list policy.
    
- **Runtime not starting for user:**
    
    - May require a machine restart after installation
        
    - Sysadmin might need to configure `UiPathRemoteRuntime.exe` for the user session
        
    - For multi-hop RDP, install Remote Runtime on all intermediary machines
        

---
### ✅ Summary

- **UiPath Extensions** support web & app automation by enabling native selector detection.
    
- **UiPath Remote Runtime** is required for reliable automation over RDP (e.g., Citrix, VMware).
    
- Installation must be performed on **both client and remote machines**.
    
- Ensure the **activity package version matches** the Remote Runtime version to avoid selector issues.
    

---
# 🌐 Browser Automation with WebDriver Protocol

**⏱ Duration:** 15 min  
**📚 Lesson Objectives:**

- Understand what the WebDriver protocol is and how it applies to browser automation.
    
- Learn how to install and configure it for different browsers.
    

---

## 🔍 What is the WebDriver Protocol?

- A **popular browser automation protocol** exposing a REST API in a separate executable from the browser.
    
- Supports actions like:
    
    - Opening browsers
        
    - Clicking elements
        
    - Typing into fields
        
    - DOM exploration
        
    - JavaScript injection
        
- Used in **headless** and **visual** browser automation.
    
- UiPath integrates WebDriver for **background browser automation** without visual interaction, but also supports UI-driven automation.
    

---

## ✅ Supported Browsers

- Google Chrome
    
- Mozilla Firefox
    
- Microsoft Edge
    

> No need to install UiPath browser extensions when using WebDriver, but you **must install the browser’s corresponding WebDriver executable**.

> Selectors generated via WebDriver are identical to those from UiPath browser extensions (except for window frames).

---

## ⚙️ Configuring WebDriver Protocol

Each browser requires a specific WebDriver:

|Browser|WebDriver Executable|Notes|
|---|---|---|
|Google Chrome|`chromedriver.exe`|Ensure the version matches the installed Chrome version.|
|Mozilla Firefox|`geckodriver.exe`|Use the latest version for best compatibility.|
|Microsoft Edge|`msedgedriver.exe`|Edge and driver are updated together.|

---

## 🧰 Installing the WebDriver Protocol

1. **Download** the WebDriver for your browser.
    
2. **Install** it in a directory, e.g., `C:\webdriver\Chrome`.
    
3. Open `Edit the system environment variables` from Start Menu.
    
4. Click **Environment Variables**.
    
5. Edit the **Path** variable and **add the WebDriver folder path**.
    
6. Click **OK** to save all changes.
    
7. **Restart the UiPath Robot Service**.
    

---

## 🌍 Opening a Browser (WebDriver Settings)

Inside `Open Browser` or `Attach Browser` activities, configure the following:

### Visual Browser Automation:

- `CommunicationMethod`: WebDriver
    
- `BrowserType`: Chrome / Firefox / Edge
    

### Headless Browser Automation:

- `CommunicationMethod`: WebDriver
    
- `BrowserType`: Chrome / Firefox / Edge
    
- `Hidden`: True
    

---

## ⚠️ Known Issues & Limitations

### 🧭 Visual Automation via WebDriver

- **Iframes not supported** for selector validation.
    
- Always starts a **new browser session** – no saved cookies or browser data.
    
- **Multiple tabs cause instability** – use single-tab automation to avoid tab switching issues.
    

### 👻 Headless Automation via WebDriver

- **No visible browser window** — visual activities (e.g., default Click or Type Into) won’t work unless you:
    
    - Use `SimulateClick`, `SimulateType`, `SimulateHover` or
        
    - Enable `SendWindowMessages`
        
- **Image-based activities** (e.g., Click Image, Find Image) are **not supported**.
    
- **Event monitoring** (e.g., Click Trigger) is **not supported**.
    
- `<WND>` tags in `Close Application` won't stop the WebDriver process — use `<HTML>` tags instead.
    
- WebDriver opens the browser in the **same position/size**, which may affect selectors on adaptive web pages. Stick to **default sizes**.
    

---

## 📌 Lesson Summary

- WebDriver is a REST-based protocol for browser automation, independent of browser GUI.
    
- UiPath supports Chrome, Firefox, and Edge using this protocol.
    
- Works in both **headless** and **visual** modes.
    
- Generates the **same selectors** as UiPath browser extensions.
    
- Use case: ideal for background automation, but with known limitations for UI-based or image-triggered activities.
    