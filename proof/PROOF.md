# Proof: The Self-Describing Cyclic Number Property is Unique to Width 7 in Base 10

## Theorem

Let r >= 2, n = 2^r - 1 prime, k = n - r, and b = n + r. The cyclic number
C = (b^(n-1) - 1) / n has all prime-power factor-blocks expressible as
low-complexity combinations of {n, k, r} only when r = 3.

At r = 3: n = 7, k = 4, b = 10, and C = 142857 = r^3 (n+k)(2n-1)(2^k + nr).

## Setup

b^(n-1) - 1 factors via cyclotomic polynomials Phi_d(b) for d | (n-1).
Three conditions must hold simultaneously for the factor-blocks to
decompose into {n,k,r}-expressions.

## Condition 1 (uniqueness spine)

Phi_2(b) = b + 1 = n + k requires k = r + 1.

Since k = 2^r - 1 - r:

    2^r - 1 - r = r + 1
    2^(r-1) = r + 1

At r = 3: 2^2 = 4 = 4. Solution.

For r >= 4: 2^(r-1) >= 8 > r + 1. Exponential exceeds linear permanently.
Proof by induction: if 2^(r-1) > r + 1, then 2^r = 2 * 2^(r-1) > 2(r+1) > (r+1) + 1.

**Unique solution: r = 3.** This condition alone establishes uniqueness.

## Condition 2 (independent confirmation)

n | Phi_6(b) with Phi_6(b)/n = 2n - 1.

Phi_6(b) = b^2 - b + 1 = (n+r)^2 - (n+r) + 1.

Setting equal to n(2n-1) and simplifying:

    n(n - 2r) = r^2 - r + 1

At r = 1: n(n-2) = 1(1-2) = -1, but r^2-r+1 = 1. Fails (sign).
At r = 2: n(n-4) = 3(3-4) = -3, but r^2-r+1 = 3. Fails (sign).
At r = 3: n(n-6) = 7(7-6) = 7, and r^2-r+1 = 7. Holds.
For r >= 4: exponential growth of n = 2^r - 1 makes LHS much larger than RHS.

**Unique nontrivial solution: r = 3.**

## Condition 3 (for prime r)

r | Phi_3(b) requires r | (2^(2r) - 2^r + 1).

Since b = n + r and n = 2^r - 1:

    Phi_3(b) = b^2 + b + 1 ≡ n^2 + n + 1 (mod r)

By Fermat's little theorem (r prime): 2^r ≡ 2 (mod r).
So 2^(2r) ≡ 4 (mod r).
Thus: n^2 + n + 1 ≡ 4 - 2 + 1 = 3 (mod r).

For r | 3 with r prime: r = 3.

Note: this argument requires r prime. Composite solutions exist (e.g., r = 57).
Condition 1 already establishes uniqueness regardless.

**Unique prime solution: r = 3.**

## Intersection

- Condition 1: r = 3 (unique)
- Condition 2: r = 3 (unique nontrivial)
- Condition 3: r = 3 (unique prime)

The unique simultaneous solution is r = 3: the [7,4,3] Hamming code
in base 10 = 7 + 3.

## Verification

At r = 3, b = 10:

    Phi_1(10) = 9 = 3^2
    Phi_2(10) = 11 = 7 + 4
    Phi_3(10) = 111 = 3 * 37 = 3 * (2^4 + 7*3)
    Phi_6(10) = 91 = 7 * 13 = 7 * (2*7 - 1)

    10^6 - 1 = 9 * 11 * 111 * 91 = 999999

    999999 / 7 = 142857 = 3^3 * 11 * 13 * 37
               = r^3 * (n+k) * (2n-1) * (2^k + n*r)

## Corollary

Base 10 = n + r is the canonical base for the [7,4,3] code. Each
perfect binary code [2^r-1, 2^r-1-r, r] has canonical base b = n + r.
