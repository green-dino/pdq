---
categories: ['Microsoft 365', 'Security', 'Admin Center', 'Microsoft Purview', 'Microsoft Intune', 'Microsoft Fabric']
date: '2023-11-03'
description: 'Best Practices for Administering Microsoft 365 and Related Services'
slug: 'best-practices-microsoft-365-administration'
tags: ['Microsoft 365', 'Security Best Practices', 'Admin Center', 'Microsoft Purview', 'Microsoft Intune', 'Microsoft Fabric', 'Data Loss Protection', 'Information Protection', 'Audit Log']
title: 'Best Practices for Administering Microsoft 365 and Related Services'
---

**There is no warranty of this information. Make changes after consulting with your organizations leadership and change management process. Changes you make here will impact your organizations security posture**

1. **Microsoft 365 admin center**
   - **Step 1 - Ensure a policy and procedure is in place at the organization:**
     - In order for accounts to be effectively used in a break-glass situation, the proper policies and procedures must be authorized and distributed by senior management.
     - FIDO2 Security Keys, if used, should be locked in a secure separate fireproof location.
     - Passwords should be at least 16 characters, randomly generated and MAY be separated in multiple pieces to be joined in an emergency.

   - **Step 2 - Ensure two emergency access accounts are defined:**
     - Navigate to [Microsoft 365 admin center](https://admin.microsoft.com).
     - Expand Users > Active Users.
     - Inspect the designated emergency access accounts and ensure the following:
       - The accounts are named correctly and do NOT identify with a particular person.
       - The accounts use the default .onmicrosoft.com domain and not the organization's.
       - The accounts are cloud-only.
       - The accounts are unlicensed.
       - The accounts are assigned the Global Administrator directory role.

   - **Step 3 - Ensure at least one account is excluded from all conditional access rules:**
     - Navigate [Microsoft Entra admin center](https://entra.microsoft.com/).
     - Expand Azure Active Directory > Protect & Secure > Conditional Access.
     - Inspect the conditional access rules.
     - Ensure one of the emergency access accounts is excluded from all rules.

   - **Ensure Administrative accounts are separate and cloud-only:**
     - **Ensure administrative accounts are licensed without attached applications and cloud-only.**
     - Ensure Administrative accounts are separate and cloud-only:
       - Navigate to [Microsoft 365 admin center](https://admin.microsoft.com).
       - Click to expand Users and select Active users.
       - Sort by the Licenses column.
       - For each user account in an administrative role, verify the following:
         - The account is Cloud only (not synced).
         - The account is assigned a license that is not associated with applications (e.g., Microsoft Entra ID P1, Microsoft Entra ID P2).

2. **Microsoft 365 Defender**
    -  Email
        - Ensure Safe Links for Office Applications is Enabled
        - Ensure the Common Attachment Types Filter is enabled
        - Ensure notifications for internal users sending malware is Enabled
        - Ensure Safe Attachments policy is enabled
        - Ensure Safe Attachments for SharePoint, OneDrive, and Microsoft Teams is Enabled
        - Ensure Exchange Online Spam Policies are set to notify administrators
        - Ensure that an anti-phishing policy has been created
        - Ensure that SPF records are published for all Exchange Domains
        - Ensure that DKIM is enabled for all Exchange Online Domains
        - Ensure DMARC Records for all Exchange Online domains are published
        - Ensure the spoofed domains report is reviewed weekly
        - Ensure the 'Restricted entities' report is reviewed weekly
        - Ensure all security threats in the Threat protection status report are reviewed at least weekly

3. [**Microsoft Purview**](https://compliance.microsoft.com/)
    - Audit
        - Ensure Microsoft 365 audit log search is Enabled
        - Ensure user role group changes are reviewed at least weekly

    - Data Loss Protection
        - Ensure DLP policies are enabled
        - Ensure DLP policies are enabled for Microsoft Teams
    - Information Protection
        -Ensure SharePoint Online Information Protection policies are set up and used

4. [**Microsoft Entra admin center**](https://entra.microsoft.com/)
    - Identity
    # Users
        - Ensure Security Defaults is disabled on Azure Active Directory
        The use of security defaults, however, will prohibit custom settings which are being set with more advanced settings
        - Ensure 'Per-user MFA' is disabled
        - Ensure third party integrated applications are not allowed
        - Ensure 'Restrict non-admin users from creating tenants' is set to 'Yes'
        - Ensure 'Restrict access to the Azure AD administration portal' is set to 'Yes'
        - Ensure the option to remain signed in is hidden
        - Ensure 'LinkedIn account connections' is disabled
    # Groups
        - Ensure a dynamic group for guest users is created
    # Applications
        - Ensure the Application Usage report is reviewed at least weekly
        - Ensure user consent to apps accessing company data on their behalf is not 
       allowed
        - Ensure the admin consent workflow is enabled 



References;
https://learn.microsoft.com/en-us/microsoft-365/compliance/audit-log-enable-disable?view=o365-worldwide
https://learn.microsoft.com/en-us/powershell/module/exchange/set-adminauditlogconfig?view=exchange-ps
https://learn.microsoft.com/en-us/microsoft-365/compliance/data-classification-overview?view=o365-worldwide#top-sensitivity-labels-applied-to-content
https://learn.microsoft.com/en-us/azure/active-directory/enterprise-users/groups-create-rule

https://learn.microsoft.com/en-us/azure/active-directory/enterprise-users/groups-dynamic-membership

https://learn.microsoft.com/en-us/azure/active-directory/external-identities/use-dynamic-groups

https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/configure-admin-consent-workflow

