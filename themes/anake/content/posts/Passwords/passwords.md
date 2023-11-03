+++
categories = ['Development', 'Passwords']
date = '2023-11-03'
description = 'Considerations for sensible Passwords.'
slug = 'Considerations about Passwords'
tags = ['Passwords', 'Development',]
title = 'Sensible Approaches to Passwords'
draft = false
+++

# Authentication and Password Strength Guidelines

## Authentication Solution and Sensitive Accounts

- **Do NOT** allow login with sensitive accounts (used internally within the solution) to any front-end user-interface.
- **Do NOT** use the same authentication solution (e.g., IDP / AD) for unsecured access (e.g., public access / DMZ) as used internally.

## Proper Password Strength Controls

A critical aspect of authentication is password strength. A strong password policy is essential to protect against unauthorized access. The following characteristics define a strong password:

- **Password Length**: Enforce a minimum length for passwords. Passwords shorter than 8 characters are considered weak (NIST SP800-63B).
- Set a reasonable maximum password length to avoid vulnerabilities while allowing passphrases.
- **Do not silently truncate passwords**; refer to the Password Storage Cheat Sheet for guidance on handling longer passwords.
- Allow usage of all characters, including unicode and whitespace; avoid limiting character types.
- Ensure credential rotation in the event of a password leak or compromise identification.
- Implement a **password strength meter** to assist users in creating complex passwords and blocking common or breached passwords.
- Utilize libraries like [**zxcvbn-ts**](https://github.com/zxcvbn-ts/zxcvbn) for password strength assessment.
- Consider checking passwords against **Pwned Passwords**, a service that identifies previously breached passwords. You can host it yourself or use the API.

These guidelines aim to enhance authentication security and establish robust password strength controls.
[pwnd](https://haveibeenpwned.com/Passwords)

[Long Password DOS](https://www.acunetix.com/vulnerabilities/web/long-password-denial-of-service/)


# Authentication and Error Messages

Incorrectly implemented error messages in the case of authentication functionality can be used for the purposes of user ID and password enumeration. An application should respond (both HTTP and HTML) in a generic manner.

# Authentication Responses

Using any of the authentication mechanisms (login, password reset or password recovery), an application must respond with a generic error message regardless of whether:

The user ID or password was incorrect.
The account does not exist.
The account is locked or disabled.

INCORRECT AND CORRECT RESPONSE EXAMPLES

# Login

## Incorrect response examples:

"Login for User foo: invalid password."
"Login failed, invalid user ID."
"Login failed; account disabled."
"Login failed; this user is not active."

## Correct response example:

"Login failed; Invalid user ID or password."
Password recovery¶

## Incorrect response examples:

"We just sent you a password reset link."
"This email address doesn't exist in our database."

## Correct response example:

"If that email address is in our database, we will send you an email to reset your password."

# Account creation

## Incorrect response examples:

"This user ID is already in use."
"Welcome! You have signed up successfully."
Correct response example:

"A link to activate your account has been emailed to the address provided."

