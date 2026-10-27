## Exercise 1

**Question.** Fill in the details of the proof of Theorem 1.8. Also, prove the monotone decreasing case.

> *Theorem 1.8 (Continuity of Probabilities).* If $A_n \to A$ then $\mathbb{P}(A_n) \to \mathbb{P}(A)$ as $n \to \infty$.

**Solution.**

To prove: If $A_n \to A$ then $P(A_n) \to P(A)$ as $n \to \infty$

**Case 1)** $A_n$ is monotonically increasing
$\Rightarrow A_1 \subset A_2 \subset A_3 \dots$

let $B$ be a set of events defined as:

$$
\begin{aligned}
B_1 &= A_1\\
B_2 &= A_2 - A_1\\
&\;\;\vdots\\
B_i &= A_i - A_{i-1}
\end{aligned}
$$

**I)** we show $\bigcup_{i=1}^{n} B_i = A_n$ for $n \geq 1$ using induction:

*Base case:* $n = 1$: $\quad \bigcup_{i=1}^{n} B_i = \bigcup_{i=1}^{1} B_i = B_1 = A_1$ by definition

*Inductive hypothesis:* we assume $\bigcup_{i=1}^{n} B_i = A_n$ holds for $n = k \in \mathbb{N}$

*Inductive Step:* To show $\bigcup_{i=1}^{n} B_i = A_n$ for $n = k+1$

$$
\bigcup_{i=1}^{k+1} B_i = \left(\bigcup_{i=1}^{k} B_i\right) \cup B_{k+1} \overset{\text{(from hypothesis)}}{=} A_k \cup B_{k+1} = A_n \cup (A_{k+1} - A_k)
$$

> Now we need to know if $B \cup (A - B) = A$ when $B \subset A$.
>
> let $x \in A$: as $B \subset A$
> - case 1: $x \in B \Rightarrow x \in (B \cup A - B)$
> - case 2: $x \in A - B \Rightarrow x \in (B \cup A - B)$ $\Rightarrow A \subseteq B \cup (A - B)$ $\quad (1)$
>
> let $x \in B \cup (A - B)$
> - case 1: $x \in B$ and $B \subset A \Rightarrow x \in A$
> - case 2: $x \in (A - B) \Rightarrow x \in A$ $\quad \Rightarrow B \cup (A - B) \subseteq A$ $\quad (2)$
>
> $(1), (2) \Rightarrow B \cup (A - B) = A$ when $B \subset A$

Using this result in above expression we now got $A_k \cup (A_{k+1} - A_k) = A_{k+1}$, as $A_k \subset A_{k+1}$
$\Rightarrow \bigcup_{i=1}^{n} B_i = A_{k+1} = A_n $

**II)** we also show $B_i \cap B_j = \emptyset \quad \forall i,j \in \mathbb{N},\ i \neq j$

w.l.o.g. let $i < j$

let $x \in B_i \Rightarrow x \in A_i - A_{i-1} \Rightarrow x \in A_i \Rightarrow x \in A_{j-1} \Rightarrow x \notin A_{j-1}^c \Rightarrow x \notin A_{j-1}^c \cap A_j = A_j - A_{j-1} = B_j$

$\Rightarrow$ no element of $B_i$ in $B_j \Rightarrow B_i \cap B_j = \emptyset $

$\Rightarrow$ set $B$ disjoint, as all elements pairwise disjoint

now using (I), (II) we see:

$$
\begin{aligned}
& A_n \to A \\
\Leftrightarrow\ & \lim_{n\to\infty} A_n = A \\
\Leftrightarrow\ & \lim_{n\to\infty} \left(\bigcup_{i=1}^{n} B_i\right) = A && \text{(I)} \\
\Leftrightarrow\ & \bigcup_{i=1}^{\infty} B_i = A \\
\Rightarrow\ & P\left(\bigcup_{i=1}^{\infty} B_i\right) = P(A) \\
\Leftrightarrow\ & \sum_{i=1}^{\infty} P(B_i) = P(A) && \text{(II)} \\
\Leftrightarrow\ & \lim_{n\to\infty} \sum_{i=1}^{n} P(B_i) = P(A) \\
\Leftrightarrow\ & \lim_{n\to\infty} P\left(\bigcup_{i=1}^{n} B_i\right) = P(A) && \text{(I)} \\
\Leftrightarrow\ & \lim_{n\to\infty} P(A_n) = P(A) \\
\Leftrightarrow\ & P(A_n) \to P(A)
\end{aligned}
$$

We clearly see $A_n \to A \Rightarrow P(A_n) \to P(A) $

**Case 2:** $A$ monotonically decreasing $\quad A_n \to A \quad P(A_n) \to P(A)$
$\Rightarrow A_1 \supset A_2 \supset A_3 \dots$

let $B$ be set of events defined as:
$B_i = A_i - A_{i+1}$

**I)** we note $B$ disjoint (same proof process as in Case 1)

**II)** we proove $A_n = A_1 - \bigcup_{i=1}^{n-1} B_i$ using induction

*Base case* $n = 1$: $\quad A_1 = A_1 - \emptyset = A_1 - \bigcup_{i=1}^{0} B_i$

*Induction hypothesis:* $A_n = A_1 - \bigcup_{i=1}^{n-1} B_i$ for some $n = k \in \mathbb{N}$

*Inductive step:* to show statement holds for $n = k+1$

