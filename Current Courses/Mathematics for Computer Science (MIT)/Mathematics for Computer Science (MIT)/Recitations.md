# Recitations

# Recitation 1
1.
    Notes: to prove P=>Q assume that P is true and prove that Q is also true
           Don't assume implication is true
    i. There is x, y, z, x is not y and x is not z and y is not z and x, y, z are in cabal).

    ii. Stav and David are NOT both in the cabal. At least one of Stav and David is not in cabal. 

    iii. If Martyna or Patrice is in cabal, then everyone is.
        Left side is definitely false, so right is false.

    iv. If Stav is in cabal, then David is as well. 

    v. If Darren is in cabal, then Martyna is also. 

    vi. If either of Oscar or Nick is in cabal, then Tom is not. If Tom is in cabal, then neither Oscar nor Nick is. 

    vii. If either of Oscar or David is in cabal, then Marten is not. If Marten is in cabal, then neither Oscar nor David is. 
           
So who is in cabal? 
3 people
Oscar
~~Stav~~ (iv via ii - see truth table for why it's Stav - the implication is false here)
~~Darren~~ (v via iii)
~~Patrice~~ (iii)
David (in)
Nick
~~Martyna~~ (iii)
~~Marten~~ (vii)
~~Tom~~ (vi)

Oscar, David, Nick. 

# Recitation 2
1. Geometric sum

First use well ordering principle, then induction, to prove that following formula is correct for all real values r != 1:
1 + r + r^2 + r^3 + ... + r^n = (1 - r^(n+1))/(1 - r)
**Proof by Well-Ordering**
*Proof* By contradiction, using Well-Ordering Principle. Assume theorem is false. Some nonnegative ints serve as counterexamples, collect in set C ::== {n∈N|1 + r + r^2 + ... + r^n != (1-r^(n+1))/(1-r)}. By our assumption, C is a nonempty set of non-negative integers. So, by WOP, C has a minimum element, say c. This would be smallest counterexample. Since c is smalles counterexample, we know that the formula is false for n = c but true for all nonnegative ints n < c. But formula is true for n = 0 since 1 = (1-r(0+1))/(1-r). Hence c > 0. This means c-1 is nonnegative and since it is less than c, formula is true for c - 1: 
1 + r + r^2 + r^3 + ... + r^(c-1) = (1-r^c)/(1-r)
But add r^c to both sides:
1 + r + r^2 + r^3 + ... + r^(c-1) + r^c = (1 - r^(c+1))/(1-r)
Which means that the formula does hold for c after all. This is a contradiction, we are done. 


*P(n)*: 1 + r + r^2 + r^3 + ... + r^n = (1 - r^(n+1))/(1 - r)
*Base case*: P(0) = 1 = 1-r/1-r
*Proof*: By induction, assume P(n) true. Then P(n+1):
        1 + r + r^2 + ... + r^n + r^(n+1) = (1 - r^(n+2))/(1 - r)
This proves that P(n+1) is also true, so P(n)=>P(n+1) for all n ∈ N. By induction, P(n) is true for all n∈N. 

2. Surveyevor

No red-eyed contestant should ever leave island. 

Thm 1. All purple-eyed people leave island on day p. 
*Proof*: Induction. 
*P(n)*: 1. If p > n, then all purple-eyed people survive the day.
      2. If p = n, then all purple-eyed people leave the island.
      3. If p < n, then all purple-eyed people are already gone.
*Base case*: We must verify that the three parts of P(n) hold on day n = 1. 