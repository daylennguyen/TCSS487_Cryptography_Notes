# Cryptography April 2nd 2018

### One-Time Pad

> Entire random key of the same length as the message itself
>
> One-Time Pad
>
> > C<sub>i</sub> :arrow_left:M<sub>i</sub> (XOR) K<sub>i</sub>
> >
> > M<sub>i</sub> :arrow_left: C<sub>i</sub> (XOR) K<sub>i</sub>
>
> > **Advantage:** 
>
> > Unconditionally secure (***Shannon's Theorem***)
>
> **Disadvantage:**
>
> > The problem of protecting the message "reduces" to the problem of protecting the key



## Stream Cipher

> Expansion of a short key K into a random-looking bit sequence (or mask) K<sub>i</sub> of the same length as the message.



## Stream cipher

> > k~i~ :arrow_left: *f*(K,i) // **key deprivation function**
>
> > C<sub>i</sub> :arrow_left: M<sub>i</sub> (XOR) k<sub>i</sub> // **encryption**
>
> > M<sub>i</sub> :arrow_left: C<sub>i</sub> (XOR) k<sub>i</sub> // **decryption**
>
> in practice, bits are grouped into blocks of certain fixed length



## RC4 :tm:

#### Rivest Cipher #4

Proprietary algorithm, never officially revealed.

Reverse-engineered from official implementations and published anonymously.

Flexible key size (Multiples of 8bits, up to a maximum of 2048 bits)

Small number of simple arithmetic operations, oriented towards 8-bit processors.

**Now deprecated**

#### Practical discussion:

> A certain system uses RC4:tm: to encrypt messages under a password known to the sender and the recipient

> The password is registered only once and then used to encrypt/decrypt all messages exchanged between the sender and the receiver

#### Discuss:

> Apart from the recent attacks against RC4:tm:, what other (simpler and more dangerous) vulnerability is there in that system?

> How could you exploit that vulnerability to break the system security?
>
> ------
>
> The security of any stream cipher (and also the One-Time Pad) depends on the restriction that every key is used only once

> Reason: 

## Symmetric encryption: ***Block Ciphers***

Symmetric Cipher Definition

A symmetric cipher is a reversible mathematical transform E whose computation depends, in both directions (direct nd inverse), of the same secret information, called the key



## Block cipher

The transform applies to messages of some fixed length n (characteristic of the algorithm).

- E: {0,1}^k^ x {0,1}^n^ :arrow_right: {0,1}^n^

>The cipher's internal state is not carried out from one encryption to the next (in other words, block ciphers are stateless)

>It is possible to convert a block cipher to a stream cipher efficiently (doing the opposite is possible but inefficient)

> Typically a block cipher is an iterative algorithm, where some simple key-dependent transform is applied to the data block a number of times (called rounds)

#### Main Block Ciphers

> - **DES** (Data Encryption Standard)
>
>   > First time ever that an encryption algorithm is standardized (1977) with a public specification 
>
> - **3DES** (Triple DES)
>
> - **AES** (Advanced Encryption Standard)



