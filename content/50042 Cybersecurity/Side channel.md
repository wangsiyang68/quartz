# Side Channel Attacks
---
## Physical Attack
At **ATMs**: 
1. Skimmers (to read magnetic data), key pad overlays, pinhole cameras
2. ATM relay Attack > Similar to OCBC scam, but now the fake website is a fake ATM 

At **cars**:
Context: Cars with remote fobs usually send out challenges, and if the key fob is nearby, then car can be unlocked

Attack: (**Range Extension Attack**) Create a relay of signal extenders to extend the range to up to 100m, so that the car can be unlocked even though the key owner is not nearby

Solution: Require key owner to press key OR distance bounding protocol; measure the time taken from signal to emit to receive; do not open door if key is far away
Problem: timing is too fast/short to calculate the distance correctly

## Actually side channel attacks
Types:
1. Power Monitoring attack
2. Timing attack
	1. Based on measuring how much time various computations take to perform
	2. Idea: setup the cache properly
3. Electromagnetic
4. Audio side channels
5. Optical side channels
6. Other types

**Measure power consumption**
Context: Credit card store the secret key, which is then used to perform some operations (RSA, modular exponentiation via square and multiply)
- Key idea: power signature/consumption of square and multiply are different
	- Multiply consume more power than square because square is just bit shifting
	- a low followed by a high indicates 1 (since you squared and multiply)
	- just a low followed by another low indicates two 1s
Fix: make sure power consumption for all operations uniform/random

**Measure time taken to access data** (in cache)
Implementations: Meltdown/Spectre
- Key ideas: Speculative execution and cache side channel attack 
1. Speculative execution relies on a branch predictor: it thinks that if statement will probably be true based on prior history
2. Will run the statements in if block and preemptively store them in the cache so that faster to retrieve answer if the if statement is true

Some implementation side key ideas:
- k (secret byte) is assumed to be always in cache because it is an important system value that needs to be read (...password for eg?)
	- Therefore getting k in step 2 is fast
- 4096 is because usually computers will load a bunch of stuff from cache at one go, instead of just one byte by one byte
	- Therefore, attack code loads the the (k * 4096)th item into the cache 
	- Then later, we will iterate over i to find the (i * 4096)th item into the cache. When the response is fast, we will be able to deduce that `i == k`

Fix:
- Cache replacement policy: dont make it Least Recently Used, which makes it harder/less reliable to evict `array1_size` and `array2[]`
- Add some random delay from cache response so that it is difficult to tell the short cache response time
#foc 