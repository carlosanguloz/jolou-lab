# Cournot Competition Model [Version 1]

## 1. Purpose

Version 1 implements the standard symmetric Cournot model with linear demand and constant marginal cost.

This version of the model remains simple in order to establish a clear, testable foundation for the development of Jolou.

## 2. Model

There are \(N\) firms producing a homogeneous product.

Firm \(i\) chooses quantity

\[
q_i \geq 0.
\]

Total industry output is

\[
Q = \sum_{i=1}^{N} q_i,
\]

and inverse demand is

\[
p = a - bQ,
\]

where

\[
a > c \geq 0,
\qquad
b > 0.
\]

All firms have constant marginal cost \(c\).

Firm \(i\)'s profit is

\[
\pi_i = (p-c)q_i.
\]

Let

\[
Q_{-i} = Q-q_i
\]

denote the total output of firm \(i\)'s competitors.

For the interior case considered in Version 1, firm \(i\)'s reaction function is

\[
R_i(Q_{-i})
=
\frac{a-c}{2b}
-
\frac{Q_{-i}}{2}.
\]

## 3. Symmetric Cournot equilibrium

In a symmetric equilibrium,

\[
q_i=q_j=q^C.
\]

The equilibrium quantities and price are

\[
q^C
=
\frac{a-c}{(N+1)b},
\]

\[
Q^C
=
\frac{N(a-c)}{(N+1)b},
\]

and

\[
p^C
=
\frac{a+Nc}{N+1}.
\]

Profit per firm is

\[
\pi^C
=
\frac{1}{b}
\left(
\frac{a-c}{N+1}
\right)^2.
\]

## 4. Welfare and concentration

Consumer surplus is

\[
CS^C
=
\frac{(a-c)^2}{2b}
\frac{N^2}{(N+1)^2}.
\]

Producer surplus is

\[
PS^C = N\pi^C.
\]

Total welfare is

\[
W^C
=
\frac{N(N+2)}{(N+1)^2}
\frac{(a-c)^2}{2b}.
\]

The efficient quantity is

\[
Q^E = \frac{a-c}{b}.
\]

Deadweight loss is therefore

\[
DWL
=
\frac{(a-c)^2}{2b(N+1)^2}.
\]

With symmetric firms, each firm's market share is \(1/N\), so the Herfindahl-Hirschman concentration measure is

\[
H
=
\sum_{i=1}^{N}s_i^2
=
\frac{1}{N}.
\]

## 5. Required outputs

Version 1 should calculate:

- \(q^C\): output per firm;
- \(Q^C\): total industry output;
- \(p^C\): market price;
- \(\pi^C\): profit per firm;
- total industry profit;
- consumer surplus;
- producer surplus;
- total welfare;
- efficient quantity;
- deadweight loss;
- \(H\): market concentration.

## 6. Validation

The implementation must reproduce the analytical expressions above.

It should also satisfy the following checks:

- \(N=1\) reproduces the monopoly outcome;
- increasing \(N\) decreases individual output and price;
- increasing \(N\) increases total output, consumer surplus and welfare;
- as \(N\rightarrow\infty\), \(p^C\rightarrow c\) and \(Q^C\rightarrow Q^E\);
- calculated quantities, prices, profits and welfare measures satisfy their defining identities.

For the benchmark

\[
a=100,\quad b=1,\quad c=20,\quad N=3,
\]

the results should include

\[
q^C=20,\quad
Q^C=60,\quad
p^C=40,\quad
\pi^C=400.
\]

## 7. Implementation principles

The economic model should:

- be implemented independently of the user interface;
- use clear and descriptive names in code;
- reject invalid inputs explicitly;
- preserve numerical precision internally;
- keep display rounding separate from computation;
- contain no React or visualisation logic.

Version 1 excludes asymmetric costs, entry, fixed costs, capacity constraints, non-linear demand and empirical estimation.

## Reference

Toxvaerd, F. (2026), *Industrial Organisation — Topic 1: Competition with Homogeneous Products*, University of Cambridge, 16 January 2026.
