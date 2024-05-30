Cryptology - Includes  Cyrptography, Protocols, Steganography

## Cryptography
- Deals with the transformation of data
**Cryptographic Algorithms**
1. Cryptographic hash function
2. Pseudo-random number generator
3. Block cipher symmetric encryption
4. Stream cipher symmetric encryption
5. Message authentication code
6. Asymmetric encryption
7. Digital signature
8. Key exchange
9. User authentication
> In databases, columns containing sensitive info is hashed

```shell
cat>hashfile3 // Create a file
Welcome to the class of cryptography
This is hte first file to be hashed

openssl md5 hashfile3 // Hash using the md5 algorithm. Outputs a hash value
```