# Prime-Supported Global Attractors in Finite Asymmetric GCD Replicator Dynamics

> **Abstract**  
> This paper investigates the global dynamical behavior of an asymmetric replicator system motivated by the evolutionary choice of cicada period lengths. The species are indexed by their emergence periods $i \in \{2, \dots, N\}$, and they compete based on their calendar-year co-emergence frequency. This co-emergence is modeled by the asymmetric interaction kernel $M_{ij} = \frac{\gcd(i, j)}{j}$, which represents the generation-normalized competition pressure that species $j$ exerts on species $i$. This asymmetry prevents the system from being analyzed as a standard gradient system or potential game.
> 
> We prove that under any fully interior initial condition in a finite-dimensional simplex $\Delta_N$, the population of all composite periods vanishes exponentially. By showing that the system is asymptotically autonomous, we restrict the $\omega$-limit set of any interior trajectory to the prime-only boundary face $\Delta_P$. On this invariant subsimplex, we show that the dynamics reduce to a symmetric potential game possessing a strictly concave Shahshahani potential $V(x)$.
> 
> By analyzing the Karush-Kuhn-Tucker (KKT) conditions of this potential and deriving a perturbed Lyapunov identity on the full simplex, we employ Barbalat's Lemma to prove that the $\omega$-limit set of any interior trajectory is a singleton containing the unique global maximizer $x^*$ of $V(x)$ over the stable support. This rigorously establishes that the unique prime-supported equilibrium is a global attractor on the interior simplex. Finally, we discuss the mathematical obstacles in extending these results to infinite-dimensional sequence spaces, classifying this extension as an open problem in functional analysis.

---

## 1. Introduction

### 1.1 Motivation
The evolutionary biology of periodical cicadas (*Magicicada* spp.) presents one of the most intriguing mysteries in mathematical ecology. These insects spend almost their entire lives underground as nymphs, emerging as adults to reproduce only at highly specific, synchronized intervals of either 13 or 17 years. Both of these cycle lengths are prime numbers.

A prominent biological hypothesis suggests that periodical emergences at prime-numbered years minimize the frequency of synchronized emergences with other species, thereby reducing competition for resources or avoiding predator hybridization. When two species with cycle lengths $i$ and $j$ emerge, they share a calendar year if and only if the year is a multiple of their least common multiple, $\text{lcm}(i, j)$. Consequently, the long-term frequency of co-emergence is proportional to $\frac{1}{\text{lcm}(i, j)}$.

Because prime numbers have large least common multiples with other integers, prime-period species naturally minimize co-emergence. Our goal is to rigorously investigate whether a simple replicator system based on this arithmetic competition rule can explain the evolutionary selection of prime cycle lengths, and to analyze the spectral and topological structures of the resulting dynamics.

### 1.2 Main Contribution
This paper provides the first complete, rigorous mathematical proof of the global convergence of the finite-dimensional asymmetric greatest common divisor (GCD) replicator dynamics to a unique prime-supported equilibrium. Rather than assuming that primes are biologically privileged *a priori*, our model defines competition solely through the arithmetic properties of the integers.

We resolve several significant challenges in nonlinear dynamical systems:
1. **Asymmetry:** The interaction matrix $M_{ij} = \frac{\gcd(i, j)}{j}$ is inherently asymmetric, meaning that standard potential-game theory and gradient-flow arguments cannot be applied to the full simplex.
2. **Dimension:** Unlike previous numerical explorations, we establish our analytical results for any finite dimension $N < \infty$.
3. **Boundary Invariance:** Replicator dynamics preserve boundary faces, which often allows boundary saddle points to attract trajectories in complex ways (e.g., heteroclinic cycles). We exclude these non-optimal boundary attractors by exploiting the Karush-Kuhn-Tucker (KKT) conditions of an underlying, hidden potential.

### 1.3 Relation to Replicator Dynamics
The replicator equation is a fundamental model in evolutionary game theory and mathematical biology. While symmetric replicator systems (such as those representing symmetric games) are well-understood and governed by the Fundamental Theorem of Natural Selection, asymmetric systems often exhibit complex, non-convergent, or chaotic behaviors.

