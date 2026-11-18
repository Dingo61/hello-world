# Euler's Prime-Generating Polynomial

### Forty primes, one beautiful formula, and one very predictable disaster

> *The universe may be complicated, but sometimes it can be fooled by a quadratic.*

A companion to **`FortyTwo.md`** and our growing museum of questionable programming decisions.

---

## 1. The remarkable discovery

Around **1772**, mathematician **Leonhard Euler** observed that the polynomial

\[
\boxed{f(n)=n^2+n+41}
\]

produces **40 distinct prime numbers** for consecutive integer inputs `n = 0, 1, ..., 39`.

A **prime number** is an integer greater than 1 whose only positive divisors are 1 and itself.

**Important distinction:** Euler's formula does **not** produce the *first* 40 primes. It produces **40 prime-valued outputs in a row**.

| n | f(n) | Prime? |
|---:|---:|:---:|
| 0 | 41 | ✅ |
| 1 | 43 | ✅ |
| 2 | 47 | ✅ |
| 3 | 53 | ✅ |
| 4 | 61 | ✅ |
| 5 | 71 | ✅ |
| 6 | 83 | ✅ |
| 7 | 97 | ✅ |
| 8 | 113 | ✅ |
| 9 | 131 | ✅ |
| 10 | 151 | ✅ |
| 20 | 461 | ✅ |
| 30 | 971 | ✅ |
| 39 | 1601 | ✅ |
| **40** | **1681 = 41 × 41** | **❌** |
| 41 | 1763 = 41 × 43 | ❌ |
| **42** | **1847** | **✅** |

Yes, **n = 42 generates another prime**. The *unbroken run* ends at 40, not the ability of the polynomial to produce primes ever again.

---

## 2. The spectacular failure at n = 40

At the next input:

\[
f(40)=40^2+40+41=1600+40+41=1681=41^2.
\]

So `1681` is composite. This is not a random glitch: the formula has 41 built into it.

At `n = 41`:

\[
f(41)=41^2+41+41=41\times43=1763.
\]

More generally, replace `n` with `41k`:

\[
f(41k)=(41k)^2+41k+41=41(41k^2+k+1).
\]

For any positive integer `k`, both factors are greater than one. **Every positive multiple of 41 is guaranteed to give a composite output.**

> **Geologist:** Forty drill holes hit ore. The trend is undeniable.  
> **Mining engineer:** Drill hole 41.  
> **Geologist:** I'd rather not.

---

## 3. Can *any* integer polynomial generate primes forever?

**Not a nonconstant polynomial with integer coefficients, for every nonnegative integer input.**

Here's the general idea. Suppose an integer polynomial `P(n)` produces a prime `p` at some integer `a`, so `P(a) = p`. For every integer `k`, polynomial arithmetic guarantees:

\[
P(a+kp)\equiv P(a)\equiv0\pmod p.
\]

In other words, `P(a+kp)` is divisible by `p`. Because a nonconstant polynomial eventually grows in absolute value, there are inputs for which its output has absolute value greater than `p`; those outputs cannot be prime.

This argument assumes the usual definition of a **positive prime**. A constant polynomial such as `P(n) = 41` is the obvious exception, but doesn't generate new primes.

---

## 4. Python: investigate Euler's polynomial

Paste this into `euler_primes.py` and run it. No third-party packages are required.

```python
from math import isqrt


def euler(n: int) -> int:
    return n * n + n + 41


def is_prime(value: int) -> bool:
    if value < 2:
        return False
    for divisor in range(2, isqrt(value) + 1):
        if value % divisor == 0:
            return False
    return True


for n in range(51):
    value = euler(n)
    status = "PRIME" if is_prime(value) else "COMPOSITE"
    print(f"n={n:2d}  f(n)={value:5d}  {status}")
```

Some interesting lines near the boundary:

```text
n=38  f(n)= 1523  PRIME
n=39  f(n)= 1601  PRIME
n=40  f(n)= 1681  COMPOSITE
n=41  f(n)= 1763  COMPOSITE
n=42  f(n)= 1847  PRIME
n=43  f(n)= 1933  COMPOSITE
n=44  f(n)= 2021  COMPOSITE
n=45  f(n)= 2111  PRIME
```

**Experiment:** Change `range(51)` to `range(1000)`. Count how many outputs are prime. The polynomial keeps producing primes, just not consecutively.

---

## 5. T-SQL: Euler meets SQL Server

Because no mathematical curiosity is complete until it's been put into a query.

