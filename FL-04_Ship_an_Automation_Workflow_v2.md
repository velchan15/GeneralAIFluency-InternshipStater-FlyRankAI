# FL-04 – Ship an Automation Workflow v2 - Week 04 Task 4

## Student
**Name:** Evelyn Anastasia

## Objective
Design and evaluate a no-code AI workflow that automates technical writing through three predefined stages.

## Workflow Overview
This workflow converts a short project description into a structured technical report.

### Workflow Diagram

```text
Project Description
        │
        ▼
Step 1
Research & Analyze Requirements
        │
        ▼
Step 2
Generate Technical Report Draft
        │
        ▼
Step 3
Review, Improve & Format
        │
        ▼
Final Technical Report
```

## Tools Used
- Claude Desktop
- Claude Projects
- AI Project Instructions (No-code)

## Project Instructions

You are an engineering and AI technical writing assistant.

Your task is to generate clear, well-structured technical reports from a short project description.

Always follow this workflow:

1. Understand the project and identify its purpose.
2. Extract important technical components, technologies, and objectives.
3. Generate a structured report with:
   - Introduction
   - Objectives
   - System Overview
   - Technologies Used
   - Expected Results
   - Conclusion
4. Review the report for clarity, grammar, and logical consistency.
5. If information is missing, clearly state assumptions instead of inventing facts.

## Workflow Steps

### Step 1 – Research & Analyze
The AI identifies the project's objective, expected functionality, and required technologies.

**Output Handoff:** Project understanding.

### Step 2 – Generate Draft
The AI generates a structured technical report containing:
- Introduction
- Objectives
- System Overview
- Technologies Used
- Expected Results
- Conclusion

**Output Handoff:** Complete first draft.

### Step 3 – Review & Improve
The AI checks grammar, organization, readability, and consistency before producing the final report.

**Final Output:** Technical report ready for review.

# Five Test Runs

## Run 1
**Input:** ESP32-based Water Quality Monitoring System

**Output Sections**
I'll create a structured technical report for this project. Since the description is brief, I'll note my assumptions clearly rather than inventing unstated details.

---

# Technical Report: ESP32-Based Water Quality Monitoring System

## 1. Introduction

Access to clean and safe water is a fundamental requirement for public health, agriculture, and industrial processes. Traditional water quality assessment methods often rely on manual sampling and laboratory analysis, which can be time-consuming, costly, and unsuitable for continuous or remote monitoring. Embedded systems and Internet of Things (IoT) technologies now offer a practical alternative, enabling real-time, low-cost, and automated monitoring of water bodies or water supply systems.

This report describes the design and implementation of a **Water Quality Monitoring System based on the ESP32 microcontroller**. The ESP32 was selected as the core processing unit due to its integrated Wi-Fi/Bluetooth connectivity, low power consumption, and sufficient processing capability for sensor data acquisition and wireless transmission.

*Assumption: Since specific deployment context (e.g., drinking water, aquaculture, river monitoring) was not provided, this report assumes a general-purpose water quality monitoring application applicable to multiple use cases.*

## 2. Objectives

The primary objectives of this project are:

1. To design a low-cost, ESP32-based embedded system capable of measuring key water quality parameters.
2. To enable real-time data acquisition from multiple sensors simultaneously.
3. To transmit collected data wirelessly to a remote server, cloud platform, or mobile/web dashboard for monitoring and analysis.
4. To provide alert mechanisms when measured parameters exceed predefined safety thresholds.
5. To ensure the system is energy-efficient and suitable for continuous or semi-continuous operation.

*Assumption: Specific target parameters (e.g., pH, turbidity, TDS, temperature) were not explicitly listed in the project description. Commonly used water quality parameters are assumed below based on standard practice in similar systems.*

## 3. System Overview

The system architecture consists of three main layers: **sensing**, **processing and control**, and **communication/visualization**.

### 3.1 Sensing Layer
The system is assumed to include the following commonly used sensors for water quality monitoring:
- **pH Sensor** – measures the acidity/alkalinity of water.
- **Turbidity Sensor** – measures water clarity by detecting suspended particles.
- **Temperature Sensor** (e.g., DS18B20) – monitors water temperature, which affects other readings.
- **TDS (Total Dissolved Solids) Sensor** – estimates the concentration of dissolved substances.

