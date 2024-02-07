### Bassics
**Symbol**: a, b, c, d, ....\
**Alphabet**: collection of symbols {a, b} ; {c, d, a}\
**String**: Sequence of symbols {aa, bb, cc, ac, da}\
**Language**: Set of strings eg - L1 = set of all strings of length 2 {00, 11, 01, 10}

**Finite Automata**:
1. It's simplest model of computation
2. It as very limited memory

There are two types:
1. With Output
	1. Moore Machine
	2. Mealy Machine
2. Without Output
	1. DFA (Deterministic Finite Automata)
	2. NFA (Non-Deterministic Finite Automata)

## DFA:
	Given the current state we will know what the next state will be
	It as unique next state
	It as no choices and randomness
	It is simple and easy
It's defined by five tuples {Q, sigma, q0, F, del}\
Q - Set of all States\
Sigma - Inputs\
q0 - Start state / Initial state\
F - Set of final states\
delta - Transition function \

## Regular Expression
If finite state machine recognises the language then it's regular expression
	the language doesn't require memory
#### Operations
1. Union 
2. Concatenation
3. Star



## NDFA
	Given the current state there are multiple next states
	The next state is chosen at random or choose all next state in parallel
 
Its is also defined by the same five states as DFA

## Minimisation of DFA
Equivalence states


## Mealy Machine
It as six tuples {Q, sigma, delta, del, lamda, q0}\
Q - Finite set of all states\
Sigma - Finite non-empty set of input alphabets\
Delta - Set of Output Alphabets\
Del - Transition Function\
Lamda - Output function\
q0 - Initial state

## Moore Machine
Same of Mealy Machine with slight difference in output function

