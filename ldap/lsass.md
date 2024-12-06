# lsass - Local Security Authority Subsystem Service

## Overview

LSASS is a system process that is responsible for enforcing security policies on the system. It plays a central role in managing authentication and authorization tasks within Windows, particularly when a user logs in or accesses resources.

## Key Functions

### Authentication:

LSASS is responsible for validating the credentials of users when they log in (e.g., checking usernames and passwords).
It handles authentication protocols such as Kerberos, NTLM, and LDAP (Lightweight Directory Access Protocol) for domain logins.

### Ticketing and Token Management:

LSASS is responsible for generating and managing security tokens, which are assigned to users or processes to grant them access to resources.
For domain environments, LSASS handles Kerberos Ticket Granting Tickets (TGT) and Service Tickets, which are used for Kerberos authentication in Active Directory.

### Logon Security:

It enforces user logon policies, such as password complexity, lockout policies, and domain-specific restrictions.

### Password Changes:

LSASS also handles password changes, including the propagation of password changes to all relevant systems in a domain.

### Communication with Active Directory:

In domain environments, LSASS communicates with Active Directory (AD) to verify credentials and perform other security-related functions for domain accounts.

## Location:

LSASS runs as a system process (lsass.exe) in Windows, typically with high privileges and it is critical for system security. It runs in the background and is always active as long as the system is running.

## Interaction Between LSASS and SAM

When a user attempts to log in, LSASS validates the credentials by checking them against the SAM (if it’s a local account) or Active Directory (if it’s a domain account). It hashes the entered password and compares it to the hashed passwords stored in the SAM database.

LSASS also uses the information from the SAM when authenticating local user accounts (those that are not part of a domain).

SAM holds the password hashes of local accounts, but LSASS is the process responsible for using that information to perform authentication and enforce security policies.

## Security Implications

SAM can be accessed directly by attackers who gain access to the file system, but it is typically locked while the system is running to prevent unauthorized access.

LSASS can be a target for attackers because it runs with high privileges. Tools like Mimikatz can extract credentials, NTLM hashes, and Kerberos tickets from LSASS memory while the system is running.