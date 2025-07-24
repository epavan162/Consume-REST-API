# 🔗 REST Contacts API Integration - Complete Guide

This guide shows how to integrate with a REST Web Service to retrieve data from an external system. We'll use the GET method to read contact information from the Contacts API and display that data in our application.

## 📋 Tasks Covered
- ✅ Create a Web App
- ✅ Integrate with the GET Contacts REST API Method
- ✅ Create a Data Action to call the REST API Method
- ✅ Display the data retrieved from the API in a Screen

---

## 🏗️ Step 1: Create App

### Getting Started
1. **Open ODC Studio** and login with your credentials

2. **Click Create** to open the new app dialog
   
<img width="104" height="128" alt="1 create" src="https://github.com/user-attachments/assets/158582ad-c045-48cc-b99e-366cc6cbaf1a" />

3. **Select App**, then click Continue

4. **Select Web app**, then click Continue

### App Configuration
5. **Set the app details:**
   - 📱 **App name:** `REST Contacts`
   - 🖼️ **App icon:** Upload the Icon
   - ✅ Click **Create app**
<img width="802" height="680" alt="2 app details" src="https://github.com/user-attachments/assets/5a80e4aa-c6e4-487d-ab28-8f454bdffc74" />

6. **🚀 Publish the app** to save it
   > 💡 Use the one-click publish button in ODC Studio.
<img width="109" height="38" alt="publish" src="https://github.com/user-attachments/assets/773d0421-2beb-4957-a668-fbb12389633d" />

---

## 🔌 Step 2: Integrate with GET Contacts Method

### Setting up REST Integration
1. **Switch to the Logic tab** 📁

2. **Right-click REST** under the Integrations folder, then select **Consume REST API...**
<img width="338" height="230" alt="3 Rest" src="https://github.com/user-attachments/assets/d40e3238-cbff-4529-be94-77a6b44a99f7" />

3. **In the Consume REST API dialog**, select **Add single method**, then click Continue
<img width="572" height="463" alt="4 Consume REST API " src="https://github.com/user-attachments/assets/27aed0f4-32cf-4d91-8833-303b48769b4b" />

### Configuring the API Method
4. **Set the Method URL:**
   ```bash
   https://expertsmobile.outsystems.com/ContactsAPI/rest/v1/contacts/
   ```
<img width="800" height="129" alt="5 Method URL" src="https://github.com/user-attachments/assets/62b05c16-3bc6-4d88-9d69-e2df9f10c1a9" />

### Testing the Connection
5. **Switch to the Test tab**, then click the **Test button** 🧪
<img width="800" height="315" alt="7 test tab" src="https://github.com/user-attachments/assets/bf9be8e9-5ebd-4294-a14e-61dfe8d60241" />

6. **After pressing the Test button**, click the **Copy to response body button**

   > 💡 By doing the Test and clicking this button, we get a sample of the response from the API. Alternative: manually enter a sample in the Body tab using this format:

   ```json
   {
     "ErrorMessage": "",
     "Contacts": [
       {
         "Title": "",
         "Name": "",
         "Gender": "",
         "Phone": "",
         "Birthday": "2014-12-31",
         "Occupation": "",
         "City": "",
         "State": "",
         "Country": "",
         "Email": "",
         "Company": ""
       }
     ],
     "Success": false
   }
   ```

### Finalizing Integration
7. **Press Finish** to add the method integration ✅
<img width="800" height="743" alt="8 After copying the response" src="https://github.com/user-attachments/assets/f8b8ceba-9761-437e-b079-5c67a644334c" />

8. **Rename the REST API** to `ContactsAPI`
<img width="383" height="210" alt="9 REST API to ContactsAPI" src="https://github.com/user-attachments/assets/7be45811-6a89-4849-a54e-af97213d12eb" />

9. **🚀 Publish the app** to save it
<img width="109" height="38" alt="publish" src="https://github.com/user-attachments/assets/9e531b58-6c44-40b5-ba9d-6b6d49fcb5a9" />

---

## 🖥️ Step 3: Call the GetContacts API Method

