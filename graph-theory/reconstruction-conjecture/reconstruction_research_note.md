# Graph reconstruction and a restricted theorem

*Ordinary uncoloured decks of bipartite graphs*

25 November 2026 — Working research note

**Status.** This note does not solve the Kelly–Ulam reconstruction conjecture. It gives a complete argument for a restricted class, together with explicit obstructions to broader proof attempts. The argument was derived and reviewed within this AI-assisted research session; it has not been checked in a proof assistant or independently reviewed by a human expert. Its novelty has not been established.

## 1. Statement and relation to existing work

All graphs below are finite, simple and undirected. The ordinary deck is

$$
\mathcal D(G)=\{\!\{\operatorname{iso}(G-v):v\in V(G)\}\!\},
$$

where $\operatorname{iso}$ denotes the unlabelled isomorphism class and multiplicities are retained. A graph is reconstructible if every graph with the same deck is isomorphic to it. We call a graph 2-connected when it has at least three vertices, is connected, and remains connected after deleting any one vertex.

Define the degree type of a vertex by

$$
\tau_G(v)=\left(d_G(v),\{\!\{d_G(w):w\in N_G(v)\}\!\}\right).
$$

**Theorem 1**. *Every 2-connected bipartite graph whose vertex degree types are pairwise distinct is reconstructible from its ordinary, uncoloured vertex-deleted deck.*

The type-inversion idea is closely related to Appendix B.4 of Tsoukalas et al. [1]. Their stated result uses incidence deletion, which retains the deleted vertex as an isolate, and a fixed bipartition preserved by card isomorphisms. The present argument concerns ordinary cards without supplied side colours. The balanced-side alignment argument in Section 6 is the additional step developed here. Neither statement resolves the unrestricted reconstruction conjecture.

## 2. Information that the ordinary deck determines

Suppose $G,H$ have the same deck on $n\ge3$ vertices. Choose a bijection $f:V(G)\to V(H)$ such that $G-v\cong H-f(v)$ for each $v$. Every edge occurs in exactly $n-2$ cards, so

$$
e(G)=\frac{1}{n-2}\sum_{C\in\mathcal D(G)}e(C),
 \qquad d_G(v)=e(G)-e(G-v).
$$

Thus the degree multiset, and the degree associated with each missing vertex, are determined by the deck.

Let $D_k$ be the number of degree-$k$ vertices in $G$, let $c_{v,k}$ be that number in $G-v$, and put

$$
a_{v,k}=\#\{w\in N_G(v):d_G(w)=k\}.
$$

Comparing the degree histograms before and after deletion gives

$$
c_{v,k}=D_k-\mathbf 1_{\{d_G(v)=k\}}-a_{v,k}+a_{v,k+1}.\tag{1}
$$

Since $a_{v,0}=0$, this recurrence determines all $a_{v,k}$. Consequently

$$
\tau_G(v)=\tau_H(f(v)).\tag{2}
$$

This is the familiar reconstructibility of the neighbourhood degree list; see also Barrus and Donovan [2]. Relabel $H$ along $f$ from now on. Then $G,H$ have the same vertex set, their types agree pointwise, and $G-u\cong H-u$ for every $u$. No isomorphism between different cards has been assumed to agree on their surviving vertices.

## 3. A polynomial lemma

The following elementary fact supplies the balanced-side argument.

**Lemma 2**. *Let $P$ be a nonzero polynomial over $\mathbb Q$ in indeterminates $z_0,\ldots,z_{n-1}$. If $z_j-1$ divides $P$ for each of $k$ distinct indices $j$, then $P$ has at least $k+1$ nonzero homogeneous components of distinct total degrees.*

*Proof.* Write $P=\sum_{i=1}^{\ell}H_{d_i}$, where the $H_{d_i}$ are nonzero homogeneous polynomials and $d_1<\cdots<d_\ell$. Assume for contradiction that $\ell\le k$. For any selected coordinate $z_j$, divisibility implies $P|_{z_j=1}=0$. Evaluating this identity at the rational vector $z/z_j$ gives

$$
0=P(z/z_j)=\sum_{i=1}^{\ell}z_j^{-d_i}H_{d_i}(z).
$$

Put $D=d_\ell$ and select $\ell$ distinct indices $j_1,\ldots,j_\ell$ among the available factors. Multiplication by $z_{j_r}^{D}$ gives the system

$$
\sum_{i=1}^{\ell}z_{j_r}^{D-d_i}H_{d_i}(z)=0,
 \qquad 1\le r\le\ell.
$$

Its coefficient determinant is nonzero: different permutations in the determinant expansion give distinct monomials $\prod_r z_{j_r}^{D-d_{\pi(r)}}$, because the exponents $D-d_i$ are distinct. The matrix is therefore invertible over $\mathbb Q(z_0,\ldots,z_{n-1})$. All $H_{d_i}$ must vanish, a contradiction. ◻

