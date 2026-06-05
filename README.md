# 142857-base10-lens

The cyclic number 142857 = (10^6 - 1)/7 has a cyclotomic factorization
that decomposes into the parameters of the [7,4,3] binary Hamming code.
This decomposition is provably unique among all Hamming-family codes.

## The finding

    142857 = 3³ × 11 × 13 × 37
           = r³ × (n+k) × (2n-1) × (2^k + n·r)

where r=3, n=7, k=4 are the [7,4,3] Hamming code parameters
and base 10 = n + r.

## The proof

The identity Φ₂(b) = n + k requires 2^(r-1) = r + 1, which has
unique positive integer solution r = 3. Two independent conditions
from other cyclotomic factors confirm uniqueness. See `proof/PROOF.md`.

## Verification

```bash
pip install sympy
python3 verification/verify_all.py
```

This checks every claim: factorization, Hamming decomposition,
cyclotomic structure, all three uniqueness conditions, the null
test through p=47, half-split arithmetic, and digit invariants.

## Null test

No other full-reptend prime through p=47 produces a cyclic number
whose prime factors decompose into its own structural parameters.
31 = 2^5 - 1 (next Mersenne-prime Hamming length) is not even
full-reptend in base 10 (period 15, not 30).

## Author

Vitex Probasco, University of Massachusetts Amherst (non-academic affiliate)
vitexprobasco@umass.edu

Background: Retired U.S. Army — 35F (All-Source Intelligence Analyst),
35Q (Cryptologic Network Warfare Specialist), 17C (Cyber Operations NCO)

## License

CC-BY-4.0
