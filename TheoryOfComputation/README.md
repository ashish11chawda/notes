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

- It is Simplest mode of communication
- It has very limited memory

**DFA** - Deterministic Finite Automata

Every DFA can be defined using 5 tuples: ( Q, &Sigma;, q<sub>0</sub>, F, &delta;)
- Q = Set of all states
- &Sigma; = Inputs
- q<sub>0</sub> = Start State/Initial State
- F = Set of Final states
- &delta; = Transition function that maps Q &times; &Sigma; &rarr; Q

> Example of DFA:
> 
> ![DFA Illustration](images/DFA_I1.png)
> 
> - The letters A,B,C,D inside circles are states
> - The arrows or edges are transitions from one state to another
> - `A` is the initial state so the extra start arrow
> - `D` is the final state so the double circle
> ---
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

**Example 1 of DFA**
L1 = List of all strings that start with`0` = {0,00,01,001,010,011,000,...}

This is a infinite set.

![DFA Example 1](images/DFA_E1.png)

|||
|:--:|:--:|
|Q|{A,B,C}|
|&Sigma;|{0,1}|
|q<sub>0</sub>|A|
|F|{B}|
Let's Verify
1. `001` ✔

![Verify 1](./images/DFA_E1_01.png)

This String gets accepted because it reaches final state of the DFA which is B.

---
2. `101` ❌

![](images/DFA_E1_02.png)

This String does not get accepted because it does not reach final state.

**Example 2 of DFA**

Construct a DFA that accepts sets of all strings over {0,1} of length 2.
- &Sigma; = {0,1}
- L = {00,01,10,11}
![DFA Example 2](images/DFA_E2.png)

|||
|:--:|:--:|
|Q|{A,B,C,D}|
|&Sigma;|{0,1}|
|q<sub>0</sub>|A|
|F|{c}|
Let's Verify
1. `00` ✔

![Verify 1](./images/DFA_E2_01.png)

This String gets accepted because it reaches final state of the DFA which is C.

---
2. `10` ✔

![](images/DFA_E2_02.png)

This String gets accepted because it reaches final state of the DFA which is C.

---
3. `001` ❌

![](images/DFA_E2_03.png)

This String does not get accepted because it does not reach final state.

---
4. `1` ❌

![](images/DFA_E2_04.png)
 
This String does not get accepted because it does not reach final state.

**Example 3 of DFA**
Construct a DFA that accepts any strings over {a,b} that does not contain the string `aabb` in it
 
&Sigma; = {a,b}

Let's Simplify our problem by designing a DFA which accepts all strings that contains `aabb` in it.
 
![DFA Example 3](images/DFA_E3_01.png)

> **Flip the states**
> - Make the final states into non final states
> - Make the non-final states into final states

After flipping the states we get our required DFA.

![DFA Example 3](images/DFA_E3.png)

**Example 4 of DFA**

Figure out what the following DFA does:

![DFA Example 4](images/DFA_E4.png)

Accepted Strings:
- 10
- 111...10
- 01

L = {Accepts the string `01` or a string of atleast `1` followed by a `0`}

After reaching at a state if there isn't any place to go, then that string goes to a dead state.

So, complete DFA is follows:

![DFA Example 3](images/DFA_E4_01.png)

### Regular Language

A language is said to be a Regular Language if and only if some Finite state Machine recognizes it.

A Non-regular language is
- not recognised by any FSM
- which require memory
  - Memory of FSM is limited
  - It can't store or count strings

Example of Non-regular Language:
- `ababbababb` : repeating string `ababb`
- a<sup>n</sup> b<sup>n</sup> : aaabbb or aaaabbbb

#### Operations on Regular Languages

1. Union
   - A &Union; B = { x | x &isin; A or x &isin; B }

2. Concatenation
   - A &#x2218; B = {xy | x &isin; A and y &isin; B }

3. Star
   - A<sup>\*</sup> = {x<sub>1</sub>,x<sub>2</sub>,x<sub>3</sub>.........x<sub>n</sub> | k &ge; 0 and each x<sub>i</sub> &isin; A }

**Example on Regular Language Operations:**

A = {pq, r}

B = {t, uv}

A &cup; B = {pq, r, t, uv}

A &#x2218; B = {pqt, pquv, rt, ruv}

A<sup>\*</sup> = { &straightepsilon;, pq, r, pqr, rpq, pqpq, rr, pqpqpq, rrr, ....... }

> **Theorem 1:** The class of Regular Languages is closed under Union.

> **Theorem 2:** The class of Regular Languages is closed under Concatenation.

> The union of two regular language is a regular language and concatenation of two regular language is a regular language.