# Spring Boot - HTTPs setup - Self Signed

## Tools required
1. openssl

## Setup Local Certificate Authority
.. Step 1. Create Private key for Local Certificate Authority
```openssl genrsa -des3 -out localCA.key 2048```