## 4. How bipartite deletion changes a type polynomial

Use the common type data from (2) to define

$$
m_v(z)=\prod_{k=0}^{n-1}z_k^{a_{v,k}},
 \qquad P_U(z)=\sum_{v\in U}m_v(z).
$$

The total degree of $m_v$ is $d(v)$, so the monomial encodes the whole type, including the vertex degree. Under the distinct-type hypothesis the $m_v$ are pairwise distinct.

Fix a vertex $u$ of degree $d$ in a bipartite graph. For a vertex $x$ in the opposite part, every surviving neighbour of $x$ is in $u$'s own part, and hence is not adjacent to $u$. Those neighbours retain their degrees when $u$ is deleted. It follows that the type monomial of $x$, computed intrinsically in the card, is

$$
m_x \quad\text{if }x\notin N(u),
 \qquad m_x/z_d \quad\text{if }x\in N(u).
$$

Thus the sum $L_u$ of local type monomials on the card's opposite side obeys

$$
L_u=P_{\operatorname{opp}(u)}+(1-z_d)Q_u,
 \qquad Q_u=\sum_{x\in N(u)}m_x/z_d.\tag{3}
$$

The quotients in $Q_u$ are polynomials, since every neighbour of $u$ has one occurrence of degree $d$ in its profile. Equation (3) uses no identification of the individual vertices inside a card.

## 5. Recognising the bipartite structure and part sizes

Every card of $G$ is connected and bipartite, so the same holds for every card of $H$. This implies that $H$ is connected and has no cut vertex.

If $H$ were nonbipartite, a shortest odd cycle would have to use every vertex; otherwise it would survive in a bipartite card. Such a spanning shortest odd cycle has no chord, since a chord creates a shorter odd cycle. Therefore $H$ would be an odd cycle. Its degree multiset would make the connected graph $G$ another cycle of the same odd order, contradicting bipartiteness. Hence $H$ is also 2-connected and bipartite.

Each card is connected and therefore has a unique bipartition up to swapping its two parts. If the original part sizes are $p\le q$, their values are recovered from the deck by

$$
q=\max_{C\in\mathcal D(G)}\{\text{larger part size of }C\},
 \qquad p=n-q.
$$

The maximum is attained by deleting from a smaller part. In particular, $G,H$ have the same unordered pair of part sizes.

### Unequal parts

Suppose $p<q$, and orient both bipartitions so their first parts have size $p$. Deleting from the smaller part gives card sizes $\{p-1,q\}$, whereas deleting from the larger part gives $\{p,q-1\}$. These patterns are distinct, even if $q=p+1$. The card-matching bijection therefore preserves the original parts.

Only cards deleting a vertex of the smaller part are needed. In each of these, the opposite side is intrinsically the unique part of size $q$. Thus the matched cards have equal $L_u$, and their opposite-side global polynomials $P_{\operatorname{opp}(u)}$ also agree. Equation (3) and cancellation give

$$
\sum_{x\in N_G(u)}m_x
 =z_dQ_u^G=z_dQ_u^H
 =\sum_{x\in N_H(u)}m_x.\tag{4}
$$

Distinct monomials identify individual neighbours. Recovering all neighbourhoods in the smaller part recovers every edge. We do not need to orient cards deleting from the larger part; some of those cards are balanced when $q=p+1$.

## 6. Balanced parts: forcing a consistent alignment

Suppose now that both parts have size $s$. Write the bipartitions, on the common vertex set obtained by relabelling along $f$, as

$$
G:\ A\sqcup B,\qquad H:\ A'\sqcup B'.
$$

Every card has part sizes $s-1$ and $s$. The side opposite its deleted vertex is intrinsically the size-$s$ side. Hence matched cards have equal $L_u$, even though we have not yet shown that the global bipartitions agree.

Partition the common vertex set into four blocks:

$$
X=A\cap A',\ Y=A\cap B',\ Z=B\cap A',\ W=B\cap B'.
$$

Set

$$
R=P_Z-P_Y,\qquad S=P_W-P_X.
$$

For $u\in X\cup W$, the difference between the two global opposite-side polynomials is $R$ or $-R$. By equality of $L_u$ and equation (3),

$$
z_{d(u)}-1\mid R\qquad(u\in X\cup W).
$$

Likewise, for $u\in Y\cup Z$ that difference is $S$ or $-S$, giving

$$
z_{d(u)}-1\mid S\qquad(u\in Y\cup Z).
$$

Let

$$
\alpha=\#\{d(u):u\in X\cup W\},
 \qquad \beta=\#\{d(u):u\in Y\cup Z\}.
$$

