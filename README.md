# 🚚 SwiftShip Tracker

### Salesforce-Based Parcel Management & AI-Powered Tracking System

SwiftShip Tracker is a **Salesforce-based parcel management and tracking solution** designed to centralize parcel booking, delivery operations, shipment status management, customer communication, and conversational parcel tracking.

The system uses **Salesforce Developer Edition, Custom Objects, Salesforce Flow, Prompt Builder, and Agentforce** to provide a centralized platform for managing the parcel lifecycle from booking to delivery confirmation.

---

## 🌟 Project Overview

Traditional parcel management often requires customers to contact support repeatedly or use multiple applications to track shipments.

**SwiftShip Tracker** addresses this problem by bringing parcel information, delivery data, automation, security, reporting, and AI-assisted tracking into a single Salesforce platform.

The system manages:

* 📦 Parcel booking
* 🚚 Delivery management
* 📍 Shipment status and location information
* 👤 Sender management
* 👥 Receiver management
* 🤖 AI-powered parcel tracking
* ⚡ Salesforce Flow automation
* 🔐 Role-based security
* 📊 Reports and dashboards
* 💬 Agentforce conversational assistance

The core data model consists of four custom objects:

**Parcel → Delivery → Sender → Receiver**

---

## 🎯 Objectives

The primary objectives of SwiftShip Tracker are to:

* Centralize parcel, sender, receiver, and delivery information.
* Simplify parcel booking and tracking.
* Provide shipment status and location visibility.
* Reduce manual operational work through Salesforce automation.
* Provide conversational parcel tracking using Agentforce.
* Improve delivery-agent efficiency.
* Provide secure, role-based access.
* Support operational monitoring through reports and dashboards.

---

## ✨ Key Features

### 📦 1. Parcel Management

The Parcel object stores the core shipment information, including:

* Parcel ID
* Parcel Status
* Parcel Weight
* Estimated Delivery Date
* Sender relationship
* Receiver relationship

Parcel IDs use an auto-number format such as:

```text
P-001
P-002
P-003
```

---

### 🚚 2. Delivery Tracking

The Delivery object maintains delivery-specific information such as:

* Current Location
* Estimated Delivery Date
* Delivery status
* Parcel relationship

The delivery lifecycle includes:

```text
Booked
   ↓
In Transit
   ↓
Out for Delivery
   ↓
Delivered
```

---

### 👤 3. Sender Management

The Sender object maintains:

* Sender Address
* Contact Number
* Email Address
* Related parcel information

---

### 👥 4. Receiver Management

The Receiver object maintains:

* Receiver Address
* Contact Number
* Email Address
* Sender relationship
* Parcel relationship

---

### 🤖 5. AI-Powered Parcel Tracking

One of the major features of SwiftShip Tracker is its **Agentforce-based conversational tracking system**.

The customer can ask the Agentforce assistant for parcel information using a Parcel ID.

Example:

```text
User:
Track parcel P-001
```

The Agentforce agent passes the request to the **Parcel Details Flow**.

The Flow:

1. Receives the Parcel ID.
2. Searches the Parcel record.
3. Retrieves the required parcel information.
4. Calls the Prompt Builder template.
5. Generates a structured tracking response.
6. Returns the response to the Agentforce agent.

The response can contain:

```text
Parcel Tracking Update

Parcel Name: ...
Parcel ID: P-001
Status: In Transit
Weight: 2.5 kg
Estimated Delivery Date: ...
```

---

## 🧠 AI Architecture

The AI tracking workflow follows:

```text
Customer
   │
   ▼
Agentforce
   │
   ▼
Parcel Updates Subagent
   │
   ▼
Parcel Details Flow
   │
   ▼
Get Parcel Record
   │
   ▼
Prompt Builder
   │
   ▼
Tracking Response
   │
   ▼
Agentforce
   │
   ▼
Customer
```

The project uses a Prompt Builder template named:

```text
Retrieve Parcel Details
```

with API name:

```text
Retrieve_Parcel_Details
```

---

## ⚡ Salesforce Automation

Salesforce Flow is used to connect the Agentforce agent with parcel data.

