Cryptology - Includes  Cyrptography, Protocols, Steganography

## Cryptography
- Deals with the transformation of data
**Cryptographic Algorithms**
*Keyless*
1. Cryptographic hash function
2. Pseudo-random number generator
*Single Key*
1. Block cipher symmetric encryption
2. Stream cipher symmetric encryption
3. Message authentication code
*Two-Key*
1. Asymmetric encryption
2. Digital signature
3. Key exchange
4. User authentication
> In databases, columns containing sensitive info is hashed

```shell
cat>hashfile3 // Create a file
Welcome to the class of cryptography
This is the first file to be hashed

openssl md5 hashfile3 // Hash using the md5 algorithm. Outputs a hash value
```