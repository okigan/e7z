[![Build Status](https://travis-ci.org/okigan/e7z.svg?branch=master)](https://travis-ci.org/okigan/e7z)

# e7z -- Encrypting 7zip with public key then decrypting 7zip with private key

Wrapper around 7z & openssl with public key encryption and private key decryption of stored data.

## Required packages:

1. openssl

2. 7z

## Usage:

### Create archive:

```shell
e7z -k pub.pem a archive.7z [input_folder|input_file]
```
#### How it work 

1. Create a random password 
2. Encrypt a password with **pub.pem** then store in **archivePassword.ssl** 
3. Archive **archivePassword.ssl** to **archive.7z**
4. Archive **input_folder** or **input_file** to **archive.7z** with a password 

### Extract:

```shell
e7z -k key.pem x archive.7z
```

#### How it work

1. Extract **archivePassword.ssl** from **archive.7z** 
2. Decrypt **archivePassword.ssl** with **key.pem** to get a password
3. Extract **archive.7z** with a password to get **input_folder** or **input_file**

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