$$
\begin{aligned}
& A_1 - \bigcup_{i=1}^{n} B_i = \\
&= \left(A_1 - \bigcup_{i=1}^{n-1} B_i\right) - B_n =
&& \Big|\ -\bigcup_{i=1}^{n} B_i = \cap \bigcap_{i=1}^{n} B_i^c \\
&= A_n - B_n = \\
&= A_n \cap B_n^c = \\
&= A_n \cap (A_n - A_{n+1})^c = \\
&= A_n \cap (A_n \cap A_{n+1}^c)^c = \\
&= A_n \cap (A_n^c \cup A_{n+1}) = \\
&= (A_n \cap A_n^c) \cup (A_n \cap A_{n+1}) = && \Big|\ A_{n+1} \subset A_n \qquad D^c \cap D = \emptyset \\
&= \emptyset \cup A_{n+1} = \\
&= A_{n+1}
\end{aligned}
$$

$\Rightarrow$ statement holds for $n = k+1$
$\qquad \Rightarrow$ holds $\forall n \in \mathbb{N}$

now using (I), (II)

$$
\begin{aligned}
& A_n \to A \\
\Leftrightarrow\ & \lim_{n\to\infty} A_n = A \\
\Leftrightarrow\ & \lim_{n\to\infty} \left(A_1 - \bigcup_{i=1}^{n-1} B_i\right) = A && \text{(II)} \\
\Leftrightarrow\ & A_1 - \bigcup_{i=1}^{\infty} B_i = A \\
\Rightarrow\ & P\left(A_1 - \bigcup_{i=1}^{\infty} B_i\right) = P(A)
\end{aligned}
$$

> we note $B_i \subset A_1$, as $B_i = A_i - A_{i-1} \subset A_i \subset A_1$
> $\Rightarrow \bigcup_{i=1}^{\infty} B_i \subset A_1 \quad \text{(III)}$

$$
\begin{aligned}
\Rightarrow\ & P(A_1) - P\left(\bigcup_{i=1}^{\infty} B_i\right) = P(A) \\
\Leftrightarrow\ & P(A_1) - \sum_{i=1}^{\infty} P(B_i) = P(A) && \text{(I)} \\
\Leftrightarrow\ & \lim_{n\to\infty} P(A_1) - \sum_{i=1}^{n-1} P(B_i) = P(A) && \text{(I)} \\
\Leftrightarrow\ & \lim_{n\to\infty} P(A_1) - P\left(\bigcup_{i=1}^{n-1} B_i\right) = P(A) && \text{(III)} \\
\Leftrightarrow\ & \lim_{n\to\infty} P\left(A_1 - \bigcup_{i=1}^{n-1} B_i\right) = P(A) && \text{(II)} \\
\Leftrightarrow\ & \lim_{n\to\infty} P(A_n) = P(A) \\
\Leftrightarrow\ & P(A_n) \to A
\end{aligned}
$$

now we clearly see $A_n \to A \Rightarrow P(A_n) \to P(A)$ also when $A$ monotonically decreasing

$\Rightarrow$ In general if $A_n \to A \Rightarrow P(A_n) \to P(A)$

---

## Exercise 2

**Question.** Prove the statements in equation (1.1).

> Equation (1.1) and the properties listed with it:
> $$\mathbb{P}(\emptyset) = 0,\qquad A \subset B \Rightarrow \mathbb{P}(A) \le \mathbb{P}(B),\qquad 0 \le \mathbb{P}(A) \le 1,\qquad \mathbb{P}(A^c) = 1 - \mathbb{P}(A),$$
> $$A \cap B = \emptyset \implies \mathbb{P}(A \cup B) = \mathbb{P}(A) + \mathbb{P}(B). \qquad (1.1)$$

**Solution.**

$\emptyset \cap \emptyset = \emptyset \Rightarrow \emptyset$ disjoint from $\emptyset$
$\Rightarrow$ from axiom 3:

$$
\begin{aligned}
P\left(\bigcup_{i=1}^{\infty} \emptyset\right) &= \sum_{i=1}^{\infty} P(\emptyset) \\
P(\emptyset) &= \sum_{i=1}^{\infty} P(\emptyset) \\
\Rightarrow P(\emptyset) &= 0
\end{aligned}
$$

$A \subset B \quad$ let $C = B - A = B \cap A^c$
$A \cap C = B \cap A \cap A^c = \emptyset \Rightarrow A, C$ disjoint
$\Rightarrow$ we define $A_1 = A;\ A_2 = C;\ A_{i>2} = \emptyset$
$\Rightarrow$ from axiom 3 $\quad P\left(\bigcup_{i=1}^{\infty} A_i\right) = \sum_{i=1}^{\infty} P(A_i)$

$$
\begin{aligned}
P(B) &= P(A) + P(C) \qquad \Big|\ P(C) \ge 0 \text{ from axiom 1} \\
\Rightarrow P(A) &\le P(B)
\end{aligned}
$$

```math
\left.\begin{array}{l} P(A) \ge 0 \text{ from Axiom 1} \\ A \subset \Omega \Rightarrow P(A) \le P(\Omega) = 1 \text{ from axiom 2} \end{array}\right\} \Rightarrow 0 \le P(A) \le 1
```
```math
\left.\begin{array}{l} A^c = \Omega - A \\ A \cup A^c = A \cup (\Omega - A) = \Omega \\ A \text{ disjoint from } A^c \end{array}\right\} \Rightarrow \begin{array}{l} P(A \cup A^c) = P(\Omega) \\ P(A) + P(A^c) = 1 \\ P(A^c) = 1 - P(A) \end{array}
```

$A \cap B = \emptyset$
$\Rightarrow A$ and $B$ disjoint
$\quad \Rightarrow P(A \cup B) = P(A) + P(B) \qquad \Big|$ Axiom 3 on $A_1 = A;\ A_2 = B;\ A_{i>2} = \emptyset$

