# Cryptography
Implementation of RSA, DH and ECDH Algorithms

## Requirements: 

1. Python 2.7 and above
2. Install the following python packages:
  - !pip install pyDHE
  - !pip install tinyec
  - !pip install pycryptodome
  
## Import Libraries: 
 - from tinyec import registry
 - import hashlib, secrets, binascii
 - from sympy import isprime
 - import random
 - import numpy as np
 - import time as t
 - import tracemalloc
 - import pyDHE
 - import pandas as pd
 - from Crypto.PublicKey import RSA
 - from Crypto.Cipher import PKCS1_OAEP
 - import matplotlib.pyplot as plt

### We are implementing and comparing three Asymmetric/Public Key Cryptographic algorithms - RSA, DH and ECDH:

## Diffie Hellman

 - DH key exchange is a key exchange protocol that allows the sender and receiver to communicate over a public channel to establish a mutual secret without being transmitted over the internet. DH securely generates a unique session key for encryption and decryption that has the additional property of forwarding secrecy. 
 - In our code, we generate two private keys for A and B (using pydhe library), then we generate 2 public keys for A and B (size 8192 bits), using this we can comput the secret key for A and B. This is the Diffie Hellman key exchange algorithm. If both the shared keys are the same, then key exchange was successful. 
 - For encryption and decryption of message, we made our own mathematical function since diffie only does key exchange, and use that for encryption and decryption of our message.
 - We also noted the encryption time, decryption time (using time library) and memory usage (using tracemalloc library) (in lists) for 5 trials of the same algorithm since key generation is different every time. 

## Rivest-Shamir-Adleman (RSA)

- The RSA algorithm is an asymmetric cryptography algorithm; this means that it uses a public key and a private key (i.e two different, mathematically linked keys). As their names suggest, a public key is shared publicly, while a private key is secret and must not be shared with anyone.
- In our code, we generate a key pair of 3072 bits and use it to generate a public key. We then convert the message into bytes and then encrypt and decrypt it using RSA library of python.
 - We also noted the encryption time, decryption time (using time library) and memory usage (using tracemalloc library) (in lists) for 5 trials of the same algorithm since key generation is different every time. 

## Elliptic Curve Diffie Helman (ECDH)

- Elliptic-curve Diffie–Hellman (ECDH) is a key agreement protocol that allows two parties, each having an elliptic-curve public–private key pair, to establish a shared secret over an insecure channel. 
- In our code, We use ECDH to generate generate our 256 bit key pair (using tinyec library)
- Since ECC uses two points for key (x,y), we then use hashlib to convert this into a single 256 bit secret key
- We then use our own function to perform encryption and decryption.
- We also noted the encryption time, decryption time (using time library) and memory usage (using tracemalloc library) (in lists) for 5 trials of the same algorithm since key generation is different every time. 

### Following is the experiment result of our implementation:

### Trial Results for RSA algorithm
![alt text](https://github.com/lalwanii26/Cryptography/blob/main/images/RSA%20Trials.png?raw=true)

### Trial Results for DH algorithm
![alt text](https://github.com/lalwanii26/Cryptography/blob/main/images/DH%20Trials.png?raw=true)

### Trial Results for ECDH algorithm
![alt text](https://github.com/lalwanii26/Cryptography/blob/main/images/ECDH%20Trials.png?raw=true)

### Average Encryption Time
![alt text](https://github.com/lalwanii26/Cryptography/blob/main/images/Average%20Encryption%20Time.png?raw=true)

### Average Decryption Time
![alt text](https://github.com/lalwanii26/Cryptography/blob/main/images/Average%20Decryption%20Time.png?raw=true)

### Average Memory Allocation
![alt text](https://github.com/lalwanii26/Cryptography/blob/main/images/Average%20Memory%20Used.png?raw=true)

### Evaluation Metrics
![alt text](https://github.com/lalwanii26/Cryptography/blob/main/images/Evaluation%20metrics.png?raw=true)

## NOTE: Please note that since key generation is random for all 3 algorithms, encryption time, decryption time and memory usage will differ with every run of the code. This is the reason we used the average of 5 different trials for our results. 

