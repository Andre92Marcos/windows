# sam - Security Account Manager

## Overview

SAM is a database in Windows that stores user credentials (like passwords) and other account-related information. It's a critical part of the Windows authentication system.

The SAM is primarily used for local authentication on a machine, where Windows manages the login credentials and performs the authentication process.

## Relationship between LDAP and SAM

When working with LDAP, particularly in a Windows environment (e.g., Active Directory), SAM data (user accounts, groups, etc.) can be accessed and managed through the directory.

While SAM is used to manage local user accounts, Active Directory (AD) extends this concept to a network-wide, scalable service, allowing administrators to manage users across many machines using LDAP queries.

LDAP allows querying Active Directory for user details stored in the SAM database, although it's accessed via a directory service like AD rather than directly interacting with SAM on a single machine.

