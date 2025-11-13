HealthLedger – Blockchain-Based Hospital Data Management System

HealthLedger is a full-stack hospital data management platform built using Hyperledger Fabric, Node.js, React.js, and Python.
It ensures secure, tamper-proof, and role-based access to patient medical records.

🚀 Tech Stack
🔗 Blockchain

Hyperledger Fabric (Chaincode for patient, doctor, vitals, and access control)

🖥 Backend

Node.js API Gateway

REST APIs for patient, doctor, admin, and vital data handling

📊 Frontend

React.js dashboard

Live charts for vitals monitoring

Login portal for Admin, Doctor, and Patients

📡 IoT Integration

Python IoT Simulator sends real-time vitals to the blockchain:

Heart Rate

Blood Pressure

Temperature

Oxygen Level

🔐 Role-Based Access
👨‍⚕️ Admin

Add new patients

Manage doctors

Assign doctors to patients

🧑‍⚕️ Doctor

View patients assigned to them

View medical history and vitals

Update diagnoses / notes

🧑‍🦱 Patient

View their personal health records

Track real-time vitals

📡 IoT Simulator

Pushes continuous health data to blockchain

Ensures tamper-proof secure vitals storage

🧱 Blockchain Features

Immutable patient records

Encrypted data transactions

End-to-end traceability

Tamper-proof vital logs

Smart contract-based access control

⭐ Main Features
🔗 Hyperledger Fabric Blockchain

Stores patients, vitals, prescriptions, and medical logs

Chaincode written in JavaScript

Network setup includes:

2 Organizations

1 Orderer

Certificate Authorities (CAs)

Single Channel: mychannel

🛡 API Gateway

Tech: Node.js + Express
Purpose: Acts as the main backend service
Features:

Communicates with Fabric via Fabric Node SDK

Identity-based access control

REST APIs for:

Patients

Doctors

IoT vitals ingestion

Full patient details retrieval

📡 Python IoT Simulator

Simulates real biomedical devices by generating live vitals:

Blood Pressure

Sugar Level

Temperature

Timestamp / User ID / Device ID

Flow:
IoT Simulator → API Gateway → Blockchain

🌐 React Frontend

Frontend built using React + TailwindCSS + Axios + Recharts

📌 Application Routes
Route	Page	Purpose
/	Dashboard	Admin dashboard, live vitals chart, patient list
/admin	AdminPortal	Add & manage patients
/doctor	DoctorPortal	View patients assigned to the doctor
/patient	PatientPortal	Patient login & personal portal
/patient/:id	PatientDetails	Full patient record: vitals + history
Libraries Used:

Recharts → Charts for vitals

Axios → API communication

TailwindCSS → UI styling