---

## Exercise 3

**Question.** Let $\Omega$ be a sample space and let $A_1, A_2, \dots$ be events. Define $B_n = \bigcup_{i=n}^{\infty} A_i$ and $C_n = \bigcap_{i=n}^{\infty} A_i$.

(a) Show that $B_1 \supset B_2 \supset \cdots$ and that $C_1 \subset C_2 \subset \cdots$.

(b) Show that $\omega \in \bigcap_{n=1}^{\infty} B_n$ if and only if $\omega$ belongs to an infinite number of the events $A_1, A_2, \dots$.

(c) Show that $\omega \in \bigcup_{n=1}^{\infty} C_n$ if and only if $\omega$ belongs to all the events $A_1, A_2, \dots$ except possibly a finite number of those events.

**Solution.**

Sample space $\Omega$ with $A_1, A_2, \dots$ events
let $B_n = \bigcup_{i=n}^{\infty} A_i$ and $C_n = \bigcap_{i=n}^{\infty} A_i$

**a)** to show $B_1 \supset B_2 \supset B_3 \dots$ and $C_1 \subset C_2 \subset C_3 \dots$

for the $B$'s it suffices to show $B_k \subset B_{k-1} \quad \forall k \in \mathbb{N} \setminus \{1\}$

let $x \in B_k \Rightarrow x \in \bigcup_{i=k}^{\infty} A_i \Rightarrow x \in \left(\bigcup_{i=k}^{\infty} A_i\right) \cup A_{k-1} \Rightarrow x \in \bigcup_{i=k-1}^{\infty} A_i \Rightarrow x \in B_{k-1}$
$\Rightarrow B_k \subset B_{k-1} \quad \forall k \in \mathbb{N} \setminus \{1\}$

for the $C$'s it suffices to show $C_k \subset C_{k+1} \quad \forall k \in \mathbb{N}$

let $x \in C_k \Rightarrow x \in \bigcap_{i=k}^{\infty} A_i \Rightarrow x \in \left(\bigcap_{i=k+1}^{\infty} A_i\right) \cap A_k \Rightarrow x \in \bigcap_{i=k+1}^{\infty} A_i \Rightarrow x \in C_{k+1}$
$\Rightarrow C_k \subset C_{k+1} \quad \forall k \in \mathbb{N}$

**b)** we need to proove $\omega \in \bigcap_{n=1}^{\infty} B_n \Leftrightarrow \forall i \in I: \omega \in A_i$ and $|I| = |\mathbb{N}|$

1) $\Rightarrow$ direction: Proof through contradiction

let $\omega \in \bigcap_{n=1}^{\infty} B_n$ and assume $I$ not infinite $|I| = k \in \mathbb{N}$

let $x = \max(I)$

$$
\begin{aligned}
&\Rightarrow \omega \notin A_i \quad \forall i > x \\
&\Rightarrow \omega \notin \bigcup_{i=x+1}^{\infty} A_i \\
&\Rightarrow \omega \notin B_{x+1} \\
&\Rightarrow \omega \notin \bigcap_{n=1}^{\infty} B_n \quad \text{↯} \quad \Rightarrow \text{assumption wrong and } |I| = |\mathbb{N}| \text{ infinite}
\end{aligned}
$$

2) $\Leftarrow$ direction: we have $|I| = |\mathbb{N}| \Rightarrow \nexists k \in \mathbb{N}: \forall n \geq k: \omega \notin A_n$

$$
\begin{aligned}
&\Rightarrow \omega \in \bigcup_{n=x}^{\infty} A_n \quad \forall x \in \mathbb{N} \\
&\Rightarrow \omega \in B_x \quad \forall x \in \mathbb{N} \\
&\Rightarrow \omega \in \bigcap_{n \geq 1}^{\infty} B_i 
\end{aligned}
$$

**c)** to show $\omega \in \bigcup_{n=1}^{\infty} C_n \Leftrightarrow \forall i \in I: \omega \notin A_i$ and $|I| < |\mathbb{N}|$ not infinite

1) $\Rightarrow$ direction:

$$
\begin{aligned}
& \omega \in \bigcup_{n=1}^{\infty} C_n \\
\Rightarrow\ & \exists m \in \mathbb{N}: \omega \in C_m \\
\Rightarrow\ & \exists m \in \mathbb{N}: \omega \in \bigcap_{i=m}^{\infty} A_i \\
\Rightarrow\ & \exists m \in \mathbb{N}: \omega \in A_i \quad \forall i \geq m \\
& \quad \Rightarrow \omega \in A_i \text{ in at most } m \text{ cases} \Rightarrow |I| < |\mathbb{N}|
\end{aligned}
$$

2) $\Leftarrow$ direction:
$|I| < |\mathbb{N}| \Rightarrow$ let $x = \max(I)$

$$
\begin{aligned}
\text{then } & \omega \in A_i \quad \forall i > x \\
\Rightarrow\ & \omega \in \bigcap_{i=x+1}^{\infty} A_i \\
\Rightarrow\ & \omega \in C_{x+1} \\
\Rightarrow\ & \omega \in \bigcup_{n=1}^{\infty} C_{x+1} 
\end{aligned}
$$

---

## Exercise 4

**Question.** Let $\{A_i : i \in I\}$ be a collection of events where $I$ is an arbitrary index set. Show that

$$
\left(\bigcup_{i \in I} A_i\right)^c = \bigcap_{i \in I} A_i^c \quad \text{and} \quad \left(\bigcap_{i \in I} A_i\right)^c = \bigcup_{i \in I} A_i^c
$$

