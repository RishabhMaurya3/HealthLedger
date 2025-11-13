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

# ⚙ Prerequisites (WSL Ubuntu Recommended)

Install the following inside WSL:

## 1️⃣ Docker
```bash
sudo apt update
sudo apt install docker.io docker-compose -y
sudo usermod -aG docker $USER
Restart WSL.

2️⃣ Node.js via NVM
bash
Copy code
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
source ~/.bashrc
nvm install 18
nvm use 18
3️⃣ Python 3 + pip
bash
Copy code
sudo apt install python3 python3-pip -y
4️⃣ Hyperledger Fabric Binaries
bash
Copy code
cd HealthLedger/blockchain
curl -sSL https://bit.ly/2ysbOFE | bash -s
Installs:

peer

orderer

configtxgen

cryptogen

🚀 Step-by-Step: Running the Full System
Everything below assumes:

bash
Copy code
cd HealthLedger
1️⃣ Start the Blockchain Network
bash
Copy code
cd blockchain/test-network
./network.sh down
./network.sh up createChannel -ca
Expected:

Orderer up

Peers up

Channel mychannel created

2️⃣ Deploy the Chaincode
Install dependencies:

bash
Copy code
cd ../chaincode/hospital/javascript
npm install
Deploy chaincode:

bash
Copy code
cd ../../../test-network
./network.sh deployCC -ccn hospital -ccp ../chaincode/hospital/javascript -ccl javascript
Expected:

Chaincode definition committed

3️⃣ Start the API Gateway
bash
Copy code
cd ../../api-gateway
npm install
npm start
Runs at:
http://localhost:4000

Available APIs:

bash
Copy code
GET    /patients
POST   /patients
GET    /patients/:id
GET    /doctor/:doctorId/patients
POST   /iotdata
GET    /iotdata
4️⃣ Start the IoT Simulator
bash
Copy code
cd ../iot-simulator
pip3 install -r requirements.txt
python3 iot_sim.py
Sends vitals every few seconds.

5️⃣ Start the React Frontend
bash
Copy code
cd ../frontend
npm install
npm start
Opens at:
http://localhost:3000

🧭 Frontend Navigation Overview
Dashboard (/)
Live IoT vitals chart

Patient list

Add patient shortcut

Admin Portal (/admin)
Add patients

Manage all patients

Doctor Portal (/doctor)
Select doctor identity

View assigned patients only

Patient Portal (/patient)
Patient enters ID

Redirects to /patient/:id

Patient Details (/patient/:id)
Vitals graph

Detailed medical history

Assigned doctor

IoT timeline