Suppose both unions are nonempty. Since the vertex monomials are all distinct and the positive and negative index sets are disjoint, $R,S$ are nonzero. The monomials in $R$ have degrees among the $\beta$ values occurring in $Y\cup Z$, but $R$ is divisible by $\alpha$ distinct coordinate-minus-one factors. Lemma 2 implies

$$
\beta\ge\alpha+1.
$$

Applying the same argument to $S$ implies

$$
\alpha\ge\beta+1,
$$

a contradiction. Thus either $Y=Z=\varnothing$ or $X=W=\varnothing$. The bipartitions agree, possibly after one global swap of $A',B'$.

Now the global opposite-side polynomial agrees for each matched card. Cancelling $1-z_d$ in (3) yields (4) for every $u$. Distinctness of the $m_x$ identifies the neighbour sets and proves $G=H$ on the relabelled vertex set. This completes the proof of Theorem 1.$\square$

### A weaker invariant without distinct types

**Proposition 3**. *For balanced 2-connected bipartite graphs, the ordinary deck determines the unordered pair of degree-type multisets on the two bipartition sides.*

*Proof.* Run the balanced argument without assuming distinct monomials. If $R,S$ were both nonzero, $R$ would still have at most $\beta$ homogeneous components and $S$ at most $\alpha$, so the same contradiction applies. Therefore $R=0$ or $S=0$. The first equality says the side polynomials agree with the current orientation; the second says they agree after swapping $H$'s sides. ◻

## 7. Scope, a concrete instance, and the unresolved step

The theorem includes balanced graphs whose two sides have identical degree multisets. For example, the bipartite graph with biadjacency matrix

$$
\begin{pmatrix}
 0&0&1&0&0&1\\
 1&0&1&0&1&1\\
 0&0&0&1&0&1\\
 1&1&0&1&1&1\\
 1&1&0&0&0&1\\
 1&1&0&1&0&0
 \end{pmatrix}
$$

is 2-connected, has twelve distinct types, and has degree multiset $\{2,2,3,3,4,5\}$ on each side. These properties are checked by the accompanying finite verifier. The polynomial argument is needed to handle the side ambiguity without an assumption that their degree multisets differ.

Two substantive obstacles prevent this proof from establishing the full conjecture:

1.  With repeated types, equality of sums of $m_x$ gives counts of neighbours of each type, not the identity of each neighbour. The final inference in (4) no longer follows.

2.  In a nonbipartite graph there is no opposite side on which all surviving neighbour degrees remain unchanged. Deleting $u$ may change the degrees of other neighbours of $x$, so the simple factor identity (3) is unavailable.

The additional invariant above does not repair either gap. Extending the proof to all bipartite graphs, and then to arbitrary graphs, remains unresolved here.

## 8. Explicit obstructions found during the attempt

### Distinct global types do not label a surviving card

Let $F$ be the cone over a five-vertex path $p_1p_2p_3p_4p_5$: an apex is adjacent to every path vertex. Add a vertex $x$ adjacent to $\{p_5,p_4\}$ to form $G_0$, or adjacent to $\{p_5,p_3\}$ to form $H_0$. Both share the same card $F$, and both have the same seven pairwise-distinct types:

$$
\begin{gathered}
 (2;3,4),\ (2;3,5),\ (3;2,3,5),\ (3;2,4,5),\\
 (3;3,4,5),\ (4;2,3,3,5),\ (5;2,3,3,3,4).
\end{gathered}
$$

Nevertheless $G_0$ has five triangles and $H_0$ has four. Thus a card plus all distinct global types need not determine its completion. This is not a counterexample to reconstruction: their full decks differ. It explains why the proof above must establish alignment instead of assuming it.

### There need not be any uniquely completable card

A stronger attempted lemma was that every graph has some card which, together with the entire multiset of degree types, determines the graph. Exhaustive generation and exact canonicalisation found that this holds through seven vertices but fails for four graphs on eight vertices.

Here is a short explicit certificate. All three graphs below have vertex set $\{0,\ldots,7\}$; $ij$ abbreviates the edge $\{i,j\}$:

$$
\begin{aligned}
 E(K)&=\{12,13,04,34,05,25,36,46,27,57,67\},\\
 E(K_1)&=\{02,03,23,14,24,15,36,56,47,57,67\},\\
 E(K_2)&=\{02,13,23,14,24,05,46,56,37,57,67\}.
\end{aligned}
$$

Their common type multiset is

$$
(2;3,3)^{\times2},\quad(3;2,3,3)^{\times4},
 \quad(3;3,3,3)^{\times2}.
$$

Their cards satisfy

$$
\begin{aligned}
 K-0&\cong K-1\cong K_1-1,\\
 K-6&\cong K-7\cong K_1-7,\\
 K-2&\cong K-3\cong K-4\cong K-5\cong K_2-2.
\end{aligned}
$$

