# Six-Bites # 
Cateogry: Cryptography  
Difficulty: Easy  
Challenge Author: KNOXDEV  
Team: OsirisProtocol (https://ctftime.org/team/151343/#.Ynh0zJJAj_s.link)

**Challenge Prompt** 

My friend sent me the flag, but its encrypted! I heard them yell something about six bites...but I don’t understand what they mean! Can you decrypt the flag?  

**Ciphertext:** kwsbqhS}_aYLH_!WYg+kDIV0yp[k

## First Steps ##  

This challenge should arguably be a walk in the park for a CTF junkie and utilizes the common theme of known plain text attacks and xors. For a newbie, this challenge presents a unique obstacle - how to determine what encryption was used. We can utilize the hint (and maybe a bit of luck) to understand that the 6 bytes will likely be used in a key. Having rudimentary knowledge of ciphers helps solve this challenge - however, we can guess based on a key that we will use some form of stream cipher in this case XOR. 

## What is XOR ## 

EXclusive OR (XOR) - also known as exclusive disjunction - is a form of cipher where the bitwise xor operator is used applied byte by byte between a key and the plain text to create the ciphertext or between the ciphertext and the key to produce the plain text. 

The XOR function follows the following rules that are helpful to understanding the logic of this challenge: 

A XOR A = 0 
A XOR 0 = A       
A XOR B = B XOR A (Commutative Property)
(A XOR B) XOR C = A XOR (B XOR C) (Associative Property)


For us let's define: 

Ciphertext = PlainText XOR Key


## The XOR Vulnerability ## 

XOR in theory is super secure if:
  1. A unknown random key is used 
  2. No parts of the text are known

We know this is a flag so we can abuse that information to get what we want. Let's recall our formula: Ciphertext = Plaintext XOR Key. We will make use of the **Known Plain Text** attack model.  We know that PlainText XOR CipherText = Key (See Proof At End) 

## Applying Known PlainText ##

Recall that the flag format is sdctf{ (this is 6 bytes which should act as another hint). 

Now let's apply Plaintext XOR CipherText = Key to find the flag. Here is an example of how this works with our first value:  

Plaintext: s (Binary: 01110011) 	
Ciphertext: k (Binary: 01101011) 

01110011 XOR  
01101011  
\-------------
00011000 (Hex: 18) 

We got the first part of the key. We can apply this same process to the next 5 bytes or use some more high-tech tooling.

## Obtaining The Key With Some Neat Tools ##

Cyberchef is a phenomenal tool if you have not already used it before. Let's set up our recipe to use "XOR Brute Force". In the input box, we will put the first character (k). In the XOR Brute Force make sure the key length is set to 1 and the crib is set to the known-plaintext of s. The recipe returns:  

Key = 18: s
Key = 38: S

Select 18 because the flag format is lowercase. Repeat this process with the next 5 bytes to get the key. 

Key = 18 13 10 16 17 13

## Solving The Cipher ##

Finally, take the key and ciphertext to get the plaintext. Using CyberChef use XOR with the key 18 13 10 16 17 13 and the input as the ciphertext kwsbqhS}_aYLH_!WYg+kDIV0yp[k

This gives: **sdctf{KnOwN_PL1ANt3xT_A#acK}** and problem solved. 


## Proof Of PlainText XOR CipherText = Key ##

Recall PlainText XOR Key = CipherText  
Let Plaintext = A Key = B and CipherText = C 

Therefore: A XOR B = C 

XOR A by both sides (Since both sides are equal the result is the same): A XOR (A XOR B) = A XOR C 

Apply Associative Property: (A XOR A) XOR B = A XOR C 

Apply A XOR A = 0: 0 XOR B = A XOR C 

Simplify 0 XOR B: B = A XOR C (This is because bitwise 0 XOR 0 is 0 and 0 XOR 1 is 1 therefore as a 0 XOR B is B). 

Finally, replace the values: Key = Plaintext XOR CipherText. 