### 3.2 Processing and Control Layer
The **ESP32 microcontroller** serves as the central processing unit. It performs the following functions:
- Reads analog and digital signals from connected sensors via ADC and GPIO pins.
- Processes raw sensor data, applying calibration and filtering as needed.
- Compares readings against threshold values to detect anomalies.
- Manages power states to optimize energy consumption.

### 3.3 Communication and Visualization Layer
- The ESP32 transmits processed data via **Wi-Fi** to a cloud platform or local server using protocols such as **MQTT** or **HTTP**.
- Data can be visualized through a **web dashboard** or **mobile application**, allowing users to monitor water quality trends over time.
- An **alert system** (e.g., notifications or SMS) can be triggered when values fall outside acceptable ranges.

*Assumption: The exact communication protocol and dashboard platform were not specified. MQTT/HTTP with a generic cloud dashboard (e.g., Blynk, Firebase, or a custom web server) is assumed as a typical implementation choice.*

## 4. Technologies Used

| Category | Technology/Component |
|---|---|
| Microcontroller | ESP32 (Wi-Fi + Bluetooth enabled) |
| Sensors | pH sensor, turbidity sensor, DS18B20 temperature sensor, TDS sensor |
| Communication Protocol | Wi-Fi, MQTT/HTTP |
| Data Visualization | Web dashboard / mobile application (e.g., Blynk, Firebase, ThingSpeak) |
| Power Supply | Battery or USB-powered, with potential for solar charging |
| Programming Environment | Arduino IDE / ESP-IDF (C/C++) |

*Assumption: Specific software platforms and power supply details were not stated; commonly adopted tools for ESP32-based IoT projects are listed as representative examples.*

## 5. Expected Results

Upon successful implementation, the system is expected to:
- Continuously monitor and report water quality parameters in real time.
- Provide historical data trends accessible via a remote dashboard.
- Generate timely alerts when water quality falls below acceptable standards.
- Demonstrate reliable wireless connectivity and low power consumption suitable for extended deployment.
- Serve as a scalable prototype that can be extended with additional sensors or integrated into larger environmental monitoring networks.

## 6. Conclusion

The ESP32-based Water Quality Monitoring System presents a cost-effective and scalable solution for real-time water quality assessment. By combining multiple sensor inputs with wireless communication capabilities, the system enables continuous monitoring without the need for manual sampling. This approach supports proactive water management, early detection of contamination, and data-driven decision-making for both public and private stakeholders.

Future enhancements may include integration with machine learning models for predictive water quality analysis, expansion of sensor arrays, and deployment of solar-powered units for remote or off-grid locations.

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/51b6a7d2-b7c5-4d2e-9b4a-606ff11333ad" />


---

## Run 2
**Input:** Library Management Website

**Output Sections**
# Technical Report: Library Management Website

**Note on assumptions:** The project description provided is brief ("Library Management Website"), so I've made reasonable assumptions about scope based on standard library management system conventions. These are flagged inline where applicable.

## 1. Introduction

A Library Management Website is a web-based software system designed to digitize and streamline the core operations of a library, including cataloging, book borrowing/returning, member management, and administrative oversight. Traditional manual library systems are prone to inefficiencies such as misplaced records, delayed book tracking, and limited accessibility for users. This project aims to address these challenges by providing an online platform accessible to both library staff and patrons, improving operational efficiency and user experience.

*Assumption: The system is intended for use by a small-to-medium institution (e.g., a school, university, or public library branch) with both staff (admin) and patron (user) roles.*

## 2. Objectives

The primary objectives of the Library Management Website are:

- To provide an online catalog of available books and resources, searchable by title, author, genre, or ISBN.
- To enable registered users to browse, reserve, and borrow books electronically.
- To allow library staff to manage inventory, track due dates, and process returns efficiently.
- To automate notifications for due dates, overdue fines, and reservation availability.
- To maintain accurate, centralized records of members, transactions, and inventory.
- To improve accessibility, allowing users to interact with library services remotely.

## 3. System Overview

The system is composed of the following core modules:

