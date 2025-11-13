# HealthLedger – Blockchain-Based Hospital Data Management System

HealthLedger is an end-to-end hospital data platform powered by:

- **Hyperledger Fabric blockchain**
- **Node.js API Gateway**
- **Python IoT Vitals Simulator**
- **React.js Frontend with live charts**

The system ensures secure, tamper-proof patient records with role-based access:

- **Admin** → Add/manage patients  
- **Doctor** → View patients assigned to them  
- **Patient** → View their own health records  
- **IoT Simulator** → Sends live vitals to the blockchain  
- **Blockchain** → Stores all patient and vitals data immutably  

---

# ⭐ Main Features

## 🔗 Hyperledger Fabric Blockchain
- Stores:
  - Patients  
  - Vitals  
  - Prescriptions  
  - Medical logs  
- Chaincode written in **JavaScript**
- Network setup:
  - **2 Orgs**
  - **1 Orderer**
  - **Certificate Authorities**
  - **Single Channel:** `mychannel`

---

## 🛡 API Gateway (Node.js + Express)
- Communicates with Fabric using **Fabric Node SDK**
- Identity-based access
- Provides REST APIs for:
  - Patients  
  - Doctors  
  - IoT vitals  
  - Full patient detail retrieval  

---

## 📡 Python IoT Simulator
Generates real live vitals data:

- Blood pressure  
- Sugar  
- Temperature  
- Timestamp / User / Device ID  

**Flow:**  
`IoT Simulator → API Gateway → Blockchain`

---

## 🌐 React Frontend

### Application Routes

| Route | Page | Purpose |
|-------|--------|---------|
| `/` | **Dashboard** | Admin dashboard + live vitals chart + patient list |
| `/admin` | **AdminPortal** | Add/manage patients |
| `/doctor` | **DoctorPortal** | View assigned patients |
| `/patient` | **PatientPortal** | Patient login/portal |
| `/patient/:id` | **PatientDetails** | Full patient record (vitals + history) |

### Uses:
- **Recharts** – charts  
- **Axios** – API client  
- **TailwindCSS** – UI styling  

---

## 📥 Clone Repository

Clone your project:

```bash
git clone https://github.com/RishabhMaurya3/HealthLedger.git
cd HealthLedger