*Hint:* First prove this for $I = \{1, \dots, n\}$.

**Solution.**

let $\{A_i : i \in I\}$ be a collection of events

to prove: **a)** $\left(\bigcup_{i \in I} A_i\right)^c = \bigcap_{i \in I} A_i^c \qquad$ **b)** $\left(\bigcap_{i \in I} A_i\right)^c = \bigcup_{i \in I} A_i^c$

| a) | b) |
|---|---|
| let $x \in \left(\bigcup_{i \in I} A_i\right)^c$ | let $x \in \left(\bigcap_{i \in I} A_i\right)^c$ |
| $\Leftrightarrow x \notin \bigcup_{i \in I} A_i$ | $\Leftrightarrow x \notin \bigcap_{i \in I} A_i$ |
| $\Leftrightarrow x \notin A_i \;;\; \forall i \in I$ | $\Leftrightarrow \exists m \in I : x \notin A_i$ |
| $\Leftrightarrow x \in A_i^c \;;\; \forall i \in I$ | $\Leftrightarrow \exists m \in I : x \in A_i^c$ |
| $\Leftrightarrow x \in \bigcap_{i \in I} A_i^c$ | $\Leftrightarrow x \in \bigcup_{i \in I} A_i^c$ |
| $\Rightarrow \left(\bigcup_{i \in I} A_i\right)^c = \bigcap_{i \in I} A_i^c$ | |

---

## Exercise 5

**Question.** Suppose we toss a fair coin until we get exactly two heads. Describe the sample space $S$. What is the probability that exactly $k$ tosses are required?

**Solution.**

Sample space is a sequence of throws containing exactly two heads, with the last throw being a head. More formaly:

$$
\Omega = \{\, \{T\}^n H \{T\}^m H \mid n, m \in \mathbb{N}_0 \,\}
$$

Each sequence of length $k$ is equally likely as tosses are independent. Let $\omega \in \Omega$ and $|\omega| = k$ then $P(\omega) = \left(\tfrac{1}{2}\right)^k$.
we know $\omega_k = H \Rightarrow$ that leaves $k-1$ places where other $H$ can be
$\Rightarrow$ total of $k-1$ $\omega \in \Omega$ with $|\omega| = k$

$$
\Rightarrow P(|\omega| = k) = (k-1)\left(\tfrac{1}{2}\right)^k
$$

---

## Exercise 6

**Question.** Let $\Omega = \{0, 1, \dots\}$. Prove that there does not exist a uniform distribution on $\Omega$ (i.e., if $\mathbb{P}(A) = \mathbb{P}(B)$ whenever $|A| = |B|$, then $\mathbb{P}$ cannot satisfy the axioms of probability).

**Solution.**

we have $\Omega = \{0, 1, \dots\}$ i.e. $|\Omega| = |\mathbb{N}|$

let $P$ be uniform on $\Omega$
$\Rightarrow P(x) = \varepsilon \in \mathbb{R} \quad \forall x \in \Omega$
$P(\Omega) = 1 \Rightarrow \varepsilon \neq 0$

$$
\begin{aligned}
P(\Omega) &= \sum_{\omega \in \Omega} P(\omega) \\
1 &= \sum_{\omega \in \Omega} \varepsilon \\
\frac{1}{\varepsilon} &= \sum_{\omega \in \Omega} 1
\end{aligned}
\qquad , \ \tfrac{1}{\varepsilon} \in \mathbb{R}, \text{ but right side is infinity}
$$

$\Rightarrow$ equality does not hold ↯

$\Rightarrow$ impossible to do a uniform on this $\Omega$

---

## Exercise 7

**Question.** Let $A_1, A_2, \dots$ be events. Show that

$$
\mathbb{P}\left(\bigcup_{n=1}^{\infty} A_n\right) \le \sum_{n=1}^{\infty} \mathbb{P}(A_n).
$$

*Hint:* Define $B_n = A_n - \bigcup_{i=1}^{n-1} A_i$. Then show that the $B_n$ are disjoint and that $\bigcup_{n=1}^{\infty} A_n = \bigcup_{n=1}^{\infty} B_n$.

**Solution.**

$A_1, A_2, \dots$ events
to show $\quad P\left(\bigcup_{n=1}^{\infty} A_n\right) \le \sum_{n=1}^{\infty} P(A_i)$

let $B_n = A_n / \left(\bigcup_{i=1}^{n-1} A_i\right)$

let $n_1, n_2 \in \mathbb{N}$
w.l.o.g. $n_1 < n_2$

$$
\begin{aligned}
B_{n_1} \cap B_{n_2} &= \left(A_{n_1} / \left(\bigcup_{i=1}^{n_1-1} A_i\right)\right) \cap \left(A_{n_2} / \left(\bigcup_{i=1}^{n_2-1} A_i\right)\right) = \\
&= A_{n_1} \cap \left(\bigcap_{i=1}^{n_1-1} A_i^c\right) \cap A_{n_2} \cap \left(\bigcap_{i=1}^{n_2-1} A_i^c\right) = \\
&= \underline{A_{n_1}} \cap \left(\bigcap_{i=1}^{n_1-1} A_i^c\right) \cap A_{n_2} \cap \left(\left(\bigcap_{i=1}^{n_1-1} A_i^c\right) \cap \underline{A_{n_1}^c} \cap \left(\bigcap_{i=n_1+1}^{n_2-1} A_i^c\right)\right) = \\
&= \emptyset
\end{aligned}
$$

$\Rightarrow$ all $B$ are disjoint

