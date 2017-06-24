---
layout: post
title: "Cryptography Week 1: Intro"
tag: [Cryptography, Coursera]
category: Learning
---

### Principles of Modern Crypto:

#### Definitions:Define what security means in a particular context
Giving a proper defintion of what you want will help you figure out exactly what you need, and may help you find nuances that you might have otherwise missed

#### Assumptions: Certain kinds of problems are impossible to solve effeciently; ex P!=NP; explicitly state what aasumptions you have made

#### Proofs of Security: Propose scheme, provide mathematical proof if why its secure

Reasons "secure" schemes break in the real world:
1)Wrong definition of security chosen
2) Assumption was wrong

### Kerchkhoffs Principle: Encryption Scheme should be public; only keys should be private

***

### Private Key Encryption:
3 main algorithms:
Gen --> Key Generation to create a random k in K
Enc --> Encryption Algorithm takes k and m (message chosen from M) and outputs c (ciphertext)
Dec --> Decrption Algorithm takes c and k and outputs m
Dec(Enc(m))=m
Encryption can be randomized; Decryption is deterministic
K and M are their respective spaces; ie m is a message chosen from M, the set of all possible messages

***

### Perfect Secrecy:
Cryptographic definitions have 2 parts:
1) threat model meant to capture real world capabilities attackers are assumed to have
2) Security guarantee : What is it that we are trying to prevent the attacker from doing?

### Several threat models:
1) Get ciphertext
2)Get plain and ciphertext
3)Choose plain, get ciphertext, often with ability to decrypt certain chosen ciphertexts

An encryption scheme is secure iff regardless of any prior knowledge the attacker has of the plaintext, the ciphertext observed by the attacker should leak no additional information about the plaintext