### 📄 Create the Screen

1. **Switch to the Interface tab** 🎨

2. **Add a new empty Screen** named `Contacts` under the MainFlow
<img width="338" height="221" alt="10 Call the GetMethods" src="https://github.com/user-attachments/assets/9d66e7a1-377a-4f72-913e-d58017f0155b" />

3. **Change the Accessible by property** of the Screen from "Authenticated users" to "Everyone"

4. **Inside the Title placeholder**, add the text: `Contacts`

### ⚙️ Set up Data Action

1. **Right-click the Contacts Screen** and select **Fetch Data from Other Sources**
<img width="341" height="299" alt="11 Fetch Data from Other Sources" src="https://github.com/user-attachments/assets/dbfbdaab-3960-43a6-b237-ebe62c805e1d" />

2. **Configure Data Action:**
   - 📝 **Name:** `GetContacts`
   - 🔄 **Change Output Parameter:** `Out1` → `List`

3. **Set Data Type:**
   - In the **Data Type dropdown** of the List Output Parameter, select **List...**
<img width="349" height="370" alt="12 List Output Parameter, select List" src="https://github.com/user-attachments/assets/02c8deb6-4fcb-4f47-b749-27bfdaf94bfd" />

   - In the **List Element Type dialog**, filter by "contact"
   - Pick the **ContactItem** 🎯
<img width="416" height="439" alt="13 pick the ContactItem" src="https://github.com/user-attachments/assets/a821ba3a-3a76-4d28-9097-b00a0d00ae61" />

### 🔗 Connect to API

4. **Drag a Run Server Action** and drop it between the Start and End elements

5. **In the Select Action dialog**, pick the **GetContacts REST API Method**
<img width="416" height="439" alt="14 GetContacts REST API Method" src="https://github.com/user-attachments/assets/a2e507db-a649-401a-8501-4207ce5d1d43" />

6. **Configure Data Flow:**
   - Hover mouse in the connector between GetContacts and End
   - Click to open **AI-assisted suggestions**
   - Select **"Set List to GetContacts.Response.Contacts"**
<img width="350" height="367" alt="15 Set List to GetContacts Response Contacts" src="https://github.com/user-attachments/assets/a3e00d22-f587-4901-aabd-a27cd6bec579" />

   > 🤖 If AI-assisted suggestions yield different options, create the Assign manually:
   ```
   List = GetContacts.Response.Contacts
   ```

### 📊 Display the Data

7. **Return to the Contacts Screen**

8. **Drag the List Output Parameter** of the GetContacts Data Action and drop it on the **MainContent placeholder area**
<img width="1070" height="426" alt="16 List Output Parameter of the GetContacts Data Action," src="https://github.com/user-attachments/assets/109a91b3-0a6d-40b1-9613-77c25659d256" />


9. **🚀 Publish the app** to save it
<img width="109" height="38" alt="publish" src="https://github.com/user-attachments/assets/d48f3152-d2ae-410f-b598-e5037d33af16" />

10. **🌐 Open the app in the browser**

---

## 🎉 Final Result

The app now displays contacts available from the API. Since the API is public, the data may vary.

---

## 📦 What Was Created

During this integration, several elements were created in ODC Studio:

### 🔧 Backend Components
- **Under Integrations > REST:** The ContactsAPI with the GetContacts REST API Method
- **Method Output Parameter:** Response with Data Type set to a Structure in the Data tab
- **Data Action:** GetContacts that calls the REST API and returns contact data

### 🎨 Frontend Components  
- **Screen:** Contacts that displays the retrieved contact information

### 🚀 Integration Summary
The integration demonstrates how to consume a single method of a REST API and display the results in your application.

---

## 📝 Key Takeaways

| Component | Purpose | Location |
|-----------|---------|----------|
| REST API Integration | Connects to external service | Logic Tab > Integrations |
| Data Action | Fetches and processes API data | Screen > Data Actions |
| Screen Display | Shows contact information to users | Interface Tab > Screens |

> ✅ **Success!** You now have a fully functional REST API integration that retrieves and displays contact data from an external source.
