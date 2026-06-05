# 142857-base10-lens

The cyclic number 142857 = (10⁶−1)/7 has a cyclotomic factorization
whose surviving prime-power factor-blocks reconstruct the {n,k,r} = {7,4,3}
Hamming-family scaffold. The Hamming-family uniqueness condition singles
out r=3.

Repository: https://github.com/TheCosmicPattern/142857-base10-lens

## Known vs New

**Known:** 142857 is cyclic — multiplying by 1 through 6 rotates digits.

**New:** Its complete prime-power factorization reconstructs the {7,4,3}
scaffold, this alignment has a cyclotomic explanation, and the canonical-
base condition proves it unique to r=3.

## The finding

    142857 = 3³ × 11 × 13 × 37

Every factor-block is a scaffold expression:

| Factor-block | Value | Scaffold expression |
|-------------|-------|-------------------|
| 3³ | 27 | r³ |
| 11 | 11 | n + k |
| 13 | 13 | 2n − 1 |
| 37 | 37 | 2^k + n·r |

Combined: `142857 = r³(n+k)(2n−1)(2^k+nr)` with r=3, n=7, k=4, b=10=n+r.

## Notation

{n, k, r} is the Hamming-family scaffold: total length, data width, check
count. For r=3 this coincides with the conventional [7,4,3] code notation
because the minimum distance also equals 3.

## The proof

The cyclotomic condition Φ₂(b) = n+k requires 2^(r−1) = r+1, which has
unique positive integer solution r = 3. Two independent conditions from
Φ₆ and Φ₃ confirm. See `proof/PROOF.md` for full details.

Three distinct claims verified:
1. **Hamming-family uniqueness** — proved by the three conditions
2. **Base-10 null screen** — computed through p=47 (no other full-reptend
   prime's cyclic number passes the scaffold grammar test)
3. **Phi-prime inheritance** — when 6 divides the period, the primes
   {3, 7, 11, 13, 37} from Phi_1..Phi_6 propagate into all later cyclic
   numbers (with 7 absent only for p=7 where it is divided out). When 6
   does not divide the period, only {3, 11} survive.

## Verification

```bash
pip install -r requirements.txt
python3 verification/verify_all.py
```

Expected output: 8 sections, all PASS. Tests factorization, scaffold
grammar, cyclotomic structure, uniqueness conditions, formal grammar
null test, half-split arithmetic with Q=143 derivation, digit invariants,
and phi-prime inheritance (generalization to all cyclic numbers).

## Files

```
proof/PROOF.md          — main proof (Markdown)
proof/proof.tex         — proof (LaTeX, compiles to 4-page PDF)
verification/verify_all.py — full verification suite
docs/PROOF_EXTENDED.md  — extended proof with geometric reading
docs/SUBSTACK_DRAFT.md  — Substack post draft
docs/WRITEUP.txt        — plain-text writeup
docs/images/            — equation and diagram images
```

## Author

Vitex Probasco, University of Massachusetts Amherst (non-academic affiliate)
vitexprobasco@umass.edu

Background: Retired U.S. Army — 35F (All-Source Intelligence Analyst),
35Q (Cryptologic Network Warfare Specialist), 17C (Cyber Operations NCO)

Disclosure: AI tools used for organization and drafting due to a TBI
affecting working memory. All mathematical analysis, proofs, and
verification are the author's own work.

## License

CC-BY-4.0