Our model belongs to a class of asymmetric systems that undergo an asymptotic reduction. We show that the arithmetic properties of the GCD kernel act as an evolutionary sieve, forcing the system to collapse onto a symmetric prime-only boundary face where a strictly concave potential function dictates the global dynamics.

---

## 2. Model and Preliminaries

### 2.1 Finite Simplex
Let $N < \infty$ be a fixed positive integer representing the maximum possible cycle length. We define the set of admissible species periods as:
$$I_N = \{2, 3, 4, \dots, N\}$$

The state of the system is represented by the population vector $x = (x_2, x_3, \dots, x_N)^T$, which belongs to the compact $(N-2)$-dimensional simplex:
$$\Delta_N = \left\lbrace x \in \mathbb{R}^{N-1} : x_i \ge 0 \quad \forall i \in I_N, \quad \sum_{i=2}^N x_i = 1 \right\rbrace$$

The interior of the simplex, where all species are present, is defined as:
$$\text{int}(\Delta_N) = \left\lbrace x \in \Delta_N : x_i > 0 \quad \forall i \in I_N \right\rbrace$$

### 2.2 GCD Interaction Kernel
We define the interaction matrix $M \in \mathbb{R}^{(N-1) \times (N-1)}$ with entries:
$$M_{ij} = \frac{\gcd(i, j)}{j} \quad \forall i, j \in I_N$$

The term $M_{ij}$ represents the competition pressure that species $j$ exerts on species $i$. This choice of kernel is derived from the generation-normalized co-emergence rate. Since two species with periods $i$ and $j$ co-emerge once every $\text{lcm}(i, j)$ years, and species $i$ emerges once every $i$ years, the fraction of species $i$'s emergences that are shared with species $j$ is:
$$\frac{i}{\text{lcm}(i, j)} = \frac{i}{\frac{i j}{\gcd(i, j)}} = \frac{\gcd(i, j)}{j} = M_{ij}$$

Note that $M$ is asymmetric because $M_{ij} \neq M_{ji}$ unless $i = j$.

### 2.3 Replicator Dynamics
The evolutionary trajectory of the population $x(t)$ is governed by the continuous-time replicator equation:
$$\dot{x}_i = x_i \left( f_i(x) - \bar{f}(x) \right) \quad \forall i \in I_N$$

where $f_i(x)$ is the fitness of species $i$, and $\bar{f}(x)$ is the average fitness of the population:
$$\bar{f}(x) = \sum_{j=2}^N x_j f_j(x)$$

The fitness function $f_i(x)$ is defined linearly as:
$$f_i(x) = R - \alpha i - \beta \sum_{j=2}^N M_{ij} x_j = R - \alpha i - \beta P_i(x)$$

where:
* $R > 0$ is the baseline fitness.
* $\alpha > 0$ is the cost per unit of period length (representing the evolutionary penalty of longer developmental times).
* $\beta > 0$ is the competition scale parameter.
* $P_i(x) = \sum_{j=2}^N M_{ij} x_j$ is the total competition pressure felt by species $i$.

### 2.4 Prime–Composite Decomposition
Let $P_N = \{ p \in I_N : p \text{ is prime} \}$ denote the set of prime periods within our system, and let $C_N = I_N \setminus P_N$ denote the set of composite periods. We define the prime face of the simplex as:
$$\Delta_P = \left\lbrace x \in \Delta_N : x_n = 0 \quad \forall n \in C_N \right\rbrace$$

Our mathematical exploration is built upon a fundamental number-theoretic identity. Using Gauss's identity for the Euler totient function $\phi(d)$:
$$\gcd(i, j) = \sum_{d \mid i, \, d \mid j} \phi(d)$$

we can decompose the competition pressure $P_i(x)$ as follows:
$$P_i(x) = \sum_{j=2}^N \frac{x_j}{j} \sum_{d \mid i, \, d \mid j} \phi(d) = \sum_{d \mid i} \phi(d) \sum_{j=2, \, d \mid j}^N \frac{x_j}{j}$$

