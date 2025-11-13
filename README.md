# HealthLedger – Blockchain-Based Hospital Data Management System

HealthLedger is a full-stack hospital data management platform built on **Hyperledger Fabric**, featuring a secure, immutable, and real-time patient monitoring system.  
It integrates Blockchain, React, Node.js, and IoT to deliver trusted healthcare data management.

---

# 🚀 Tech Stack Overview

## 🔗 Hyperledger Fabric Blockchain
- Stores:
  - Patient records  
  - Vitals  
  - Prescriptions  
  - Medical logs  
- Chaincode written in **JavaScript**
- Network Setup:
  - **2 Organizations**
  - **1 Orderer**
  - **Certificate Authorities**
  - **Single Channel:** `mychannel`

---

## 🛡 API Gateway (Node.js + Express)
- Communicates with Fabric using **Fabric Node SDK**
- Identity-based access control
- REST APIs for:
  - Patients  
  - Doctors  
  - IoT vitals  
  - Full patient detail retrieval  
- Backend for both IoT Simulator and React UI

---

## 📡 Python IoT Vitals Simulator
Simulates biomedical sensors and generates:

- Blood Pressure  
- Sugar Level  
- Temperature  
- Timestamp  
- User ID / Device ID  

**Flow:**  
`IoT Simulator → API Gateway → Blockchain`

---

## 🌐 React Frontend
Frontend built using **React + TailwindCSS + Recharts + Axios**

### Application Routes
| Route | Page | Purpose |
|-------|--------|---------|
| `/` | **Dashboard** | Admin dashboard + live vitals chart + patient list |
| `/admin` | **AdminPortal** | Add/manage patients |
| `/doctor` | **DoctorPortal** | View assigned patients |
| `/patient` | **PatientPortal** | Patient login + portal |
| `/patient/:id` | **PatientDetails** | Full patient record (vitals + history) |

### Frontend Libraries
- **Recharts** → live vitals charts  
- **Axios** → API communication  
- **TailwindCSS** → UI styling  

---

# 🔐 Role-Based Access Control

## 👨‍💼 Admin
- Add/manage patients  
- Manage doctors  
- Assign doctors to patients  

## 👨‍⚕️ Doctor
- View assigned patients  
- Access medical history  
- Monitor vitals  
- Add diagnosis/notes  

## 🧑‍🦱 Patient
- View personal health records  
- Track real-time vitals  

## 📡 IoT Device
- Sends continuous vitals directly to blockchain  

---

# 🧱 Blockchain Features
- Immutable medical records  
- Tamper-proof vitals storage  
- Smart contract-based access  
- Secure and auditable logs  
- End-to-end traceability  
