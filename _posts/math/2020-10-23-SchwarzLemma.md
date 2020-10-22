---
layout: post
title: Schwarz Lemma and Automorphism on the open disk
date: 2020-10-23 00:00
tags: [complex-analysis, math]
categories: complex-analysis
excerpt_separator: <!--more-->
---

$$\mathbb{C}$$의 open unit disk $$\mathbb{D}$$에 대해, holomorphic function $$f : \mathbb{D} \to \mathbb{D}$$를 생각하자. Schwarz Lemma는 이러한 $$f$$의 성질에 대한 Lemma이고, 이는 $$\mathbb{D}$$의 Automorphism group을 characterize하는 데 큰 도움을 준다.

<!--more-->

$$\newcommand{\mb}{\mathbb}$$ $$\newcommand{\abs}[1]{\left\lvert #1 \right\rvert}$$ $$\newcommand{\mr}{\mathrm}$$ $$\newcommand{\mbf}{\mathbf}$$ $$\newcommand{\ev}[1]{\left< #1 \right>}$$

## Lemma (Schwarz)

$$f : \mb{D} \to \mb{D}$$가 holomorphic이고, $$f(0) = 0$$을 만족한다고 하자. 다음 세 성질이 성립한다.

1. $$\abs{f(z)} \le \abs{z}$$.
2. 만약 $$z_0 \neq 0$$에 대해 $$\abs{f(z_0)} = \abs{z_0}$$가 성립한다면, $$f$$는 rotation.
3. $$\abs{f’(0)} \le 1$$. 등호가 성립한다면 $$f$$는 rotation.



증명은 기초 복소해석을 공부했다면 크게 어렵지는 않다.

*Proof.*

$$f(0) = 0$$이므로, $$g(z) := f(z) / z$$가 역시 $$\mb{D}$$에서 holomorphic이다. 이 때 임의의 $$ r < 1$$에 대해, 반지름 $$r$$짜리 circle $$C_{r}(0) = \partial D_{r}(0)$$를 생각하면
$$
\sup_{z \in C_{r}(0)} \abs{g(z)} = \frac{1}{r}\sup_{z \in C_{r}(0)} \abs{f(z)} \le \frac{1}{r}
$$
이 성립한다. 이 때 $$g$$가 holomorphic이므로 Maximum Modulus Principle에 의해 $$\sup_{z \in D_{r}(0)} \abs{g(z)} \le \frac{1}{r}$$이고, $$r \to 1^{+}$$의 극한에서 $$\abs{g(z)} \le 1\implies \abs{f(z)} \le \abs{z}$$를 얻는다.

만약 $$\abs{g(z_0)} = 1$$을 만족하는 $$z_0 \neq 0$$이 있다면 역시 Maximum Modulus principle에 의해 $$g$$는 constant function이어야 한다. $$g(z) = g(z_0) = e^{i\theta}$$라고 두면, $$f(z) = e^{i\theta}z$$는 rotation이 된다.

$$g(0) = f’(0)$$임에 주목하자. 마찬가지로 $$\abs{g(0)} \le 1$$이어야 하고, $$\abs{g(0)} = 1$$이라면 역시 $$f$$는 rotation이 된다. 증명 끝.



## Applications of Schwarz Lemma

**Definition.** $$\mb{C}$$의 open set $$U, V$$에 대해, $$f : U \to V$$가 holomorphic이고 bijection이면 $$f$$를 **conformal map**이라고 한다. 특별히 $$U = V$$인 경우 $$f$$를 $$U$$의 **automorphism**이라고 한다.

위 정의에서 $$f^{-1} : V \to U$$가 holomorphic임은 보일 수 있다. 

**Proposition.** $$U$$의 모든 automorphism을 모은 집합을 $$\mr{Aut}(U)$$라고 하면, $$(\mr{Aut}(U), \circ)$$는 군을 이룬다.

**Theorem.** $$f \in \mr{Aut}(\mb{D})$$에 대해 $$f(0) = 0$$이라면 $$f$$는 rotation이다.

*Proof.* $$f$$에 대해 Schwarz lemma를 적용하면, $$\abs{f(z)} \le \abs{z}$$가 성립한다. 반면 $$f^{-1}$$에 대해 Schwarz lemma를 적용하면, $$\abs{z} = \abs{f^{-1}(f(z))} \le \abs{f(z)}$$가 성립하여 $$\abs{f(z)} = \abs{z}$$가 되고, $$f$$는 rotation이어야 한다.



이제 이 사실에 기반하여 $$\mr{Aut}(\mb{D})$$를 Characterize하자. 그 전에 다음과 같은 도구를 소개한다.

**Definition.** (Blaschke factor) $$\alpha \in \mb{D}$$에 대해, $$\psi_{\alpha} : \mb{D} \to \mb{D}$$는 $$\mr{Aut}(\mb{D})$$의 원소이며, $$\psi_{\alpha}(0) = \alpha, \psi_{\alpha}(\alpha) = 0$$이다. 그 식은 아래와 같고, 모든 성질을 아래 식으로부터 유도가능하다.
$$
\psi_{\alpha}(z) = \frac{\alpha - z}{1 - \overline{\alpha}z}
$$
또 하나 주목할 만한 성질로, $$\psi_{\alpha} \circ \psi_{\alpha} = \mr{id}_{\mb{D}}$$가 성립한다. 이것도 계산해보면 된다.

**Theorem.** 모든 $$\mr{Aut}(\mb{D})$$의 원소는 $$\psi_{\alpha}$$와 rotation의 합성으로 표현할 수 있다.

$$f \in \mr{Aut}(\mb{D})$$를 생각하자. $$g = \psi_{f(0)} \circ f$$는 $$g(0) = 0$$을 만족하는 Automorphism이므로 rotation이고, 양쪽에 $$\psi_{f(0)}$$를 합성하면 증명 끝.

즉, 모든 $$\mr{Aut}(\mb{D})$$의 원소는 2개의 parameter $$\theta, \alpha$$에 대해
$$
\psi_{\alpha}(z) = e^{i\theta} \frac{\alpha - z}{1 - \overline{\alpha}z}
$$
와 같이 쓸 수 있다.

**Theorem.** $$\mr{Aut}(\mb{D}) \simeq \mbf{SU}(1,1) / \{\pm 1\}$$.

$$\mbf{SU}(1, 1)$$이란 $$J = \begin{pmatrix} 1 & 0 \\ 0 & -1\end{pmatrix}$$에 대해, $$\ev{\mbf{z},\mbf{w}} = \mbf{z}^{\dagger} J \mbf{w}$$와 같이 정의된 Hermitian form $$\ev{\cdot,\cdot} : \mb{C}^{2} \times \mb{C}^{2} \to \mb{C}$$ 을 보존하는 special matrix들의 집합을 말한다. 즉 모든 $$\mbf{z},\mbf{w} \in \mb{C}^{2}$$에 대해 $$\ev{M\mbf{z}, M\mbf{w}} = \ev{z,w}$$를 만족하는 $$\det(M) = 1$$인 matrix들의 집합을 $$\mbf{SU}(1,1)$$이라고 쓴다. 당연히 행렬곱에 대해 군 구조를 가진다.

$$J$$ 자리에 $$I$$를 넣어서 만든 group은 $$\mbf{SU}(2)$$라고 부른다.

열심히 계산을 하면 $$\mbf{SU}(1,1)$$의 모든 원소는 $$\abs{a}^{2} - \abs{b}^{2} = 1$$을 만족하는 $$a, b \in \mb{C}$$에 대해 $$U_{a,b} = \begin{pmatrix} a & b \\ \overline{b} & \overline{a} \end{pmatrix}$$의 꼴로 쓸 수 있다는 사실을 증명할 수 있다. 이 때 $$a = ue^{i\theta}, b = ve^{i\phi}$$라고 쓰면, $$u^{2} - v^{2} = 1$$이 성립한다. 이 때 $$\alpha = -b / a$$에 대해, $$\varphi : U_{a,b} \mapsto e^{2i\theta}\psi_{\alpha}$$는 two-to-one homomorphism이 된다. $$U_{a,b}$$에 의해 만들어지는 linear fractional map $$z \mapsto (az + b) / (\overline{b} z + \overline{a})$$가 $$e^{2i\theta} \psi_{\alpha}$$와 같고, 이 관계로부터 map이 group homomorphism임을 쉽게 보일 수 있다.

따라서 $$\ker\varphi = \{\pm 1\}$$로부터 $$\mbf{PSU}(1,1) := \mbf{SU}(1,1) / \{\pm 1\} \simeq \mr{Aut}(\mb{D})$$를 얻고, 추가적으로 $$\mb{Aut}(\mb{D})$$가 $$\mb{D} \times S^{1}$$의 기하적 구조를 가지므로 $$\mbf{PSU}(1,1) \approx \mb{D} \times S^{1}$$임도 알 수 있다.

