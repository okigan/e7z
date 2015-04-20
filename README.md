[![Build Status](https://travis-ci.org/okigan/e7z.svg?branch=master)](https://travis-ci.org/okigan/e7z)

e7z -- Encrypting 7zip with private key support

A bash script (prototype) to wrap 7z and openssl to enable 
usage of public/private keys to safeguard the content.

Usage:

Create archive:

  e7z -k id_rsa a archive.7z input_file

Extract:

  e7z  -k id_rsa x archive.7z


Generate private key:

  ssh-keygen -t rsa -C "your_email@example.com"
