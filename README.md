# DataP
# Portfolio: Security Engineering, Data Automation & IAM

Welcome to my technical portfolio. This repository highlights projects combining data analytics, process automation, hands-on network security, and cloud identity management.

---

# [Project 1: Nox Run Club Insights Engine](https://www.instagram.com/p/Da-5vLJS4-E/?utm_source=ig_web_copy_link&dlrf=MzRlODBiNWFlZA==&srtk=MzRlODBiNWFlZA==)

### Overview
Engineered an autonomous email insights service built to ingest, process, and distribute operational metrics and health telemetry for the Nox Run club community. 

* **Pipeline Architecture:** Automated data ingestion, cleaning, and reporting workflows using Python and Google Apps Script.
* **Data Hygiene & Validation:** Designed validation logic to filter out corrupt or inconsistent records prior to automated summarization.
* **Security & GRC Relevance:** Demonstrates core proficiency in scripting, data manipulation, and automated reporting—skills directly applicable to SIEM log parsing, anomaly detection, and compliance auditing.

## Automated Telemetry & Pipeline Flow  
![Pipeline Architecture Diagram](Images/Picture1.png)  

## Sample Metric & Performance Output  
![Report Dashboard & Data Metrics](Images/Picture2.png)

---

# [Project 2: Wireless Traffic Analysis & Identity / Access Control Lab](https://github.com/RonitMalik/BlackFriday_pythonScrapper)

### Overview
Built a dedicated security testing laboratory using Kali Linux to evaluate wireless perimeter vulnerabilities, capture raw 802.11 network traffic, and model Role-Based Access Controls (RBAC).

* **Perimeter & Packet Analysis:** Configured a local testing environment to capture and inspect wireless handshakes and broadcast traffic using Wireshark, identifying encryption weaknesses and credential exposure risks.
* **IAM & Access Enforcement:** Modeled identity lifecycle management workflows, enforcing the Principle of Least Privilege (PoLP) and validating access control policies.
* **Security Relevance:** Proves hands-on capability in network sniffing, packet analysis, and perimeter hardening, bridging offensive visibility with defensive architecture.

## Wireshark Packet Capture & Handshake Analysis  
![Kali Linux Wireshark Capture](Images/Kali_Wireshark.png)  

## IAM Role & RBAC Mapping Architecture  
![IAM Policy Model](Images/IAM_RBAC.png)

---

# [Project 3: AWS Cloud IAM Hardening & Least-Privilege Audit](https://github.com/RonitMalik/BlackFriday_pythonScrapper)

### Overview
Simulated an enterprise cloud environment to audit over-privileged IAM policies and remediate security vulnerabilities in AWS. Designed custom JSON policies to enforce strict resource scoping, Multi-Factor Authentication (MFA), and secure transport logic.

* **Policy Remediation:** Refactored overly permissive wildcard (`*`) IAM policies into strict, least-privilege configurations limiting access to designated S3 resource ARNs.
* **Condition-Based Access Control:** Implemented explicit `Deny` conditions requiring active MFA sessions and TLS encryption for all incoming cloud API requests.
* **Validation:** Verified policy logic and access boundaries using the AWS CLI Policy Simulator.

## Remediated Least-Privilege JSON Policy Structure
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "RestrictedS3ReadOnlyAccess",
      "Effect": "Allow",
      "Action": [
        "s3:ListBucket",
        "s3:GetObject"
      ],
      "Resource": [
        "arn:aws:s3:::prod-analytics-data-atl",
        "arn:aws:s3:::prod-analytics-data-atl/*"
      ]
    },
    {
      "Sid": "EnforceMFAAndTLS",
      "Effect": "Deny",
      "Action": "s3:*",
      "Resource": "*",
      "Condition": {
        "Bool": {
          "aws:MultiFactorAuthPresent": "false",
          "aws:SecureTransport": "false"
        }
      }
    }
  ]
}
