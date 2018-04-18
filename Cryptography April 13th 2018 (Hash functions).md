# Cryptography April 13th 2018 (Hash functions)

NOTE: 

First, Review:

Encryption schemes

​	One- time pad: 

​		Encrypt	`[ M ]	(XOR) [ K ] = [ C ]`

​		Decrypt `[ C ]  (XOR) [ K ] = [ M ]`

​	Stream Ciphers (RC4)

​		you have a short key (with initialization vector) --> 

​			RC4 -> outputs a pseudo -random key stream ( XOR ) [ M ] = [ C (cipher) ] 

​				We should send the cipher with the IV		

​		Cant be reused initialization vector

​		Can reuse the key

​	Block Cipher

​		Encrypts blocks of a message 

​			[ M ] & [ K ] --> [ AES ] = [ C ]

​			[ M ]

​		Modes of operation, 

​		**ECB** is insecure in that it is **deterministic** 

​		**CBC** mode of operation and **CTR** mode of operation,

​		Ex, CTR mode (counter)

​			[ CTR ] --> [AES k ] --> [ C ] (XOR) [ Msub1 ]

​			[ CTR + 1 ] --> [AES k ] --> [ C ] (XOR) [ Msub2 ]

## Hash functions

​	(Arbitrary Length) [ M ] -->  [ HASH ] --> [ Y ] ( Fixed Length )

​	This problem is intractable 

### Basic Properties

​	Collisions, when two different inputs which produce the same outputs

​	Collision Resistance

​	Pre-Image Resistance

​	Second Pre-Image Resistance

​	Hash functions give Authenticity, Confidentiality, and 

### Modern Definition:

#### Random Oracle Model:

> ###### Give an input *x*
>
> ​	inside the random oracle **x**, there is an elf that flips  a coin **r** times
>
> ​		then he will send an output string of y, resulting in the coin flips
>
> ​	If given input x then the elf will know he has seen this input before so he will give the same output
>
> ​		if given a different input (xsub2) than the elf the output that the elf gives is (ysub2)
>
> ​		Note: 	if we try 2^r+1 inputs then we have a 100% probability of finding a collision
>
>   				also, if we try 2^r inputs than we will have [ 2^(r/2) ] ( 50% chance of finding a collision 

Actual Hash Functions

​	Broken:	

​		MD Family: MD2, MD4, MD5, MD6. (

​			Completely quebrada except for MD6.)

​		SHA family (SHA-0, SHA-1 designed inspired by MD)

​		Reputable State of the art: SHA-3 (Keccak)

Sponges:

​	Absorbing phase: 

​		Feeding bits into xor 

​			first step: ( Vector which are specified ) [ 0 ] --> XOR <--- [ b, block of padded message]



MAC = Message authentication ode