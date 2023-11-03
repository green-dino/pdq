+++
categories = ['Security']
date = '2023-11-03'
description = 'Exploring Attack Patterns: Exploiting Software Weaknesses Beyond Expectations'
slug = 'exploring-attack-patterns-exploiting-software-weaknesses'
tags = ['Security', 'Software Weaknesses', 'Attack Patterns', 'CWE', 'Vulnerabilities']
title = 'Exploring Attack Patterns: Exploiting Software Weaknesses Beyond Expectations'
draft = false
+++


# Exploring Attack Patterns: Exploiting Software Weaknesses Beyond Expectations

Quality Assurance efforts usually focus on testing that the feature works as expected. In the security world, we examine the software functions in ways never imagined to give us more access to resources and data.


## Key Questions for Understanding the Technology

To understand a technology or system, consider the following key questions:

1. **How does the technology work?**
2. **What are the data inputs?**
3. **What are the data outputs?**
4. **When does the analysis occur?**
5. **What are the analytical algorithms?**
6. **How does it operate at scale?**
7. **How can it be circumvented?**
8. **How do humans interact with the technology?**
9. **What are the user's responsibilities?**
10. **How does this interaction scale?**

## Introduction

Malicious actors care deeply about their work and they do not want to be disrupted while doing it, hence why they spend time working on supply side attacks and doing what they do best avoiding detection. This article will help you counter their efforts and make their jobs more difficult. 


Think about something concrete, a house, car, building. Now think about how a malicious actor might try to get in to that. A house has windows, vents, doors while a car has doors and windows. 

Think about the systems in a house, HVAC, Power, Appliances and a car has similar systems but slightly different a motor or engine, transmission, drive-train and entertainment features. 

Now think about the abstract, a computer here, there, locally or remote has ports, protocols and procedures. These ports, protocols and procedures offer services that we have learned to rely on in our lives.

Lets extend that thinking pattern you just explored to some new concepts. **Attack Surface Analysis**

### Attack Surface Analysis helps you to:

Identify what functions and what parts of the system you need to review/test for security vulnerabilities

Identify high risk areas of code that require defense-in-depth protection - what parts of the system that you need to defend

Identify when you have changed the attack surface and need to do some kind of threat assessment


# The need for testing beyond expected behavior

The Attack Surface of an application comprises four key components:

1. **Paths for Data/Commands:**
   - The sum of all entry and exit points for data and commands in the application.
   - Includes resource connection, authentication, authorization, activity logging, data validation, and encoding.

2. **Protection Code for Paths:**
   - The code responsible for safeguarding the paths mentioned above.
   - Encompasses measures like resource connection security, access control, and data validation.

3. **Valuable Data:**
   - All valuable data utilized in the application, such as secrets, keys, intellectual property, critical business data, personal data, and PII (Personally Identifiable Information).

4. **Protection Code for Data:**
   - The code responsible for protecting the valuable data.
   - Includes encryption, checksums, access auditing, data integrity, and operational security controls.



## Organizing Attack Patterns by Mechanisms

Here we review attack patterns hierarchically based on common techniques used when exploiting vulnerabilities. These categories represent the various methods employed to attack a system. It's important to note that they don't reflect the consequences or objectives of the attacks.

**Overlap Potential:**
Some attack patterns may align with more than one category depending on one's perspective. To mitigate this, each attack pattern within a category is presented with a technique that is consistently applicable, without exceptions.

###  Types of attack patterns 

1. **Engage in Deceptive Interactions**
2. **Abuse Existing Functionality**
3. **Manipulate Data Structures**
4. **Manipulate System Resources**
5. **Inject Unexpected Items**
6. **Employ Probabilistic Techniques**
7. **Manipulate Timing and State**
8. **Collect and Analyze Information**
9. **Subvert Access Control**


To enhance security, you can overlay this model with various types of users, including their roles and privilege levels when accessing the system. The complexity of your analysis increases with the number of different user types, but it's crucial to focus primarily on two extremes: unauthenticated, anonymous users, and highly privileged admin users (e.g., database administrators and system administrators).

Here's a structured approach to this analysis:

1. **User Types and Attack Points:**
   - Group each type of user based on their roles, privilege levels, and the points within the system they can access, whether authorized or not.
   - Differentiate between unauthenticated, anonymous users and highly privileged admin users.

2. **Attack Point Categories:**
   - Categorize attack points into buckets based on factors such as:
     - Risk (external-facing or internal-facing)
     - Purpose of the attack
     - Implementation details
     - Design considerations
     - Technology used

3. **Count and Prioritize:**
   - Count the number of attack points in each category.
   - Select representative cases for each attack point category.

4. **Focused Review/Assessment:**
   - Concentrate your security review or assessment on these selected representative cases.

- The goal of identifying and understanding attack patterns

## Identifying and Mapping the Attack Surface

When identifying and mapping the Attack Surface, consider the following steps:

1. **Building a Baseline Description:**
   - Create a comprehensive picture and take notes about the Attack Surface.
   - Spend a few hours reviewing design and architecture documents from an attacker's perspective.

2. **Identifying Points of Entry/Exit:**
   - Review the source code to identify various points of entry and exit.
   - These can include:
     - User interface (UI) forms and fields
     - HTTP headers and cookies
     - APIs
     - Files
     - Databases
     - Other local storage
     - Email or other messaging systems
     - Runtime arguments
     - And any other specific entry/exit points relevant to your system.

