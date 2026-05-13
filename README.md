# Okta-Zero-Trust-IAM
Implementing a hardened Zero-Trust identity perimeter using Okta, featuring adaptive MFA, network zones, and NIST-compliant credential policies.
# Okta Zero-Trust IAM Implementation
**Architecting an enterprise identity perimeter with Okta, featuring adaptive MFA, network zones, and NIST-compliant credential hardening.**

### **Project Overview**
This project demonstrates the implementation of a **Zero-Trust Identity and Access Management (IAM)** framework using the Okta Identity Cloud. The goal was to engineer a hardened identity perimeter that enforces context-aware access controls, adaptive multi-factor authentication (MFA), and NIST-compliant credential policies. 

### **Technologies & Tools Used**
* **Identity Provider**: Okta Identity Cloud
* **Security Framework**: Zero-Trust Architecture
* **Authentication**: Adaptive MFA (Okta Verify), Windows Hello
* **Compliance**: NIST Password Complexity Standards
* **Monitoring**: Okta System Logs (SIEM Telemetry)

---

### **1. Network Perimeter Configuration and Trusted Zones**
I established the organization’s digital boundary by configuring a **Trusted IP Zone**. By defining a **"Corporate Network"** via specific Gateway IPs, I created the necessary telemetry for the system to distinguish between verified internal traffic and untrusted external requests. 

<img src="images/01-network-zones.png" width="800">

---

### **2. Adaptive MFA Orchestration and Identity Governance**
I engineered a comprehensive **MFA Enrollment Policy** targeted at privileged groups. I implemented **Role-Based Access Control (RBAC)** to ensure that different segments of the identity lifecycle are governed by appropriate security triggers.

<img src="images/02-mfa-policy.png" width="800">

---

### **3. Context-Aware Enrollment and Geofencing Logic**
I established the conditional logic governing the enrollment gateway. This enforces a **geofencing** strategy where enrollment is only allowed if the user’s IP originates from the pre-defined **"Corporate Network"** zone.

<img src="images/03-geofencing.png" width="800">

---

### **4. Policy Hierarchy and Authenticator Enrollment Summary**
This overview confirms the successful orchestration of the **MFA Enrollment Policy** at **Priority 1**. This ensures that specialized security requirements take precedence over the standard "Default Policy."

<img src="images/04-policy-summary.png" width="800">

---

### **5. Zero-Trust Boundary: The "Implicit Deny" Rule**
I implemented the final safety net: a global **"Deny Enrollment"** rule. When an authentication request does not meet the specific "Allow" criteria, it falls through to this rule where access is explicitly **Denied**.

<img src="images/05-implicit-deny.png" width="800">

---

### **6. Password Governance and Complexity Hardening**
I implemented a rigorous **Password Requirement** policy aligning with **NIST-standard guidelines**, establishing a **12-character minimum length** to increase the computational cost of brute-force attacks.

<img src="images/06-password-complexity.png" width="800">

---

### **7. Account Lockout Policies and Brute-Force Mitigation**
I implemented a strict **Lockout Policy** to defend against automated credential-stuffing. The configuration enforces a **lockout after 3 unsuccessful attempts** with a 30-minute automatic unlock.

<img src="images/07-account-lockout.png" width="800">

---

### **8. User Identity Verification Challenge**
The platform requires the test user to initiate a verification email. This **Out-of-Band (OOB)** authentication step ensures that the user has physical control over the secondary communication channel.

<img src="images/08-challenge.png" width="800">

---

### **9. User Enrollment Flow: MFA Trigger**
This step validates that the **MFA Enrollment Policy** is correctly triggering. The user is prompted to request a verification email, protecting against unauthorized or accidental sign-in requests.

<img src="images/09-mfa-trigger.png" width="800">

---

### **10. Factor Enrollment Completion and Endpoint Verification**
This validates the successful enrollment of **Okta Verify** on the target device. It demonstrates integration with local device security features like **Windows Hello**.

<img src="images/10-enrollment-complete.png" width="800">

---

### **11. Final Dashboard Access and Portal Entry**
Once all security criteria are met, the user is granted access to the end-user dashboard. This proves the successful end-to-end execution of the Zero-Trust access flow.

<img src="images/11-dashboard-success.png" width="800">

---

### **12. Auditing and Compliance: System Log Verification**
The final component provides forensic proof. As captured in the **Okta System Logs**, the event `user.mfa.factor.activate` was recorded with a status of **SUCCESS**, confirming the policies were executed correctly.

<img src="images/12-system-logs.png" width="800">

---

> ### **Final Conclusion**
> This implementation demonstrates that **Identity is the new perimeter.** By moving away from static passwords toward an **Adaptive, Zero-Trust model**, I have significantly reduced the organizational attack surface while maintaining a seamless user experience.
