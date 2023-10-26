+++
title = 'How attackers operate '
date = 2023-10-24T11:00:00-07:00
draft = false
tags = ['Assessments']
+++

# Methods of Gaining Initial Access in Cybersecurity

Cyber attackers, like "Octo Tempest," employ various methods to gain initial access to organizations. These methods include:

1. **Social Engineering**: Deceptive tactics to manipulate employees.
2. **Phone-Based Social Engineering**: Tricking users into taking actions like installing malicious software or revealing information.
   - Installing a Remote Monitoring and Management (RMM) utility.
   - Navigating to fake login portals.
   - Removing a FIDO2 token.
   - Manipulating the help desk to reset passwords or change/add multi-factor authentication.
   - Purchasing employee credentials on the black market.
   - Sending SMS phishing messages with fake login links.
   - Using mobile telecommunications access for SIM swaps and call forwarding to control an employee's phone.

These methods highlight the importance of being vigilant in the face of potential cyber threats.

Here are examples of tools to consider detection enginereing around.

# Additional tradecraft and techniques:
PingCastle and ADRecon to perform reconnaissance of Active Directory 

Advanced IP Scanner to probe victim networks

Govmomi Go library to enumerate vCenter APIs 

PureStorage FlashArray PowerShell module to enumerate storage arrays 

AAD bulk downloads of user, groups, and devices

# Techniques for Privilege Elevation

Cyber attackers, such as "Octo Tempest," employ various techniques to elevate their privileges within an organization. These techniques include:

1. **SIM Swap and Phone Number Forwarding**: Utilizing pre-existing access to mobile telecommunications and business process outsourcing organizations to initiate a SIM swap or set up call number forwarding on an employee's phone. Once control over the employee's phone number is achieved, Octo Tempest can initiate a self-service password reset on the user's account.

2. **Social Engineering**: Involves contacting an organization's help desk and using manipulative tactics to trick them into resetting an administrator's password or changing/adding a multi-factor authentication token/factor.

These techniques highlight the need for organizations to be vigilant and implement robust security measures to protect against privilege escalation by malicious actors.

# Advanced Social Engineering for Privilege Escalation

In the realm of cybersecurity, malicious actors often employ advanced social engineering strategies for privilege escalation. These strategies involve several key elements:

- **Stolen Password Policy Procedures**: Cyber attackers may exploit knowledge of an organization's password policy procedures to their advantage. This allows them to navigate the organization's security measures more effectively.

- **Bulk Downloads**: Attackers often use bulk downloads of user, group, and role exports to gain insights and information that can aid in privilege escalation.

- **Familiarity with Target Organization**: A deep understanding of the target organization's procedures is crucial for successful privilege escalation. Attackers leverage their knowledge to manipulate and bypass security measures.

- **Building Trust**: Building trust is a common tactic. Attackers may use compromised accounts, demonstrate an understanding of the organization's procedures, and employ various methods to gain trust within the organization.

- **Bypassing Password Reset Procedures**: In some cases, attackers go to great lengths, such as using a compromised manager's account to approve their requests and bypass password reset procedures.

These tactics underscore the need for organizations to not only strengthen their technical defenses but also educate their employees about the importance of vigilance in recognizing and countering advanced social engineering attempts.

# Compromising Security Measures for Stealth

- **Account Compromise**: The threat actor gains unauthorized access to accounts belonging to security personnel. These accounts are typically responsible for managing security products and features within the organization.

- **Disabling Security Features**: Once inside, the attacker turns off security products and features that are designed to protect the organization's digital environment. This action weakens the organization's defenses and allows them to operate more freely.

- **Use of EDR and Device Management**: The attacker leverages Endpoint Detection and Response (EDR) tools and device management technologies. These tools are used to deploy malicious software, remove or impair security products, and execute various actions that support their malicious intent.

- **Data Theft**: Among the attacker's objectives is data theft. They target sensitive files, which could include credentials, messaging databases, and other valuable information. This stolen data can be used for further compromise or exploitation.