3. **Managing Numerous Attack Points:**
   - Recognize that the total number of different attack points can be significant, potentially reaching into the thousands.
   - To make this manageable, categorize them into different types based on function, design, and technology.
   
4. **Categorized Attack Points:**
   - Organize your attack points into types that reflect their respective functions, design aspects, and technology.
   - Consider categories such as:
     - Login/authentication entry points
     - Admin interfaces
     - Inquiries and search functions
     - Data entry (CRUD) forms
     - Business workflows
     - Transactional interfaces/APIs
     - Operational command and monitoring interfaces/APIs
     - Interfaces with other applications/systems
     - And any other relevant types specific to your system.


## Identifying Weaknesses in Software
Common software vulnerabilities (e.g., SQL injection, XSS, buffer overflows)
Use the [CWE](https://cwe.mitre.org) to find common weaknesses 
This can identify interesting trends in real-world, exploitable weaknesses that can inform security policy and investment decision-making. To observe both upward and downward trends in CWE ranks. 

## Benefits of CWEs (Common Weakness Enumerations)

CWEs offer several valuable benefits:

1. **Demonstrative Examples:**
   - CWEs provide demonstrative examples, often including sample attack payloads that serve as a starting point for crafting our own exploits.

2. **Links to Observed Examples:**
   - They also link to observed examples, which are instances found in real production software. These are typically connected to CVEs (Common Vulnerabilities and Exposures).

3. **Links to Attack Patterns:**
   - One of the most valuable aspects is that CWEs link to related attack patterns. These attack patterns are part of a knowledge base called [CAPEC](https://capec.mitre.org) (Common Attack Pattern Enumeration and Classification). CAPEC helps identify and understand common attack patterns used by malicious actors.


Three specific weaknesses in software security have shown a consistent upward trend in ranking, and software developers and maintainers should prioritize addressing them:

1. **CWE-862: Missing Authorization**
   - In 2019, it was ranked 36th.
   - Entered the CWE Top 25 in 2020, ranked 25th, and has consistently moved up.
   - In 2023, it's ranked 11th, indicating a need for more diligent implementation of authorization techniques.

2. **CWE-918: Server-Side Request Forgery (SSRF)**
   - In 2019, it was ranked 32nd.
   - Entered the CWE Top 25 in 2021, ranked 24th, and has steadily climbed.
   - In 2023, it's ranked 19th, showing a consistent upward trend.

3. **CWE-639: Authorization Bypass Through User-Controlled Key**
   - In 2019, it was ranked outside the top 40.
   - Steadily climbed in rank over the years, reaching 38th in 2023.
   - This upward trend is worth monitoring for further movement and improvements in security.

These weaknesses highlight areas where security measures should be prioritized, and developers should pay attention to implementing safeguards against them.

## Thinking Like an Attacker
Attackers are thinking about how to avoid detection, heres a common approach to how an attacker conducts footprinting and builds resources to complete their work. 

### Fingerprinting of the Operating System
- **Objective:** To determine the underlying OS for proper path traversal.
- **Techniques:**
  - Port Mapping: Identifying listening ports and protocol types.
  - TCP/IP Fingerprinting: Observing OS-specific responses.
  - Inducing Errors: Generating errors for informative messages.
  - Surveying the Application: Identifying user input areas for specifying file names or paths.

| Technique              | Description                                     |
|------------------------|-------------------------------------------------|
| Port Mapping           | Identify listening ports and protocol types.   |
| TCP/IP Fingerprinting  | Observe OS-specific responses for OS guessing. |
| Inducing Errors        | Generate errors to find informative messages.  |
| Surveying the App      | Identify user input areas for file paths.       |

### Experimentation with Input Parameters
- **Objective:** Observe system responses to variations in input parameters.

| Technique             | Description                                           |
|-----------------------|-------------------------------------------------------|
| Access Common Files   | Access common files in root directories.              |
| Access Drive Letters  | Access specific drive or volume letters.             |
| Access UNC Shares     | Access known Windows UNC shares.                     |

### Exploiting Vulnerabilities
- **Objective:** Inject path traversal syntax to access, modify, or execute arbitrary files.

| Technique              | Description                                           |
|------------------------|-------------------------------------------------------|
| Manipulate File Paths  | Manipulate file paths through absolute sequences.    |
| Download/Modify/Execute| Download, modify, or attempt to execute files.       |


## Conclusion
When it comes to security testing, even if you've thoroughly covered all the basics like examining Common Weakness Enumerations (CWEs) related to Broken Access Control and tracking down common attack patterns, you can't claim absolute freedom from vulnerabilities. You can't guarantee the software's security with certainty.

And that's perfectly fine.

There might still be business logic bugs that slipped through the cracks. There could be untested input patterns or unknown tainted payloads that could potentially exploit weaknesses. As you gain more experience, your testing methodology will improve, and you'll likely discover and address these issues over time.

The process doesn't end there, though. You'll need to apply the same scrutiny to the other nine items in the Top 10 list. By doing so, you'll establish a solid foundation for protecting against common risks and using real-world attack patterns. It's an ongoing journey towards a more secure software environment.


[Drop me a line](mailto:john@grcand.me) 

