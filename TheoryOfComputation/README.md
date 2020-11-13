# Theory of Computation

- It is about what kind of things we can really compute mechanically, how fast and how much space does it take to do so.
- What a machine does?
    ![A Machine designed with TOC](./images/machineBlockD.png)
- Levels in this Subject
    ![Levels in TOC](images/levelInSubject.png)
    - `FSM` : Finite State Machine
    - `CFL` : Context Free Language

## Finite State Machine

- **Symbol**
>  - Example: a,b,c,1,2,3...
- **Alphabet**
  - &Sigma; - Collection of Symbols 
>  - Example: {a,b}, {d,e,f,g}, {0,1,2}
- **String**
  - Sequence of Symbols
>  - Example: a,b,1,2,aa,bb,ab,ba
- **Language**
  - Set of strings
  - > Example: &Sigma; = {0,1}
  - > L1 = Set of all strings of length 2 = {00,11,01,10}
  - > L2 = Set of all strings of length 3 = {000, 001, 010, 011, 100, 101, 110, 111}
  - > L3 = Set of all strings that begin with 0 = {0,00,01,000,001,010,0000,......}

| Finite | Infinite |
|:--:|:--:|
| L1 and L2 | L3 |

### Powers of &Sigma;

Let Alphabet set be &Sigma; = {0,1}

&Sigma;<sup>0</sup> = Set of all strings of length 0
- &Sigma;<sup>0</sup> = { &straightepsilon; }

&Sigma;<sup>1</sup> = Set of all strings of length 1
- &Sigma;<sup>1</sup> = { 0,1 }

&Sigma;<sup>2</sup> = Set of all strings of length 2
- &Sigma;<sup>2</sup> = { 00,01,10,11 }

&Sigma;<sup>3</sup> = Set of all strings of length 3
- &Sigma;<sup>3</sup> = { 000, 001, 010, 011, 100, 101, 110, 111 }

&Sigma;<sup>n</sup> = Set of all strings of length n

### Cardinality

Numbers of Element in a set

For 2 alphabets, cardinality is 2<sup>n</sup>

&Sigma;<sup>\*</sup> = &Sigma;<sup>0</sup> &cup; &Sigma;<sup>1</sup> &cup; &Sigma;<sup>2</sup> &cup; .....

&Sigma;<sup>\*</sup> = { &straightepsilon; } &cup; {0,1} &cup; { 00,01,10,11 } &cup; ........
> Set of all possible strings of all lengths over {0,1} which is infinite &infin;

![FlowChart Finite Automata](images/flowchartFA.png)

**DFA** - Deterministic Finite Automata
- It is Simplest mode of communication
- It has very limited memory

( Q, &Sigma;, q<sub>0</sub>, F, &delta;)
- Q = Set of all states
- &Sigma; = Inputs
- q<sub>0</sub> = Start State/Initial State
- F = Set of Final states
- &delta; = Transition function Q &times; &Sigma; &rarr; Q

> Example of DFA:
> 
> ![DFA Example](images/DFA_I1.png)
> 
> - Q = {A, B, C, D}
> - &Sigma; = {0,1}
> - q<sub>0</sub> = A
> - F = {D}
> 
||**0**|**1**|
|:--:|:--:|:--:|
|**A**|C|B|
|**B**|D|A|
|**C**|A|D|
|**D**|B|C|

> **Example 1 of DFA**
> L1 = List of all strings that start with`0` = {0,00,01,001,010,011,000,...}
> ![DFA Example 1](images/DFA_E1.png)
> 
|||
|:--:|:--:|
|Q|{A,B,C}|
|&Sigma;|{0,1}|
|q<sub>0</sub>|A|
|F|{B}|
> Let's Verify
> 1. `001` ✔
> 
> ![Verify 1](./images/DFA_E1_01.png)
> 
> This String gets accepted because it reaches final state of the DFA which is B.
> 
> 2. `101` ❌
> 
> ![](images/DFA_E1_02.png)
> 
> This String does not get accepted because it does not reach final state.