**3.1 User Management Module**
Handles registration, authentication, and role-based access control for two primary user types: administrators (library staff) and members (patrons).

**3.2 Catalog Management Module**
Manages the addition, update, and removal of book records, including metadata such as title, author, category, ISBN, and availability status.

**3.3 Borrowing and Returns Module**
Tracks book checkouts, due dates, returns, and calculates overdue fines where applicable.

**3.4 Search and Reservation Module**
Enables users to search the catalog and place holds/reservations on unavailable items.

**3.5 Admin Dashboard**
Provides library staff with tools to monitor inventory levels, generate reports, and manage member accounts.

**3.6 Notification System**
Sends automated alerts (e.g., email or in-app) for due dates, reservation availability, and overdue items.

*Assumption: The system follows a typical client-server web architecture with a relational database backend, as no specific architecture was provided.*

## 4. Technologies Used

Since specific technology choices were not provided, the following represents a commonly adopted stack for this type of application. These should be confirmed or adjusted based on actual project requirements:

| Layer | Suggested Technology | Purpose |
|---|---|---|
| Frontend | HTML, CSS, JavaScript (or React/Vue) | User interface and interactivity |
| Backend | Node.js / Django / PHP (Laravel) | Application logic and server-side processing |
| Database | MySQL / PostgreSQL / MongoDB | Storing book records, user data, and transactions |
| Authentication | JWT / Session-based Auth | Secure login and role management |
| Hosting | Cloud platform (e.g., AWS, Azure, or shared hosting) | Deployment and accessibility |
| Version Control | Git/GitHub | Source code management |

*Assumption: Technology stack is illustrative; actual implementation should align with team expertise, scalability needs, and institutional constraints.*

## 5. Expected Results

Upon successful implementation, the Library Management Website is expected to deliver:

- A fully functional online catalog with real-time book availability status.
- Reduced manual workload for library staff through automated tracking of loans and returns.
- Improved user satisfaction via self-service borrowing, reservations, and account management.
- Accurate, centralized data reducing the risk of lost or mismanaged records.
- Timely notifications that reduce overdue incidents and improve resource turnover.
- A scalable foundation that can be extended with future features (e.g., e-book integration, fine payment gateways, or analytics dashboards).

## 6. Conclusion

The Library Management Website addresses key inefficiencies in traditional library operations by offering a centralized, digital platform for cataloging, borrowing, and member management. By automating routine administrative tasks and improving accessibility for patrons, the system is positioned to enhance both operational efficiency and user experience. Further refinement of requirements—particularly around technology stack, user scale, and integration needs—will help ensure the final implementation aligns precisely with institutional goals.

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/b5554381-3069-4ee4-8dbb-23729aa371f3" />


---

## Run 3
**Input:** AI Resume Analyzer

**Output Sections**
# Technical Report: AI Resume Analyzer

**Note on assumptions:** The project description provided is minimal ("AI Resume Analyzer"). To produce a complete report, I have made reasonable assumptions about scope, based on common implementations of this type of system. These are flagged explicitly below rather than presented as confirmed facts.

---

## 1. Introduction

The AI Resume Analyzer is a software system designed to automatically evaluate resumes (CVs) using artificial intelligence and natural language processing (NLP) techniques. Its core purpose is to reduce the manual effort involved in reviewing candidate resumes by extracting relevant information, scoring candidates against job criteria, and providing actionable feedback to either recruiters or job applicants.

*Assumption: The target users are either (a) recruiters/HR teams screening candidates, or (b) job seekers wanting feedback on their resumes. This report addresses both use cases generically, since the specific audience was not stated.*

## 2. Objectives

The primary objectives of the system are assumed to be:

- Automatically parse resumes in common formats (PDF, DOCX) and extract structured data (skills, experience, education, certifications).
- Match extracted candidate data against a given job description or role requirements.
- Score or rank resumes based on relevance and fit.
- Identify gaps, missing keywords, or formatting issues that may hurt a candidate's chances (e.g., with Applicant Tracking Systems).
- Provide a summary report or dashboard output for the end user.

## 3. System Overview

*Assumption: A typical pipeline architecture is described below, as no specific architecture was provided.*

