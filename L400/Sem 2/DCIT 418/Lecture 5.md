Cryptology - Includes  Cyrptography, Protocols, Steganography

## Cryptography
- Deals with the transformation of data
**Cryptographic Algorithms**
*Keyless*
1. Cryptographic hash function
2. Pseudo-random number generator
*Single Key*
1. Block cipher symmetric encryption - Message is divided into equal blocks, which are then encrypted individually. eg. DES, Triple DES, AES
2. Stream cipher symmetric encryption  - The bitstream is what is encrypted, not the raw message/packet
3. Message authentication code
*Two-Key*
1. Asymmetric encryption
2. Digital signature - Uses the private key to perform encryption, with the private key being used to decrypt. eg of Public key system is RSA
3. Key exchange
4. User authentication
> In databases, columns containing sensitive info is hashed
> Hashing is a one-way function, which prevents hashes from being reversed

```shell
cat>hashfile3 // Create a file
Welcome to the class of cryptography
This is the first file to be hashed

openssl md5 hashfile3 // Hash using the md5 algorithm. Outputs a hash value
```

**Applications of Cryptography**
1. Satellite communication
2. Paid subscription streaming services
3. Online banking
4. GSM / Telecomm services
5. GPS
6. Websites with HTTPS

`In performing online transactions, the public key of the website is used to encrypt the transaction, with the private key being used on the end servers to decrypt`
`For Digtal signature, the private key is used to encrypt`