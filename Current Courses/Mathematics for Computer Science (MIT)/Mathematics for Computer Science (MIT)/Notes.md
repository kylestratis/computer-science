# MIT OCW 6.042 - Mathematics for CS

## Symbols
∀ - For all 
∈ - in the set of/is a member/element of 
N - the (set of) natural numbers: {0, 1, 2, 3, ...}
∃ - there exists
=> - implies (also →)
<=> - if and only if (iff)
∧ - and
¬ - not
V - or

## Lecture 1 - Introduction and Proofs
* **Proof** - a method for ascertaining the truth. 
Examples of ascertaining truth: Experimentation and observation; sampling and counterexamples; judge and juries; religion/word of God/word of your boss/professor said it (authority); inner conviction; "I don't see why it's not true" (transfers burden of proof to someone else). 

* **Mathematical proof** - a verification of proposition by a chain of logical deductions from a set of axioms. 
* **Proposition** - a statement that is either true or false. E.g. "2 + 3 = 5" - a true proposition. 
    - Another ex: '∀n∈N, n^2 + n + 41 is a prime number'.
* **Predicate** - a proposition whose truth depends on the value of a variable

So lets try:
n       n^2 + n + 41    Prime?
0           41          Y
1           43          Y
2           47          Y
3           53          Y
...
20          461         Y
...
39          1601        Y
First 40 values of n, the predicate is true. So first 40, so must be true, right? Wrong:

40^2 + 40 + 41 = 1681 = 41^2
Another example where not prime is 41, since every term is divisible by 41. 

Ex. a^4 + b^4 + c4 = d^4 has no positive integer solutions (proposition)
Conjectured to be true by Euler in 1769. Disproved by Noam Elkies 218 years later:
a = 95,800, b = 217,519, c = 414,569, d = 422,481

So correct true proposition:
∃ a, b, c, d ∈ N+, a^4 + b^4 + c^4 = d^4
N+: {1, 2, 3, ...}  |---predicate---------|

Ex. 313(x^3 + y^3) = z^3 has no positive integer solutions. Actualy false, but shortest, smallest counter-example has > 1000 digits. 
Factoring large integers is important - it's how to break cryptosystems like RSA. Because of that, RSA uses 1000-digit modulyses instead of hundred-digit like they used to. 

Main idea - don't try a few cases and assume it's done. 

Ex: the regions in any map can be colored in 4 colors so that adjacent regions have different colors - Four Color Theorem. 
Kempe was thought to have proved it, but he got to it by saying maps had to look like certain types. Proof by picture sucks. But Appel and Haken finally proved the theorem with a computer a hundred years later to use a computer to check thousands of cases. 

Another proposition:
Every even positive integer but 2 is the sum of 2 primes. E.g. 24 = 11 + 13
Nobody knows if this is true or false. Goldbach's conjecture. 

Another:
∀ n ∈ Z, n >= 2 => n^2 >= 4
Z: all integers - {0, 1, -1, 2, -2, ...}

**Implies** - an implication p implies q is said to be true if p is false or q is true. 
Truth table:
p | q | p => q | q => p | p <=> q
----------------------------------
T | T | T      |    T    |  T
T | F | F      |    T    |  F
F | T | T      |    F    |  F
F | F | T      |    T    |  T

"False implies anything could be true"
pigs fly => I'm king 
is T. Because pigs don't fly. 

Another example:
∀ n ∈ Z, n >= 2 <=> n^2 >= 4
False: n = -3, (-3)^2 >= 4
Iff means implication both ways: p => q AND q => p

**Axioms** - propositions that we assume to be true. 
e.g. If a = b and b = c, then a = c

Axioms can be contradictory in different contexts: In Euclidean geometry, there's a central axion that says given a line L and a point p not on L, there is exactly one line through p parallel to L. 
But in spherical gemoetry, there is an axiom that contradicts this - given a line L and a point p not on L, there is no line through p parallel to L on the sphere. 
But in hyperbolic geometry, there is an axiom that say given a line L and a point p not on L, there are infinitely many lines through p parallel to L. 