The system is expected to follow a multi-stage pipeline:

1. **Input Handling** – Accepts resume files (PDF/DOCX/plain text) and, optionally, a target job description.
2. **Text Extraction & Preprocessing** – Extracts raw text, cleans formatting artifacts, and normalizes content (e.g., section headers like "Experience," "Education," "Skills").
3. **Information Extraction (NLP/NER)** – Uses named entity recognition and pattern matching to identify key entities: names, job titles, skills, dates, institutions, and certifications.
4. **Semantic Matching** – Compares extracted candidate profile against job requirements using semantic similarity techniques (e.g., embeddings) rather than simple keyword matching.
5. **Scoring & Ranking** – Produces a quantitative score or qualitative rating reflecting candidate-job fit.
6. **Output Generation** – Presents results via a report, dashboard, or API response, including strengths, weaknesses, and improvement suggestions.

## 4. Technologies Used

*Assumption: The following represent a plausible, commonly used technology stack for this type of application. The actual stack was not specified in the project description.*

| Layer | Likely Technology |
|---|---|
| Programming Language | Python |
| NLP Processing | spaCy, NLTK, or Hugging Face Transformers |
| Resume Parsing | PDFMiner, python-docx, or pyresparser |
| Semantic Matching | Sentence-BERT / embedding models (e.g., OpenAI or open-source embeddings) |
| Backend Framework | Flask or FastAPI |
| Frontend (if applicable) | React or a simple web UI |
| Database | PostgreSQL / MongoDB for storing parsed data and results |
| Deployment | Docker containers, cloud hosting (AWS/GCP/Azure) |

## 5. Expected Results

Based on the stated objectives, the system is expected to deliver:

- Reduced manual screening time for recruiters by automating initial resume triage.
- Consistent, bias-reduced evaluation criteria compared to manual review (with the caveat that model bias must still be actively managed and audited).
- Actionable feedback for candidates to improve resume alignment with target roles.
- A measurable match score or ranking that correlates with actual candidate suitability, subject to validation against real hiring outcomes.

*Note: Without defined success metrics (e.g., accuracy targets, processing time benchmarks) in the original description, quantitative performance claims cannot be made.*

## 6. Conclusion

The AI Resume Analyzer, as reconstructed from the available project description, represents a practical application of NLP and machine learning to streamline resume screening and improve candidate-job matching. While the general architecture and objectives outlined here reflect standard practice for such systems, several details — including the exact user base, technology stack, and success metrics — were not specified and have been noted as assumptions throughout this report. To finalize a precise and actionable specification, further input is recommended on target users, required integrations (e.g., existing ATS platforms), and performance benchmarks.

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/fed41901-960d-479f-936b-ec6e51014fd1" />


---

## Run 4
# Technical Report: Smart Parking IoT System

*Note: The project description provided was brief ("Smart Parking IoT System"). Where specific details were not given, reasonable industry-standard assumptions have been made and are explicitly flagged below.*

## 1. Introduction

Urban areas worldwide face growing challenges related to parking space scarcity, traffic congestion, and inefficient use of available infrastructure. The Smart Parking IoT System is proposed as a technology-driven solution that leverages Internet of Things (IoT) sensors, wireless connectivity, and data processing to monitor, manage, and optimize parking space utilization in real time. This report outlines the system's purpose, objectives, architecture, and expected outcomes based on the given project scope.

**Assumption:** The system is intended for deployment in an urban or semi-urban setting (e.g., shopping malls, office complexes, or public street parking), as no specific deployment environment was specified.

## 2. Objectives

The primary objectives of the Smart Parking IoT System are:

* To detect and report the real-time occupancy status of individual parking spaces.
* To provide users with accurate, up-to-date information on parking availability via a mobile application or web dashboard.
* To reduce the time and fuel spent searching for parking, thereby lowering traffic congestion and emissions.
* To enable centralized monitoring and management of parking facilities for administrators.
* To collect historical usage data to support analytics and future infrastructure planning.

## 3. System Overview

The system is composed of the following functional layers:

**3.1 Sensing Layer**
Ultrasonic or infrared sensors are installed at each parking slot to detect the presence or absence of a vehicle. *(Assumption: Ultrasonic sensors are used due to their common adoption in similar systems; the original description did not specify sensor type.)*

