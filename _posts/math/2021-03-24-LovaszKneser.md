---
layout: post
title: Tucker's Lemma를 이용한 Kneser's Conjecture 증명
date: 2021-03-24 00:00:00
tags: [combinatorics, topological-combinatorics, graph-theory]
categories: combinatorics
excerpt_separator: <!--more-->
---


$[n] = \{1, \cdots, n\}$과 $2 \le 2k \le n$에 대해, Kneser graph $\mar{KG}(n, k)$는 $\binom{[n]}{k}$를 정점 집합으로 하고, $S \cap S' = \emptyset$인 모든 $S, S'$에 대해 간선을 이어준 그래프로 정의된다. Lovasz-Kneser Theorem (Kneser's conjecture)란 이 그래프의 chromatic number $\chi(\mar{KG}(n, k)) \ge n - 2k + 2$가 성립한다는 정리이다. 이 글에서는 Tucker's lemma를 이용한 J. Matousek의 증명을 소개한다.

<!--more-->

## Tucker’s lemma

Tucker’s lemma는 Borsuk-Ulam theorem의 이산적인 버전으로 생각할 수 있다. 자세한 대응 관계를 보이는 것은 간단하지 않으므로, statement를 우선 받아들이기로 하자.

**Lemma (Tucker).** $n$-차원 ball $B^{n}$의 triangulation $T$의 정점들이 그 경계인 $\partial B^{n} = S^{n-1}$에서 antipodally symmetric이라고 하자. 즉, $v \in S^{n-1}$에 $T$의 정점이 있으면 $-v$에도 정점이 있다. 이 때, $\lambda : V(T) \to \{\pm 1, \pm 2, \cdots, \pm n\}$이 모든 $v \in S^{n-1}$에 대해 $\lambda(-v) = -\lambda (v)$를 만족하면, $\lambda(u) + \lambda(v) = 0$인 $uv \in E(T)$가 존재한다.

Lemma의 증명 역시 생략한다.

## Kneser’s conjecture

귀류법으로, coloring $c$가 존재하여 $\mar{KG}(n, k)$를 $n - 2k + 1$가지 색으로 칠한다고 하자. 이 색을 $2k, \cdots, n$과 같이 번호를 매긴다. 이제 적당한 $B^{n}$의 triangulation $T$를 잡아서 Tucker’s lemma로 귀결시켜보자.

정점이 $$\{\maf{0}, \pm \maf{e}_{1}, \cdots, \pm\maf{e}_{n}\}$$으로 주어진 $B^{n}$ (정확히는 “정팔면체”)의 자연스러운 triangulation $K$를 생각해 보자. 이 때, $$L = K \setminus \{\maf{0}\}$$에 대해, barycentric subdivision $L’$을 생각하자. 이제 여기서 다시 $\maf{0}$을 집어넣고 모든 simplex를 이어주면 (즉, $$\maf{0}$$에 대한 cone을 만들어주면) simplex $K’$을 얻을 수 있다.

- 여담으로, $K$의 refinement로 triangulation이 주어지는 경우, Tucker’s lemma의 pure combinatorial proof가 알려져 있다. 언젠가 시간이 나면 적을 예정

아무튼 $K’$은 자명히 antipodally symmetric이다. 이제 $x \in V(K’)$을 $n$차원 벡터로 보았을 때, $[n]$의 서로소인 부분집합 $x^{+}, x^{-}$를 다음과 같이 정의할 수 있다.
$$
x^{+} := \{i \in [n] \mid x_{i} > 0\}, \quad x^{-} := \{i \in [n] \mid x_{i} < 0\}
$$
이 때, $V(K’)$의 labeling $\lambda$를 정의하자. 집합들의 total order $\le$를 $\sz{A} < \sz{B}$이면 $A < B$가 성립하고, 크기가 같은 경우에는 아무 tie-breaker (사전순 등)를 주어서 정의한다.

1. $\sz{x^{+}} + \sz{x^{-}} \le 2k-2$인 경우
   $$
   \lambda(x) := \begin{cases} \sz{x^{+}} + \sz{x^{-}} + 1 & x^{+} \ge x^{-} \\ -(\sz{x^{+}} + \sz{x^{-}} + 1) & x^{+} < x^{-} \end{cases}
   $$
   이 경우 $\sz{\lambda(x)} \le 2k - 1$이다.

2. $\sz{x^{+}} + \sz{x^{-}} \ge 2k - 1$인 경우
   둘 중 (정의한 order $\le$에 따라) 큰 집합 $x^{big}$의 크기가 $k$ 이상임에 주목하자. 이 때 $x^{big}$의 가장 작은 $k$개 원소로 이루어진 집합을 $A$라고 할 때,
   $$
   \lambda(x) := \begin{cases} c(A) & x^{+} > x^{-} \\ -c(A) & x^{+} < x^{-}\end{cases}
   $$
   로 정의한다. 이 경우 $\sz{\lambda(x)} \ge 2k$이다.

$\lambda(-v) = -\lambda(v)$를 보장하는 것만 중요하기 때문에 tie-breaker를 아무렇게나 주어도 된다. $x^{+} = x^{-}$인 경우는 둘 모두 공집합인 $x = \maf{0}$뿐임을 생각하자. 실제로 Tucker’s lemma가 요구하는 것보다 강한 조건인, 모든 $v \in V(K’)$에 대해 $\lambda(-v) = -\lambda(v)$가 성립한다.

Tucker’s lemma를 적용하면, $\lambda(v) + \lambda(w) = 0$인 $vw \in E(K’)$이 존재한다. $E(K’)$의 구조를 생각해보면, $\maf{0}$이 한 끝점이거나 $L’$의 한 면의 barycentric subdivision에 속한다. 두 경우 모두 $v^{\pm} = (v^{+}, v^{-}), w^{\pm} = (w^{+}, w^{-})$에 inclusion order를 줬을 때 $v^{\pm} < w^{\pm}$ 또는 $v^{\pm} > w^{\pm}$이 성립해야 한다는 사실을 알 수 있다.

1. $\sz{\lambda(v)}, \sz{\lambda(w)} \le 2k - 1$일 수 없다는 것이 이제 자명하다. $v^{\pm} < w^{\pm}$이라고 하면 $\sz{v^{+}} + \sz{v^{-}} < \sz{w^{+}} + \sz{w^{-}}$이기 때문.
2. 따라서 $\sz{\lambda(v)} \ge 2k$이다. 편의상 $\lambda(v) = -\lambda(w) > 0$이라고 가정하자. 이 경우 $v^{+} \cap w^{-} = \emptyset$이고, 따라서 $c(A) = \lambda(v) = -\lambda(w) = c(B)$를 만족하는 크기 $k$인 두 집합 $A \subseteq v^{+}, B \subseteq w^{-}$는 서로소이다. 즉 $\mar{KG}(n, k)$에서 $A, B$는 같은 색을 갖는 연결된 간선으로, $c$가 coloring임에 모순이다. 증명 끝.