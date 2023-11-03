+++
title = 'Living Off The land'
date = 2023-11-02T11:00:00-07:00
draft = false
tags = ['lotl']
+++

# Threat Assessment and PowerShell

## Introduction

In a structured approach to threat assessments, defenders turn to multiple reliable sources to provide prioritized best practices for defending against the top five most common attacks observed across the community. Additionally, they focus on threats posed by Cyber Threat Actors (CTAs) who utilize Living off the Land (LotL) attacks.

## PowerShell and Its Benefits

- **Automation:** Administrators can automate tasks using PowerShell cmdlets, reducing the need for manual configurations, especially for tedious tasks.

- **Shortcuts:** PowerShell allows administrators to work around software constraints. For example, IT administrators can push out configuration settings, like password policies, to all systems across a network.

- **Scalability:** IT administrators can efficiently collect information from enterprise assets, even in larger enterprises, through automation. PowerShell remoting enables scripts designed for scale, reaching a large group of systems for tasks like installing updates and configuration settings.

- **Visibility:** PowerShell provides visibility into various system files and data through the command-line, making it easier for data collection and analysis.

## Cyber Threat Actors (CTAs) and PowerShell

CTAs leverage PowerShell for several reasons:

- **Evading Defenses:** PowerShell is a native Windows tool functional on other platforms like Linux and macOS. CTAs use it without raising red flags, as it is also used by IT professionals. They can even employ PowerShell to disable critical threat detection tools like anti-malware applications.

- **Automation:** CTAs use the Windows Application Programming Interface (API) to automate tasks and evade detection.

- **Access to Modules:** CTAs can access widely available PowerShell modules on open source platforms, allowing them to modify PowerShell for malicious purposes.

- **Malware Development:** CTAs can write malware in PowerShell. Examples include Netwalker, RogueRobin, PowerWare, and POWELIK.

- **Post-Exploitation:** CTAs use post-exploitation frameworks (e.g., CobaltStrike, PowerSploit, PowerShell Empire, Mimikatz), which leverage PowerShell components, to compromise a network and steal credentials.

- **Social Engineering:** CTAs can use social engineering to send a macro-enabled document, subsequently launching PowerShell.

- **Payload Encoding:** CTAs can encode payloads using the command-line and load PowerShell into other processes.

- **Script Bypass:** CTAs can use scripts, such as WScript and CScript, to bypass script-based constraints on operating systems.

- **Attack Surface Expansion:** CTAs can increase their attack surface by using other applications, such as the WMI command-line, to run scripts.



# Securing PowerShell Best Practices

## General Recommendations

1. **Establish Baseline Activity**: Begin by setting up a baseline of PowerShell activity. This is crucial, especially for monitoring devices, to differentiate normal from abnormal behavior.

2. **Disable Unnecessary Components**: Disable any PowerShell components that are not required. If there's no business need, remove access to them.

3. **Limit Execution Location**: Consider applications that can restrict PowerShell scripts to run only from specific locations or paths. This reduces the attack surface.

4. **Restrict Activities**: Configure PowerShell to block activities commonly used by Cyber Threat Actors (CTAs), such as executing commands on remote systems or downloading content from the internet.

5. **Configuration Flexibility**: Depending on the application and enterprise needs, establish configurations at different levels (user-level, application-level, command-level, etc.) to implement these controls.

6. **Script Signing**: Implement script signing as a best practice. Ensure scripts are signed by trusted publishers for added security.

7. **Protecting Sensitive Information**: Refrain from storing sensitive information, like credentials, in PowerShell scripts. If credentials are necessary, deploy controls to protect them effectively.

## Windows-Specific Configurations

8. **Group Policy Setting**: Utilize the 'Turn on Script Execution' Group Policy setting in Windows to control script execution on systems.

9. **PowerShell Execution Policies**: Understand the seven PowerShell execution policies, such as AllSigned, Bypass, Default, RemoteSigned, Restricted, Undefined, and Unrestricted.

10. **Execution Policy on Windows Servers**: Change the default policy on Windows servers from RemoteSigned to AllSigned, requiring all scripts to be signed by trusted publishers.

11. **Execution Policy on Windows Clients**: Note that Restricted is the default policy on Windows clients, preventing the execution of scripts. Users can still run commands.

12. **Execution Policy Configuration**: Recognize that the Execution Policy configuration reduces the risk of unintentional violations but may not prevent direct script execution via the command-line.

13. **Forensic Investigation**: In the event of policy bypass, review the Windows Registry Key, 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell\ Value: ExecutionPolicy,' to identify the last modified timestamp for forensic purposes.

14. **Last Write Time Analysis**: Export the Registry Key to a text file to display the Last Write Time.

These best practices aim to enhance the security of PowerShell usage while providing flexibility to adapt to enterprise requirements and configurations.


# PowerShell Customization and Automation

## PowerShell Profiles

1. **Profile Customization**: Administrators can use PowerShell profiles to customize and automate activities when PowerShell starts. Profiles can be tailored to specific events or applications.

2. **Security Concerns**: PowerShell profiles can be manipulated by malicious actors for malicious actions, including establishing persistence mechanisms. Secure profiles by preventing changes and limiting modifications to a restricted group of administrators.

3. **Execution Policy Control**: Profiles can be controlled within the PowerShell Execution Policy, where scripts and configuration files (including profiles) can be prevented from running under the Restricted setting.

4. **Policy Considerations**: Carefully set policies to balance PowerShell access based on business needs.

## Script Review and Approval

5. **Configuration Manager**: Utilize Configuration Manager, now part of Microsoft Endpoint Manager, to review and approve scripts. It enforces separation of duties by separating script authors from approvers.