we also show $\bigcup_{i=1}^{n} B_i = \bigcup_{i=1}^{n} A_i$ through induction

*Base:* $B_1 = A_1 / \left(\bigcup_{i=1}^{0} A_i\right) = A_1 / \emptyset = A_1$

*Induction hypothesis:* let $\bigcup_{i=1}^{n} B_i = \bigcup_{i=1}^{n} A_i \quad \forall n \le k \in \mathbb{N}$

*Induction step:* then $\bigcup_{i=1}^{k+1} B_i = \bigcup_{i=1}^{k+1} A_i$ must hold

$$
\begin{aligned}
\bigcup_{i=1}^{k+1} B_i &= \\
&= B_{k+1} \cup \left(\bigcup_{i=1}^{k} B_i\right) = \\
&= A_{k+1} / \left(\bigcup_{i=1}^{k} A_i\right) \cup \left(\bigcup_{i=1}^{k} A_i\right) = \\
&= A_{k+1} \cap \left(\bigcup_{i=1}^{k} A_i\right)^c \cup \left(\bigcup_{i=1}^{k} A_i\right) = \\
&= \left(A_{k+1} \cup \left(\bigcup_{i=1}^{k} A_i\right)\right) \cap \left(\left(\bigcup_{i=1}^{k} A_i\right) \cup \left(\bigcup_{i=1}^{k} A_i\right)^c\right) = \\
&= \bigcup_{i=1}^{k+1} A_i \cap \Omega = \\
&= \bigcup_{i=1}^{k+1} A_i
\end{aligned}
$$

$$
\Rightarrow P\left(\bigcup_{i=1}^{\infty} A_i\right) = P\left(\bigcup_{i=1}^{\infty} B_i\right) = \sum_{i=1}^{\infty} P(B_i) \le \sum_{i=1}^{\infty} P(A_i) \qquad \Big|\ B_i \subset A_i
$$

---

## Exercise 8

**Question.** Suppose that $\mathbb{P}(A_i) = 1$ for each $i$. Prove that

$$
\mathbb{P}\left(\bigcap_{i=1}^{\infty} A_i\right) = 1.
$$

**Solution.**

$P(A_i) = 1 \quad \forall i \in \mathbb{N} \quad \Rightarrow P(A_i^c) = 0$

$$
P\left(\bigcap_{i=1}^{\infty} A_i\right) = 1 - P\left(\left(\bigcap_{i=1}^{\infty} A_i\right)^c\right) = 1 - P\left(\bigcup_{i=1}^{\infty} A_i^c\right) =
$$

> | from ⑦ $\ P\left(\bigcup_{i=1}^{\infty} A_i^c\right) \le \sum_{i=1}^{\infty} P(A_i^c) = \sum_{i=1}^{\infty} 0 = 0$
> Axiom 1 $\Rightarrow P\left(\bigcup_{i=1}^{\infty} A_i^c\right) = 0$

$$
\Rightarrow P\left(\bigcap_{i=1}^{\infty} A_i\right) = 1 - 0 = 1
$$

---

## Exercise 9

**Question.** For fixed $B$ such that $\mathbb{P}(B) > 0$, show that $\mathbb{P}(\cdot \mid B)$ satisfies the axioms of probability.

**Solution.**

for fixed $B$ with $P(B) > 0$ to show $P(\cdot \mid B)$ satisfies probability axioms

let $A \subset \Omega \qquad P(A \mid B) = \dfrac{P(A \cap B)}{P(B)}$

$P$ valid probability measure
$\Rightarrow P(A \cap B) \ge 0$ and we know $P(B) > 0$
$\Rightarrow \dfrac{P(A \cap B)}{P(B)} \ge 0 \Rightarrow P(A \mid B) \ge 0 \quad (1)$

$$
P(\Omega \mid B) = \frac{P(\Omega \cap B)}{P(B)} = \frac{P(B)}{P(B)} = 1 \quad (2)
$$

let $A_1, A_2, A_3, \dots \subset \Omega$ disjoint events

$$
P\left(\bigcup_{i=1}^{\infty} A_i \,\Big|\, B\right) = \frac{P\left(\left(\bigcup_{i=1}^{\infty} A_i\right) \cap B\right)}{P(B)} = \frac{P\left(\bigcup_{i=1}^{\infty} (A_i \cap B)\right)}{P(B)}
$$

$A_i$'s disjoint $\Rightarrow A_i \cap B$ also disjoint events $\quad \left((A_i \cap B) \cap (A_j \cap B) = (A_i \cap A_j) \cap B = \emptyset\right)$
as $P$ valid probability measure we get

$$
\frac{P\left(\bigcup_{i=1}^{\infty} (A_i \cap B)\right)}{P(B)} = \frac{\sum_{i=1}^{\infty} P(A_i \cap B)}{P(B)} = \sum_{i=1}^{\infty} \frac{P(A_i \cap B)}{P(B)} = \sum_{i=1}^{\infty} P(A_i \mid B) \quad (3)
$$

$(1), (2), (3) \Rightarrow P(\cdot \mid B)$ is a valid probability measure

---

## Exercise 10

**Question.** You have probably heard it before. Now you can solve it rigorously. It is called the "Monty Hall Problem." A prize is placed at random behind one of three doors. You pick a door. To be concrete, let's suppose you always pick door 1. Now Monty Hall chooses one of the other two doors, opens it and shows you that it is empty. He then gives you the opportunity to keep your door or switch to the other unopened door. Should you stay or switch? Intuition suggests it doesn't matter. The correct answer is that you should switch. Prove it. It will help to specify the sample space and the relevant events carefully. Thus write $\Omega = \{(\omega_1, \omega_2) : \omega_i \in \{1, 2, 3\}\}$ where $\omega_1$ is where the prize is and $\omega_2$ is the door Monty opens.

