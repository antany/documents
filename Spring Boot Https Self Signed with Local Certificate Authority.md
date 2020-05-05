# Spring Boot - HTTPs setup - Self Signed

## Tools required
1. openssl

## Setup Local Certificate Authority
#### Step 1. Create Private key for Local Certificate Authority <br> 
```openssl genrsa -des3 -out localCA.key 2048```
above command ask for password, keep it safe, it will be required in next steps

#### Step 2: Create Local Auth
```openssl req -x509 -new -nodes -key localCA.key -sha256 -days 365 -out localCA.pem``` <br>
note: when asked for common name, specify the domain name, in my case its just <b>localhost</b>
