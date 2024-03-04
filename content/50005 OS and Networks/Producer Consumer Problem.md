# Producer Consumer Problem
---
An example of a situation in code that requires synchronisation due to [[Race Condition]]

## Precedence Constraints
- Producer cannot produce too much before consumer consumes (i.e. any new info got to wait before entering buffer, no Buffer Overflow)
- Consumer cannot consume before producer produces, need to make sure that not reading old value (i.e. no false start)

## Solution
(for **multiple** producer & consumer problem)
Binary semaphore and counting semaphore
- Binary semaphore is almost the same as Mutex Lock

Producer program:

```C
void send (char c){
   wait(space);
   wait(mutex_p);

   buf[in] = c;
   in = (in + 1)%N;

   signal(mutex_p);
   signal(chars);
}
```

Consumer program:

```c
char rcv(){
   char c;
   wait(chars);
   wait(mutex_c);

   c = buf[out];
   out = (out+1)%N;

   signal(mutex_c);
   signal(space);
}
```

#os