+++
title = 'Considerations about Active Directory'
date = 2023-10-21T11:00:00-07:00
draft = false
tags = ['Hardening']
+++


# Active Directory Privileged Access

## Introduction
- The challenge of understanding the access privileges of various groups in Active Directory.
- Often, the full impact of a group's access is not fully comprehended by the organization.
- Attackers frequently exploit access, even if it's not always privileged access, to compromise Active Directory.

## Components of Access Rights
1. Active Directory group membership.
2. AD groups with privileged rights on computers.
3. Delegated rights to AD objects through modifications of default permissions (for security principals, both direct and indirect).
4. Rights assigned to SIDs in SIDHistory to AD objects.
5. Delegated rights to Group Policy Objects.
6. User Rights Assignments configured on workstations, servers, and Domain Controllers via Group Policy (or Local Policy) defining elevated rights and permissions on these systems.
7. Local group membership on a computer or computers (similar to GPO assigned settings).
8. Delegated rights to shared folders.

# Understanding the "Account Operators" Group in Active Directory

In Active Directory, the "Account Operators" group is a built-in group with default privileges that play a specific role in managing user and group accounts within the domain. This document aims to explain the purpose and limitations of the "Account Operators" group to assist those configuring Active Directory.

## Role of the "Account Operators" Group

The "Account Operators" group has the following primary roles:
- **Limited Account Creation Privileges:** Members of this group are granted the ability to create and modify most types of accounts, including user accounts, local groups, and global groups within the domain.

- **Logon to Domain Controllers:** Members of the "Account Operators" group have the privilege to log in locally to domain controllers. This allows them access to these critical servers for administrative purposes.

## Limitations of the "Account Operators" Group

While the "Account Operators" group offers significant privileges, there are important limitations to be aware of:
- **Cannot Manage Administrator Account:** Members of this group do not have the authority to manage the Administrator user account or the user accounts of administrators. This ensures the security of these high-privilege accounts.

- **Cannot Modify User Rights:** The "Account Operators" group is restricted from modifying user rights, which are critical permissions and privileges assigned to users.

- **No Management of Certain Groups:** Members of this group cannot manage the following groups: Administrators, Server Operators, Account Operators, Backup Operators, or Print Operators. These restrictions are in place to prevent unintended changes to critical groups.

## Usage Best Practices

To maintain a secure and well-managed Active Directory environment, consider the following best practices regarding the "Account Operators" group:
- **Leave Membership Empty:** By default, the "Account Operators" group has no members. As a best practice, it's advisable to keep this group empty and not assign any users to it. This ensures that no unintended changes or actions are taken by group members.

- **Avoid Delegated Administration:** It is recommended not to use the "Account Operators" group for delegated administration. Instead, use specific groups and roles tailored to the tasks and responsibilities of administrators.

- **Cannot Be Renamed, Deleted, or Moved:** The "Account Operators" group cannot be renamed, deleted, or moved within Active Directory. It is a built-in group with a fixed name and purpose.

## Compatibility

The "Account Operators" group applies to specific versions of the Windows Server operating system. Its presence and privileges are part of the default security groups within Active Directory, tailored to the specific version in use.

Understanding the role and limitations of the "Account Operators" group is essential for maintaining a secure and well-managed Active Directory environment.

# Understanding the "Administrators" Group in Active Directory

The "Administrators" group is a crucial security group in Active Directory, having significance both at the local and domain controller levels. This document aims to clarify the role, privileges, and importance of the "Administrators" group for those configuring Active Directory.

## "Administrators" Group Roles

The "Administrators" group serves vital roles at both the local and domain levels:

### Local "Administrators" Group
- **Full Control of Local Computer:** Members of the local "Administrators" group have complete and unrestricted access to the computer where they are part of this group. They can perform administrative tasks and manage the computer's configuration.

### Active Directory "Administrators" Group
- **Full Admin Rights on Active Directory:** Members of the Active Directory "Administrators" group possess full administrative rights over the Active Directory domain and Domain Controllers. This grants them unparalleled control over the entire domain.

## Importance and Privileges

Members of the "Administrators" group, regardless of whether it's the local or Active Directory group, enjoy significant privileges:

- **Unrestricted Access:** Those in the "Administrators" group have unrestricted access to the computer or domain controller where they are members. This means they can make system-wide changes, install software, and configure the system as needed.

- **Control Over Domain Controllers:** The "Administrators" group has built-in capabilities that give its members full control over the domain controllers. This level of access is critical for maintaining and managing the domain effectively.