**3.2 Communication Layer**
Sensor data is transmitted to a central gateway or cloud server using a low-power wireless protocol such as Wi-Fi, LoRa, or NB-IoT, depending on deployment scale and range requirements.

**3.3 Processing and Storage Layer**
A backend server or cloud platform receives, processes, and stores occupancy data. This layer aggregates data from all sensors and maintains a real-time database of parking slot statuses.

**3.4 Application Layer**
A user-facing mobile app or web dashboard displays available parking spaces, guides users to open slots, and may support features such as reservation or payment integration.

**3.5 Management Layer**
An administrative dashboard allows facility operators to monitor system health, view analytics, and manage parking rules or pricing.

## 4. Technologies Used

| Component | Technology (Assumed/Typical) |
|---|---|
| Sensing | Ultrasonic/IR sensors, microcontrollers (e.g., Arduino, ESP32) |
| Connectivity | Wi-Fi / LoRaWAN / NB-IoT |
| Backend | Cloud platform (e.g., AWS, Firebase, or similar IoT-supporting service) |
| Database | Real-time or NoSQL database for sensor data |
| Frontend | Mobile application (Android/iOS) and/or web dashboard |
| Data Analytics | Basic reporting/analytics tools for usage trends |

**Assumption:** Specific vendors, platforms, and hardware models were not provided; the table reflects commonly used technologies in comparable smart parking implementations.

## 5. Expected Results

Upon successful implementation, the system is expected to deliver:

* Real-time visibility of parking space availability with high accuracy.
* Reduced average time spent by drivers searching for parking.
* Improved traffic flow and reduced congestion near parking facilities.
* Data-driven insights for facility operators to optimize space allocation and pricing.
* A scalable foundation that can be extended to multiple parking locations or integrated with smart city infrastructure.

## 6. Conclusion

The Smart Parking IoT System addresses a practical urban mobility challenge by combining sensor-based detection, wireless communication, and data-driven applications. While this report is based on a limited initial project description and includes several reasonable assumptions regarding scope, hardware, and platform choices, it provides a solid technical foundation. To refine this report further, additional details—such as target deployment size, specific hardware constraints, budget, and required integrations (e.g., payment systems or municipal traffic systems)—would be valuable.

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/56b3d493-bbb4-4778-86fa-f9f2ba53d7aa" />


---

## Run 5
**Input:** Student Attendance System using Face Recognition

**Output Sections**
# Technical Report: Student Attendance System Using Face Recognition

## Introduction

Manual attendance tracking in academic institutions is time-consuming, prone to human error, and vulnerable to proxy attendance (students marking presence for absent peers). A Student Attendance System using Face Recognition addresses these issues by automating identity verification through biometric facial data, enabling accurate, real-time, and contactless attendance logging. This report outlines the purpose, architecture, technologies, and expected outcomes of such a system.

## Objectives

The primary objectives of the system are:

1. **Automate attendance recording** by identifying students through facial recognition rather than manual roll calls or ID card swipes.
2. **Eliminate proxy attendance** by ensuring that only the physically present, verified individual is marked.
3. **Reduce administrative overhead** for instructors and staff by generating attendance records automatically.
4. **Provide real-time and historical reporting** for attendance analytics (e.g., per-student, per-class, per-semester statistics).
5. **Ensure data security and privacy** in the storage and handling of biometric and academic records.

## System Overview

The system is designed around a pipeline that captures facial images, matches them against a pre-registered database, and logs attendance accordingly. A typical architecture includes:

1. **Enrollment Module**
   Each student's facial data is captured (multiple angles/lighting conditions recommended) and converted into a unique facial embedding (a numerical representation of facial features), which is stored in a database linked to the student's ID.

2. **Image Acquisition Module**
   A camera (classroom-mounted or entry-point camera) captures live video or still images of students at the start of a session.

3. **Face Detection and Preprocessing**
   Detected faces are cropped, aligned, and normalized (lighting/scale correction) to improve recognition accuracy.

4. **Face Recognition Engine**
   The processed face is converted into an embedding and compared against the enrolled database using similarity/distance metrics. A match above a defined confidence threshold identifies the student.

