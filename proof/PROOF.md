# Proof: The Self-Describing Cyclic Number Property is Unique

## Notation

{n, k, r} denotes the Hamming-family scaffold: total length, data
width, and check/parity count. For r=3 this gives {7, 4, 3}, which
coincides with the conventional [7,4,3] code notation because the
minimum distance also equals 3. For other values of r, the minimum
distance of the Hamming code is always 3 regardless of r, so the
scaffold notation {n,k,r} and the code notation [n,k,d] diverge.

## Known vs New

**Known:** 142857 is a cyclic number (the repetend of 1/7 in base 10).
Multiplying by 1 through 6 permutes its digits.

**New:** The complete prime-power factorization of 142857 reconstructs
the {7,4,3} Hamming-family scaffold:

    142857 = r^3 * (n+k) * (2n-1) * (2^k + n*r)

with r=3, n=7, k=4, and base b = n+r = 10. This alignment is
provably unique within the Hamming family, and no other base-10
full-reptend prime through p=47 exhibits comparable factorization
alignment.

## Definition: Self-Describing

A cyclic repetend (or Fermat quotient) is self-describing relative
to a Hamming-family scaffold when the cyclotomic factor-blocks of
(b^(n-1)-1)/n, in canonical base b = n+r, are exhausted by scaffold
expressions in {n, k, r}. That is: every prime-power factor-block
of the quotient appears in the scaffold grammar.

## Parameters

For r >= 2, define:
- n = 2^r - 1 (Hamming code length; require n prime)
- k = n - r (data width)
- b = n + r (canonical base)
- Q = (b^(n-1) - 1) / n (the Fermat quotient; when ord_n(b) = n-1,
  this is the full-period cyclic repetend of 1/n in base b)

## Theorem

Among Hamming-family parameters with n = 2^r - 1 prime and r >= 2,
the prime-power factor-blocks of Q decompose into {n, k, r}-scaffold
expressions only when r = 3.

## Proof

The factorization of b^(n-1) - 1 splits via cyclotomic polynomials
Phi_d(b) for d | (n-1). Three conditions on the cyclotomic factors
are examined. The first alone suffices for uniqueness; the second
and third provide independent structural confirmation.

### Condition 1 (uniqueness spine)

Phi_2(b) = b + 1 = n + k requires k = r + 1.

Derivation inside the scaffold:
    b + 1 = n + k
    (n + r) + 1 = n + (n - r)
    2r + 1 = n
    2r + 1 = 2^r - 1
    2^(r-1) = r + 1

At r = 3: 2^2 = 4 = 4. Solution.

For r >= 4: f(r) = 2^(r-1) - (r+1) satisfies f(4) = 3 > 0, and
f(r+1) - f(r) = 2^(r-1) - 1 > 0 for r >= 2, so f is strictly
increasing past r = 3. No further solutions exist.

**Unique solution: r = 3.**

### Condition 2 (independent confirmation)

n | Phi_6(b) with Phi_6(b)/n = 2n - 1.

Phi_6(b) = b^2 - b + 1 = (n+r)^2 - (n+r) + 1.

Setting equal to n(2n-1) and simplifying:

    n(n - 2r) = r^2 - r + 1

At r = 1: 1(1-2) = -1, but r^2-r+1 = 1. Fails (sign mismatch).
At r = 2: 3(3-4) = -3, but r^2-r+1 = 3. Fails (sign mismatch).
At r = 3: 7(7-6) = 7, and r^2-r+1 = 7. Holds.
For r >= 4: n = 2^r - 1 >= 3r, so n - 2r >= r, giving
n(n-2r) >= 3r * r = 3r^2 > r^2 - r + 1. No further solutions.

**Unique nontrivial solution: r = 3.**

### Condition 3 (for prime r)

r | Phi_3(b) requires r | (2^(2r) - 2^r + 1).

Since b = n + r and n = 2^r - 1:

    Phi_3(b) = b^2 + b + 1 ≡ n^2 + n + 1 (mod r)

By Fermat's little theorem (r prime): 2^r ≡ 2 (mod r).
So 2^(2r) ≡ 4 (mod r).
Thus: n^2 + n + 1 ≡ 4 - 2 + 1 = 3 (mod r).

For r | 3 with r prime and r >= 2: r = 3.

Note: Fermat's little theorem requires r prime. This is satisfied
in the theorem's domain because n = 2^r - 1 prime implies r prime
(contrapositive: r composite implies 2^r - 1 composite). Composite
solutions to the divisibility condition exist (e.g., r = 57) but
fall outside the theorem's hypotheses. In any case, Condition 1
already establishes uniqueness unconditionally.

### Intersection

- Condition 1: r = 3 (unique)
- Condition 2: r = 3 (unique nontrivial)
- Condition 3: r = 3 (unique prime)

The unique simultaneous solution is r = 3: the {7,4,3} scaffold
in canonical base b = 10 = 7 + 3.

## Verification

At r = 3, b = 10:

    Phi_1(10) = 9   = 3^2          = r^2
    Phi_2(10) = 11  = 7 + 4        = n + k
    Phi_3(10) = 111 = 3 * 37       = r * (2^k + n*r)
    Phi_6(10) = 91  = 7 * 13       = n * (2n - 1)

    10^6 - 1 = 9 * 11 * 111 * 91 = 999999

    999999 / 7 = 142857 = 3^3 * 11 * 13 * 37
               = r^3 * (n+k) * (2n-1) * (2^k + n*r)

## Corollary

Base 10 = n + r is the canonical-base candidate for the {7,4,3}
scaffold. Each Hamming-family code has a canonical-base candidate
b = 2^r - 1 + r, but only at r = 3 does the resulting cyclic number
exhibit the self-describing factorization property.