### Parcel Details Flow

The Auto-launched Flow contains:

```text
Start
  ↓
Get Parcel Records
  ↓
Parcel Updates
  ↓
Assignment Outputs
  ↓
End
```

The Flow accepts a Parcel ID as input and returns the formatted parcel tracking response.

---

## 🔐 Security

SwiftShip Tracker uses Salesforce security features to control access to parcel information.

### Security Components

* Profiles
* Permission Sets
* Role Hierarchy
* Field-Level Security
* Sharing Rules
* Record-Level Security

### Role Hierarchy

```text
Administrator
      ↓
Delivery Manager
      ↓
Delivery Agent
      ↓
Customer
```

Sensitive information such as sender email, receiver contact information, and location-related fields can be restricted based on user permissions.

---

## 🗄️ Data Model

### Custom Objects

| Object       | Purpose                                  |
| ------------ | ---------------------------------------- |
| **Parcel**   | Stores core parcel information           |
| **Delivery** | Stores delivery and location information |
| **Sender**   | Stores sender information                |
| **Receiver** | Stores receiver information              |

### Important Relationships

```text
Sender
   │
   ├──────────┐
   │          │
   ▼          ▼
Parcel ──── Receiver
   │
   ▼
Delivery
```

The report defines Parcel, Delivery, Sender, and Receiver as the main custom objects of the solution.

---

## 🛠️ Technology Stack

| Category           | Technology                                     |
| ------------------ | ---------------------------------------------- |
| Platform           | Salesforce Developer Edition                   |
| UI                 | Lightning App, Lightning Record Pages          |
| Database           | Salesforce Objects                             |
| Automation         | Salesforce Flow                                |
| AI                 | Agentforce                                     |
| Prompt Engineering | Prompt Builder                                 |
| Security           | Profiles, Permission Sets, Role Hierarchy, FLS |
| Reporting          | Salesforce Reports & Dashboards                |
| Cloud Platform     | Salesforce Lightning Experience                |

---

## 📋 Functional Requirements

The system is designed to support:

* FR-1 — Parcel booking and record creation
* FR-2 — Parcel status tracking
* FR-3 — Weight management
* FR-4 — Estimated delivery date management
* FR-5 — Sender information management
* FR-6 — Receiver information management
* FR-7 — Delivery and current-location tracking
* FR-8 — Agent parcel status updates
* FR-9 — Automated customer notifications
* FR-10 — AI-powered parcel tracking
* FR-11 — Reports and dashboards
* FR-12 — Customer access through Experience Cloud

---

## 🔄 Parcel Lifecycle

```text
        ┌──────────────┐
        │    Booking   │
        └──────┬───────┘
               ↓
        ┌──────────────┐
        │ Parcel Record│
        │   Created    │
        └──────┬───────┘
               ↓
        ┌──────────────┐
        │   Dispatch   │
        └──────┬───────┘
               ↓
        ┌──────────────┐
        │  In Transit  │
        └──────┬───────┘
               ↓
        ┌──────────────┐
        │Out for        │
        │Delivery       │
        └──────┬───────┘
               ↓
        ┌──────────────┐
        │   Delivered  │
        └──────────────┘
```

---

## 🧪 Testing

The project defines functional and security test scenarios covering:

| Test ID | Test Area               |
| ------- | ----------------------- |
| T-01    | Parcel Creation         |
| T-02    | Object Relationships    |
| T-03    | Delivery Tracking       |
| T-04    | Tabs & Navigation       |
| T-05    | Prompt Template         |
| T-06    | Flow Execution          |
| T-07    | Agentforce Tracking     |
| T-08    | Unknown Parcel Handling |
| T-09    | Permission Validation   |
| T-10    | Security Validation     |

The testing process validates parcel creation, object relationships, Flow execution, Agentforce responses, data retrieval, and security permissions.

---

## 📊 Agile Development

The project followed an Agile approach using user stories and sprint planning.

### Sprint Structure

```text
Sprint 1 → Developer Setup
Sprint 2 → Data Modeling
Sprint 3 → Automation
Sprint 4 → Apex
Sprint 5 → Reports
Sprint 6 → Dashboards & AI
```