- **Deploying Malicious Payloads**: To maintain control and continue their activities, the attacker deploys malicious payloads onto the compromised systems. These payloads could be various forms of malware or hacking tools.

This complex process allows the threat actor to infiltrate an organization, disable security measures, steal critical data, and execute malicious actions. It underscores the need for organizations to be vigilant in safeguarding their security personnel's accounts and continually improving their security measures to counteract these threats.

# Manipulating Identity Providers for Illicit Access

- **Federating Domains**: Threat actors use tools like AADInternals to federate existing domains or create and federate new domains. Federation involves linking an external domain (e.g., an organization's domain) with a service provider's identity system.

- **Spoofing Domains**: In some cases, the attacker might add and federate new domains to impersonate legitimate ones. This is done to trick the identity provider into accepting their requests.

- **Golden SAML Attack**: With a successfully manipulated federation, the threat actor can exploit it to generate forged valid Security Assertion Markup Language (SAML) tokens. These tokens are like digital tickets that vouch for a user's identity and permissions. What's noteworthy is that these tokens carry claims, such as satisfying multi-factor authentication (MFA), making them appear genuine. This technique is known as "Golden SAML."

- **Okta-Based Impersonation**: Sometimes, attackers use identity providers like Okta as their source of truth. They leverage Okta's Org2Org functionality to impersonate any desired user account within the system.

This process allows threat actors to compromise the identity verification systems and generate deceptive tokens, granting them unauthorized access to target systems. It emphasizes the importance of robust security measures and vigilance in safeguarding identity providers.

# Harvesting and Exfiltrating Data

 **Data Access**: The attacker gains access to valuable data stored in different repositories and systems. This includes code repositories, large document management and storage systems (like SharePoint), SQL databases, cloud storage blobs/buckets, and even email data.

- **Legitimate Tools**: To carry out these actions stealthily, the threat actor employs legitimate management clients. These tools are intended for tasks like database management and storage, making their actions less suspicious. Some examples include DBeaver, MongoDB Compass, Azure SQL Query Editor, and Cerebrata.

- **Connection and Collection**: The attacker's purpose is to connect to these data sources and collect information. This could include documents, databases, code, and more. This data is often sensitive and valuable.

- **Exfiltration**: Once the data harvesting is complete, the threat actor needs a way to move the stolen data to a location of their choosing. They often use anonymous file-hosting services for this, such as GoFile.io, Sh.Azl, StorjShare, Temp.sh, MegaSync, Paste.ee, Backblaze, and AWS S3 buckets. These services make it difficult to trace the origin of the data.

This process allows the attacker to access, collect, and exfiltrate data without raising immediate suspicions. Organizations need to implement robust data security measures to counteract these threats and protect their sensitive information.

# Advanced Data Extraction and Exfiltration Technique
- **Azure Data Factory**: This platform is typically used for legitimate data integration and movement tasks, making it an inconspicuous choice for a threat actor. By harnessing the capabilities of Azure Data Factory and its automated pipelines, the attacker can systematically extract data from a variety of sources.

- **SFTP Servers**: The data is transferred to external SFTP servers hosted and controlled by the attacker. This approach is designed to blend in with typical big data operations, making it harder to detect. Using SFTP, a common method for securely transferring data, adds an extra layer of camouflage to the malicious activity.

- **Microsoft 365 Backup Solutions**: In addition to the Azure Data Factory technique, threat actors frequently register legitimate Microsoft 365 backup solutions, such as Veeam, AFI Backup, and CommVault. These solutions are designed for data backup and recovery. However, the attackers exploit them to export the contents of SharePoint document libraries, expediting the exfiltration of sensitive data.

This technique showcases the adaptability and sophistication of modern cyber threats. It underlines the importance of constant vigilance and advanced security measures to counteract these tactics. Organizations need to be aware of the potential misuse of seemingly legitimate tools and platforms for illicit data extraction and exfiltration.

# Ransomware Deployment and Data Theft
- **Data Theft Objectives**: Threat actors who deploy ransomware often combine it with data theft objectives. Before encrypting the victim's data, they may exfiltrate sensitive information. This dual approach not only holds the data hostage but also threatens to expose it, increasing the pressure on victims to pay the ransom.

- **Targeted Platforms**: Ransomware attacks aren't limited to Windows systems; they also target Unix/Linux endpoints and VMware hypervisors. This diversity in targeted platforms allows the threat actors to affect a wide range of systems and potentially disrupt the entire organization's operations.

- **ALPHV/BlackCat Variant**: The specific variant of ransomware mentioned in this context is ALPHV/BlackCat. Variants of ransomware often have unique characteristics, and some are more damaging than others. In this case, the threat actors have selected a variant that may be particularly effective in achieving their objectives.

- **Hypervisor-Level Encryption**: Notably, the threat actors use hypervisor-level encryption. This means they encrypt the entire virtualization infrastructure, including virtual machines and their data. Such an approach can have a significant impact on organizations because it makes recovery efforts considerably more challenging post-encryption. Restoring virtual environments is complex and time-consuming.

This analysis highlights the severity of ransomware attacks, especially when combined with data theft, multi-platform targeting, and advanced encryption techniques. It underscores the importance of robust cybersecurity measures, data backup strategies, and proactive security practices to mitigate the risks and consequences of such attacks.

# Post-Encryption Ransom Negotiation

- **Direct Communication**: Following the encryption of a victim's data, the threat actors frequently establish direct communication with the target organization and its personnel. This direct contact serves multiple purposes, such as delivering ransom demands and instructions.

- **"Proof of Life"**: As part of the negotiation process, the attackers may provide a form of "proof of life." In this context, this proof of life involves sharing samples of exfiltrated data. This is done to convince the victim that the attackers indeed have access to their sensitive information and can potentially expose or misuse it.

- **Public Leaks**: A noteworthy consequence of these post-encryption communications is that many of them have been leaked publicly. These leaks often involve communication records, ransom notes, and sometimes even the exfiltrated data samples. These public disclosures can lead to significant reputational damage for the affected organizations.

This analysis highlights the interpersonal aspect of ransomware attacks, where communication and negotiation play a crucial role. It also underscores the potential consequences of such negotiations being exposed to the public, including reputational harm to targeted organizations. Organizations must prepare not only for ransomware prevention but also for potential responses to mitigate these risks.

# Identity Management

To bolster your organization's security, a deep understanding of authentication processes within your environment is paramount. This includes the centralization of administrative change visibility, which simplifies the detection of potential threats.

# User and Sign-In Risk

Vigilance is key when it comes to the scrutiny of user and sign-in risk detections, particularly for administrators. Keep an eye out for common alerts like "Impossible Travel," "Unfamiliar Sign-in Properties," and "Anomalous Token."

# Conditional Access Policies

To fortify your security measures, it's crucial to review the coverage and effectiveness of Conditional Access policies. Pay special attention to the utilization of trusted locations and exclusions to ensure that your security measures are optimally configured.

# Custom Domains

A secure identity infrastructure is built upon understanding all existing and new custom domains in the tenant, along with their federation settings. This examination is critical to maintaining your organization's security.

# Administrator Groups and Roles

Regular scrutiny of administrator groups, roles, and privileges is essential, particularly for any recent modifications. Unauthorized changes in this area can introduce significant security risks.

# Microsoft Entra ID Users

To safeguard your environment, keep a vigilant eye on recently created Microsoft Entra ID users and registered device identities. It's important to verify their legitimacy and ensure they are not associated with potential threats.

# App Access

Monitoring for unusual access to organizational applications, especially those housing sensitive data like Microsoft SharePoint and OneDrive, is a proactive measure to prevent data breaches. Detecting anomalous access is a key part of maintaining robust cybersecurity.