```sql
-- SQL Server 2019+
WITH Numbers AS (
    SELECT 0 AS n
    UNION ALL
    SELECT n + 1
    FROM Numbers
    WHERE n < 50
)
SELECT
    n,
    n * n + n + 41 AS EulerValue,
    CASE
        WHEN n = 40 THEN '41 squared: composite'
        WHEN n = 41 THEN '41 x 43: composite'
        WHEN n BETWEEN 0 AND 39 THEN 'prime'
        WHEN n = 42 THEN 'prime again!'
        ELSE 'not checked here'
    END AS Observation
FROM Numbers
OPTION (MAXRECURSION 100);
```

**Warning:** The `CASE` expression is a **label for known examples**, not a general primality test. SQL Server does not have a built-in `IS_PRIME()` function.

> **DBA:** Should this be a persisted computed column?  
> **Euler:** I have been dead for centuries and still cannot escape change control.

---

## 6. FORTRAN 77: the original engineer approves

Fixed-form FORTRAN 77: statements start in column 7.

```fortran
      PROGRAM EULER
      INTEGER N, VALUE
      DO 100 N = 0, 42
         VALUE = N*N + N + 41
         PRINT *, N, VALUE
  100 CONTINUE
      END
```

Forty consecutive primes, followed by a nasty surprise. No package manager required.

---

## 7. The 80-prime trick

Another famous polynomial is:

\[
\boxed{g(n)=n^2-79n+1601.}
\]

It produces a prime output for **80 consecutive inputs**, `n = 0, 1, ..., 79`. But there is a trick:

\[
g(n)=f(n-40).
\]

And Euler's original polynomial has the symmetry:

\[
f(-n-1)=f(n).
\]

Therefore, the 80 outputs consist of **the same 40 primes, each appearing twice**. The longer streak doesn't produce 80 distinct primes.

> An excellent way to double your reported intercepts without drilling another hole. Not recommended in a JORC report.

---

## 8. Why 41? Meet 163

The quadratic's discriminant is:

\[
\Delta=b^2-4ac=1-4(41)=\boxed{-163}.
\]

The positive number **163** is a **Heegner number**, a special number in algebraic number theory. That connection helps explain why Euler's formula has such an unusually long prime-producing streak.

It also appears in a remarkable near-integer:

\[
e^{\pi\sqrt{163}}\approx 262537412640768743.99999999999925\ldots
\]

So the value is extraordinarily close to the integer

`262537412640768744`.

**Important:** It is *not* exactly an integer. This is a deep mathematical phenomenon, not evidence of cosmic intervention (or Deep Thought doing overtime).

For readers who want to explore further, look up **Heegner numbers**, **class number one**, and **Ramanujan's constant**.

---

## 9. The Hitchhiker's Guide crossover

Euler gives:

```text
f(0) = 41
f(1) = 43
```

And precisely between those **twin primes** sits:

```text
               42
    The Answer to Life,
 the Universe, and Everything
```

At input `n = 42`, Euler returns the prime `1847`, because apparently the answer to the Ultimate Question is another question.

This is a playful coincidence, **not** a claim Douglas Adams based 42 on Euler's polynomial.

---

## 10. Engineering lessons from a mathematical curiosity

1. **Patterns are not proofs.** Forty successful tests don't establish a law for all inputs.
2. **Check the edge cases.** The next input, `n = 40`, tells the most interesting story.
3. **Understand the mechanism.** Factoring the polynomial explains where failures must occur.
4. **Separate correctness from coincidence.** A prime at `n = 42` doesn't restore the original streak.
5. **Check the question.** Producing 40 consecutive prime values is different from producing the first 40 primes.

> *If the model looks perfect, investigate what happens one block beyond the boundary.*

---

## References and further reading

- Heffernan, Lord et al., **“Euler's prime-producing polynomial revisited”**, *The Mathematical Gazette*: https://www.cambridge.org/core/journals/mathematical-gazette/article/eulers-primeproducing-polynomial-revisited/1F76183BF30CECE688E31E8F10F37AC8
- OEIS **A005846** — values of Euler's prime-producing polynomial: https://oeis.org/A005846
- Project Euler problem 27 discussion (including the 80-value transformation): https://math.berkeley.edu/~elafandi/euler/p27/
- Heegner numbers overview: https://en.wikipedia.org/wiki/Heegner_number

---

**Repository status:** ✅ Mathematics checked  
**Prime streak:** 40/40, then a spectacular failure  
**Answer to everything:** Still 42  
**Ultimate lesson:** *Never extrapolate your resource model just because the previous 40 blocks looked magnificent.*
