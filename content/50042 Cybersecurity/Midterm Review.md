# Midterm Review
---
q1. calculationss

get the number of asics that u can run: 10 ** 4
get search per second = (5 * 10 ** 8)  * (10  ** 4) = 5 * (10 ** 12)
get search per year = above * 3600  * 24 * 365
years to brute force = 2 ** 128 / above

part 2:
get search per second = 2 ** 128 / (3600 * 24)
fml need to log_2(y/5 ** 12 )

q2. hashy hashes fn
$f : \{0,1\}_{2n} -> \{0,1\}_{n}$
subscript = length
items in curly brackets = choices
- use the decryption function well when trying to find a collision in h $E^{-1}$

q3. cipher mode chaining
- Write out the statements, then replace the P with the C in the statement
- pi = ci XOR E(k,i-1)
- #todo: try to write out ciphertext decryptions for known cipher block methods on wikipedia

q4. more cipher mode chaining
- recall that the AES is 128 bit, and the 21st byte, means that it is starting from the (21 * 8 )th bit 

- pollard rho method?
#foc 