2 sort of guiding principles to axioms: axioms should be consistent and complete. 
Consistent - a set of axioms is consistent if no proposition can be proved to be both true and false
Complete: a set of axioms is said to be complete if it can be used to prove every proposition is either true or false. 

In the 1930s Kurt Godel proved it isn't possible that there exists any set of axioms that are both consistent and complete. 

## Symbols
∀ - For all 
∈ - in the set of/is a member/element of 
N - the (set of) natural numbers: {0, 1, 2, 3, ...}
∃ - there exists
=> - implies (also →)
<=> - if and only if (iff)
∧ - and
¬ - not
V - or
| - divides

## Lecture 2 - Induction
**Direct proof** - proof where you start with some axioms, have some theorems you know or proved along the way, and make logical deductions until you get to where you want to go. 
**Proof by contradiction** - and indirect proof; assume opposite of what you're trying to prove, then take steps for logiical deductions forward until you arrive at a contradiction, something where you prove false equals true.

So to prove proposition P is true, assume P is false (not P is true). Then use that hypothesis to derive a falsehood e.g. prove a falsehood is true. This is called deriving a contradiction. Therefore it must be that p is true. 

If  ¬P => F is true, then P = true

Ex. Thm: sqrt(2) is irrational. 
Hard to do directly. Easy with proof by contradition:

