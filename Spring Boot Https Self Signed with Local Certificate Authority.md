# Spring Boot - HTTPs setup - Self Signed

## Tools required
1. openssl

## Setup Local Certificate Authority
#### Step 1. Create Private key for Local Certificate Authority <br> 
```openssl genrsa -des3 -out localCA.key 2048```
above command ask for password, keep it safe, it will be required in next steps

#### Step 2: Create Local Auth
```openssl req -x509 -new -nodes -key localCA.key -sha256 -days 365 -out localCA.pem``` <br>

## Create Certs using the Certificate Authority created in previous steps
#### Step 1. Generate private key
```openssl genrsa -out myweb.key 2048```

#### Step 2. Generate certificate signing request
```openssl req -new -key myweb.key -out myweb.csr```<br>
note: when asked for Common Name use your domain name, in my case its localhost

#### Step 3. Create a config fix
create config file localhost.ext with following information <br>
```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = @alt_names

[alt_names]
DNS.1 = localhost
```
<br>

One line command<br>
```printf "authorityKeyIdentifier=keyid,issuer\nbasicConstraints=CA:FALSE\nkeyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment\nsubjectAltName = @alt_names\n\n[alt_names]\nDNS.1 = dev.mergebot.com" > localhost.ext```


