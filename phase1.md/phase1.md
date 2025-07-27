# 🚀 Phase 1: Public Version of Azure Image-to-Text Pipeline

This phase implements the solution with **public access**, useful for learning and testing.

---

## ✅ Components Used

- Azure Web App (Python/Flask)
- Azure Blob Storage (public)
- Azure Function App (.NET C# with Blob Trigger)
- Azure Table Storage
- Azure Cognitive Services (Computer Vision)

---

## 🛠 Steps to Deploy

### 1. Create a Storage Account (LRS, public access)
- Name: `securefileupload`
- Create a Blob container: `imageanalysis`

### 2. Create a Web App
- Runtime: Python 3.10
- Hosting: Linux or Windows
- Add this environment variable:
BLOB_CONNECTION_STRING = <your-storage-connection-string>


### 3. Deploy Web App Code
- Use VS Code Azure tools or GitHub Actions
- File structure:
webapp/
app.py
requirements.txt
templates/
upload.html


### 4. Upload Image
- Go to Web App UI
- Select image and upload → Image will appear in Blob container `uploads`

---

## ⚙️ Function App Setup

### 1. Create a Function App (Consumption or Premium)
- Language: .NET
- Trigger: Blob
- Input container: `imageanalysis` (same as blob)
- Storage: Use same as blob account

### 2. Create Computer Vision Resource
- Note the **Key** and **Endpoint**

### 3. Create Table Storage
- Table name: `ImageText`
- In the same Storage Account

### 4. Set Environment Variables for Function App
COGNITIVE_API_KEY
COGNITIVE_API_ENDPOINT
AZURE_STORAGE_CONN_STRING
AzureWebJobsStorage
StorageAccountName


## 🔄 How It Works

1. Upload image in web app → goes to Blob
2. Function App triggers on new blob
3. Calls Cognitive Services API
4. Extracted text saved to Azure Table Storage

---

## ✅ Output

- Use **Storage Explorer** to view Table Storage `ImageText`
- Confirm text extracted from uploaded image