**Solution.**

we define our sample space using tuples where first element depicts where the prize is and the second which door Monty opens.

$\Rightarrow \Omega = \{(\omega_1, \omega_2) \mid \omega_1, \omega_2 \in [3]\}$

we however know Monty never reveals prize, and does not open '1' as we have chosen it

$\Rightarrow$ tuples $(1,1), (2,2), (3,3), (2,1), (3,1)$ have probability $0$

assuming the prize has the same chance to be behind all doors:
$P(\omega_1 = 1) = P(\omega_1 = 2) = P(\omega_1 = 3) = \tfrac{1}{3}$

$$
\begin{aligned}
\Rightarrow P((1,2)) + P((1,3)) &= \tfrac{1}{3} \\
P((2,3)) &= \tfrac{1}{3} \\
P((3,2)) &= \tfrac{1}{3}
\end{aligned}
$$

$P(\text{win} \mid \text{no switch}) = P(\omega_1 = 1) = \tfrac{1}{3}$
$P(\text{win} \mid \text{switch}) = P((2,3) \cup (3,2)) = \tfrac{1}{3} + \tfrac{1}{3} = \tfrac{2}{3}$

---

## Exercise 11

**Question.** Suppose that $A$ and $B$ are independent events. Show that $A^c$ and $B^c$ are independent events.

**Solution.**

$$
\begin{aligned}
P(A^c \cup B^c) &= P(A^c) + P(B^c) - P(A^c \cap B^c) \\
P(A^c \cap B^c) &= (1 - P(A)) + (1 - P(B)) - P(A^c \cup B^c) = \\
&= 1 - P(A) + 1 - P(B) - P((A \cap B)^c) = \\
&= 1 - P(A) + 1 - P(B) - (1 - P(A \cap B)) = && \Big|\ A, B \text{ independent} \\
&= 1 - P(A) + 1 - P(B) - 1 + P(A)P(B) = \\
&= 1 - P(A) - P(B) + P(A)P(B) = \\
&= (1 - P(A))(1 - P(B)) = \\
&= P(A^c)\,P(B^c) \quad \Rightarrow A^c, B^c \text{ independent}
\end{aligned}
$$

---

## Exercise 12

**Question.** There are three cards. The first is green on both sides, the second is red on both sides and the third is green on one side and red on the other. We choose a card at random and we see one side (also chosen at random). If the side we see is green, what is the probability that the other side is also green? Many people intuitively answer 1/2. Show that the correct answer is 2/3.

**Solution.**

Let us number the faces with $[6]$ so that the first card is $1, 2$
the second is $3, 4$
the third is $5, 6$

and w.l.o.g. let $1, 2, 3$ be the green faces
$\Rightarrow \Omega = [6]$ with a unifor $P$
we are interested in faces $1, 2$, as drawing $3$ leads to red on other side

$$
\Rightarrow P(\{1,2\} \mid \{1,2,3\}) = \frac{|\{1,2\}|}{|\{1,2,3\}|} = \frac{2}{3}
$$

---

## Exercise 13

**Question.** Suppose that a fair coin is tossed repeatedly until both a head and tail have appeared at least once.

(a) Describe the sample space $\Omega$.

(b) What is the probability that three tosses will be required?

**Solution.**

**a)** the sample space contains sequences of identical coin results ending in the opposite result

$$
\Rightarrow \Omega = \{H\}^+ T \cup \{T\}^+ H
$$

**b)** all same length sequences have the same probability as tosses are i.i.d. and $P(H) = P(T) = \tfrac{1}{2}$
$\Rightarrow$ we are interested in $\omega = HHT$ and $\omega = TTH$, or a total of $2$ outcomes each with probability $\left(\tfrac{1}{2}\right)^3$ (because of i.i.d.)

$$
\Rightarrow P(|\omega| = 3) = 2 \cdot \left(\tfrac{1}{2}\right)^3 = \tfrac{1}{4}
$$

---

## Exercise 14

**Question.** Show that if $\mathbb{P}(A) = 0$ or $\mathbb{P}(A) = 1$ then $A$ is independent of every other event. Show that if $A$ is independent of itself then $\mathbb{P}(A)$ is either 0 or 1.

**Solution.**

let $P(A) = 0$; $\quad BA \subset A \Rightarrow P(BA) \le P(A) = 0 \Rightarrow P(BA) = 0$
$\qquad \Rightarrow P(BA) = P(A)P(B) \Rightarrow$ independent

let $P(A) = 1$:

```math
BA = B - BA^c \Rightarrow P(BA) = P(B) - P(BA^c) \qquad \Big|\ \begin{array}{l} BA^c \subset A^c \qquad P(A^c) = 1 - P(A) = 0 \\ \Rightarrow P(BA^c) \le P(A^c) = 0 \\ \Rightarrow P(BA^c) = 0 \end{array}
```

$\qquad \Rightarrow P(BA) = P(B) - 0 = P(B) \cdot 1 = P(B)P(A) \Rightarrow$ independent

$\Rightarrow$ if $P(A) \in \lbrace 0, 1 \rbrace$ then $A$ independent from all other events

if $A$ independent of itself then $P(A \cap A) = P(A)P(A)$

```math
\begin{aligned}
P(A) &= P(A)^2 \qquad \Big|\ : P(A) \neq 0 \\
1 &= P(A)
\end{aligned}
```

$\Rightarrow$ only possibility is $P(A) \in \lbrace 0, 1 \rbrace$

---

