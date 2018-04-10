# Cryptography (April 9th 2018): 
# Review and Defining a secure cipher

```
Note: Substitute professor from network security
Review: 
     Computational Secure Schemes
     Perfect Secrecy
     One-Time Padding
```
------

## **Stream Ciphers**
> A **stream cipher** is a cipher that **takes a short key**
> sometimes you concatenate those two
> **Then input:** 
>
> >  (K , IV)  -> [ stream cipher ]  -> [    PAD    ]
>
> **Then**
>
> > The **onetime pad** is **(XOR)'d with the [MESSAGE]**
> >
> > and outputs: **[CIPHER TEXT,IV]**
>
> Which would be given to Bob 
>
> > Bob takes the key and (K , IV) -> [ stream cipher ] -> [	 PAD	 ] 
> >
> > Then the one-time pad is (XOR)'d with the  [CIPHER TEXT]
>
> - NEEDS TO HAVE A NEW IV WITH EVERY MESSAGE

------

## Block Ciphers

> #### Types: DES (BAD) and AES(128)
>
> #### 2DES is obsolete because of the meet in the middle attack
>
> #### 3DES is used instead, 
>
> > - although the security level is 112
> >
> >
> > - the key length 158
> > - AES is quicker and has a better security level

## Mode of Operation of a Block Cipher

#### Electronic Code Book: ECB

- > If you have a general message that is not a multiple of the blocks
  >
  > then you will need to **pad** (with zero) the message 
  >
  > and add the length to the end
  >
  > then you split the message into blocks and use the same key on each block (AES sub K)

#### Cipher Block Chaining: CBC

- > You have blocks of message (already been padded)
  >
  > Then you get a initialization vector (IV )
  >
  > which is a random string of bits (same length as the message block/block cipher)
  >
  > XOR the first message bloc with (IV which outputs a (AES sub  K)

### Counter Mode of Operation

- > Takes a counter and 
  >
  > [ COUNTER ]-> [ AES sub k ] gives a [ pseudo-random output ] 
  >
  > which can be ( XOR'd ) with the message
  >
  > Encrypt the counter with the key and send it together with the cipher text

# Defining a Secure Cipher

### Claude Shannon defined much of digital logic in his thesis paper



### Random Variable

> A function mapping a sample space (Which is finite) into real numbers.
>
> ***P(x)*** = the probability of **x**
>
> ***X*** represents the **possible values** in p(x) 
>
> ***Example:*** 
>
> > **X** = alphabet
> >
> > ***X*** = {  H, T  }
> >
> > ​	P(H) = 1/2
> >
> > ​	P(T) = 1/2
>
> ##### Another Example:
>
> > **X** is a random variable representing the number of heads after 4 coins tosses
> >
> > > X = { 0, 1, 2, 3, 4 }
> > >
> > > P(x=0) = (1/2) * (1/2) * (1/2) * (1/2) = (1/16)
> >
> > What's the **probability of heads equals two?**
> >
> > > P(x = 2) = P(HHTT) + P(HTHT) + P(HHTT)
> >
> > What about **heads equals one?**
> >
> > > P(X = 1) = 4 * ( 1/2 * 1/2 * 1/2 * 1/2  )
> > >
> > > ​	       = ( 1/4 )

## Random Variables Pt. 2

> Prob[X=x] 
>
> denotes the probability of a random var X takin the value x
>
> Pr[ x,y ] is the probability that X takes value x and Y takes value y
>
> #### Pr[ X=x , Y=y ] :
>
> > X*Y = { (HH), (HT), (TH), (TT) }
> >
> > Pr[ X=H, Y=H ] = 1/2 * 1/2 = 1/4
>
> #### K = key space = { 0 , 1 }
>
> > P( K = k ) = ( 1 / |K| )
> >
> > M = message space = { 0 , 1 }^k
> >
> > ​	P( M = m )
>
> #### C = cipher text space --> ( C = c)

## Final definition of a secure cipher:

A cipher is perfectly secure if for any P(m), any 

**cipher text** C and any message M, we have:

> P( M = m | C = c ) = P( M = m )
