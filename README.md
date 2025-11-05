# examsecure-project
**IU Master's Project - Online exam monitoring system**
ExamSecure utilizes a lightweight, event-driven architecture based on the MERN stack (MongoDB, Express, React, Node.js) to monitor academic integrity non-invasively. The system is designed around the principle of Privacy-by-Design, ensuring only minimal, pseudonymized activity metadata is collected.

   1. **Presentation Tier (Client - React.js)**
This is the interface the student interacts with and runs entirely within the web browser. Its primary function is robust, non-invasive detection.

-**Technology:** React.js

-**Core Role**: Runs all the detection logic using standard browser APIs.

-**Integrity Indicators (Multi-Indicator Approach)**:

--Tab-Switch/Focus Loss: Detected via the Page Visibility API and window onblur events (High Weight).

--Prolonged Inactivity: Detected by tracking mouse and keypress events (Low Weight).

-**Data Sent**: Sends lightweight, time-stamped Violation Events (JSON payload) to the server via HTTP POST.

2. **Application Tier (Server - Node.js/Express)**
This is the central processing unit of the system, responsible for receiving, processing, and storing the event data.

-**Technology**: Node.js and Express

-**Core Role**: Receives, validates, and processes incoming integrity events in real-time.

-**Processing**: The server hosts the main API endpoint (/api/violation) that logs the events. It will calculate the Integrity Score by applying different weights to the event types (e.g., Tab-Switch is weighted higher than Inactivity).

-**Output**: Stores the final integrity records in the MongoDB database.

3. **Data Tier (Database - MongoDB)**
The dedicated storage for all project data, adhering strictly to the data minimization principle.

-**Technology**: MongoDB

-**Core Role**: Stores time-series metadata for every exam session.

-**Data Stored (Pseudonymized)**: Only non-PII (Personally Identifiable Information) metadata is saved, including sessionId, eventType, timestamp, and the calculated integrityScore. No keystroke content, video, or biometric data is ever collected.




<img width="661" height="131" alt="saupdated123" src="https://github.com/user-attachments/assets/0f2bcb01-2dc8-4283-a3f2-ada25e83870e" />
