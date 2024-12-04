# Kerberos

## Overview

In the Kerberos authentication protocol, TGT (Ticket Granting Ticket) and TGS (Ticket Granting Service) are central components that facilitate secure authentication and access to network services.

## Ticket Granting Ticket

Definition: The TGT is a special type of Kerberos ticket issued by the Authentication Service (AS) during the initial login or authentication process.

### Purpose:

    Proves the user’s identity within the Kerberos realm.
    Allows the user to request service tickets (TGS tickets) from the Ticket Granting Service without needing to re-enter credentials.

### How It Works:

    The client sends their credentials (username and password, hashed as part of the process) to the Key Distribution Center (KDC).
    The KDC validates the credentials and issues the TGT.
    The TGT is encrypted with the KDC’s secret key, making it tamper-proof.

### Duration:

    The TGT has a limited validity period (e.g., 8 hours by default in many systems) and can often be renewed.


## Ticket Granting Service (TGS)

Definition: The TGS is a component of the Key Distribution Center (KDC) that issues service tickets for specific network services.

### Purpose:

    Grants access to specific services within the network, such as file servers, databases, or applications.
    The user must present the TGT to request a TGS ticket for the desired service.

### How It Works:

    The client sends the TGT to the TGS, along with a request for access to a specific service (identified by its Service Principal Name, or SPN).
    The TGS validates the TGT.
    If valid, the TGS issues a service ticket encrypted with the service’s secret key.
    The client uses the service ticket to authenticate directly with the desired service.

## Workflow Example

Initial Login (TGT Issuance):
    User logs in and gets a TGT from the AS.
Request Service Ticket (TGS Process):
    User sends the TGT to the TGS to request a service ticket for a specific resource.
Access Service:
    User sends the service ticket to the target service (e.g., a file server) for access.

## Key Differences Between TGT and TGS

Aspect	TGT	TGS
Purpose	Authenticate the user to the KDC.	Provide access to specific services.
Issuer	Authentication Service (AS).	Ticket Granting Service (TGS).
Usage Scope	Realm-wide, reusable.	Service-specific, one-time use.
Encryption	Encrypted with KDC's key.	Encrypted with the service's key.

## Summary

The TGT is the user's "passport" within the Kerberos system, allowing them to request access to other services without re-authentication.
The TGS provides "visas" (service tickets) for accessing specific services, ensuring secure communication with those services.
This layered ticketing system reduces the need to transmit passwords repeatedly, enhancing security in large network environments like Active Directory.