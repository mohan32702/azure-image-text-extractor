# 🔐 Phase 2: Private and Secure Architecture with Private Endpoints & VNet

In this phase, we enhance the solution by removing public access to all components and securing traffic using **Private Endpoints**, **VNet**, and **Private DNS Zones**.

---

## 🔧 Private Network Setup

### 1. Create a Virtual Network with 3 Subnets:
- `default-subnet` → Web App (delegated)
- `functionapp-subnet` → Function App (delegated)
- `hybridsubnet` → Private Endpoints

> ⚠️ Delegated subnets cannot be shared even between function app and web apps.

---

## 🔐 Disable Public Access

- **Web App**: Disable public access → Enable **VNet integration**
- **Function App**: Disable public access → Enable **VNet integration**
- **Storage Account**: Disable public access → Use **Private Endpoints** for Blob and Table
- **Cognitive Services**: Disable public access → Use **Private Endpoint**

---

## 🔁 Private DNS Setup

- When creating PEs, Azure auto-creates and links **Private DNS Zones**
- You can validate DNS name resolution from inside VM (optional)

---

## 🔄 Workflow

1. Upload image in **Web App** (inside VNet)
2. Image goes to Blob Storage (via Private Endpoint)
3. Blob trigger fires Function App (via Private Endpoint)
4. Function calls **Computer Vision API** (via PE)
5. Extracted text saved to **Table Storage** (via PE)

---

## 🧪 Test End-to-End

1. Upload an image using the private Web App
2. Validate blob is uploaded in `imageanalysis`
3. Check Function App logs for successful run
4. Open **Storage Explorer with SAS token**
   - View Table `ImageText`
   - Verify the extracted text

---


## ✅ Security Highlights

- **No public internet access**
- **All services communicate via Azure backbone**
- **Private DNS ensures name resolution**
- **VNet integration adds isolation and control**

---