Pf (by contradiction):
    Assume for purpose of contradiction that sqrt(2) is rational (¬P => true).
    => sqrt(2) = a/b (fraction in lowest terms)
    => 2 = a^2/b^2
    => 2b^2 = a^2  [note: a^2 must be even because 2b^2 is even]
    => a is even (2 | a - 2 divides a)
    => 4 | a^2
    => 4 | 2b^2
    => 2 | b^2
    => b is even
    => a/b is NOT in lowest terms (because both are even)
    => contradiction (also #)
    => sqrt(2) is irrational. QED

**Induction axiom** - Let P(n) be a predicate. If P(0) is true and ∀n∈N (P(n) => P(n+1)) is true, then ∀n∈N P(n) is true.
i.e. If P(0), P(0)=>P(1), P(1)=>P(2), ..., then P(0), P(1), P(2)... are true. 

Simple proof using induction.
*Thm*: ∀n>=0, 1 + 2 + 3 + ... + n = n(n+1)/2
            Σ(i=0->n)i = Σ(1<=i<=n)i
            If n=1, 1 + 2 + ... + n = 1 (sum numbers from 1 to 1)
            If n<=0 1 + 2 + ... + n = 0
n = 4 -> 1 + 2 + 3 + 4 = 10 = 4(5)/2
*Proof* by induction.
        Let P(n) be proposition that Σ(i=1->n) = n(n+1)/2
        *Base case*: P(0) is true: Σ(i=1->0)i = 0 = 0(0+1)/2
        *Inductive step*: For n>=0, show P(n)=>P(n+1) is true
            Assume P(n) is true for purposes of induction (i.e., assume 1+2+...+n = n(n+1)/2), need to show 1+2+...+(n+1) = (n+1)(n+2)/2
            (It looks like we're assuming what we are trying to prove is true, but we are doing it in the context of establishing implication is true, then apply induction axiom to conclude P(n) is true for all n.)
            1 + 2 + ... + n + (n + 1)
            \ n(n+1)/2     / + n + 1 = (n^2 + n + 2n + 2)/2 = (n+1)(n+2)/2 QED
        ∀n>=0, Σ(i=0->n)i = n(n+1)/2

*Thm*: ∀n∈N 3|(n^3-n) (e.g. n=5 3|(125-5))
*Proof* by induction. 
        Let P(n) be 3|(n^3-n)
        *Base case*: n=0: 3|(0-0)
        *Inductive step*: For n>=0, show P(n)=>P(n+1) is T
        Assume P(n) is true, i.e. 3|(n^3-n)
        Examine (n+1)^3-(n+1) = n^3 + 3n^2 + 3n + 1 - (n+1)
                              = n^3 + 3n^2 + 2n -mult of 3? ??? 
                              Use assumption that n^3-n IS mult of 3 (key ot induction). Put -n in:
                              = n^3 - n + 3n^2 + 3n This is indeed a mult of 3, since we assume n^3-n is mult of 3, then other terms are obviously mult of 3. 
                              3|3n^2
                              3|3n
                              3|n^3-n by P(n)
3|((n+1)^3-(n+1)) QED

So general steps:   1. 'by induction'
                    2. Predicate
                    3. Base case
                    4. Inductive step

Don't have to use P(0) as base case - doesn't matter where you start in fact as long as you verify starting point and implication for all n at starting point and beyond
*Base case*: P(b) is true
*Inductive step*: ∀n >=b P(n)=>p(n+1)
*Conclude*: ∀n >=b P(n)

Do a false proof using induction:
*Thm (not!)* All horses are the same color. 
                This can't be inductive hypothesis - no n to plug number into
*Proof*: by induction
        Let P(n) In any set of n (where n>=1), the horses are all the same color
        *Base case*: P(1) - in any set of 1 horses, all horses in set are of same color. True - just one horse
        *Inductive step*: Assume P(n) is true. 
        Consider set of n+1 horses, call horses h1, h2, hn+1. What do I know about h1 to hn? They're same color because P(n) is true. 
        Also, what do we know about h2, h3, hn+1 - all the same color because they are a set of n horses. 
        Since (H1)=color,(H2...Hn) = color(Hn+1)
        => all are the same. QED

So what went wrong? "..." did! In particular, in case n=2. We didn't completely do all inductive steps. 
In inductive step, did we prove P(1) => P(2)? So I've got a set of 2 horses, h1, h2. Nothing in "...". Then h1 is the same color of itself. The next set becomes h2 (else where h2, h3, ..., hn). In base case, you have h1 and empty set. So the bridge in the inequality breaks ((H2...Hn = color(Hn+1))). 
We proved: P(1), P(2)=>P(3), P(3)=>P(4), etc.
We DID NOT prove: P(1)=>P(2)
**Be very careful that you establish all implications from base case. If you start with P(2), then the proof (almost) works -> in any set of n>=2 then all horses can be same color. But the base case of P(2) fails, so the proof doesn't totally work either. 

Next example will show how to prove there is a solution and help you get to it. 

2^n courtyard with donor statue. Architect insisted in L-tiles. Need to figure out how to do 2^n courtward with space for Bill statue. 

**Thm**: ∀n, ∃ a way to tile a 2^n x 2^n region with a center square missing (for Bill).
**Proof**: by induction.
    *P(n)* (pretty much whole thing in thm except "∀n")
    *Base case*: P(0) Yes - center square with no tiles (2^0 x 2^0)
    *Inductive step*: For n>=0, assume P(n) to verify IH.
            So we need to show P(n+1) is true. 
            Consider a 2^n+1 x 2^n_1 courtyard. Divide into 4 blocks that are 2^n x 2^n. You can take a corner out of each in the center, place an L-tyle there then the remaining space has space for Bill. *BUT* P(n) assumes Bill in the center of the 2^n region, so this isn't the proof. 
            So we are changing IH to say corner sq instead of center, now that works. Since Bill is now in the corner of 2^n AND 2^n+1. 
            Bill wants to be in the center, though! 
            Instead, it's easier to prove with *any* square missing, instead of center or corner. This is a stronger theorem. 
            Remember we are trying to show P(n)=>P(n+1). With corner, it moves, but with Bill anywhere, he doesn't move as size grows. Making the theorem harder can make proving it easier. Now we proved we can tile it and Bill can be anywhere, including the center like we wanted. 

Now: Recitation 2