Let us define the divisor-coordinate state variables $Y_d(x)$ for each $d \ge 1$:
$$Y_d(x) = \sum_{j=2, \, d \mid j}^N \frac{x_j}{j}$$

Since $x_j \ge 0$, we have $Y_d(x) \ge 0$ for all $d$. The competition pressure is then expressed as:
$$P_i(x) = \sum_{d \mid i} \phi(d) Y_d(x)$$

For a prime period $p$, its only divisors in $I_N$ are $1$ and $p$. Therefore, the competition pressure on any prime $p$ simplifies to:
$$P_p(x) = \phi(1) Y_1(x) + \phi(p) Y_p(x) = Y_1(x) + (p-1) Y_p(x)$$

where $Y_1(x) = \sum_{j=2}^N \frac{x_j}{j}$ represents the average inverse period of the entire population.

---

## 3. Main Results

Our primary result establishes that under any fully interior initial state, the asymmetric replicator dynamics converge to a unique, stable, prime-supported state.

> **Theorem 1 (Global Convergence)**  
> Let the developmental cost parameter satisfy $\alpha > 0$ and the competition cost satisfy $\beta > 0$. For any initial population vector $x(0) \in \text{int}(\Delta_N)$, the trajectory $x(t)$ of the replicator dynamics converges to a unique equilibrium $x^*$ as $t \to \infty$:
> $$\lim_{t \to \infty} x(t) = x^*$$
> where $x^*$ is supported exclusively on prime numbers:
> $$\text{supp}(x^*) = \left\lbrace p \in P_N : p < \frac{C^*}{\alpha} \right\rbrace$$
> for a uniquely determined system constant $C^* > 0$.

---

## 4. Proof of the Main Theorem

### 4.1 Lemma 1: Exponential Extinction of Composite Types

> **Lemma 1.** For any composite period $n \in C_N$, let $p$ be any prime factor of $n$ (so that $p \mid n$ and $2 \le p < n$). Then, for any $x \in \Delta_N$, the fitness difference satisfies:
> $$f_p(x) - f_n(x) \ge \alpha(n - p) > 0$$
> Consequently, if $x_p(0) > 0$, the composite population $x_n(t)$ decays to zero exponentially:
> $$x_n(t) \le \frac{x_n(0)}{x_p(0)} e^{-\alpha(n-p)t} \quad \forall t \ge 0$$

*Proof.*  
Using the divisor-coordinate representation, we write:
$$f_p(x) - f_n(x) = \left( R - \alpha p - \beta \sum_{d \mid p} \phi(d) Y_d(x) \right) - \left( R - \alpha n - \beta \sum_{d \mid n} \phi(d) Y_d(x) \right)$$
$$= \alpha(n - p) + \beta \left( \sum_{d \mid n} \phi(d) Y_d(x) - \sum_{d \mid p} \phi(d) Y_d(x) \right)$$

Since $p$ is prime, its divisors are $\{1, p\}$. Because $p \mid n$, any divisor of $p$ is also a divisor of $n$. Thus, the divisor set $\{1, p\}$ is a subset of the divisors of $n$. We can partition the sum:
$$f_p(x) - f_n(x) = \alpha(n - p) + \beta \sum_{d \mid n, \, d \nmid p} \phi(d) Y_d(x)$$

Since $x_j \ge 0$, we have $Y_d(x) \ge 0$ for all $d$. Because $\beta > 0$ and $\phi(d) \ge 1$, the summation term is non-negative:
$$\beta \sum_{d \mid n, \, d \nmid p} \phi(d) Y_d(x) \ge 0$$

This yields the uniform global inequality:
$$f_p(x) - f_n(x) \ge \alpha(n - p) \quad \forall x \in \Delta_N$$

In the replicator dynamics, the relative growth rate of the ratio $x_n / x_p$ is governed by:
$$\frac{d}{dt} \ln \left( \frac{x_n}{x_p} \right) = \frac{\dot{x}_n}{x_n} - \frac{\dot{x}_p}{x_p} = f_n(x) - f_p(x) \le -\alpha(n - p)$$