The documented backlog contains **37 total story points**, with an average planned velocity of approximately **6.2 points per sprint**.

---

## 👥 Project Team

**Team Leader**

* Balamurugan S

**Team Members**

* Balaganesh P
* Arun Prasath F
* Abishek V
* Kiresh R

**Team Number:** 5

**Institution:** A.V.C. College of Engineering

**Program:** Salesforce Developer

---

## 🚀 Project Setup

This project was configured and tested using a **Salesforce Developer Edition organization**.

General setup flow:

```text
1. Create Salesforce Developer Edition Account
        ↓
2. Configure Salesforce Org
        ↓
3. Create Custom Objects
        ↓
4. Create Object Relationships
        ↓
5. Create Custom Fields
        ↓
6. Configure Salesforce Flow
        ↓
7. Create Prompt Builder Template
        ↓
8. Configure Agentforce
        ↓
9. Configure Permission Sets
        ↓
10. Test Parcel Tracking
```

The project was developed and tested in a Salesforce Developer Edition environment for academic purposes.

---

## 💡 Business Value

SwiftShip Tracker provides several operational benefits:

* Centralized parcel information
* Reduced manual tracking effort
* Improved customer self-service
* Conversational AI-based tracking
* Better delivery visibility
* Secure access control
* Structured parcel and delivery data
* Improved operational monitoring

---

## ⚠️ Current Limitations

The current academic implementation has some limitations:

* It depends on accurate Salesforce data.
* Agentforce responses depend on prompt configuration and available data.
* Salesforce configuration requires maintenance.
* External courier integrations are not included.
* Production deployment has not been performed.
* Advanced live-location capabilities can be added in future versions.

The project was built in a **Salesforce Developer Edition org** and was not deployed to production.

---

## 🔮 Future Enhancements

Future versions can include:

* 📍 Live GPS-based delivery tracking
* 🌐 Expanded Experience Cloud customer portal
* 📊 Advanced delivery analytics
* 🔗 External courier API integration
* 🤖 More advanced Agentforce capabilities
* 📦 Parcel booking through conversational AI
* 🔄 Parcel rescheduling through AI
* 🚀 Salesforce CI/CD deployment
* ⚙️ Additional automated logistics workflows

---

## 📁 Suggested Repository Structure

```text
SwiftShip-Tracker/
│
├── README.md
├── Documentation/
│   └── SwiftShip_Tracker_Project_Report.pdf
│
├── Salesforce/
│   ├── Objects/
│   ├── Flows/
│   ├── Prompt-Templates/
│   ├── Agentforce/
│   ├── Permission-Sets/
│   └── Reports/
│
├── Screenshots/
│   ├── Salesforce-Setup/
│   ├── Objects/
│   ├── Flows/
│   ├── Agentforce/
│   └── Testing/
│
└── LICENSE
```

---

## 🎓 Academic Project

**SwiftShip Tracker** was developed as an academic Salesforce implementation project to demonstrate practical knowledge of:

* Salesforce CRM
* Custom Object Modeling
* Salesforce Flow
* Prompt Builder
* Agentforce
* Role-Based Security
* Salesforce Data Management
* Reports & Dashboards
* Agile Project Development

---

## 📌 Project Status

**Status:** Academic Prototype / Developer Edition

**Platform:** Salesforce Developer Edition

**AI:** Agentforce + Prompt Builder

**Automation:** Salesforce Flow

**Database:** Salesforce Custom Objects

**Deployment:** Developer Edition only

---

## 👨‍💻 Author

### Balamurugan S

**B.Tech Information Technology**
A.V.C. College of Engineering

**Project:** SwiftShip Tracker
**Role:** Team Leader

---

## ⭐ Acknowledgement

This project demonstrates the application of Salesforce CRM, automation, conversational AI, and secure data management to solve practical parcel-management challenges.

---

### 📄 Documentation

For detailed architecture, configuration steps, data model, AI implementation, security design, testing approach, and project planning, refer to the complete project documentation included in this repository.
