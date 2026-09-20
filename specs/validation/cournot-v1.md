# Cournot Competition Model [Version 1] - Validation

This document defines the minimum checks required for the implementation of Version 1 Cournot.

## 1. Benchmark case

For

\[
a=100,\quad b=1,\quad c=20,\quad N=3,
\]

the implementation must return:

| Output | Expected value |
|---|---:|
| \(q^C\) | 20 |
| \(Q^C\) | 60 |
| \(p^C\) | 40 |
| \(\pi^C\) | 400 |
| Total industry profit | 1200 |
| Consumer surplus | 1800 |
| Producer surplus | 1200 |
| Total welfare | 3000 |
| \(Q^E\) | 80 |
| Deadweight loss | 200 |
| \(H\) | \(1/3\) |

## 2. Internal identities

For every valid input, the implementation must satisfy:

\[
Q^C = Nq^C,
\]

\[
p^C = a-bQ^C,
\]

\[
PS^C = N\pi^C,
\]

\[
W^C = CS^C + PS^C,
\]

and

\[
H = \frac{1}{N}.
\]

It must also satisfy

\[
W^C + DWL
=
\frac{(a-c)^2}{2b}.
\]

## 3. Monopoly case

When

\[
N=1,
\]

the model must reproduce:

\[
q^C = Q^C = \frac{a-c}{2b},
\]

and

\[
p^C = \frac{a+c}{2}.
\]

## 4. Comparative statics

Holding \(a\), \(b\) and \(c\) constant, increasing \(N\) must:

- decrease \(q^C\);
- increase \(Q^C\);
- decrease \(p^C\);
- increase consumer surplus;
- increase total welfare;
- decrease deadweight loss;
- decrease \(H\).

## 5. Limiting behaviour

The analytical implementation must be consistent with:

\[
p^C \rightarrow c
\]

and

\[
Q^C \rightarrow Q^E
\]

as

\[
N\rightarrow\infty.
\]

This is primarily an analytical property (not a requirement to test an infinite numerical value).

## 6. Invalid inputs

The implementation must reject inputs where:

- \(N<1\);
- \(N\) is not an integer;
- \(b\leq0\);
- \(c<0\);
- \(a\leq c\).

The error-handling mechanism will be defined with the TypeScript interface.

## 7. Numerical behaviour

Tests involving floating-point calculations must use an appropriate numerical tolerance (do not rely on exact equality where a rounding error may occur).
