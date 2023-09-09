---
title: "Interesting DFA"
date: 2023-08-30T13:10:06-05:00
draft: false
math: true
tags: ["CS 374"]
---

### Deterministic Finite Automaition

Definition: $(Q, s, A, \delta)$

$Q$: A set of all the possible state.

$s \in Q$ : starting state. The state to start the machine. 

$A \subseteq Q$: The set of states we accept. Return "good" when we end there. 

$\delta$: A function $Q \times \Sigma \rightarrow Q$. The set of all transition functions.

---



There is an interesting DFA design question. The question is as follows:

**Given a bit-string (a string that contains only 0s and 1s), design a DFA that accepts the string if and only if the number represented by the string is divisible by 5.**

Initially, I was thinking of the trailing bits of the binary representation. However, there are too many states to consider. A better way of constructing the states of this machine is to consider the reminders. By doing this, it only uses 5 states --- it worth a try. So, I tried to write out the binary numbers and tried to design the transition functions for simple cases. It turns out that the result works well.

![dfa machine](../myimg/dfa/dfa.png)

I also wrote a short python script for verifying this:

```python
# verifying dfa
# for this specific task, we need to use DFA to determine wheter the incomming bit string can be divible by 5. 

# The general definition of a DFA is: 
# M = (Q, q0, A, S)
# Q is a finite set of states
# q0 is the start state
# A is a set of accepting states
# delta is a transition function that takes a state and an input symbol and returns a state

# also consider the alphabet sigma, we can use this to generate random inputs
sigma = [0, 1] # this is the alphabet.

# We need to define the machine, and then we can verify it
Q = [0, 1, 2, 3, 4]
q0 = 0
A = [0]

# represent the transition function as a dictionary
# the key is a tuple of (state, input symbol)
# the value is the next state
# the size of this dictionay == |Q| * |sigma|

delta = {
    (0, 0): 0,
    (0, 1): 1,
    (1, 0): 2, 
    (1, 1): 3,
    (2, 0): 4,
    (2, 1): 0,
    (3, 0): 1,
    (3, 1): 2,
    (4, 0): 3,
    (4, 1): 4
}


# now we can write a function to verify the DFA
# we assume that the given dfa is an tuple of (Q, q0, A, S)
def verify_dfa(dfa, input_string):
    # first we need to check if the input_string is valid
    for c in input_string:
        if (int)(c) not in sigma:
            return False
    
    # start the verification
    current_state = dfa[1]
    for c in input_string:
        current_state = dfa[3][(current_state, (int)(c))]  # looking up the dict for the next state 

    if current_state in dfa[2]:
        return True
    return False
# end of verify_dfa


# now we can test the function
dfa = (Q, q0, A, delta)

import random

# randomly generate strings of length less than length l
test_num = 100
l = 10

result = True
for _ in range(test_num):
    length = random.randint(1, l)
    input_string = ''
    for _ in range(length):
        input_string += str(random.randint(0, 1))

    if (int(input_string, 2) % 5 == 0) != verify_dfa(dfa, input_string):
        result = False
        break
    # print in the order: dfa result, actual resultinput string in decimal, seperated by tab

    # print(verify_dfa(dfa, input_string), end='\t')
    # print(int(input_string, 2) % 5 == 0, end='\t')
    # print(int(input_string, 2), end='\n')
# end of for

print(f"tested {test_num} times with bit string of length less than {l}, ", end="")
if result:
    print("the DFA is correct!")
else:
    print("the DFA is not correct!")

```