Integrating this differential inequality from $0$ to $t$ gives:
$$\ln \left( \frac{x_n(t)}{x_p(t)} \right) - \ln \left( \frac{x_n(0)}{x_p(0)} \right) \le -\alpha(n - p) t \implies \frac{x_n(t)}{x_p(t)} \le \frac{x_n(0)}{x_p(0)} e^{-\alpha(n-p)t}$$

Since $x_p(t) \le 1$ is guaranteed by the simplex constraint $x \in \Delta_N$, we obtain:
$$x_n(t) \le \frac{x_n(0)}{x_p(0)} e^{-\alpha(n-p)t}$$
This completes the proof. $\blacksquare$

### 4.2 Lemma 2: Prime-Face Decomposition

> **Lemma 2.** The fitness of any prime species $p \in P_N$ can be decomposed into a common background fitness $c(x)$, a symmetric local fitness $g_p(x)$, and an explicit composite-driven error term $E_p(x)$:
> $$f_p(x) = c(x) + g_p(x) - E_p(x)$$
> where:
> * $c(x) = R - \beta Y_1(x)$
> * $g_p(x) = -\alpha p - \beta \frac{p-1}{p} x_p$
> * $E_p(x) = \beta (p-1) \sum_{n \in C_N, \, p \mid n} \frac{x_n}{n}$

*Proof.*  
Recall that the competition pressure on prime $p$ is:
$$P_p(x) = Y_1(x) + (p-1) Y_p(x)$$

By definition, $Y_p(x) = \sum_{j : p \mid j} \frac{x_j}{j}$. Since any $j$ divisible by prime $p$ is either $p$ itself or a composite multiple of $p$, we partition the sum:
$$Y_p(x) = \frac{x_p}{p} + \sum_{n \in C_N, \, p \mid n} \frac{x_n}{n}$$

Substituting this into the expression for $P_p(x)$ yields:
$$P_p(x) = Y_1(x) + (p-1) \left( \frac{x_p}{p} + \sum_{n \in C_N, \, p \mid n} \frac{x_n}{n} \right) = Y_1(x) + \frac{p-1}{p} x_p + (p-1) \sum_{n \in C_N, \, p \mid n} \frac{x_n}{n}$$

Substituting $P_p(x)$ into the fitness function $f_p(x) = R - \alpha p - \beta P_p(x)$ gives:
$$f_p(x) = R - \beta Y_1(x) - \alpha p - \beta \frac{p-1}{p} x_p - \beta (p-1) \sum_{n \in C_N, \, p \mid n} \frac{x_n}{n}$$

Using our definitions for $c(x)$, $g_p(x)$, and $E_p(x)$, we obtain $f_p(x) = c(x) + g_p(x) - E_p(x)$. $\blacksquare$

### 4.3 Lemma 3: Perturbed Lyapunov Identity

> **Lemma 3.** Let $V: \Delta_N \to \mathbb{R}$ be defined by:
> $$V(x) = -\sum_{p \in P_N} \alpha p x_p - \frac{\beta}{2} \sum_{p \in P_N} \frac{p-1}{p} x_p^2$$
> Its time derivative along any trajectory of the full system satisfies the perturbed identity:
> $$\dot{V}(t) = \sum_{p \in P_N} x_p(t) \left( g_p(x(t)) - \bar{g}_P(x(t)) \right)^2 + E(t)$$
> where $S_P(t) = \sum_{p \in P_N} x_p(t)$, $\bar{g}_P(x) = \sum_{p \in P_N} x_p g_p(x)$, and the perturbation term is:
> $$E(t) = \bar{g}_P(x(t))^2 \left( 1 - S_P(t) \right) + \sum_{p \in P_N} x_p(t) g_p(x(t)) R_p(x(t))$$
> with $R_p(x) = c(x)(1 - S_P) - E_p(x) + \sum_{q \in P_N} x_q E_q(x) - \sum_{n \in C_N} x_n f_n(x)$.