## Exercise 15

**Question.** The probability that a child has blue eyes is $1/4$. Assume independence between children. Consider a family with 3 children.

(a) If it is known that at least one child has blue eyes, what is the probability that at least two children have blue eyes?

(b) If it is known that the youngest child has blue eyes, what is the probability that at least two children have blue eyes?

**Solution.**

$$
\Omega = \{(\omega_1, \omega_2, \omega_3) \mid \omega_1, \omega_2, \omega_3 \in \{B, N\}\} \quad \text{and} \quad P(\omega) = \left(\tfrac{1}{4}\right)^{|\omega|_B} \left(\tfrac{3}{4}\right)^{|\omega|_N}
$$

**a)**

$$
P(|\omega|_B \ge 2 \mid |\omega|_B \ge 1) = \frac{P(|\omega|_B \ge 2 \cap |\omega|_B \ge 1)}{P(|\omega|_B \ge 1)} = \frac{P(|\omega|_B \ge 2)}{P(|\omega|_B \ge 1)} = \frac{P(|\omega|_B = 3) + P(|\omega|_B = 2)}{1 - P(|\omega|_B = 0)} =
$$

$$
= \frac{1 \cdot \left(\frac{1}{4}\right)^3 + \binom{3}{2}\left(\frac{3}{4}\right)\left(\frac{1}{4}\right)^2}{1 - \left(\frac{3}{4}\right)^3} = \frac{\frac{1}{64} + \frac{9}{64}}{\frac{37}{64}} = \frac{10}{64} \cdot \frac{64}{37} = \frac{10}{37}
$$

**b)**

$$
P(|\omega|_B \ge 2 \mid \omega_1 = B) = 1 - P(|\omega|_B < 2 \mid \omega_1 = B) = 1 - \frac{P(|\omega|_B < 2 \cap \omega_1 = B)}{P(\omega_1 = B)} = 1 - \frac{P(BNN)}{\frac{1}{4}} = 1 - \frac{\frac{1}{4} \cdot \frac{3}{4} \cdot \frac{3}{4}}{\frac{1}{4}} =
$$

$$
= 1 - \tfrac{9}{16} = \tfrac{7}{16}
$$

---

## Exercise 16

**Question.** Prove Lemma 1.14.

> *Lemma 1.14.* If $A$ and $B$ are independent events then $\mathbb{P}(A \mid B) = \mathbb{P}(A)$. Also, for any pair of events $A$ and $B$, $\mathbb{P}(AB) = \mathbb{P}(A \mid B)\mathbb{P}(B) = \mathbb{P}(B \mid A)\mathbb{P}(A)$.

**Solution.**

To prove: if $A \perp B$ then $P(A \mid B) = P(A) \qquad$ **a)**

for any pair of events $A, B$: $\quad P(AB) = P(A \mid B)P(B) = P(B \mid A)P(A) \qquad$ **b)**

**a)** we know

$$
\begin{aligned}
P(A \mid B) &= \frac{P(A \cap B)}{P(B)} && \Big|\ A \perp B \\
P(A \mid B) &= \frac{P(A)P(B)}{P(B)} \\
P(A \mid B) &= P(A)
\end{aligned}
$$

**b)** we know

$$
\begin{aligned}
P(A \mid B) &= \frac{P(A \cap B)}{P(B)} \quad \Big|\ \cdot P(B) && \text{inversely} \quad P(B \mid A) = \frac{P(B \cap A)}{P(A)} \quad \Big|\ \cdot P(A) \\
P(A \cap B) &= P(A \mid B)P(B) && \qquad\qquad\qquad\quad\;\; P(B \cap A) = P(B \mid A)P(A)
\end{aligned}
$$

---

## Exercise 17

**Question.** Show that

$$
\mathbb{P}(ABC) = \mathbb{P}(A \mid BC)\,\mathbb{P}(B \mid C)\,\mathbb{P}(C).
$$

**Solution.**

to show $P(ABC) = P(A \mid BC)P(B \mid C)P(C)$

$BC$ also a normal event and $P$ valid probability measure

$$
\Rightarrow P(A \mid BC) = \frac{P(ABC)}{P(BC)} \quad \Big|\ \cdot P(BC)
$$

$$
P(ABC) = P(A \mid BC)\,P(BC)
$$

we know

$$
P(B \mid C) = \frac{P(BC)}{P(C)} \quad \Big|\ \cdot P(C)
$$

$$
P(BC) = P(B \mid C)P(C)
$$

$$
\Rightarrow P(ABC) = P(A \mid BC)\,P(BC) = P(A \mid BC) \cdot P(B \mid C) \cdot P(C)
$$

---

## Exercise 18

**Question.** Suppose $k$ events form a partition of the sample space $\Omega$, i.e., they are disjoint and $\bigcup_{i=1}^{k} A_i = \Omega$. Assume that $\mathbb{P}(B) > 0$. Prove that if $\mathbb{P}(A_1 \mid B) < \mathbb{P}(A_1)$ then $\mathbb{P}(A_i \mid B) > \mathbb{P}(A_i)$ for some $i = 2, \dots, k$.

**Solution.**

We have $k$ disjoint events $A_1, A_2, \dots, A_k$ that form a partition of $\Omega$
$B \subset \Omega$
to show: if $P(A_i \mid B) < P(A_i)$ for some $i$ then $P(A_j \mid B) > P(A_j)$ for some $j$

assume $P(A_i \mid B) \le P(A_i) \quad \forall i \in [k]$

