# Device Security
> Squids can be set up with specific rules to block certain sites, with all traffic being routed through them

## Network Protoocls
1. **IPSec** - 
2. **TLS**
3. **HTTPS**
4. **SSH**
5. **IEEE 802.11i**
6. **S//MIME**
> Read on how they work 

# Chapter 3: Classical Encryption Techniques

`Cipher refers to the algorithm`
Cryptographic systems are grouped according to 3 independent dimensions
1. Type of operation used to transform plaintext to ciphertext
2. Number of keys used
3. How the plaintext is processed
> Single-key encryption is aka conventional / secret key encryption.
> All encryption algorithms are based on substitution and transposition
> Public keys are generated from the private key

**Unconditionally secure** - If the ciphertext does not contain enough info to determine the uniquely the corresponding plaintext, no matter how much ciphertext is available. Meets the following criteria
	- Cost of breaking the ciphertext exceeds the benefit
	- Time needed to break the ciphertext exceeds the useful life expectancy
- Computationally secure - When an encryption algorithm meets one of the above criteria