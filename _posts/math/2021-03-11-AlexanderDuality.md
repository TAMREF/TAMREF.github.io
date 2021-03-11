---
layout: post
title: Combinatorial Alexander Duality의 증명
date: 2021-03-11 00:00:00
tags: [combinatorics, topological-combinatorics]
categories: combinatorics
excerpt_separator: <!--more-->
---

Simplicial Complex에서 Alexander Duality는 다음과 같다.
$$
\tilde{H_{i}}(A) \simeq \tilde{H}^{n-i-1}(S^{n} \setminus A)
$$
이 글에서는 그 Combinatorial Variant와 [Björner & Tancer (2007)](https://arxiv.org/pdf/0710.1172.pdf)의 증명을 다룬다.

<!--more-->

$$\newcommand{\pd}{\partial}\DeclareMathOperator{\idx}{idx}\DeclareMathOperator{\im}{im}\newcommand{\abs}[1]{\left\lvert #1 \right\rvert}\newcommand{\bs}{\setminus}\newcommand{\norm}[1]{\left\lVert #1 \right\rVert}$$

모든 set은 finite set이라고 가정한다. 또한, Alexnader Duality의 응용 등에 대해서는 다루지 않는다.

기본적으로 공부 도중에 기록을 위해 만든 post이기 때문에 내용이 추후 가감될 수 있다.

## Alexander Dual

Vertex set $$V$$ 위에 정의된 Simplicial Complex $$\Delta$$ 에 대해, Alexander Dual $$\Delta^{*}$$는 같은 Vertex Set 위에서 다음과 같이 정의된다.
$$
\Delta^{*} := \{\sigma \mid \overline{\sigma} \notin \Delta \}
$$
단, $$\overline{\sigma}$$는 $$\sigma$$의 complement.

Duality라는 이름이 붙은 만큼, 당연히 $$\Delta^{**} = \Delta$$가 성립한다. Matroid Duality와는 전혀 다른 대상인 듯하다.

![image-20210312004006221](https://tamref.github.io/images/alexander.png)

논문의 이미지를 빌린 설명이다. 이 경우 $$S$$의 Facet은 $$\{12, 13, 23, 14\}$$이고, $$S^{*}$$의 facet은 $$\{12, 13\}$$이 된다.

## Homology Group

Commutative Ring $$R$$에 대해, $$\Delta$$의 (reduced) Chain Complex $$\tilde{C}_{\ast}(\Delta, R)$$는 다음과 같은 free basis $$\tilde{B_{i}}$$를 갖는 free $$R$$-module $$\tilde{C_{i}}$$들의 chain으로 정의된다.
$$
\tilde{B_{i}} := \{e_{\sigma} \mid \sigma \in \Delta, \dim \sigma = i\}, i \ge -1
$$
$$\dim \emptyset = -1$$임에 주목하자. $$\sigma = \{\sigma_1, \sigma_2, \cdots, \sigma_{k := \dim \sigma + 1}\}$$이라고 두었을 때 $$e_{\sigma} = \mathbf{e}_{\sigma_1} \wedge \cdots \wedge \mathbf{e}_{\sigma_k}$$ 처럼 생각해도 좋다.

Chain complex의 Boundary map $$\pd_{i}$$는 다음을 만족하는 유일한 homomorphism으로 정의된다.
$$
\pd_{i}(e_{\sigma}) = \sum_{j \in \sigma} (-1)^{\idx_{\sigma}(j) - 1}e_{\sigma \setminus j}
$$
단, $$\idx_{\sigma}(j)$$는 $$j$$가 $$\sigma$$의 몇 번째로 작은 원소인지 (1-based)를 의미한다. 정의로부터 $$\pd_{i-1}\pd_{i} = 0$$임을 알 수 있다. $$i$$에 대한 context가 명확할 때는 그냥 $$\pd$$라고 쓴다.

$$i$$-th Reduced Homology Group $$\tilde{H}_{i}(\Delta) = \ker \pd_{i} / \im \pd_{i+1}$$으로 정의된다. $$\Delta$$가 Graph인 경우, (혹은 1차원으로 $$\Delta$$를 restrict해서 보는 경우) $$\tilde{H}_{0}$$는 $$R^{\beta_{0}-1}$$ (단, $$\beta_{0}$$는 그래프의 connected component 개수), $$\tilde{H_{1}}$$의 free part의 rank는 $$\beta_{1}$$ (Cycle dimension)과 같다.

## Cohomology Group

각 $$e_{\sigma}$$에 대해, Dual basis $$e^{\sigma}$$를 생각하자. $$\tilde{B}^{i} := \{e^{\sigma} \mid \sigma \in \Delta, \dim \sigma = i\}$$를 free basis로 갖는 free module $$\tilde{C}^{i}$$로 이루어진 Cochain complex $$\tilde{C}^{\ast}(\Delta, R)$$를 생각할 수 있다. 이 때 Coboundary operator $$\pd^{i}$$를 다음과 같이 정의하자.
$$
\pd^{i}(e^{\sigma}) = \sum_{j \notin \sigma} (-1)^{\idx_{\sigma + j}(j)} e^{\sigma + j}
$$
$$\pd^{i}$$는 $$\pd_{i}$$의 Dual map이고 (즉, $$C^{i-1} \to C^{i}$$), 이는 $$\left<e^{\tau}, \pd e_{\sigma}\right> = \left<\pd e^{\tau}, e_{\sigma}\right>$$를 검증하면 된다. 별다른 문제가 없으면 얘도 $$\pd$$로 쓴다.

$$i$$-th Reduced Cohomology Group $$\tilde{H}^{i}(\Delta) = \ker \pd^{i+1} / \im \pd^{i}$$로 정의된다.

이제 Combinatorial Alexander Duality를 State할 수 있다:

**Theorem 1 (Combinatorial Alexander Duality)**
$$
\tilde{H}_{i}(\Delta; R) \simeq \tilde{H}^{\abs{V} - i - 3}(\Delta^{*}; R)
$$
$$V$$는 ground set, $$R$$은 chain complex가 정의된 commutative ring이다.

**Cf. (Combinatorial Hodge Theory)**
$$
\tilde{H}_{i}(\Delta; F) \simeq \tilde{H}^{i}(\Delta; F)
$$
Hodge duality가 Field에 대해서만 성립하는 것과 대조된다.

## Relative Homology

$$\Delta \subseteq \Gamma$$인 두 simplicial complex $$\Gamma, \Delta$$를 생각하자. Quotient complex $$\Gamma / \Delta$$는 그냥 $$\Gamma \setminus \Delta$$이다. 이 때 Relative Complex $$C_{i}(\Gamma, \Delta) = C_{i}(\Gamma) / C_{i}(\Delta)$$로 정의된다. Relative Boundary Operator $$d_{i}$$역시 자연스럽게
$$
d_{i}([e_{\sigma}]) = \sum_{j \in \sigma, \\ \sigma \bs j \notin \Delta} (-1)^{\idx_{\sigma}(j) - 1} [{e_{\sigma - j}]}
$$
로 정의된다. (단, $$[e_{\sigma}]$$는 $$e_{\sigma}$$의 equivalence class)

마찬가지로 $$\tilde{H_{n}}(\Gamma, \Delta; R) := \ker d_{n} / \im d_{n+1}$$. 이 때 projection $$\pi : \tilde{C}(\Gamma) \to \tilde{C}(\Gamma, \Delta)$$와 inclusion $$\iota : \tilde{C}(\Delta) \to \tilde{C}(\Gamma)$$로부터 자연스럽게 induce되는 map, 또 $$\pd$$로부터 자연스럽게 induce되는 connecting homomorphism $$\pd^{*}$$에 의한 **Long Exact Homology Sequence**를 찾을 수 있다.
$$
\cdots \to \tilde{H}_{i}(\Gamma) \to \tilde{H}_{i}(\Gamma, \Delta) \to \tilde{H}_{i-1}(\Delta) \to \tilde{H}_{i-1}(\Gamma) \to \cdots
$$
당연한 이야기지만, $$\Gamma \bs \Delta = \Gamma’ \bs \Delta’$$라면 둘의 relative homology는 동일하다. 이로부터, $$\Delta$$의 cone $$C\Delta$$에 대해 $$\tilde{H}(\Gamma, \Delta) \simeq \tilde{H}(\Gamma \cup C\Delta)$$임을 얻을 수 있다. ($$\Delta$$에 해당하는 부분을 모두 “contract”한다고 생각하면 쉽다)

이 LEHS는 증명에 필요한 다음 Lemma를 제공한다.

**Lemma 2.** $$H_{i}(\Delta) \simeq H_{i+1}(2^{V}, \Delta)$$.

*Proof.* Long-exact sequence를 생각하면
$$
\cdots \textcolor{red}{\tilde{H}_{i}(2^{V})=0} \to \tilde{H}_{i}(2^{V}, \Delta) \to \tilde{H}_{i-1}(\Delta) \to \textcolor{red}{H_{i-1}(2^{V})=0} \to \cdots
$$
증명 끝.

## Idea sketch

이제 $$\tilde{H}_{i+1}(2^{V}, \Delta) \simeq \tilde{H}^{\abs{V} - i - 3} (\Delta^{*})$$를 보이면 된다. 적절한 isomorphism을 construct하는 게 목표.

$$\sigma \in 2^{V} / \Delta \implies \overline{\sigma} \in \Delta^{*}$$가 성립한다. 즉, homomorphism $$e_{\sigma} \mapsto e^{\overline{\sigma}}$$같은 mapping을 생각해서, 이게 Chain isomorphism이 된다는 걸 증명하면 둘의 homology도 같다는 사실을 증명할 수 있다. ($$\dim \sigma + \dim \overline{\sigma} = \abs{V} - 2$$임에 주목하면 차원이 맞는다) 

하지만 아쉽게도 이 mapping은 chain isomorphism이 아니고, 때문에 적당한 sign issue를 처리해주어야 한다.

논문에서는 complex에 대응되는 Lattice를 잡고, 이를 “뒤집는다”는 발상을 통해 증명을 떠올렸다고 하는데, 그것이 얼마나 motivational한지는 모르겠다. 

## Proof

$$S(\sigma)$$를 적당히 $$\sum_{i \in \sigma} (i - 1)$$로 정의하자. sign issue를 잡기 위해 사용할 양이다.

**Proposition 3.** $$k \in \sigma$$에 대해, $$\idx_{\sigma}(k) + S(\sigma \bs k) \equiv \idx_{\overline{\sigma} + k}(k) + S(\sigma) \pmod{2}$$.

증명은 계산하면 나온다.

결국 두 homology group이 isomorphic하다는 것을 확인하기 위해, Module isomorphism $$\phi_{j} : C_{j+1}(2^{V}, \Delta) \to C^{\abs{V} - j - 3}(\Delta)$$를 다음과 같이 정의하자.
$$
\phi_{j}(e_{\sigma}) = (-1)^{S(\sigma)} e^{\overline{\sigma}}
$$
이제 $$\phi$$가 $$\phi d = \pd \phi$$를 만족한다는 것만 보이면 $$\phi$$가 chain isomorphism이 되어 증명이 끝난다.
$$
\begin{aligned}
\pd \phi(e_{\sigma}) &= (-1)^{S(\sigma)} \sum_{j \notin \overline{\sigma}, j + \overline{\sigma} \in \Delta^{*}} (-1)^{\idx_{\overline{\sigma} + j}(j)}e^{\overline{\sigma} + j}\\
\phi d(e_{\sigma}) &= \phi(\sum_{j \in \sigma, \sigma - j \notin \Delta }(-1)^{\idx_{\sigma}(j)} e_{\sigma - j})\\
&= \sum_{j \in \sigma, \overline{\sigma} + j \in \Delta^{*}} (-1)^{\idx_{\sigma}(j)}(-1)^{S(\sigma - j)}e^{\overline{\sigma} + j}
\end{aligned}
$$
두 값은 **Proposition 3**에 의해 각 항이 같다. 증명 끝.

## Connection to Classic Alexander Duality

Combinatorial Alexander Duality는 Alexander Duality의 특수한 경우로 볼 수 있다. 편의상 $$\Delta$$가 정의된 $$V = [n+2]$$로 두고, $$S^{n}$$을 $$\pd 2^{[n+2]}$$로 생각하자. 이 때 $$\norm{S^{n}} \bs \norm{\Delta}$$와 $$\norm{\Delta^{*}}$$가 아무튼 homotopy equivalent하다는데, 이걸 이용하면

$$\tilde{H_{i}}(\Delta) \simeq \tilde{H}^{n-i-1}(S^{n} \bs \Delta)$$임이 Alexander Duality에서, $$\tilde{H}^{n-i-1}(S^{n} \bs \Delta) = \tilde{H}^{(n+2)-i-3}(\Delta^{*})$$를 얻을 수 있다. Homotopy equivalence에 대한 증명은 나중에 알게 되면 추가하기로 한다..