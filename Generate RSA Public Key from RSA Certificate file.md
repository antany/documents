this below method help to get java RSAPublic key object from firebase public key in below format.

-----BEGIN CERTIFICATE-----
MIIDHDCCAgSgAwIBAgIIUAu/wmcX4dQwDQYJKoZIhvcNAQEFBQAwMTEvMC0GA1UE
AxMmc2VjdXJldG9rZW4uc3lzdGVtLmdzZXJ2aWNlYWNjb3VudC5jb20wHhcNMjAw
NTEzMDkxOTU3WhcNMjAwNTI5MjEzNDU3WjAxMS8wLQYDVQQDEyZzZWN1cmV0b2tl
bi5zeXN0ZW0uZ3NlcnZpY2VhY2NvdW50LmNvbTCCASIwDQYJKoZIhvcNAQEBBQAD
ggEPADCCAQoCggEBAKsAwNDay6jPuWS/wmtF7vIyrGmg6akt+bI/Yx/baZhEpJm7
Fe7qmMyuS8MrkbhxXiEPIGhZKg5MQ1EKZ2TaSbZ9nXrpxFUUtH2CGop4k/XgmZC6
sEQPkxblQZrXTy11rj0pUQecklUPImOPR6lV9b2aDTQ/8nhaJ2e2FoknrU4eRWij
/zO7Z8cx78z3TfakDDG3AkeZo9sBReFIZc5kwHwxaWhqc/rPgGVT/zT3FMB0Lab+
PSwIMkgLMstBN5x1MTyi5SUcHaq0BT6lxJ6wvATWVDvl6rqd3qjWoF7VgwDsAWAs
5lrA6qNdc3O7h9P6Cq5SsE1GIhT/WcoFvIu9DucCAwEAAaM4MDYwDAYDVR0TAQH/
BAIwADAOBgNVHQ8BAf8EBAMCB4AwFgYDVR0lAQH/BAwwCgYIKwYBBQUHAwIwDQYJ
KoZIhvcNAQEFBQADggEBAHVT7pVhCziNoGGP4wfQ+0fd0p/m5p4E84tZiHquAx+Z
WnqpBa8YcstXTnaFWm1ValFkehXRPN81PVlIWuo3ba/qCLphu7foFNOpfhsuoiFp
XfjRJk/2GDnYoQ3tm1Z6VmjsIexHKG/9wHxNpClCzC7D5XHpt50R+zO9hof5+FXi
Kov9ndgfUb0jZZzjnp18fiOQL/PVWIxrBH7SeK/shiNKdHc9kyWHHlgehw37tN7Y
vRMqbQR/siWtgRr+nh0pI181qVLaOHAZvpk6b1mwOWjWt66prPQ76I3Vn+n83Al2
wz8B/WmLPhtl5bvasJKD4n+ZjHBc+Ap1LzyhXz/YpYI=
-----END CERTIFICATE-----



```
private static RSAPublicKey generateRSAPublicKeyFromCertFile(String publicKey) throws Exception {
		String baseKey = publicKey.replaceAll("\\r\\n", "").replaceAll("-----BEGIN CERTIFICATE-----", "")
				.replaceAll("-----END CERTIFICATE-----", "");
		byte[] decoded = Base64.getDecoder().decode(baseKey);
		InputStream certstream = new ByteArrayInputStream(decoded);
		Certificate cert = CertificateFactory.getInstance("X.509").generateCertificate(certstream);
		RSAPublicKey pk = (RSAPublicKey) cert.getPublicKey();
		return pk;
	}
```  
  
