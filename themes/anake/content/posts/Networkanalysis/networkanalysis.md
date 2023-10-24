+++
title = 'Networking'
date = 2023-10-21T11:00:00-07:00
draft = false
tags = ['Network Considerations']
+++
# I. Introduction
Computer systems are connected, with networks. The network components are presented in seven layers, from physical to Application, layers are interconnected with systems built of components. This document will explains three concepts 

Transport Layer Protocol vulnerabilities, controls and mitigations 

Network Layer Protocols vulnerabilities, controls and mitigations 

Media Access Control(MAC) vulnerabilities, controls and mitigations 


| OSI Layer | Network Communication Stack Layer |
|-----------|-----------------------------------|
|   7. Application    | Application Layer             |
|   6. Presentation   | Presentation Layer            |
|   5. Session        | Session Layer                 |
|   4. Transport      | Transport Layer               |
|   3. Network        | Network Layer                 |
|   2. Data Link      | Data Link Layer                |
|   1. Physical       | Physical Layer                |


# [Transport Layer Protocols](https://datatracker.ietf.org/doc/html/rfc5246)
Transport Layer security is designed to create a secure connection between acliet and server, while they communicate on an insecure channel. By design TLS is designed to be secure and assumes that the attacker possess the abilitiy to capture, modify, delete, replay and otherwise have the ability to tamper with the messages over the channel. 


| Security Aspect         | Description                                                           |
|------------------------|-----------------------------------------------------------------------|
| Confidentiality        | Protection against an attacker from reading the contents of traffic. |
| Integrity              | Protection against an attacker modifying traffic.                    |
| Replay Prevention      | Protection against an attacker replaying requests against the server.|
| Authentication         | Allowing the client to verify that they are connected to the real server (note that the identity of the client is not verified unless client certificates are used). |



[OWASP SSL audit for testers](https://wiki.owasp.org/index.php/O-Saft)

# Mixed active content

This occurs when an active resource, like scripts to CSS are loaded over an unsecure channel, unencrypted HTTP, this is dangerous since a malicious actor can modify these files since they are sent on an unsecure communications channel, permitting a malicious actor to execute arbitrary code (Javascript or CSS), this passive content loaded over the insecure communication channel can leak information or allow an attacker to deface the page. 

Good programming practices in web development are important to consider in mitigating this vulnerability. 

When a resource is not available via https:// consider these options

Include the resource from a different host, if one is available.

Download and host the content on your site directly, if you are legally allowed to do so.

Exclude the resource from your site altogether.

Considering non-standard tags 
```(<a>)``` Anchor tags do not create mixed content errors, but there image gallery scripts that override the functionality of the ```(<a>)``` tag which loads the HTTP resource ```href``` attribute in to a lightbox, creating a mixed content problem. 

Consider a content security policy to enable addressing this misconfigurations at scale. 

## HTTP to HTTPS redirect 
 Sites will accept connections over HTTP (unencrypted channels) and redirect from 301 Moved Permanently to the Strict Transport Security header to instruct the browser to use HTTPS in teh future, however attackers can intercept this communication with tools like [sslstrip](https://github.com/moxie0/sslstrip) to intercept and manipulate subsequent requests. 


  


References:

  Orzach, & Khanna, D. (2022). Network Protocols for Security Professionals : Probe and Identify Network-Based Vulnerabilities and Safeguard Against Network Protocol Breaches. (1st ed.).