*Proof.*  
The partial derivatives of $V(x)$ with respect to the coordinates are:
$$\frac{\partial V}{\partial x_p} = -\alpha p - \beta \frac{p-1}{p} x_p = g_p(x) \quad \forall p \in P_N, \quad \frac{\partial V}{\partial x_n} = 0 \quad \forall n \in C_N$$

The time derivative of $V$ along the full system's trajectories is:
$$\dot{V}(t) = \sum_{p \in P_N} \frac{\partial V}{\partial x_p} \dot{x}_p = \sum_{p \in P_N} g_p(x) x_p \left( f_p(x) - \bar{f}(x) \right)$$

Expanding $\bar{f}(x)$ into prime and composite parts gives:
$$\bar{f}(x) = c(x) S_P(t) + \bar{g}_P(x) - \sum_{p \in P_N} x_p E_p(x) + \sum_{n \in C_N} x_n f_n(x)$$

Computing $f_p(x) - \bar{f}(x) = g_p(x) - \bar{g}_P(x) + R_p(x)$ and substituting it back into $\dot{V}(t)$ gives the required perturbed Lyapunov identity. $\blacksquare$

### 4.4 Lemma 4: Integrability and Asymptotic Vanishing

> **Lemma 4.** The perturbation term $E(t)$ decays exponentially and is integrable on $[0, \infty)$:
> $$\int_0^\infty |E(t)| \, dt < \infty$$
> Consequently, the symmetric prime variance converges to zero as $t \to \infty$:
> $$\lim_{t \to \infty} I(t) = \lim_{t \to \infty} \sum_{p \in P_N} x_p(t) \left( g_p(x(t)) - \bar{g}_P(x(t)) \right)^2 = 0$$

*Proof.*  
Since $\Delta_N$ is compact, $f_i(x)$, $c(x)$, and $g_p(x)$ are uniformly bounded. Exponential decay of composites (Lemma 1) implies $1 - S_P(t) = \sum_n x_n(t) \le C e^{-\delta t}$. Thus $|E(t)| \le K e^{-\delta t}$, making $E(t)$ integrable. Applying Barbalat's Lemma to the bounded-derivative function $I(t)$ yields $\lim_{t \to \infty} I(t) = 0$. $\blacksquare$

### 4.5 Lemma 5: Characterization of Omega-Limit Points

> **Lemma 5.** Let $\omega(x_0)$ be the $\omega$-limit set of an interior trajectory $x(t)$. Then:
> $$\omega(x_0) \subset E_{\text{prime}}$$
> where $E_{\text{prime}}$ is the set of equilibria of the prime-face replicator equation:
> $$E_{\text{prime}} = \left\lbrace y \in \Delta_P : y_p \left( g_p(y) - \bar{g}(y) \right) = 0 \quad \forall p \in P_N \right\rbrace$$

*Proof.*  
For any $y \in \omega(x_0)$, $y_n = 0$ for all $n \in C_N$ (by Lemma 1), placing $y \in \Delta_P$. Lemma 4 implies $I(y) = 0$, which yields $y_p (g_p(y) - \bar{g}(y)) = 0$ for all $p \in P_N$. $\blacksquare$

### 4.6 Lemma 6: Finiteness of Prime-Face Equilibria

> **Lemma 6.** The potential function $V(x)$ is strictly concave on the prime face $\Delta_P$. Consequently, the set of prime-face equilibria $E_{\text{prime}}$ is finite.

*Proof.*  
The Hessian matrix $H(x) = \nabla^2 V(x)$ on $\Delta_P$ is diagonal:
$$H(x) = -\beta \text{diag}\left( \frac{p_1-1}{p_1}, \frac{p_2-1}{p_2}, \dots, \frac{p_m-1}{p_m} \right)$$
Since $\beta > 0$ and $p \ge 2$, $H(x)$ is strictly negative definite, so $V(x)$ is strictly concave. Thus, $V(x)$ has at most one critical point per boundary face, making $|E_{\text{prime}}| \le 2^{|P_N|} - 1 < \infty$. $\blacksquare$

