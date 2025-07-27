# 🔍 Azure Image-to-Text Pipeline (Blob ➝ Function ➝ OCR ➝ Table Storage)

This project demonstrates a secure, end-to-end Azure solution where:

- A user uploads an image via a **Flask Web App**
- The image is stored in **Azure Blob Storage**
- A **Blob-triggered Azure Function** extracts text from the image using **Azure Cognitive Services (Computer Vision)**
- The extracted text is stored in **Azure Table Storage**
- The entire solution is implemented in:
  - **Phase 1**: Public access (learning purpose)
  - **Phase 2**: Fully private architecture using **Private Endpoints** and **VNet Integration**

---

## 🔁 Architecture

User (Web App)
↓
Azure Blob Storage (uploads/imageanalysis)
↓
Azure Function (Blob Trigger)
↓
Cognitive Services (OCR)
↓
Azure Table Storage (ImageText)

---

## 🧱 Technologies Used

- Python (Flask)
- Azure Blob Storage
- Azure Function App (.NET C#)
- Azure Cognitive Services (Computer Vision API)
- Azure Table Storage
- VNet, Private Endpoints, Private DNS (for secure design)
- Microsoft Storage Explorer

---

## 📂 Project Structure

azure-image-text-extractor/
│
├── README.md
├── Phase1.md
├── Phase2.md
├── webapp/
│ ├── app.py
│ ├── requirements.txt
│ └── templates/
│ └── upload.html
│
├── functionapp/
│ ├── ProcessImage.sln
│ └── (Function code files here)


## 🚀 How to Deploy

1. Follow steps in `Phase1.md` to deploy a public version.
2. Follow steps in `Phase2.md` to switch to a private version with VNet, Private Endpoints, and DNS.
3. Upload an image using the Web App UI — text will appear in Table Storage automatically.

