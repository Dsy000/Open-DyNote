# Cert to JSK convert 
A JKS file (Java KeyStore) is a type of file format used in Java-based applications to store private keys and digital certificates. It is a binary format that is used to securely store sensitive information such as SSL/TLS certificates, keys, and truststore certificates.

The JKS file is used by the Java Virtual Machine (JVM) to authenticate and establish secure connections with external entities. It is commonly used in web servers, application servers, and other Java-based applications that require secure communication. The JKS file can be managed and manipulated using the keytool command-line tool that is included with the Java Development Kit (JDK).

To convert a CRT file (a digital certificate) to a JKS file (a Java KeyStore), you can use the following steps:

1) Convert the CRT file to a PKCS12 format using the OpenSSL command-line tool. You can do this by running the following command in your terminal or command prompt:
```
openssl pkcs12 -export -in certificate.crt -out certificate.p12 -name "CertificateAlias"
```
This will create a PKCS12 file named certificate.p12 and set the alias name to CertificateAlias. You will be prompted to enter a password for the PKCS12 file.


2) Convert the PKCS12 file to a JKS format using the keytool command-line tool. You can do this by running the following command in your terminal or command prompt:
```
keytool -importkeystore -srckeystore certificate.p12 -srcstoretype PKCS12 -destkeystore keystore.jks -deststoretype JKS
```
This will create a JKS file named keystore.jks. You will be prompted to enter the password for the PKCS12 file and the password for the JKS file.


3)verify that the JKS file was created successfully by running the following command:
```
keytool -list -v -keystore keystore.jks
```
