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

```

## ⚙️ Prerequisites (Install These Once Only)

Install all dependencies **inside WSL Ubuntu** (recommended).

---

### **1. Docker + Docker Compose**  
Required for running Hyperledger Fabric.

```bash
sudo apt update
sudo apt install docker.io docker-compose -y
sudo usermod -aG docker $USER

```

## ⚙️ Prerequisites (Install These Once Only)

Install inside WSL Ubuntu (recommended).

1. Docker + Docker Compose
Required for running the Fabric network.


COMMANDS:
```bash
sudo apt update
sudo apt install docker.io docker-compose -y
sudo usermod -aG docker $USER

```

Restart WSL after this:
```bash
wsl --shutdown
```


Reopen Ubuntu.
2. Node.js (via NVM)
COMMANDS:
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
source ~/.bashrc
nvm install 18
nvm use 18
```

3. Python 3

COMMAND:
```bash
sudo apt install python3 python3-pip -y
```

4. Hyperledger Fabric Binaries
COMMANDS:
```bash
cd blockchain
curl -sSL https://bit.ly/2ysbOFE | bash -s
```
This installs:
peer
orderer
configtxgen
cryptogen


### 🚀 FULL PROJECT SETUP (RUN IN ORDER)


1. Start the Hyperledger Fabric Network

COMMANDS:
```bash
cd blockchain/test-network
./network.sh down
./network.sh up createChannel -ca
```

Expected:
Peers started
Orderer started
Channel "mychannel" created

-----------------------------------------------------------

2. Deploy Hospital Chaincode

Chaincode location:
```bash
blockchain/chaincode/hospital/javascript
```

Install dependencies:
```bash
cd ../../chaincode/hospital/javascript
npm install
```

Deploy chaincode:
```bash
cd ../../../test-network
./network.sh deployCC -ccn hospital -ccp ../chaincode/hospital/javascript -ccl javascript
```

-----------------------------------------------------------

3. Start the API Gateway (Backend)

COMMANDS:
```bash
cd ../../../api-gateway
npm install
npm start
```

Backend URL:
```bash
http://localhost:4000
```

-----------------------------------------------------------

📘 API Endpoints
```bash
GET    /patients                       → Get all patients
POST   /patients                       → Add patient
GET    /patients/:id                   → Patient details + IoT logs
GET    /doctor/:doctorId/patients      → Patients assigned to doctor
POST   /iotdata                        → Submit vitals
GET    /iotdata                        → Get all vitals
```
-----------------------------------------------------------

4. Start IoT Simulator

COMMANDS:
```bash
cd ../iot-simulator
pip3 install -r requirements.txt
python3 iot_sim.py
```

Sends every few seconds:
Blood pressure
Sugar
Temperature
Timestamp
Patient ID

-----------------------------------------------------------

5. Start React Frontend

COMMANDS:
```bash
cd ../frontend
npm install
npm start
```
Frontend URL:
```bash
http://localhost:5173
```



