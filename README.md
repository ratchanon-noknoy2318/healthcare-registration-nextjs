<h1 align="center">Patient Intake System</h1>

<p align="center">
  <strong>Modern Digital Intake Platform for Community Healthcare</strong><br>
  <sub>Streamlining patient registration, lookup, and communication for real-world clinical workflows</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Status-Production_Ready-brightgreen" />
  <img src="https://img.shields.io/badge/Use_Case-Healthcare_System-blue" />
  <img src="https://img.shields.io/badge/Stack-Next.js_+_Google_Apps_Script_+_LINE-black" />
</p>

<p align="center">
  <img src="https://res.cloudinary.com/dpa96jvla/image/upload/v1779584919/%E0%B8%94%E0%B8%B5%E0%B9%84%E0%B8%8B%E0%B8%99%E0%B9%8C%E0%B8%97%E0%B8%B5%E0%B9%88%E0%B8%A2%E0%B8%B1%E0%B8%87%E0%B9%84%E0%B8%A1%E0%B9%88%E0%B9%84%E0%B8%94%E0%B9%89%E0%B8%95%E0%B8%B1%E0%B9%89%E0%B8%87%E0%B8%8A%E0%B8%B7%E0%B9%88%E0%B8%AD_1_v8yqdd.png" alt="Patient Intake System Preview" width="100%" />
</p>
---

## 🧠 The Problem

Community healthcare teams still rely heavily on manual patient intake processes:

- Paper-based registration slows down operations
- Patient lookup is time-consuming and error-prone
- Communication between staff and patients is fragmented
- Data inconsistency across systems

---

## 💡 The Solution

**Patient Intake System** digitizes and automates the intake workflow:

- Instant patient registration
- Fast patient lookup
- LINE-based communication
- Real-time synchronization with Google Sheets

Designed specifically for **field nurses and municipal healthcare teams**

---

## ⚙️ Core Features

- 🧑‍⚕️ Patient Registration
- 🔍 Instant Patient Lookup
- 💬 LINE Messaging Integration
- 📊 Real-time Google Sheets Sync
- 🔔 Automated Appointment Notification
- ⚡ Lightweight UI (Next.js)

---

## 📈 Impact

- ⬇ Reduced manual data entry workload
- ⬆ Improved intake speed
- ⬆ Increased data accuracy
- 🏥 Applied in municipal healthcare workflows

---

## 🧱 Tech Stack

- **Frontend:** Next.js
- **Backend Services:** Google Apps Script
- **Messaging:** LINE Messaging API
- **Database:** Google Sheets
- **UI Framework:** Tailwind CSS

---

## 🔌 Integrations & API Endpoints

### 🟢 LINE Messaging API
Used to notify healthcare staff automatically.

```http
POST /v2/bot/message/push
```

### 🔵 Google Apps Script Web App
Used for patient registration, lookup, dashboard data, and appointment workflows.

```http
GET  /exec
POST /exec
```

**Supported Actions (Query Parameters):**
* `register_new`
* `register_existing`

---

## 📖 API Usage Examples

### 1. Patient Registration (Google Apps Script)
To register a new patient via the Google Apps Script backend Web App module.

**Request Payload (`POST /exec?action=register_new`)**
```json
{
  "firstName": "John",
  "lastName": "Doe",
  "citizenId": "1100000000000",
  "phoneNumber": "0812345678",
  "symptoms": "Mild fever and cough for 2 days"
}
```

**Response (`200 OK`)**
```json
{
  "status": "success",
  "message": "Patient registered successfully",
  "data": {
    "patientId": "HN-2026-0001",
    "registrationTime": "2026-05-28T05:30:00.000Z"
  }
}
```

---

### 2. Staff Notification (LINE Messaging API)
Triggered automatically when a new patient registers to alert the field nurses.

**Request Payload (`POST /v2/bot/message/push`)**
```json
{
  "to": "your_line_admin_user_id",
  "messages": [
    {
      "type": "text",
      "text": "🚨 New Telemedicine Registration!\nName: John Doe\nSymptoms: Mild fever and cough for 2 days.\nPlease review the lookup queue."
    }
  ]
}
```

---

## 🏗 System Flow

```mermaid
graph TD
    NextJS[Next.js Frontend UI] -->|1. Submit Form| GAS[Google Apps Script Backend]
    GAS -->|2. Sync Data| Sheets[(Google Sheets Database)]
    GAS -->|3. Trigger Alert| LINE[LINE Messaging API]
    LINE -->|4. Push Notification| Nurses[Field Nurses Team]
```

---

## 🚀 Getting Started

### Prerequisites
* Node.js (v18 or higher)
* npm or yarn

### Installation Steps

1. Clone the repository:
   ```bash
   git clone https://github.com/ratchanon-noknoy2318/patient-registration-platform-nextjs
   ```

2. Navigate into the project directory:
   ```bash
   cd patient-registration-platform-nextjs
   ```

3. Install project dependencies:
   ```bash
   npm install
   ```

4. Create a `.env.local` file in the root directory and configure your credentials:
   ```env
   CHANNEL_ACCESS_TOKEN=your_line_channel_access_token
   ADMIN_USER_ID=your_line_user_id
   APPS_SCRIPT_WEB_APP_URL=your_google_apps_script_web_app_url
   ```

5. Run the development server:
   ```bash
   npm run dev
   ```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.
