## RSA Algorithm

RSA is an algorithm used by modern computers to encrypt and decrypt messages. It is an asymmetric cryptographic algorithm. Asymmetric means that there are two different keys. This is also called public key cryptography, because one of them can be given to everyone.

To create RSA we will use OpenSSL library:

```markdown
openssl genpkey -algorithm RSA -pkeyopt rsa_keygen_bits:2048 -pkeyopt rsa_keygen_pubexp:3 -out privkey-A.pem 
// creates Private Key privkey-A.pem

openssl pkey -in privkey-A.pem -text | less 
// to view the Private Key dissociated in various parts like modulus, prime1, prime 2

openssl pkey -in privkey-A.pem -out pubkey-A.pem -pubout 
// to generate the Public Key pubkey-A.pem corresponding to privkey-A.pem

openssl pkey -in pubkey-A.pem -pubin -text | less 
// to view the Private Key dissociated in various parts like modulus, public exponent

openssl pkeyutl -encrypt -in message.txt -pubin -inkey pubkey.pem -out cipher.bin 
// to encrypt message.txt using pubkey-A.pem and storing the corresponding binary file as cipher.bin

opeenssl pkeyutl -decrypt -in cipher.bin -inkey privkey-A.pem -out recmsg.txt 
// to decrypt cipher.bin using privkey-A.pem and storing the corresponding text file as recmsg.txt

```
## SHA1 Hash Function

In cryptography, SHA-1 (Secure Hash Algorithm 1) is a cryptographic hash function which takes an input and produces a 160-bit (20-byte) hash value known as a message digest - typically rendered as a hexadecimal number, 40 digits long. It was designed by the United States National Security Agency, and is a U.S. Federal Information Processing Standard.

To create SHA1 Hash Function we will use OpenSSL library:

```
openssl genpkey -algorithm RSA -pkeyopt rsa_keygen_bits:2048 -pkeyopt rsa_keygen_pubexp:3 -out privkey-B.pem
openssl pkey -in privkey-B.pem -out pubkey-B.pem -pubout
// generate a set of private and public key

openssl dgst -sha1 message.txt
// to view the Hash value of the message

openssl dgst -sign privkey-B.pem -out signature.bin message.txt
// to encrypt the Hash value into a binary file signature.bin

openssl dgst -sha1 -verify pubkey-B.pem -sign signature.bin recmsg.txt
// to verify that the received message was send by the particular sender
```

If the hash value and message matches it shows "Verified OK" on the screen or else "Verification Failure".

## PenTBox Honeypot

In computer terminology, a honeypot is a computer security mechanism set to detect, deflect, or, in some manner, counteract attempts at unauthorized use of information systems. Generally, a honeypot consists of data (for example, in a network site) that appears to be a legitimate part of the site, but is actually isolated and monitored, and that seems to contain information or a resource of value to attackers, who are then blocked.

```
sudo ruby pentbox.rb
// open the pentbox ruby file using admin privileges.

// select the 2 option Network Security
// open the 3 option Honeypot

// configure the honeypot using various honeypot

//this will then store the details of various intrusions
```