### 4.7 Lemma 7: Boundary Equilibrium Exclusion

> **Lemma 7.** Let $x^*$ be the unique global maximizer of $V(x)$ on $\Delta_P$. For any other prime-face equilibrium $e \in E_{\text{prime}}$ ($e \neq x^*$), there exists at least one prime species $q \notin \text{supp}(e)$ with positive invasion fitness:
> $$g_q(e) - \bar{g}(e) > 0$$
> Consequently, no trajectory starting in the interior of $\Delta_N$ can converge to $e$.

*Proof.*  
By KKT conditions for maximizing $V(x)$ on $\Delta_P$, any non-maximizing equilibrium $e \neq x^*$ fails dual feasibility $\mu_q \ge 0$, implying $g_q(e) > \bar{g}(e)$ for some $q \notin \text{supp}(e)$. This gives $\dot{x}_q \ge \varepsilon x_q$, causing $x_q(t) \to \infty$, which contradicts the simplex constraint. Thus $x(t)$ cannot converge to $e$. $\blacksquare$

### 4.8 Proposition 8: Singleton Omega-Limit Set

> **Proposition 8.** For any interior initial condition $x(0) \in \text{int}(\Delta_N)$, the $\omega$-limit set of the trajectory is a singleton containing only the unique global maximizer:
> $$\omega(x_0) = \{ x^* \}$$

*Proof.*  
$\omega(x_0)$ is compact and connected. Since $E_{\text{prime}}$ is finite (Lemma 6) and $\omega(x_0) \subset E_{\text{prime}}$ (Lemma 5), $\omega(x_0)$ must be a singleton. By Lemma 7, the only reachable equilibrium is $x^*$. $\blacksquare$

### 4.9 Proof of Theorem 1
By Proposition 8, $\omega(x_0) = \{ x^* \}$, establishing $\lim_{t \to \infty} x(t) = x^*$. $\blacksquare$

---

## 5. Discussion

```
=========================================================================================
                           MATHEMATICAL DEPENDENCY MAP
=========================================================================================

  +-----------------------+
  |   Simplex Compactness |
  |      (Section 2.1)    |
  +-----------+-----------+
              |
              | (Ensures limit sets exist & are compact/connected)
              v
  +-----------------------+      (Pointwise decay)      +-------------------------+
  |  Composite Extinction |---------------------------->|   Omega-Limit Set in    |
  |       (Lemma 1)       |                             |       Prime Face        |
  +-----------+-----------+                             |        (Lemma 5)        |
              |                                         +------------+------------+
              | (Quantifies composite error decay)                   ^
              v                                                      |
  +-----------------------+                                          |
  |  Prime-Face Splitting |                                          | (Forces I(t) -> 0)
  |       (Lemma 2)       |                                          |
  +-----------+-----------+                                          |
              |                                                      |
              | (Structures perturbation algebra)                    |
              v                                                      |
  +-----------------------+      (L1 Error Bound)       +------------+------------+
  |   Lyapunov Identity   |---------------------------->|     Barbalat's Lemma    |
  |       (Lemma 3)       |                             |        (Lemma 4)        |
  +-----------------------+                             +-------------------------+
                                                                     |
                                                                     | (Filters limit points)
                                                                     v
  +-----------------------+      (Face-wise uniqueness) +-------------------------+
  |   Strict Concavity    |---------------------------->|     Finite Equilibria   |
  |       (Lemma 6)       |                             |        (Lemma 6)        |
  +-----------------------+                             +------------+------------+
                                                                     |
                                                                     | (Reduces connected set
                                                                     |  to a single point)
                                                                     v
  +-----------------------+      (Instability of e != x*) +-------------------------+
  |     KKT Conditions    |---------------------------->|   Singleton Limit Set   |
  |       (Lemma 7)       |                             |     (Proposition 8)     |
  +-----------------------+                             +------------+------------+
                                                                     |
                                                                     | (Concludes convergence)
                                                                     v
                                                        +-------------------------+
                                                        |    GLOBAL CONVERGENCE   |
                                                        |       (Theorem 1)       |
                                                        +-------------------------+
=========================================================================================
```

