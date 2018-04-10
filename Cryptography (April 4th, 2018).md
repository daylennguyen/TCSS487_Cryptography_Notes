# ***Cryptography (April 4th, 2018)***

```
Note: The class began with a Quiz (#2)
```

## DES (Data Encryption Standard)

> - **Hardware-oriented** structure, but fairly efficient in software
> - Is a **(block cipher)** 64-bit blocks, 52-bit keys
> - Each round applies a simple transform that depends on 48 of the 56 key bits.
> - Choice of the sub-key bits for each round follows a linear schedule (no mixing, only permutations and repetition)
> - *Feistel network*

------

### **Feistel network**

> ***Involution***

( Key ) :arrow_right:  [KS] :arrow_right: (K<sub>n</sub>) :arrow_right: [F]

- extract 48 bits from the master key

> ######  Plain text

​		will be split in half

------

### The F function (**Round function** is used during each iteration)

- Expansion :arrow_right: Key Addition (the key, K<sub>i</sub> is 48 bits and is fed to the [xor]) :arrow_right: Substitution :arrow_right: Permutation

> ***Involution***

#### Input and Output size of the steps (F function):

> |                              |                     # of bits processed                      |
> | ---------------------------- | :----------------------------------------------------------: |
> | **Expansion** :arrow_down:   |           32 bits (Mux) (input), output of 48-bits           |
> | **Key Addition**:arrow_down: | 48 bits in the inputs (XOR) (from both the mux and K<sub>i</sub>) |
> | **Substitution**:arrow_down: | Look up table layer </br>(input) (8x6) 48-bits :arrow_right: (output) (8x4) 32-bits |
> | **Permutation**:arrow_down:  |           32 bit input from the substitution layer           |
>
> ## ( *pure* ) DES is **obsolete**
>
> > - 56-bit key is insufficient to resist modern computational capabilities
> > - block size may be too small to present future attacks as well
> > - definitively retired by NIST in 2004

> ## 3DES
>
> > - Palliative solution to enable continue use of widely deployed hardware and software DES implementations.
> > - Triple encryption: encrypt the block 3 times each with a distinct 56-bit DES key (K_1)(K_2)(K_3) (Total of 168 key bits)
> > - Popular variant: decrypt with K_2 instead (EDE)
> > - Security roughly equivalent to a **block cipher** with 112-bit keys_ 
>
> ## 2DES ?
>
> - What about encrypting each block only twice instead, under two distinct 56-bit keys K<sub>1</sub>, K<sub>2</sub>?

# AES 

#### Modes of Operation

> - ECB (Electronic Code Book)
> - CBC (Cypher Block Chain Mode)
> - CTR mode (widely used)
>   - Pick up a counter at random 128 bit, then then encrypt it with AES and increment the counter

> #### Probabilistic vs Deterministic
>
> ##### Deterministic
>
>  - Identical messages will result in a identical encryption
>
> ##### Probabilistic 
>
> - Identical messages will result in a different identical encryption
> - Initialization vector is randomly chosen to result in a probabilistically encrypted message 
>   - initialization vector is XOR'd with the message which is then sent to the **block cipher**
>
> 
>
> ​	