$$
\begin{aligned}
&\Rightarrow \sum_{i=1}^{k} P(A_i \mid B) \le \sum_{i=1}^{k} P(A_i) && \Big|\ A_i\text{'s are disjoint partition of } \Omega \\
& && \quad\; \text{and } P(\cdot \mid B) \text{ is also valid probability measure} \\
&\Rightarrow P\left(\bigcup_{i=1}^{k} A_i \,\Big|\, B\right) \le P\left(\bigcup_{i=1}^{k} A_i\right) \\
& P(\Omega \mid B) \le P(\Omega) \\
& 1 \le 1
\end{aligned}
$$

But we know $P(A_i \mid B) < P(A_i)$ for at least one $i$
$\Rightarrow$ strict inequality $1 < 1$ ↯
$\qquad \Rightarrow \exists j \in [k]$ where $P(A_j \mid B) > P(A_j)$

---

## Exercise 19

**Question.** Suppose that 30 percent of computer owners use a Macintosh, 50 percent use Windows, and 20 percent use Linux. Suppose that 65 percent of the Mac users have succumbed to a computer virus, 82 percent of the Windows users get the virus, and 50 percent of the Linux users get the virus. We select a person at random and learn that her system was infected with the virus. What is the probability that she is a Windows user?

**Solution.**

$$
\begin{aligned}
P(W) &= \tfrac{50}{100} & P(V \mid W) &= \tfrac{82}{100} \\
P(L) &= \tfrac{20}{100} & P(V \mid L) &= \tfrac{50}{100} \\
P(M) &= \tfrac{30}{100} & P(V \mid M) &= \tfrac{65}{100}
\end{aligned}
$$

$$
P(W \mid V) = \frac{P(V \mid W) \cdot P(W)}{P(V \mid W) \cdot P(W) + P(V \mid L) \cdot P(L) + P(V \mid M) \cdot P(M)} = \frac{\frac{82 \cdot 50}{10\,000}}{\frac{82 \cdot 50 + 20 \cdot 50 + 30 \cdot 65}{10\,000}} = \frac{4100}{4100 + 1000 + 1950} =
$$

$$
= \frac{4100}{7050} = \frac{82}{141}
$$

---

## Exercise 20

**Question.** A box contains 5 coins and each has a different probability of showing heads. Let $p_1, \dots, p_5$ denote the probability of heads on each coin. Suppose that

$$
p_1 = 0,\quad p_2 = 1/4,\quad p_3 = 1/2,\quad p_4 = 3/4 \quad\text{and}\quad p_5 = 1.
$$

Let $H$ denote "heads is obtained" and let $C_i$ denote the event that coin $i$ is selected.

(a) Select a coin at random and toss it. Suppose a head is obtained. What is the posterior probability that coin $i$ was selected ($i = 1, \dots, 5$)? In other words, find $\mathbb{P}(C_i \mid H)$ for $i = 1, \dots, 5$.

(b) Toss the coin again. What is the probability of another head? In other words find $\mathbb{P}(H_2 \mid H_1)$ where $H_j$ = "heads on toss $j$."

Now suppose that the experiment was carried out as follows: We select a coin at random and toss it until a head is obtained.

(c) Find $\mathbb{P}(C_i \mid B_4)$ where $B_4$ = "first head is obtained on toss 4."

**Solution.**

$p_1 = 0 \qquad p_2 = \tfrac{1}{4} \qquad p_3 = \tfrac{1}{2} \qquad p_4 = \tfrac{3}{4} \qquad p_5 = 1$

$H$ – heads obtained
$C_i$ – coin $i$ selected

**a)** we select at random $\Rightarrow C_i = \tfrac{1}{5} \quad \forall i \in [5]$

$$
P(C_i \mid H) = \frac{P(H \mid C_i) \cdot P(C_i)}{P(H \mid C_1) \cdot P(C_1) + P(H \mid C_2) \cdot P(C_2) + P(H \mid C_3) \cdot P(C_3) + P(H \mid C_4) \cdot P(C_4) + P(H \mid C_5) \cdot P(C_5)} =
$$

$$
= \frac{p_i \cdot \frac{1}{5}}{\frac{1}{5}(p_1 + p_2 + p_3 + p_4 + p_5)} = \frac{p_i}{\frac{10}{4}} = \frac{2p_i}{5}
$$

**b)**

$$
P(H_2 \mid H_1) = \frac{P(H_2 \cap H_1)}{P(H_1)} = \frac{\sum_{i=1}^{5} P(H_1 \cap H_2 \mid C_i)\,P(C_i)}{\sum_{i=1}^{5} P(H_1 \mid C_i)\,P(C_i)} = \frac{\sum_{i=1}^{5} p_i^2}{\sum_{i=1}^{5} p_i} =
$$

$$
= \frac{0 + \frac{1}{16} + \frac{4}{16} + \frac{9}{16} + \frac{16}{16}}{\frac{10}{4}} = \frac{30}{16} \cdot \frac{4}{10} = \frac{3}{4}
$$

**c)**

$$
P(C_i \mid B_4) = \frac{P(B_4 \mid C_i)\,P(C_i)}{P(B_4)} = \frac{(1 - p_i)^3 p_i\, P(C_i)}{\sum_{i=1}^{5} P(B_4 \mid C_i)\,P(C_i)} = \frac{(1 - p_i)^3 p_i}{\sum_{i=1}^{5} (1 - p_i)^3 p_i} =
$$

$$
= \frac{(1 - p_i)^3 p_i}{0 + \frac{27}{256} + \frac{16}{256} + \frac{3}{256} + 0} = (1 - p_i)^3 p_i \cdot \frac{256}{46} = \frac{128 (1 - p_i)^3 p_i}{23}
$$