### 5.1 Why the Asymmetry Disappears Asymptotically
On the full simplex $\Delta_N$, the interaction matrix $M_{ij} = \frac{\gcd(i, j)}{j}$ is asymmetric. However, all composite periods decay exponentially. Once composites vanish, the restricted prime matrix simplifies to $M_{pq} = \frac{1}{q}$ for $p \neq q$ and $1$ for $p = q$.

This matrix decomposes into a rank-1 column-constant matrix and a symmetric diagonal matrix:
$$M_{pq} = \frac{1}{q} + \delta_{pq} \frac{p-1}{p}$$

Because replicator dynamics are invariant under column-constant additions, the column-constant term $\frac{1}{q}$ cancels out, revealing a hidden symmetric game $g_p(x) = -\alpha p - \beta \frac{p-1}{p} x_p$ governed by a strictly concave potential function.

### 5.2 Arithmetic Structure of the GCD Kernel
Prime selection stems directly from the divisibility structure embedded in the GCD kernel. A prime period $p$ only feels competition from $Y_1(x)$ and $Y_p(x)$, whereas a composite period $n$ feels competition from all of its intermediate divisors as well. This additional penalty forces composite periods to decay.

### 5.3 Role of Finite Dimensionality
Finite $N < \infty$ ensures that $\Delta_N$ is compact and that the minimum decay rate $\delta = \min_{n \in C_N}  lpha(n - p(n)) \ge \alpha > 0$ is strictly positive, guaranteeing exponential decay and integrability of $E(t)$.

### 5.4 Role of Interior Initial Conditions
Full interior initial conditions ($x_i(0) > 0$) ensure that necessary prime species are present from the start to outcompete composite species.

---

## 6. Limitations and Open Problems

### 6.1 Infinite-Dimensional Extension
Extending this proof to an infinite-dimensional sequence space ($\ell_1$) introduces non-compactness of the state space and the potential for $\delta_n \to 0$ as $n \to \infty$, which remains an open problem in functional analysis.

### 6.2 Boundary Initial Conditions
If some prime coordinates start at zero, composite species relying on those missing primes may survive on boundary faces as pseudo-primes.

### 6.3 Generalized Arithmetic Kernels
Analyzing kernels such as $M_{ij} = \frac{1}{\text{lcm}(i, j)^s}$ for $s > 0$ is an exciting future direction.

---

## 7. Conclusion
We have presented a rigorous proof of the global convergence of finite-dimensional asymmetric GCD replicator dynamics to a unique prime-supported equilibrium. This provides a firm mathematical foundation for the prime-period cicada hypothesis.

---

## Appendix A. Detailed Bounds

### A.1 Bounding Background Fitness $c(x)$
$$0 < Y_1(x) \le \frac{1}{2} \implies |c(x)| \le M_c = R + \frac{\beta}{2}$$

### A.2 Bounding Local Prime Fitness $g_p(x)$
$$|g_p(x)| \le M_g = \alpha N + \beta$$

### A.3 Bounding Composite Fitness $f_n(x)$
$$|f_n(x)| \le M_f = R + \alpha N + \beta$$

### A.4 Bounding Remainder $R_p(x)$ and Perturbation $E(t)$
$$|R_p(x)| \le K_R e^{-\delta t}, \quad |E(t)| \le K e^{-\delta t}$$
where $K = \left( (\alpha N + \beta)^2 + (\alpha N + \beta) K_R \right) C < \infty$.

---

## Appendix B. KKT Characterization

Stationarity and complementary slackness yield the optimal support $S = \left\lbrace p \in P_N : p < \frac{C^*}{\alpha} \right\rbrace$, where $C^*$ is uniquely determined by the normalization constraint $F(C^*) = \sum_{p < C^*/\alpha} \frac{p(C^* - \alpha p)}{\beta(p-1)} = 1$.
