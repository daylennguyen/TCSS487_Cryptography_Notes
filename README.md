# TCSS487 Cryptography Notes

> ##### Daylen Nguyen's Notes
>
> Professor: **Paulo Barreto** (**UWT**)
>
> Notes correlating with class lectures, taught by: **Paulo Barreto** at University of Washington - Tacoma
>
> and the textbook: **Cryptography and Network Security – Principles and Practice.**

### Table of Contents:

| ***Section Title***                            |                        ***Content***                         |
| :--------------------------------------------- | :----------------------------------------------------------: |
| **1: Basic Services**                          |                   Basic security services                    |
|                                                |                   Mechanisms and policies                    |
|                                                |                Intro to Symmetric Asymmetric                 |
|                                                |                                                              |
| **2: Symmetric Encryption and Stream Ciphers** |                Symmetric Cipher (definition)                 |
|                                                |     Stream ciphers <br />(Transformation & Application)      |
|                                                |                         One Time Pad                         |
|                                                |                             RC4                              |
|                                                |                                                              |
| **3: Symmetric encryption and Block Ciphers**  |      Block ciphers<br />(Transformation & Application)       |
|                                                |                      Main block ciphers                      |
|                                                |              DES: the F function & Obsolescence              |
|                                                |                       Feistel network                        |
|                                                |                             3DES                             |
|                                                |               Meet-in-the-middle attack (todo)               |
|                                                |                  Block cipher cryptanalysis                  |
|                                                |                                                              |
| **4: Symmetric encryption: AES**               |                                                              |
|                                                |                Linear error-correcting codes                 |
|                                                |              Substitution-Permutation Networks               |
|                                                |                       Inside RIJNDAEL                        |
|                                                | The structure of a Round<br />(SubBytes, ShiftRows, MixColumns, AddRoundKey) |
|                                                |                         Key schedule                         |
|                                                |                                                              |
|                                                |                                                              |

------

## Section 1

### Basic Services

Firstly, the text book mentions the [NIST95] definition of security:

> ##### Computer Security: 
>
> The protection afforded to an automated information system in order to attain the applicable objectives of preserving the **integrity, availability, and confidentiality** of information system resources (includes hardware, software, firmware, information/data, and telecommunications).

### Class slides:

##### Confidentiality

- that any stored, transmitted or processed info will only be revealed to authorized users. 
- information != data. Data can be visible while hiding its associated information.

##### Integrity

- Checking the consistency of info contained in the data; 
- Preventing undue modification from going noticed.
- [DOES NOT ensure data is not altered. DOES ensure that if the date is unduly modified,  the modification will always be detected]

##### Authentication

- A system's resources are not used by unauthorized entities, or in an unauthorized fashion.

  #### 	(sub-categories): Legitimacy, vs Non-repudiation

  - **Legitimacy**: The user's claimed identity is verifiable and untransferable
  - **Non-Repudiation**: Once a user possesses, sends, or receives information by means of legitimate transactions, **they will be unable to deny it**. (For instance, online transactions)

##### Availability

- Guarantee that legitimate users will not be unduly prevented from accessing the system's information and resources.

  ​

### Mechanisms and policies: 

**Security Mechanisms:** 

> techniques, procedures and algorithms that, **when suitably applied**, ensure the proper deployment of the basic security services for computing and communications.

​	To suitably apply a security mechanism one must devise a **security policy**.

##### Security policy:

>  a **set of rules or courses of action** applied to all security-related activities **within a certain domain** under the responsibility of a **certain authority**.

***Examples of security mechanisms:***

> ​		Encipherment, Digital Signature, Access Control, Data Integrity

### What is a Cryptographic algorithm?

**Cryptographic algorithm:**

> ​		Mathematical techniques for information protection

##### These can be categorized by the type of information shared between the sender and the recipient.

| Algorithm Type | Basic Definition                                             |
| -------------- | ------------------------------------------------------------ |
| Symmetric      | Security depends on secret information **shared only between sender and receiver** (hence unknown to the adversary) |
| Asymmetric     | Security depends on **reliable information shared between the sender and the receiver** (potentially known by the adversary) |
| Auxiliary      | Security does **NOT** depend on any **shared information**   |

------

## Section 2

### Symmetric Encryption:

##### Basic Definition:

> A reversible mathematical transform ***E*** whose computation depends, in both directions (direct and inverse), of the same secret information, called the key.

![1524451921333](D:\_DRIVE\#CODE\git\TCSS48_Cryptography_Notes\sym_cipher)

There are two families of symmetric ciphers: **Stream Ciphers** and Block Ciphers.

### Stream Ciphers

##### Basic Definition:

> The transform ***E*** applies to messages of any size by operating bitwise.

![1524452741497](D:\_DRIVE\#CODE\git\TCSS48_Cryptography_Notes\steamcipher)

- The cipher-text length is the same as the plain-text length
- Typically the encryption of each bit changes the cipher's internal state to ensure that the output is "random looking"

### One-Time Pad

In this context, there is an entirely random key of the same length as the message itself.

- C<sub>*i*</sub> <== M<sub>*i*</sub> *(XOR)* K<sub>*i*</sub>
- M<sub>*i*</sub> <== C<sub>*i*</sub> *(XOR)* K<sub>*i*</sub>

##### Advantage: 

> Unconditionally secure (Shannon's theorem)

##### Disadvantage

> The problem of protecting the message "reduces" to the problem of protecting the key.



### Stream Ciphers: pt.2

- In this context we have an expansion of a short key ***K*** into a random-looking bit sequence (or mask) k<sub>*i*</sub> of the same length as the message.
  - K<sub>*i*</sub> <== *f*(K,*i*)		This is the key derivation function
  	 C<sub>*i*</sub> <== M<sub>*i*</sub> ***(XOR)*** k<sub>*i*</sub>		Encryption
  	 M<sub>*i*</sub> <==  C<sub>*i*</sub>***(XOR)***k<sub>*i*</sub>		         Decryption
- In practice, bits are grouped into blocks of a certain fixed length (e.g. into bytes).

### RC4: Rivest Cipher #4 (OBSOLETE)

- Flexible key sizes: (Multiples of 8, up to a max of 2048 bits)
- Teaches us that the strength and security of stream ciphers is dependent on the restriction that any key can only be used only **once** 
  - If a key is collected by adversary and ***(XOR)***'d with a cipher than they can obtain the key that was applied.

------

## Block Ciphers (Symmetric Encryption cont.)

Basic Definition:

> The transform applies to messages of some fixed length ***n***, which is a characteristic of the algorithm

​	![1524454616386](D:\_DRIVE\#CODE\git\TCSS48_Cryptography_Notes\blockcipher)

- The ciphers internal state is not carried from one encryption to the next
  - Block ciphers are stateless
- Often times, a block cipher is an iterative algorithm, where some some key-dependent transform is applied to the data block a number of times (called rounds).

#### The three main block ciphers are:

- DES (Data Encryption Standard)
- 3DES (Triple DES)
- AES (Advanced Encryption Standard)

### DES (Data Encryption Standard) #Obsolete

> First encryption with public specification
>
> Chosen by NIST during competition in 1975

- 64-bit blocks, 56-bit keys
- Each round applies a simple transform that depends on 48 of the 56 key bits
- Choice of the subkey bits for each round follows a linear schedule
  - No mixing, only permutations and repetitions
- Makes use of the **Feistel Network**

#### Feistel Network:

![1524455057595](C:\Users\Flan\AppData\Local\Temp\1524455057595.png)

#### DES - the F Function:

The algorithm is as follows:

1. Expand the 32 input bits into 48 bits with a linear transform 
2. ***(XOR)*** round subkey K<sub>i</sub> onto the result
3. Partition the result into 8 groups of 6 bits each
4. Replace the value of each of those 6-bit groups by a 4-bit value via table lookup 
   - There are 8 distinct lookup tables called **S-BOXES**
5. Permute the resulting 32 bits to obtain the return value of the function F

#### Inside the F function (DES)

![1524455273762](D:\_DRIVE\#CODE\git\TCSS48_Cryptography_Notes\DES_Ffunction)

#### Obsolescence:

- 56-bit **key is insufficient** to resist modern computers
  - Must consider future attacks/computers aswell
- **Public research** has resulted in a **reduction in the attack cost**: 2<sup>47</sup> and then 2<sup>41</sup>  
- Retired by NIST in 2004

## 3DES

- Enabled continued use of widely deployed DES implementations.
- Use of **Triple Encryption**: 
  - Encrypt the block 3 times, each with a distinct 36-bit DES key K<sup>*1*</sup>, K<sup>*2*</sup>,K<sup>3</sup> (Totaling at 168 key bits)
- Popular variant: 
  - Decrypt with K<sup>2</sup>  instead (Encrypt, Decrypt, Encrypt)
- Security roughly equivalent to a block cipher with ~112-bit keys.

------

## AES, Advance Encryption Standard: (Sym. Encrypt cont.)

#### AES is based on Rijndael's algorithm:

- **Symmetrical**, parallel structure:
  - implementation flexibility
- AES is a **proper subset** of RIJNDAEL:
  - 128-bit blocks
  - 128-bit, 192-bit, or 256-bit keys

#### **AES Structure**: (Book)

![1524456555287](C:\Users\Flan\AppData\Local\Temp\1524456555287.png)

### **AES Transformation Functions:** (Book)

#### Round Structure:

1. **Sub Bytes**: Non-linearity
2. **Shift Rows**: Diffusion among data columns
3. **Mix Columns**: Diffusion within each data column
4. **Add Round Key**: Round sub-key application

#### AES: Substitute Bytes Transformation (SubBytes)

- A simple table lookup; AES defines a 16x16 matrix of byte values, called a **S-box**, that contains a permutation of all possible 256 8-bit values
- A **single S-box** is used for the whole cipher (DES used 8 distinct S-Boxes)
- Each byte of 'State' is mapped into a new byte as specified by the algorithm:
  - The **leftmost 4 bits** of the byte are used as a **row** value
  - the **rightmost 4 bits** are used as a **column** value
  - These **rows and col. serve as indexes** into the **s-box** to select a unique 8-bit output val.
    - Hex value x95 would map to row 9 col 5 of the S-Box

#### AES: ShiftRows Transformation

ShiftRows, the second transformation in the AES, F-function

1. **The 1st row** of State is not altered
2. **For the 2nd row,** 1-byte circular left shift is performed 
3. **For the 3rd row**, a 2-byte circular left shift is performed.
4. **For the 4th row** a 3byte circular left shift is performed

#### AES: MixColumns Transformation

- **MixColumns** operates on each column individually
  - The bytes on each column are combined linearly among themselves.
- Extreme diffusion within each column (MDS Property)
- Each byte of a column is mapped into a new value that is a function of all four bytes in that col.

![1524458526911](D:\_DRIVE\#CODE\git\TCSS48_Cryptography_Notes\mixcol)

![1524458609882](C:\Users\Flan\AppData\Local\Temp\1524458609882.png)

#### AES: AddRoundKey Transformation

- 128 bits of State are bitwise ***(XOR)***'d with the 128 bits of the round key
- This Makes the round transform **key-dependent**

![1524458810287](C:\Users\Flan\AppData\Local\Temp\1524458810287.png)

![1524456630108](C:\Users\Flan\AppData\Local\Temp\1524456630108.png)

------

## Block Cipher Modes of Operations (Sym. Encrypt. cont.)

- Block Ciphers only **operate** on messages of a **single fixed length**
  - This is what distinguishes them from stream ciphers

#### Basic Definition: 

​	An extension for other message sizes and in some cases even to other security sevices

##### Confidentiality modes:

- **(Requires padding)**: ECB and **CBC**
  - Complete its length so that the result is a factor of a set number
  - Remove padding after we decrypt


- **(Disk Sector Encryption)**: XTS, LRW, XEX and EME
  - Useful for encrypting bulk amounts of data
- **(Emulates a stream cipher):** CFB, OFB and **CTR**

##### Integrity Modes: 

- CBCMAC, **CMAC**
  - (**MAC**) Message authentication cipher
  - Issues with **CBCMAC** are **resolved by CMAC**

#### Hybrid Modes

- OCB, CCM, EAX, **GCM**

------

### Padding

- For some modes, the **message must be extended** so that the length of it becomes a multiple of the **block size**

##### Non-ambiguity hypothesis: 

​	Padding is always added (even when the message length is already a multiple of the block size)

**PKCS** padding is **bytewise**

- Append m bytes, each with the same value m

**NIST** padding is **bitwise**

- Append a '1' bit then complete with zero or more '0' bits

### ECB: Electronic Code Book, mode of operation

- The simplest mode, in which plain text is handled on block at a time and each block of plaintext is encrypted using the same key.