The graph $K$ has two triangles, both with vertex degrees $(3,3,3)$. The graph $K_1$ has two triangles, one with degrees $(2,3,3)$; $K_2$ has one triangle. Hence neither alternative is isomorphic to $K$, yet every card of $K$ has an alternative completion with the same full type multiset.

The corresponding exact small-order experiment was:

| Order | All graphs | One card plus all types suffices | Two required |
| ---: | ---: | ---: | ---: |
| 3 | 4 | 4 | 0 |
| 4 | 11 | 11 | 0 |
| 5 | 34 | 34 | 0 |
| 6 | 156 | 156 | 0 |
| 7 | 1,044 | 1,044 | 0 |
| 8 | 12,346 | 12,342 | 4 |

Here "two required" means the minimum number of selected cards when the entire global type multiset is supplied as additional data. This is not the usual reconstruction number. These calculations do not prove a two-card bound for arbitrary order.

### Spectral information does not force a one-card completion

A separate exact certificate constructs two nonisomorphic eleven-vertex graphs sharing a ten-vertex card $B$, the same full type multiset, and the same characteristic polynomials for both the graphs and their complements. The card's walk matrix has rank nine, leaving only one non-main direction. Thus even a one-dimensional spectral ambiguity need not correspond to a card automorphism. This fits the exceptional case in the reconstruction criteria of Wang, Wen and Guo [3].

For reproducibility, the card has the edges $04,24,05,35,45,16,26,46,56,17,37,47,57$ and $08,28,48,19,39,69,89$. Add vertex $10$ adjacent to $\{0,1\}$ or to $\{2,3\}$. Let $z=(1,1,-1,-1,0,0,0,0,0,0)^T$ and let $A$ be the adjacency matrix of $B$. Then $Az=0$ and $z^T\mathbf 1=0$. The reflection

$$
Q=I-zz^T/2
$$

commutes with $A$, fixes $\mathbf 1$, and exchanges the two attachment vectors. The resulting block-diagonal orthogonal similarity proves both spectral equalities, including those of the complements.

For the walk matrix $W=(\mathbf 1,A\mathbf 1,\ldots,A^9\mathbf 1)$, the submatrix on rows $1,\ldots,9$ and columns $0,\ldots,8$ has determinant $7424$. Together with $z^TW=0$, this proves $\operatorname{rank}W=9$. Every automorphism of $B$ fixes this walk space pointwise, so it is either $I$ or $Q$; $Q$ is not a permutation matrix. Thus $B$ is asymmetric. In both extensions the added vertex is the unique degree-two vertex, so an isomorphism would have to fix it and induce the identity on $B$, which cannot exchange its two neighbourhoods. The shared type multisets are verified directly by the accompanying script. These graphs also have different full decks.

## 9. Verification and provenance

The proof of Theorem 1, particularly the polynomial lemma and the balanced partition argument, received separate reviews from three model research threads. This is an internal correctness check, not an independent publication or a Lean verification. The finite certificates use exact integer or rational arithmetic and exact graph isomorphism checks. The scripts need only the Python standard library. The small-graph enumeration is evidence for the explicitly stated finite experiment, not a substitute for the theorem's proof or evidence of a solution to the full conjecture.

The checked literature still treats the general conjecture as open; the 2026 invariant-theory article [4] is one current primary source. A public reconstruction project [5] also records an explicitly unresolved main conjecture; its umbrella project credits Claude assistance. This corrects the earlier overly broad claim that no documented systematic AI-assisted reconstruction effort had been found.

## References

1. G. Tsoukalas et al., *Advancing Mathematics Research with AI-Driven Formal Proof Search*, arXiv:2605.22763v2, 8 June 2026, Appendix B.4. <https://arxiv.org/html/2605.22763v2>.
2. M. D. Barrus and E. Donovan, *Neighborhood degree lists of graphs*, Discrete Mathematics 341 (2018), 175–183. <https://arxiv.org/abs/1507.08212>.
3. W. Wang, W. Wen and S. Guo, *A Characterization of Generalized Cospectrality of Rooted Graphs with Applications in Graph Reconstruction*, Electronic Journal of Combinatorics 32(4) (2025), P4.33. <https://doi.org/10.37236/13610>.
4. E. Dufresne, G. Jeronimo, J. Kenkel, H. Lindo and N. Villamizar, *Shuffling the Deck: Invariant Theory and the Graph Reconstruction Conjecture*, arXiv:2604.16567v1, 17 April 2026. <https://arxiv.org/html/2604.16567v1>.
5. S. Schlesinger, *Reconstruction Conjecture: Formalization in Lean 4*, public research repository, accessed 25 November 2026. <https://github.com/SamuelSchlesinger/reconstruction-conjecture>. AI attribution: <https://github.com/SamuelSchlesinger/open-conjecture-formalizations>.
