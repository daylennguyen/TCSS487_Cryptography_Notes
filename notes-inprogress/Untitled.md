# Cryptography Apri 6th 2018



## Advance Encryption Standard (AES)

> - New federal standard as of 2001
>
> - Based on the Rijndael algorithm
>
> - 128-bit blocks, keys can be 128, 192 or 256 bit
>
> - unlike DES, does not use Feistel structure
>
>    - The entire block is processed during each round
>
>  -  Design uses some very clever math
>
>      - See section 8.5 of the text for a concise summary
>
>     ## Basic Structure of Rijndael
>
>     > 128-bit plain text (arranged as 4x4 array of 8-bit bytes)
>     >
>     > which is then XOR'd with a 128-bit key
>     >
>     > then sent to a substitution table to shuffle the array (16x16 sub table)
>     >
>     > which the has its resulting rows shifted
>     >
>     > ​	- (1st unchanged  2nd left by 1, 3rd left by 2)