- **Special Privileges:** Members of the "Administrators" group have special privileges, including the ability to take ownership of any object in the directory or any resource on a domain controller. This facilitates various administrative tasks.

- **Service Administrator Group:** The "Administrators" group is often considered a service administrator group due to its comprehensive control over domain controllers and critical domain resources.

## Group Characteristics

To maintain the security and integrity of the "Administrators" group, consider the following characteristics:

- **Cannot Be Renamed, Deleted, or Moved:** The "Administrators" group is a built-in group and cannot be renamed, deleted, or moved within Active Directory. Its name and purpose are fixed.

- **Control Over Domain Controllers:** This built-in group plays a significant role in controlling access to all the domain controllers within its domain. It also has the authority to modify the membership of all administrative groups.

- **Membership Modification:** Membership in the "Administrators" group can be modified by specific groups, including the default service Administrators, Domain Admins in the domain, or Enterprise Admins. This ensures that only authorized personnel can manage the group's membership.

## Compatibility

The "Administrators" group's roles and privileges apply to specific versions of the Windows Server operating system, as listed in the Active Directory default security groups by operating system version.

Understanding the role and importance of the "Administrators" group is fundamental to effectively managing and securing an Active Directory environment.

# Privileged Active Directory Permissions of Interest to Attackers

When it comes to Active Directory security, attackers are most interested in permissions that provide privileged actions. These Access Control Lists (ACLs) grant substantial control and can lead to unauthorized access. Below are some of the key ACLs that are of high interest to attackers:

## Replicating Directory Changes All
- **Description:** An extended right needed to replicate changes from a specific Naming Context (NC) to the Global Catalog, which includes secret domain data. This constraint is primarily meaningful for Domain NCs.
- **Significance:** When combined with Replicating Directory Changes, it provides the ability to "DCSync" password data for Active Directory users and computers, including Domain Admins and Domain Controllers. 
- **Example:** Attackers often target service accounts with this right, granting them access to sensitive data.

## Replicating Directory Changes (DS-Replication-Get-Changes)
- **Description:** A control access right that allows the replication of all data in a given replication NC, excluding secret domain data.
- **Significance:** It enables data extraction from Active Directory regardless of configured AD ACLs.
- **Example:** Attackers can use this right to pull data from Active Directory, circumventing normal access controls.

## GenericAll
- **Description:** This right provides full control over an object, allowing the creation or deletion of children, deletion of a subtree, reading and writing properties, examining children and the object itself, adding or removing the object from the directory, and reading or writing with an extended right.
- **Significance:** It provides full rights to the object and all its properties, including confidential attributes like LAPS local Administrator passwords and BitLocker recovery keys.
- **Example:** Organizations may delegate Full Control to specific groups for easier management but may inadvertently grant excessive privileges.

## GenericWrite
- **Description:** Provides write access to all properties.
- **Significance:** It allows reading permissions on an object, writing all properties on the object, and performing all validated writes to the object.
- **Example:** Attackers with GenericWrite can modify object properties and potentially exploit security vulnerabilities.

## WriteDACL
- **Description:** Provides the ability to modify the security on an object, which can lead to Full Control of the object.
- **Significance:** This right allows attackers to manipulate object permissions, potentially leading to full control of the object.
- **Example:** If an attacker gains access to a service account with WriteDACL, they can set their permissions on associated objects, potentially exposing sensitive data like LAPS-controlled local Administrator passwords.

## Self
- **Description:** Provides the ability to perform validated writes.
- **Significance:** It grants rights to perform operations controlled by validated write access rights, including specific attributes.
- **Example:** Self rights may be assigned for various operations, and attackers may target these to manipulate or misuse these privileges.

Understanding and securing these privileged Active Directory permissions is critical for protecting your environment from potential attacks. Effective access control and monitoring are essential for mitigating security risks.

# Active Directory Permissions for Ownership and Object Control

Active Directory permissions play a crucial role in managing and securing objects within the directory. Some permissions grant users specific abilities related to object ownership, modification, creation, and deletion. This document aims to clarify the significance of these permissions and their practical implications:

## WriteOwner
- **Description:** This permission provides the ability to take ownership of an object. When a user assumes ownership, they gain full control rights over the object.
- **Significance:** The owner of an object has the authority to make changes to it, including modifying permissions and attributes.
- **Example:** Assume ownership over a user account allows for extensive control over the account, including changing the password, group membership, and more.

