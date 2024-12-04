# ntlm - New Technology Lan Manager

## Overview

NTLM is a collection of authentication protocols created by Microsoft. It is a challenge-response
authentication protocol used to authenticate a client to a resource on an Active Directory domain.
It is a type of single sign-on (SSO) because it allows the user to provide the underlying authentication factor
only once, at login.

## Authetication Process

The NTLM authentication process is done in the following way :
	1. The client sends the user name and domain name to the server.
	2. The server generates a random character string, referred to as the challenge.
	3. The client encrypts the challenge with the NTLM hash of the user password and sends it back to the
server.
	4. The server retrieves the user password (or equivilent).
	5. The server uses the hash value retrieved from the security account database to encrypt the challenge
string. The value is then compared to the value received from the client. If the values match, the client
is authenticated.

## NetNTLMv2

When the NTLM protocol wants to do authentication over the network, it uses a challenge / response
model as described above. A NetNTLMv2 challenge / response is a string specifically formatted to
include the challenge and response. This is often referred to as a NetNTLMv2 hash, but it's not actually
a hash. Still, it is regularly referred to as a hash because we attack it in the same manner. You'll see
NetNTLMv2 objects referred to as NTLMv2, or even confusingly as NTLM.
