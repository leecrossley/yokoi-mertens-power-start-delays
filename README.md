# How long a whole range of power averages can miss a Mertens crossing

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24412112.svg)](https://doi.org/10.5281/zenodo.24412112)

This result is now maintained in [quadratic-mertens-first-crossings](https://github.com/leecrossley/quadratic-mertens-first-crossings/tree/main/results/yokoi-mertens-power-start-delays). This repository is archived and keeps its releases and DOI.

Fix any interval of positive exponents, for example $1/2\le s\le20$. There are many Yokoi real quadratic fields in which every average with weight $(y/t)^s$ is positive at every real start from $2$ through $X$. Move the start to $4X$ and all those same averages are negative. The interval from $4X$ to $8X$ alone already gives a negative average for each exponent.

For a large discriminant cutoff $D$, the scale $X$ is $2^{\lfloor c\sqrt{\log D/\log\log D}\rfloor}$. It grows faster than every fixed power of $\log D$ and slower than every fixed positive power of $D$. The fields lie in $(D/2,D]$. Their actual prime-ideal Mertens products stay above the main term through $T$, which can be as large as $\exp(c'(\log D)^{1/5})$ up to dyadic rounding. Their first dips occur before $8X$.

The theorem gives a lower count of $\sqrt D\exp[-C((\log T)^4+\log X\log\log X)]$ such fields. The proof allows every real start through $X$ and every real exponent in the chosen interval. The theorem places the first raw crossing in $(T,8X)$ and does not exclude one before $X$. Other decreasing weights can detect a dip earlier. The universal polynomial starting-point question remains open. [Theorem and proof](PROOF.md) · [Prior work](PRIOR-WORK.md)

The proof uses a short, stronger bias in the splitting of primes to keep the raw product positive. A longer, weaker bias controls the averages. Reversing that bias in a final block makes them all negative at the same start. The field can already contain large numbers of both split and inert primes in every doubled interval above $(\log d)^4$ while these signs persist.

## Replaying the checks

Run the following with Python 3.10 or later in this directory.

~~~sh
shasum -a 256 -c SHA256SUMS
python3 -B check.py
~~~

The exact rational checks test asymmetric signed tilts, the weights of discarded products, a decomposition by prime ranks and summation by parts for full and capped power weights. The family theorem is a written analytic proof. Three supporting inequalities are checked in Lean. Set NOTE to this directory's absolute path and run the following from the pinned [Mathlib checkout](https://github.com/leanprover-community/mathlib4/tree/0df444a360eaa60ab8c11dca51a86af692955474) with the release toolchain.

~~~sh
lake env lean -R "$NOTE" "$NOTE/PowerDelays.lean"
~~~

[Exact arithmetic output](evidence/check.txt) · [Lean axiom report](evidence/lean.txt)