## WriteProperty
- **Description:** The WriteProperty permission is often paired with specific attribute or property information. It allows users to modify specific attributes of an object.
- **Significance:** This permission grants control over specific attributes, which can be useful for delegated administration or limited attribute modifications.
- **Example:** The help desk group may be delegated the ability to modify specific AD object properties such as the Member attribute to manage group memberships, Display Name, Description, Phone Number, etc.

## CreateChild
- **Description:** CreateChild permission provides the ability to create objects of a specified type, or in some cases, any type within the directory.
- **Significance:** Users with this permission can create new objects, which is often critical for administrative tasks and managing the directory's structure.
- **Example:** Help desk staff with CreateChild permission can create new user accounts, groups, or other objects as needed.

## DeleteChild
- **Description:** DeleteChild permission allows users to delete objects of a specified type or any object, depending on the permission configuration.
- **Significance:** Users with this permission can remove objects from the directory, which is essential for cleaning up and maintaining the directory's structure.
- **Example:** System administrators with DeleteChild permission can remove obsolete user accounts or groups.

## Extended Right
- **Description:** Extended Right permissions offer additional rights beyond the standard permissions and can vary depending on the object.
- **Significance:** These permissions grant specific, advanced abilities that are not covered by standard permissions, potentially providing access to otherwise restricted attributes or actions.
- **Example:** All Extended Right permissions for a computer object may allow read access to attributes like the LAPS Local Administrator password, which isn't typically accessible.

Understanding these permissions and their implications is vital for properly configuring and securing your Active Directory environment. Effective management of these permissions ensures that users and groups have the necessary control over objects while maintaining security and integrity.

# Identifying Privileged Access in Active Directory

Effectively identifying accounts with privileged access in Active Directory is a critical aspect of maintaining a secure environment. This process involves exploring permissions on various AD objects, starting with Organizational Units (OUs), and then branching out to security groups. Here are some essential steps to follow:

## Enumeration of Group Membership
- Enumerate the group membership of default groups, including sub-groups. 
- Identify the specific rights required for each group and remove any unnecessary rights.
- This step helps in ensuring that access is granted only as needed, minimizing potential security risks.

## Scanning for Custom Delegation
- Scan Active Directory, focusing on OUs and security groups, to identify custom delegations.
- Custom delegations can grant non-standard access rights, and it's essential to identify and review these for potential risks.
- Ensure that custom delegations are necessary and configured appropriately for security.

## SIDHistory Review
- Check for accounts with SIDHistory. Typically, this is required during an active migration from one domain to another.
- Review the presence of SIDHistory to ensure it's only in use when necessary for migration purposes.

## User Rights Assignments in GPOs
- Review User Rights Assignments within Group Policy Objects (GPOs) that apply to Domain Controllers, Servers, and Workstations.
- Ensure that user rights are configured correctly, and no unnecessary privileges are granted.

## Review of GPOs Adding AD Groups to Local Groups
- Review GPOs that add Active Directory groups to local groups on machines.
- Confirm that these additions are still required and that the level of rights granted is appropriate.
- Eliminate any unnecessary group memberships to reduce the potential attack surface.

By following these steps, defenders can effectively identify accounts with privileged access in Active Directory. This proactive approach to access management contributes to a more secure and well-maintained Active Directory environment, reducing the risk of unauthorized access and potential security vulnerabilities.



# References

1. [BloodHound 1.3 – The ACL Attack Path Update](https://wald0.com/?p=112)

2. [Abusing Active Directory Permissions with PowerView](http://www.harmj0y.net/blog/redteaming/abusing-active-directory-permissions-with-powerview/)

3. [Abusing GPO Permissions](http://www.harmj0y.net/blog/redteaming/abusing-gpo-permissions/)

4. [AD DS Owner Rights](https://technet.microsoft.com/en-us/library/dd125370(v=ws.10).aspx)

5. [Security Descriptor Definition Language for Conditional ACEs](https://msdn.microsoft.com/en-us/library/windows/desktop/dd981030(v=vs.85).aspx)

6. [Sneaky Active Directory Persistence #15: Leverage AdminSDHolder & SDProp to (Re)Gain Domain Admin Rights](https://adsecurity.org/?p=1906)

7. [The Security Descriptor Definition Language of Love (Part 1)](https://blogs.technet.microsoft.com/askds/2008/04/18/the-security-descriptor-definition-language-of-love-part-1/)

8. [ActiveDirectoryRights Enumeration](https://msdn.microsoft.com/en-us/library/system.directoryservices.activedirectoryrights(v=vs.110).aspx)

9. [Active Directory Permissions](http://www.selfadsi.org/deep-inside/ad-security-descriptors.htm)