6. **Script Review Tools**: Implement script-checking tools like PSScriptAnalyzer to perform script reviews and detect potentially malicious behavior.

## PowerShell Parameters

7. **Secure Usage**: Secure PowerShell parameters by allowing only pre-defined parameters and using regular expressions to define permitted characters upfront.

8. **Injection Detection**: Employ PowerShell module InjectionHunter to detect malicious code that could lead to injection attacks.

9. **Syntax Checking**: Use tools in Microsoft Visual Studio to check PowerShell syntax.

## PowerShell Language Modes

10. **ConstrainedLanguage Mode**: Enable ConstrainedLanguage Mode to restrict data types in PowerShell, limiting access to .COM objects and system APIs.

11. **Enhanced Security**: Use ConstrainedLanguage Mode in conjunction with application control solutions like Device Guard or AppLocker for stronger defense. This makes it more resistant to PowerShell attacks but may impact daily operations.

## PowerShell Remoting (WinRM)

12. **PowerShell Remoting**: PowerShell can be used remotely through PowerShell remoting and the Windows Remote Management (WinRM) protocol.

13. **Access Restriction**: Restrict or disable access to WinRM if not needed to enhance security.

These action items are essential for securing PowerShell and ensuring its responsible usage while minimizing potential risks.


# PowerShell Logging and Event Log Configuration

## PowerShell Script Block Logging and Protected Event Logging

### Recommended:
1. **Enable Script Block Logging**: Implement Script Block logging to record PowerShell activities, including script execution.

2. **Enable Protected Event Logging**: Consider enabling Protected event logging to encrypt local logs, preventing the exposure of sensitive information, like credentials within scripts.

3. **Secure Log Storage**: Store encrypted logs in a secure environment, such as a Security Information and Event Management (SIEM) system or centralized logging platform for later decryption.

### Important Note:
- Protected event logging requires Script Block logging to be enabled. These two configurations work together to enhance PowerShell log security.

## Module Logging Configuration

### Recommended:
4. **Configure Module Logging**: Use Group Policy Objects (GPOs) to configure Module logging for specific modules (e.g., Microsoft.PowerShell.*, Microsoft.WSMan.Management) or capture all modules using the wildcard symbol (*).

5. **Monitor Custom Modules**: Utilize wildcard symbol (*) during monitoring and incident response to detect any custom modules used by potential threat actors.

## PowerShell-Related Log Review

### Recommended:
6. **Review PowerShell-Related Logs**: After enabling PowerShell logging, regularly review the following logs for PowerShell events:
   - Windows PowerShell.evtx
   - Microsoft-Windows-PowerShell/Operational.evtx
   - Microsoft-Windows-PowerShell/Analytic.etl (disabled by default)
   - Microsoft-Windows-WinRM/Operational.evtx
   - Microsoft-Windows-WinRM/Analytic.etl (disabled by default)
   - PowerShellCore/Operational
   - PowerShellCore/Analytical

## Command-Line Audit Logging

### Optional:
7. **Enable Command-Line Audit Logs**: Optionally, consider enabling command-line audit logs to capture command-line arguments used in security events.

### Configuration Details:
8. **Configure GPO for Process Creation**: Set the 'Include command line in process creation events' GPO to enabled to determine what information is logged in security audit events for new process creation.

9. **Set Audit Process Creation Options**: Configure the 'Audit Process Creation' setting to enable Success and/or Failure events based on your organization's requirements.

## Log Tuning and Centralization

### Recommended:
10. **Tune Log Volume**: Properly configure log settings to balance capturing critical details without generating excessive events that could lead to log alert fatigue or reduced storage capacity.

11. **Centralize Logs**: If possible, store logs in a centralized location off the local system to enhance security and prevent local user access to event logs.

12. **Deny Local User Access**: As an alternative mitigation, deny local user access to event logs if log centralization is not feasible.


# References
CERT-EU: PowerShell—Cybersecurity
Perspective
 https://media.cert.europa.eu/static/WhitePapers/CERT-EU-SWP2019-001.pdf
CIS Benchmarks https://www.cisecurity.org/cis-benchmarks/
CIS Community Defense Model 2.0 https://www.cisecurity.org/white-papers/cis-community-defense-model-2-0/
CIS Controls https://www.cisecurity.org/controls/
CIS Controls v7.1 Exploited Protocols:
Remote Desktop Protocol (RDP)
 https://www.cisecurity.org/white-papers/exploited-protocols-remote-desktop-protocol-rdp/
CIS Controls v8 Exploited Protocols:
Server Message Block (SMB)
 https://www.cisecurity.org/white-papers/cis-controls-v8-exploited-protocols-server-message-block-smb/
CIS Controls v8 Commonly Exploited
Protocols: Windows Management
Instrumentation (WMI)
 https://www.cisecurity.org/insights/white-papers/cis-controls-commonly-exploited-protocols-windows-
management-instrumentation
Globe News Wire https://www.globenewswire.com/news-release/2016/04/12/828009/26208/en/Carbon-Black-United-Threat-
Research-Report-Reveals-How-Cyber-Attackers-Exploit-Microsoft-PowerShell-to-Launch-Attacks.html
PowerShell on GitHub https://github.com/PowerShell/PowerShell
Microsoft PowerShell Documentation https://docs.microsoft.com/en-us/powershell/
Microsoft PowerShell Team https://devblogs.microsoft.com/powershell/
Microsoft Antimalware Scan
Interface (AMSI)
 https://docs.microsoft.com/en-us/windows/win32/amsi/antimalware-scan-interface-portal
MITRE ATT&CK® Framework v8.2 https://attack.mitre.org/versions/v8/matrices/enterprise/
