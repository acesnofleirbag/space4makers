# Introduction

### Finity Deterministic Automatas

Are automatas where each state have a transition for another one state in all possible entrances of a given grammatical

### Finity Non-Deterministic Automatas

Are automatas where each state can have or not a transition for another state in all possible entrances of a given
grammatical

### Regular Operations

- Union

```
T(q, x) =

    T1(q, x) if q E Q1

    T2(q, x) if q E Q2
    
    {q1, q2} if q == q0 e x == {E}

    empty if q == q0 e x != {E}
```

A initial state is added outside of the set Q1/Q2 where given a {E} (epsilon) entrance/input have a transition for the
initial state of Q1 and Q2 at the same time. The processing happens on both and the chain of chars is accepted if the
processing results on a final state on Q1 or Q2

- Concatenation

```
T(q, x) =

    T1(q, x) if q E Q1 && q !E F1

    T1(q ,x) if q E F1 && x != {E}

    T1(q, x) U {q2} q E F1 && x == {E}

    T2(q, x) q E Q2
```

The processing on Q2 only happens after the processing in Q1, if and only if the Q1 processing results on a final state
and the current chain of chars is a {E} (epsilon). The chain of chars is accepted if the result of the processing on Q2
is equals a one final state

- Star

```
T(q, x) =

    T1(q, x) if q E Q1 && q !E F1

    T1(q, x) if q E F1 && x != {E}

    T1(q, x) U {q1} if q E F1 && x == {E}

    {q1} if q == q0 && x = {E}

    empty if q == q0 && x != {E} 
```

It's the same as `a*bc` on regex operators (1 or more == k >= 0 on the theorem)

### Compilers Theory

```
Regular grammar => Regular expression => Automatas => Lexer analyser => Free Context Grammar
```

> `->` derive symbol 

```
E -> E + T | T
T -> T * F | F
F -> (E) | a
```

### First

```
S -> A B
A -> aA | a
B -> bB | b

First(S) = {} U First(a) = {a}
First(A) = {a}
First(B) = {b}
```

### Follow

```
404 | Need to finish ...
```

