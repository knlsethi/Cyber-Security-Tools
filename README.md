## RSA Algorithm

RSA is an algorithm used by modern computers to encrypt and decrypt messages. It is an asymmetric cryptographic algorithm. Asymmetric means that there are two different keys. This is also called public key cryptography, because one of them can be given to everyone.

To create RSA we will use OpenSSL library:

```markdown

openssl genpkey -algorithm RSA -pkeyopt rsa_keygen_bits:2048 -pkeyopt rsa_keygen_pubexp:3 -out privkey-A.pem // creates Private Key privkey-A.pem

openssl pkey -in privkey-A.pem -text | less // to view the Private Key dissociated in various parts like modulus, prime1, prime 2

openssl pkey -in privkey-A.pem -out pubkey-A.pem -pubout // to generate the Public Key pubkey-A.pem corresponding to privkey-A.pem

openssl pkey -in pubkey-A.pem -pubin -text | less // to view the Private Key dissociated in various parts like modulus, public exponent

openssl pkeyutl -encrypt -in message.txt -pubin -inkey pubkey.pem -out cipher.bin // to encrypt message.txt using pubkey-A.pem and storing the corresponding binary file as cipher.bin

opeenssl pkeyutl -decrypt -in cipher.bin -inkey privkey-A.pem -out recmsg.txt // to decrypt cipher.bin using privkey-A.pem and storing the corresponding text file as recmsg.txt

```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/knlsethi/Cyber-Security-Tools/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
