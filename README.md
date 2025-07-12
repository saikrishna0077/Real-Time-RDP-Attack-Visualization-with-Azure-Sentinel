# 🛡️ Real-Time RDP Attack Visualization with Azure Sentinel

**Author:** Sai Madukuri  
**Date:** September 2023  
**Tags:** Azure Sentinel, Cybersecurity, SIEM, Honeypot, Geolocation, RDP Attack, Visualization

---

## 📌 Project Overview

This project demonstrates how to detect, enrich, and visualize real-time RDP brute-force attacks using **Azure Sentinel** and a **honeypot Azure VM**.

By leveraging Sentinel's SIEM capabilities, custom PowerShell scripting, and a geolocation API, I created an interactive attack map to track where login attempts were originating across the globe.  

---

## 🧰 Tools & Technologies Used

- **Microsoft Azure**
  - Virtual Machine (Honeypot)
  - Azure Sentinel
  - Log Analytics Workspace
- **PowerShell**
- **Geolocation API** (e.g. [ip-api.com](http://ip-api.com) or [ipgeolocation.io](https://ipgeolocation.io))
- **Kusto Query Language (KQL)**

---

## 🧪 Implementation Steps

### 🔹 Step 1: Create Honeypot VM in Azure

- Deployed a Windows-based Azure Virtual Machine.
- Enabled **RDP access** (port 3389) to attract brute-force login attempts.
- Applied basic security group rules while allowing external RDP traffic.

📸 <img width="1903" height="872" alt="Azure" src="https://github.com/user-attachments/assets/ddbdb095-aeca-4bcc-a559-975d14043e60" />


---

### 🔹 Step 2: Set Up Azure Sentinel

- Created a **Log Analytics Workspace (LAW)**.
- Connected Azure Sentinel to the workspace.
- Added data connectors for:
  - Windows Security Events
  - Azure Activity Logs

📸 <img width="1888" height="887" alt="Azure 1" src="https://github.com/user-attachments/assets/ddc82421-d158-4557-bb81-b9eb345036ca" />


---

### 🔹 Step 3: IP Geolocation with PowerShell

- Wrote a PowerShell script to:
  - Extract attacker IPs from event logs.
  - Query a **Geolocation API** to get country, city, and lat/lon data.
  - Output enriched logs into Log Analytics.

📸 ![Azure 2](https://github.com/user-attachments/assets/15e9f36b-656b-4761-a8cd-64107f9ee26c)


---

### 🔹 Step 4: Create Real-Time Attack Map

- Used **KQL queries** in Azure Sentinel to filter logs with RDP login failures.
- Enriched data was visualized using Sentinel's map widget.
- Each point on the map represented a failed RDP attempt’s origin.

📸 ![Azure 3](https://github.com/user-attachments/assets/c483e0f5-4382-4477-947a-78f4b54d6d6e)

---

### 🔹 Step 5: Key Insights & Lessons Learned

This setup helped identify how vulnerable open RDP ports are in the wild. Key takeaways include:

- Use **strong, unique passwords**.
- Always **enable MFA** (Multi-Factor Authentication).
- **Restrict NSG rules** and limit public exposure of sensitive ports.
- Monitor suspicious activity in real time using SIEM tools like Sentinel.

---
Recommended Video

👉 Check out [Josh Madokar’s YouTube video](https://www.youtube.com) (🔗 link here if available) for a practical demonstration of this setup. His walkthrough complements this project with additional clarity and visuals.

---




