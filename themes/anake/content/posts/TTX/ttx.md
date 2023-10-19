+++
title = 'Detection Engineering'
date = 2023-10-19T10:00:00-07:00
draft = false
tags = ['Detection']
+++

# [Detection Engineering](https://d3fend.mitre.org)

Building an effective detection engineering system requires time, a scope and an understanding of the signals analysis you desire to perform. 
You should conduct training and assessments of your detection engineering environment focusing on understanding the threat model for your organization. 
When you consider how you will calcuate 'risk' I suggest that you use accessible language, this [tool](https://github.com/green-dino/TTX/blob/main/utils/dread.py) is focused on providing quantification and qualification of risk and even includes a random number generator to roll your chances based on 10,000 roles. 


This document, titled "Detection Engineering," serves as a comprehensive resource for individuals and teams involved in building effective detection engineering systems. The document emphasizes the importance of understanding and analyzing signals, conducting training and assessments, and comprehending the threat model relevant to your organization. It also introduces a tool for quantification and qualification of risk.

# MITRE ATT&CK: Techniques, Tactics, Subtechniques, and Procedures

MITRE ATT&CK (Adversarial Tactics, Techniques, and Common Knowledge) is a framework used to categorize the actions and behaviors of cyber adversaries. It is structured into several components, including:

## Tactics

Tactics represent high-level objectives or goals that adversaries aim to achieve during a cyberattack. These objectives are categorized into various areas:

1. **Initial Access:** This tactic encompasses techniques used by adversaries to gain their initial foothold in a target environment.

2. **Execution:** Under this tactic, adversaries execute malicious code on a target system.

3. **Persistence:** Techniques related to maintaining access to a compromised system are covered here.

4. **Privilege Escalation:** Adversaries seek to gain higher levels of access or privilege on the target system.

5. **Defense Evasion:** Techniques that help adversaries avoid detection or thwart security mechanisms fall under this tactic.

6. **Credential Access:** Adversaries aim to steal, collect, or abuse credentials for further actions.

7. **Discovery:** The discovery tactic includes methods used to gain information about the target environment.

8. **Lateral Movement:** This tactic involves techniques used by adversaries to move laterally within a network.

9. **Collection:** Techniques used to gather and exfiltrate information are categorized here.

10. **Command and Control:** Adversaries establish and maintain control over compromised systems using this tactic.

11. **Exfiltration:** Adversaries attempt to remove data from the target environment under this tactic.

12. **Impact:** Techniques that disrupt or damage systems and data are found in this category.

## Techniques

Techniques are specific methods or procedures that adversaries use to achieve the objectives defined by tactics. These are detailed actions that adversaries take during an attack. For example, "Spearphishing Attachment" is a technique under the "Initial Access" tactic.

## Subtechniques

Subtechniques are further refinements of techniques. They provide more specific details about how a technique can be executed. Subtechniques allow for a more granular understanding of adversary behavior. 

For example, "Spearphishing Attachment" might have subtechniques like "Malicious Word Document as Attachment" or "Malicious PDF Attachment" to describe different attack vectors within that technique.

## Procedures

Procedures represent detailed steps or implementations of specific techniques or subtechniques. They provide insights into how adversaries execute a particular technique in practice. These procedures can be specific to threat actor groups or campaigns and often include tools, tactics, and other contextual information.

Understanding MITRE ATT&CK's hierarchy of tactics, techniques, subtechniques, and procedures is crucial for cybersecurity professionals to detect, defend against, and respond to real-world cyber threats.

# Building Defense

[Information Technology](https://www.iso.org/obp/ui/#iso:std:iso-iec:19770:-1:ed-3:v1:en)

## Related Countermeasure Techniques
This table represents considerations for the modeling and defensive mesasures across the technology stack. There are countless combinations to consider. Don't overburden yourself, pick a few components and understand them before you move on to somethjing else. 

The Govern Section, provides where you should have documentaiton written, this can come in a variety of forms. Databases, physical print, but the important component is that the information exists and is accessibile for the teams. 

In the modeling column, consider this as a component where you can measure and model based on the risk assessment framework that you have implemented. 

Considerations for modeling and data analysis should consider these structures.
# Levels of Measurement and Quantifying Data

When dealing with data, it's essential to understand the levels of measurement, which determine the type of data you are working with and the mathematical operations you can perform on that data. There are four commonly recognized levels of measurement: Nominal, Ordinal, Interval, and Ratio. Let's explore these levels with examples drawn from the cybersecurity domain:

## 1. Nominal

- **Description:** Nominal data is the simplest level of measurement and deals with categories or labels. In this level, data is classified into distinct groups with no inherent order or numerical value. Nominal data often represents qualitative attributes or categorical variables.

- **Examples (Cybersecurity):** 
  - **Tactics:** Initial Access, Execution, Persistence
  - **File Types:** PDF, Word Document, Excel Spreadsheet
  - **User Roles:** Admin, Analyst, Guest

- **Quantification:** Nominal data is typically quantified using counts or frequencies. You can count the number of occurrences of each category, but mathematical operations like addition or subtraction are not meaningful.

## 2. Ordinal

- **Description:** Ordinal data includes categories that have a meaningful order or ranking but have unequal intervals between them. The differences between values do not have consistent meaning. Ordinal data allows you to compare data points in terms of greater than, less than, or equal to but not to determine the exact differences between them.

- **Examples (Cybersecurity):**
  - **Threat Levels:** Low, Moderate, High, Critical
  - **Severity Ratings:** Low, Medium, High
  - **User Privileges:** Read-Only, Read-Write, Administrator

- **Quantification:** Ordinal data can be quantified using ranking or ordering. You can determine the relative position of data points concerning each other, such as identifying which is greater or lesser. However, mathematical operations like addition or multiplication are not meaningful.

## 3. Interval

- **Description:** Interval data includes ordered categories with equal intervals between them. Unlike ordinal data, interval data allows meaningful comparisons of the differences between data points because the intervals are consistent. However, it lacks a true zero point, meaning that values can be negative or zero, but not undefined.

- **Examples (Cybersecurity):**
  - **Time:** Timestamps
  - **Software Version Numbers:** 2.0, 3.0, 4.0

- **Quantification:** Interval data can be quantified using numerical values, and you can perform mathematical operations like addition and subtraction on these values. However, since there is no true zero, ratios and multiplicative operations are not meaningful.

## 4. Ratio

- **Description:** Ratio data is the most advanced level of measurement, characterized by ordered categories with equal intervals and a true zero point. Ratio data allows for meaningful comparisons, addition, subtraction, multiplication, and division of data points.

- **Examples (Cybersecurity):**
  - **Count of Security Incidents**
  - **Response Time (in seconds)**
  - **Network Bandwidth (in megabits per second)**

- **Quantification:** Ratio data is quantified using numerical values, and you can perform all mathematical operations on these values because they have a true zero point. This allows for the calculation of ratios, proportions, and meaningful comparisons.

Understanding the level of measurement of your cybersecurity data is crucial when selecting appropriate statistical methods and visualizations to analyze and interpret your data effectively.

---



|          Govern            | Model                        | Harden                        | Detect                        | Isolate                       | Deceive                       | Evict                         |
|----------------------|------------------------------|------------------------------|------------------------------|------------------------------|------------------------------|----------------------------|
|                      |                             | Application Hardening          | File Analysis                  | Execution Isolation            | Decoy Environment              | Credential Eviction           |
| Asset Inventory       | Asset Vulnerability Enumeration | Application Configuration Hardening | Dynamic Analysis            | Executable Allowlisting       | Connected Honeynet             | Account Locking                |
| Configuration Inventory | Data Inventory              | Dead Code Elimination         | Emulated File Analysis         | Executable Denylisting         | Integrated Honeynet            | Authentication Cache Invalidation |
| Hardware Component Inventory | Network Node Inventory | Exception Handler Pointer Validation | File Content Rules         | Hardware-based Process Isolation | Standalone Honeynet          | Credential Revoking            |
| Network Mapping       | Software Inventory           | Pointer Authentication          | File Hashing                   | IO Port Restriction            | Decoy Object                  | File Eviction                 |
| Logical Link Mapping  | Network Traffic Policy Mapping | Process Segment Execution Prevention | Identifier Analysis          | Kernel-based Process Isolation | Decoy File                    | File Removal                   |
| Active Logical Link Mapping | Physical Link Mapping | Segment Address Offset Randomization | Homoglyph Detection          | Mandatory Access Control        | Decoy Network Resource        | Email Removal                   |
| Passive Logical Link Mapping | Active Physical Link Mapping | Stack Frame Canary Validation  | Identifier Activity Analysis | System Call Filtering           | Decoy Persona                  | Process Eviction               |
| Network Traffic Policy Mapping | Operational Activity Mapping | Credential Hardening           | Identifier Reputation Analysis | Network Isolation               | Decoy Public Release           | Process Suspension              |
| Physical Link Mapping  | Access Modeling             | Biometric Authentication       | Domain Name Reputation Analysis | Broadcast Domain Isolation     | Decoy Session Token           | Process Termination             |


## [Digital Event Types](https://d3fend.mitre.org/taxonomies/d3f:DigitalEvent/)

Fundamentally computers function in the same manner, there are considerations based on how these components work together, understanding the fundamental approach to systems engineering, and computer science will align you to understand that there are activites that occur when a user interacts with a system. This next section explores the components you should become familiar with to more clearly align your detection engineering process 

This is a simplified approach to highlighting common terminology that will keep you team communicating with language that you all understand. 

###  DNS Lookup 
- **Definition:** A Domain Name System (DNS) lookup is a record returned from a DNS resolver after querying a DNS name server. Typically considered an A or AAAA record, where a domain name is resolved to an IPv4 or IPv6 address, respectively.
###  Command 
- **Definition:** In computing, a command is a directive to a computer program acting as an interpreter of some kind, to perform a specific task. Most commonly, a command is either a directive to some kind of command-line interface, such as a shell, or an event in a graphical user interface triggered by the user selecting an option in a menu.
###  Resource Access 
- **Definition:** Ephemeral digital artifact comprising a request of a resource and any response from that resource.
###  System Call 
   - **Definition:** A system call is the programmatic way in which a computer program requests a service from the kernel of the operating system it is executed on. This may include hardware-related services (for example, accessing a hard disk drive), creation and execution of new processes, and communication with integral kernel services such as process scheduling. System calls provide an essential interface between a process and the operating system.
###  User Action 
   - **Definition:** An action performed by a user. Executing commands, granting permissions, and accessing resources are examples of user actions.


# Relationships

This section explains the relationships of the Attack and Defend matricies. A technique will require an understanding of how the system functions and operates. 
Spend time creating diagrams and relationship dependencies to determine what technique is the appropriate technique based on your knowledge, skills and abilities. 

| ATT&CK ID | ATT&CK Mitigation |  | Related D3FEND Techniques |
| --- | --- | --- | --- |
| M1013 | Application Developer Guidance | | A future release of D3FEND will define a taxonomy of Source Code Hardening Techniques. |
| M1015 | Active Directory Configuration | | D3-ANCI Authentication Cache Invalidation <br> D3-DTP Domain Trust Policy <br> D3-UAP User Account Permissions <br> M1015 scope is broad, touches on a wide variety of techniques in D3FEND. |
| M1016 | Vulnerability Scanning | | Future D3FEND releases will model the scanning and inventory domains. |
| M1017 | User Training | | Modeling user training is outside the scope of D3FEND. |
| M1018 | User Account Management | | D3-LFP Local File Permissions <br> D3-MAC Mandatory Access Control <br> D3-SCP System Configuration Permissions |
| M1019 | Threat Intelligence Program | | Establishing and running a Threat Intelligence Program is outside the scope of D3FEND. |
| M1020 | SSL/TLS Inspection | | D3-NTA Network Traffic Analysis <br> D3FEND models this as an infrastructure dependency to support D3-NTA. |
| M1021 | Restrict Web-Based Content | | D3-DNSAL DNS Allowlisting <br> D3-DNSDL DNS Denylisting <br> D3-FA File Analysis <br> D3-ITF Inbound Traffic Filtering <br> D3-NTA Network Traffic Analysis <br> D3-OTF Outbound Traffic Filtering <br> D3-UA URL Analysis <br> M1021 scope is broad, touches on a wide variety of techniques in D3FEND. |
| M1022 | Restrict File and Directory Permissions | | D3-LFP Local File Permissions |
| M1024 | Restrict Registry Permission | | D3-SCP System Configuration Permissions |
| M1025 | Privileged Process Integrity | | D3-BA Bootloader Authentication <br> D3-DLIC Driver Load Integrity Checking <br> D3-MAC Mandatory Access Control <br> D3-PSEP Process Segment Execution Prevention |
| M1026 | Privileged Account Management | | D3-DAM Domain Account Monitoring <br> D3-LAM Local Account Monitoring <br> D3-SPP Strong Password Policy |
| M1027 | Password Policies | | D3-OTP One-time Password <br> D3-SPP Strong Password Policy |
| M1028 | Operating System Configuration | | D3-PH Platform Hardening |
| M1029 | Remote Data Storage | | IT disaster recovery plans are outside the current scope of D3FEND. |
| M1030 | Network Segmentation | | D3-BDI Broadcast Domain Isolation <br> D3-ET Encrypted Tunnels <br> D3-ISVA Inbound Session Volume Analysis <br> D3-ITF Inbound Traffic Filtering |
| M1031 | Network Intrusion Prevention | | D3-ITF Inbound Traffic Filtering <br> D3-NTA Network Traffic Analysis <br> D3-OTF Outbound Traffic Filtering |
| M1032 | Multi-factor Authentication | | D3-MFA Multi-factor Authentication |
| M1033 | Limit Software Installation | | D3-EAL Executable Allowlisting <br> D3-EDL Executable Denylisting |
| M1034 | Limit Hardware Installation | | D3-IOPR IO Port Restriction |
| M1035 | Limit Access to Resource Over Network | | D3-NI Network Isolation |
| M1036 | Account Use Policies | | D3-AL Account Locking <br> D3-ANCI Authentication Cache Invalidation <br> D3-ANET Authentication Event Thresholding <br> D3-AZET may be related (is potentially related though not called out in ATT&CK definition.) |
| M1037 | Filter Network Traffic | | D3-NI Network Isolation |
| M1038 | Execution Prevention | | D3-DLIC Driver Load Integrity Checking <br> D3-EAL Executable Allowlisting <br> D3-EDL Executable Denylisting <br> D3-PSEP Process Segment Execution Prevention |
| M1039 | Environment Variable Permissions | | D3-ACH Application Configuration Hardening <br> D3-SFA System File Analysis |
| M1040 | Behavior Prevention on Endpoint | | D3-ANET Authentication Event Thresholding <br> D3-AZET Authorization Event Thresholding <br> D3-JFAPA Job Function Access Pattern Analysis <br> D3-RAPA Resource Access Pattern Analysis <br> D3-SDA Session Duration Analysis <br> D3-UDTA User Data Transfer Analysis <br> D3-UGLPA User Geolocation Logon Pattern Analysis <br> D3-WSAA Web Session Activity Analysis |
| M1041 | Encrypt Sensitive Information | | D3-DENCR Disk Encryption <br> D3-ET Encrypted Tunnels <br> D3-FE File Encryption <br> D3-MENCR Message Encryption |
| M1042 | Disable or Remove Feature or Program | | D3-ACH Application Configuration Hardening <br> D3-EDL Executable Denylisting <br> D3-MAC Mandatory Access Control |
| M1043 | Credential Access Protection | | D3-HBPI Hardware-based Process Isolation |
| M1044 | Restrict Library Loading | | D3-SCF System Call Filtering <br> D3-SCF is one possible way to filter library loading. |
| M1045 | Code Signing | | D3-DLIC Driver Load Integrity Checking <br> D3-EAL Executable Allowlisting <br> D3-SBV Service Binary Verification |
| M1046 | Boot Integrity | | D3-BA Bootloader Authentication <br> D3-TBI TPM Boot Integrity |
| M1047 | Audit | | D3-DAM Domain Account Monitoring <br> D3-LAM Local Account Monitoring <br> D3-SFA System File Analysis <br> M1047 scope is broad, touches on a wide variety of techniques in D3FEND. |
| M1048 | Application Isolation and Sandboxing | | D3-DA Dynamic Analysis <br> D3-HBPI Hardware-based Process Isolation <br> D3-MAC Mandatory Access Control <br> D3-SCF System Call Filtering <br> "Sandboxing" is often used to describe a detection environment which includes some forms of analysis (see D3-DA). Many forms of isolation (e.g., quarantining) are more static in nature and simply limit software's access to system resources. |
| M1049 | Antivirus/Antimalware | | D3-FCR File Content Rules <br> D3-FH File Hashing <br> D3-PA Process Analysis <br> Process Analysis and subclasses. |
| M1050 | Exploit Protection | | D3-AH Application Hardening <br> D3-EHPV Exception Handler Pointer Validation
