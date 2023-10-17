+++
title = "User Guide for Graphical Representation"
date = 2023-10-16T08:00:00-07:00
draft = false
tags = ["Graphical Representation", "Active Directory", "Trouble Ticket", "Work Roles", "Relationship Mapping"]
+++

# [User Guide for Graphical Representation](https://github.com/green-dino/ISO_Change_Control_Process/blob/main/Ticketing%20System/ticket%20flow%20mapping.md)

This user guide provides an overview of a graphical representation created using the Mermaid library. The diagram visualizes the relationships and connections between various elements within a system, including an Active Directory structure, a Trouble Ticket Mapping System, Primary Work Role ID Mapping, and Relationship Mapping.

## Active Directory

The "Active Directory" is represented as a subgraph and contains a hierarchy of elements within it:

- **Root (A)** is the top-level element.
- **Users (B)** are connected to the Root.
- Under Users, you have various sub-elements, including:
  - SEC-ARCH (C)
  - SYS-ARCH (D)
  - SOFT-DEV (E)
  - DATA-ARCH (F)
  - ENT-ARCH (G)
  - TECH-ARCH (H)
  - CYBER-ANALYST (I)
  - CYBER-INFRA (J)
  - DATA-ANALYST (K)
  - SYS-DEV (L)
  - NET-ENG (M)
  - SYS-ADMIN (N)
  - SEC-ASSESSOR (O)
  - SEC-CONT-ASSESSOR (P)

These elements represent different roles or categories within the Active Directory subgraph. The arrows indicate the hierarchy and relationships between these elements.

## Trouble Ticket Mapping System

The "Trouble Ticket Mapping System" is another subgraph and represents a system for handling trouble tickets:

- **User (Q)** is connected to "Creates" a Trouble Ticket (R).
- Trouble Tickets (R) are "Assigned To" (S) someone.
- The "Assigned To" (S) can "Update" the Trouble Ticket (R).
- The Trouble Ticket (R) can be "Resolved" (T).

These elements represent the flow of operations in a trouble ticket system, where users create tickets, they are assigned to individuals, updated, and eventually resolved.

## Primary Work Role ID Mapping

The "Primary Work Role ID Mapping" subgraph represents the mapping of work roles:

- **Root (A)** is connected to various work roles (D, C, E, F, G) using "has" relationships.
- The work roles (D, C, E, F, G) are also "associated with" the Root (A).

This subgraph illustrates the relationships between the Root and various work roles and how they are associated.

## Relationship Mapping

The "Relationship Mapping" subgraph shows relationships between different activities or tasks:

- Ticket Creation (TC) "Belongs to" Analyze (A).
- Ticket Assignment (TA) "Belongs to" Oversee and Govern (O).
- Ticket Tracking (TT) "Belongs to" Operate and Maintain (F).
- Ticket Resolution (TR) "Belongs to" Protect and Defend (K).
- Data Management (DM) "Belongs to" Securely Provision (N).
- Communication (CM) "Belongs to" Oversee and Govern (O).

These elements represent how various activities or tasks are related to different work roles or categories.

In summary, this graphical representation provides a visual overview of the relationships and connections between different elements, work roles, and activities in a system, making it easier to understand the structure and flow of the system.