5. **Attendance Logging**
   Upon successful identification, the system timestamps and records the student's attendance in a database, avoiding duplicate entries within the same session.

6. **Admin/Reporting Dashboard**
   A web or desktop interface allows instructors/administrators to view attendance logs, generate reports, manage student enrollment, and configure system parameters (e.g., recognition thresholds, class schedules).

*Assumption: Since the project description does not specify deployment context (single classroom vs. institution-wide), this report assumes a modular design suitable for scaling from single-room to multi-room deployment.*

## Technologies Used

| Category | Suggested Technologies |
|---|---|
| Programming Language | Python |
| Face Detection | OpenCV (Haar Cascades / DNN module), MTCNN |
| Face Recognition | FaceNet, Dlib (ResNet-based), or OpenCV's LBPH/DNN face recognizer |
| Machine Learning Framework | TensorFlow or PyTorch (for training/embedding models) |
| Database | MySQL, PostgreSQL, or SQLite (for attendance and student records) |
| Backend Framework | Flask or Django (for API and dashboard) |
| Frontend/Dashboard | HTML/CSS/JavaScript, or a framework such as React |
| Hardware | Standard/IP camera, sufficient CPU/GPU for real-time inference |

*Assumption: Specific technologies were not specified in the project brief. The above stack represents common, well-supported choices for face-recognition attendance systems; the project team may substitute equivalent tools based on infrastructure and budget constraints.*

## Expected Results

Upon successful implementation, the system is expected to deliver:

- **Recognition accuracy** of approximately 90–99%, depending on lighting conditions, camera quality, and the recognition model used.
- **Reduced attendance-taking time**, from several minutes of manual roll call to a few seconds of automated capture.
- **Elimination of proxy attendance**, since presence is verified biometrically rather than self-reported.
- **Accurate digital records** accessible for reporting, audits, and academic policy enforcement (e.g., minimum attendance requirements).
- **Scalability** to multiple classrooms or campus-wide deployment with centralized data management.

## Conclusion

The Student Attendance System using Face Recognition offers a practical, technology-driven solution to the inefficiencies and vulnerabilities of manual attendance methods. By combining face detection, recognition algorithms, and a structured database/reporting layer, the system can significantly improve accuracy, save time, and provide reliable attendance analytics for educational institutions. Future enhancements could include anti-spoofing measures (e.g., liveness detection to prevent photo/video spoofing), integration with existing student information systems, and mobile app support for remote monitoring.

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/d47ff8d5-9bfc-4f38-bf5f-79519d18f79d" />

# Time Analysis

| Activity | Time |
|-----------|------|
| Claude Project setup | 15 minutes |
| Run 1 | 1 minute |
| Run 2 | 1 minute |
| Run 3 | 1 minute |
| Run 4 | 1 minute |
| Run 5 | 1 minute |
| **Total Workflow Time** | **20 minutes** |

Estimated manual creation of five reports: **100 minutes**

Estimated workflow completion: **20 minutes**

**Estimated time saved:** **80 minutes (approximately 80%)**

## Known Failure Points

- The AI may make assumptions if project descriptions are incomplete.
- Technical specifications should always be verified manually.
- Generated reports may require formatting adjustments.
- Domain-specific terminology should be reviewed by a human.
- Final review is required before submission.

## Human Review

Human review remains essential to:
- Verify technical accuracy.
- Confirm assumptions.
- Improve clarity where needed.
- Ensure the report matches the actual project.

## Reflection

Building this workflow demonstrated how a structured AI pipeline can automate repetitive writing tasks while maintaining consistency. Organizing the work into research, drafting, and review stages significantly reduced the time required to produce technical reports. Although the workflow improved efficiency, human verification is still necessary to ensure technical correctness and completeness. This project also strengthened my understanding of workflow design and prepared me for learning the differences between workflows and autonomous AI agents.

## Conclusion

This project successfully implemented a three-step no-code AI workflow using Claude Projects. The workflow completed five different technical writing tasks consistently and reduced the overall time required compared to manual writing. The results show that structured AI workflows are effective for repetitive writing tasks while still benefiting from human oversight.
