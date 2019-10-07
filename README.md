[![Build Status](https://travis-ci.org/okigan/e7z.svg?branch=master)](https://travis-ci.org/okigan/e7z)

# e7z -- Encrypting 7zip with private key support

Wrapper around 7z & openssl with private keys encryption of stored data.

## Require packages:

1. openssl

2. 7z

## Usage:

### Create archive:

```shell
e7z -k pub.pem a archive.7z input_file
```
### Extract:
```shell
e7z -k key.pem x archive.7z
```

## Generate Public/Private Key:

1. Generate RSA key in key.pem file:

```shell
openssl genrsa -out key.pem 1024 
openssl rsa -in key.pem -text -noout 
```

2. Save public key in pub.pem file:
```shell
openssl rsa -in key.pem -pubout -out pub.pem 
openssl rsa -in pub.pem -pubin -text -noout 
```
