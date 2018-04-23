# Modes of operations

## Symmetric Encryption: Modes of Operations

Block ciphers will only operate on fixed length messages

> This is what distinguishes them from stream ciphers

### Modes of operations: (General)

Extensions for other message sizes, and in some cases even to ger security services

want to to make sure that information is unchanged

#### Confidentiality modes:

- ##### (Requires padding) 

  - ECB and **CBC**
    - Complete its length so that the result is a factor of a set number
    - Remove padding after we decrypt

- ##### (Disk Sector Encryption)

  - XTS, LRW, XEX and EME
  - Useful for encrypting bulk amounts of data

- ##### (Emulates a stream cipher) 

  - CFB, OFB and **CTR**

#### Integrity Modes:

- CBCMAC, **CMAC**
  - (MAC)Message authentication cipher
  - Issues with CBCMAC are resolved by CMAC

#### Hybrid Modes

- OCB, CCM, EAX, **GCM**

------

## Padding

> ##### Ensures  that the message input is a multiple of the block size (128 bits or 16 bytes)

#### Non ambiguity hypothesis: 

> Padding is always added, even when the message length is already a multiple of the block size

## Padding found in class literature

#### PKCS padding : byte-wise

​	Append m bytes, each with the same value *m*.

> ​	0x01, in hex if we need to append 1 byte
>
> ​	0x02 0x02, if two bytes
>
> ​	0x03 0x03 0x03, for three bytes and so forth

#### NIST padding: bit-wise

> Appending a '1' bit to the end of the message then append '0' bits, *n* number of times until the block is a multiple of the block size.

`[messages]+[1000000]` <-- Padding to make the message a multiple of the block size

> - If the message length is already a multiple of the block cipher, then we will append an extra block of padding for non-ambiguity
> - To undo this, remove 0s  until we find a 1, then remove the zeros and the 1.

## ECB: (Electronic Code Book)

> ##### Partitioning the message into blocks to be encrypted and decrypted independently

​	Similar to using a dictionary to encrypt and decrypt.

> **Problem**: equal plain text blocks yield equal cipher blocks. Furthermore, it is insecure

### CBC - Encryption

> 1. Partition the message into blocks while still padding
>    	$M_{1} M_{2}...M_{n} [P]$
> 2. XOR IV (Initialization Vector) with M_{1}
>    This will output $C_{1}$ which will be $\otimes$'d with $M_{1}$

#### CBC has security problems

- The padding itself introduces a subtle vulnerability (padding oracle attacks) that are hard to fix

CTR mode: Counter mode of operation

- IV is 12 bytes, pad with for zero bytes
- initialize the counter by encrypting it
- then xor this with 

To decrypt

​	add the pad back on to IV and encrypt it

