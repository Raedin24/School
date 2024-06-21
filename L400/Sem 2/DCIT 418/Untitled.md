**Diffie-Hellman** key exchange is a method of digital encryption used to exchange *shared secret keys*  over an insecure network.
- Allows for secure comms without pre-shared secrets or a trusted third party
**Key Establishment Process**
1. Choose  large prime numbers to be shared over the insecure network for each end
2. Each side chooses a secret key
3. The private key for each end is combined as such: Smaller public key exponent secret key, mod larger shared key. Assuming public keys of 5, 23 and secret keys of 4, 3. The result is the public key for the other party

$$
A = 5^4 mod 23 = 4 \\{\newline}
B = 5^3 mod23 = 10
$$
4. To exchange a shared key, the public key gotten for the other party is 