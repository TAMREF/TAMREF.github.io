---
layout: post
title: Riemann Mapping Theorem
date: 2020-12-11 00:00
tags: [complex-analysis, math]
categories: complex-analysis
excerpt_separator: <!--more-->
---

Riemann Mapping은 $$\mathbb{C}$$의 모든 simply connected proper subset $$\Omega$$에 대해, Conformal map $$f : \mathbb{D} \to \Omega$$가 존재한다는 매우 강력한 정리이다. 여기서는 짧고 아름다운 nonconstructive한 증명을 다룬다.

Ref: Stein & Shakarchi, Complex Analysis Ch.8

<!--more-->
$$\newcommand{\mb}{\mathbb}$$ $$\newcommand{\abs}[1]{\left\lvert #1 \right\rvert}$$ $$\newcommand{\mr}{\mathrm}$$ $$\newcommand{\mbf}{\mathbf}$$ 
$$\newcommand{\mc}{\mathcal}$$ $$\newcommand{\ev}[1]{\left< #1 \right>}$$

## Montel’s theorem

어떤 함수열 $$\ev{f_n}$$이 수렴하는 부분수열 $$\ev{f_{n(k)}}$$를 갖는다는 사실은 매우 유용하다. 물론 여기서 수렴은 모든 cpt subset에 대한 uniform convergence를 의미한다.

Arzela-Ascoli Theorem의 경우, 정의역이 cpt set인 연속함수들의 함수족 $$\mc{F}$$가 uniformly bdd, equicontinuous면 위 성질을 만족한다는 것을 보장하고 있다. 하지만 이렇게 조건이 까다로우면 복소해석 하는 맛이 안 난다.

**Theorem (Montel).** $$\mb{C}$$의 open subset $$\Omega$$에 대해, $$\mc{F} \subseteq \mc{H}(\Omega)$$ 가 $$\Omega$$의 모든 cpt subset에 대해 uniformly bounded**라면** $$\mc{F}$$는 equicontinuous이고, 수렴하는 부분수열을 갖는다. (단, 함수열의 수렴값이 여전히 $$\mc{F}$$의 원소임은 보장되지 않는다)

증명은 Arzela-Ascoli랑 비슷하고 그래서 좀 길다. 생략.

Lemma를 하나 더 소개한다.

**Lemma 1.** $$\mb{C}$$의 connected open subset $$\Omega$$에 대해, $$\Omega$$의 *injective하고 holomorphic한* 함수열 $$\ev{f_n}$$이 $$\Omega$$의 모든 cpt subset에 대해 $$f \in \mc{H}(\Omega)$$로 uniformly converge한다고 하자. 이 때, $$f$$는 injective이거나 constant이다.

*Proof.* $$f$$가 nonconstant, noninjective라고 하자. 그렇다면 $$z \neq w \in \Omega$$가 존재하여 $$f(z) = f(w)$$이다. 이제 $$g_{n}(z) = f_{n}(z) - f_{n}(w)$$, $$g(z) = f(z) - f(w)$$라고 하자. $$g_{n}$$은 여전히 injective holomorphic이다.

$$w$$는 $$g$$의 zero가 되는데, $$g$$가 nonconstant니까 isolated zero이다. 따라서 $$w$$를 원점으로 하는 작은 원 $$C$$를 잡아서 $$\frac{1}{2\pi i}\int_{C} \frac{g'(z)}{g(z)} = 1$$이 되도록 할 수 있다. 그런데 $$C$$ 위에서 $$g_{n} \rightrightarrows g, g_{n}' \rightrightarrows g'$$이므로 $$\frac{g_{n}’}{g_{n}} \rightrightarrows \frac{g’}{g}$$이다. 그런데 $$g_{n}$$은 injective라서 $$\frac{1}{2\pi i}\int_{C} \frac{g_{n}’(z)}{g_{n}(z)} = 0$$이고, 모순. $$\blacksquare$$

## Riemann Mapping Theorem

Conformal map은 holomorphic bijection을 의미한다. Dirichlet problem같은 미분방정식을 풀 때 conformal map의 존재성은 매우 중요하다; 어떤 conformal map $$f : \Omega \to \mb{D}$$가 경계에서 continuous bijection으로 extend까지 되는 경우, 잘 알려진 해를 갖는 disk에서의 dirichlet problem을 그대로 $$\Omega$$에 이식할 수 있다. 따라서 아무렇게나 $$\Omega$$가 주어졌을 때 Conformal map $$f : \Omega \to \mb{D}$$가 존재하는지는 중요한 문제가 된다. 

후자의 조건인 continuous bijection extension의 경우 $$\Omega$$가 polygon인 경우 가능하다는 것이 잘 알려져 있으며 $$\partial \Omega$$가 smooth closed curve 또는 continuous curve의 경우에도 확장이 가능하다고 하..지만 일단 이건 어려우니까, 지금은 생각하지 않는다. 일단은 conformal map의 존재성을 보자.

우선 $$\Omega = \mb{C}$$인 경우에는 불가능하다. $$f(\mb{C}) \subseteq \mb{D}$$라는 사실 자체가 $$f$$가 bounded entire function이라는 것을 함의하므로 Liouville theorem에 막힌다. 따라서 $$\Omega$$는 최소한 $$\mb{C}$$의 proper open subset이다.

또한, $$f$$는 당연히 연속함수이므로 disk의 simply connectivity를 보존해야 한다. 즉, 임의의 두 경로 사이에 homotopy가 존재하는, simply connected domain이어야 한다.

아직까지 나온게 연속성 argument밖에 없는데, 여기서 벌써 정리가 나오기 때문에 복소해석학이 사기 학문이다.

**Theorem (Riemann).** $$\mb{C}$$의 proper open simply connected subset $$\Omega$$와 고정된 한 점 $$z_0 \in \Omega$$에 대해, $$F(z_0) = 0, F’(z_0) > 0$$을 만족하는 conformal map $$F$$가 유일하게 존재한다.

유일성의 경우 Schwarz lemma를 생각하면 그리 중요한 부분이 아니다. 따라서 conformal map의 존재성만 보이기로 하자.

1. 먼저 $$\Omega$$를 적당한 $$\mb{D}$$의 원점을 포함하는 부분집합으로 보내는 conformal map을 하나 만들자. 즉, 원점을 포함하는 disk의 subset인 경우만 생각할 것이다. $$\Omega$$가 simply connected이므로 $$\log$$를 정의하는 생각을 자연스레 해볼 수 있다. $$\Omega$$가 proper subset임에 주목하여 $$a \notin \Omega$$를 잡고, $$h(z) = \log(z - a)$$로 정의하자. 그렇다면 $$h$$는 holomorphic이고, $$e^{h(z)} = z - a$$이므로 injective이다. 또한 임의의 $$z \neq w$$에 대해 $$h(z) \neq h(w) + 2\pi i$$가 성립해야 하며, exponential function이 연속이므로 $$h(z_{n}) \to h(w) + 2\pi i$$인 수열 $$z_n \in \Omega$$조차 잡을 수 없다. ($$h(z_{n}) \to h(w) + 2\pi i \implies a + e^{h(z_n)} = z_{n} \to w$$) 따라서 어떤 $$w \in \Omega$$에 대해 $$H(z) = \frac{1}{h(z) - h(w) - 2\pi i}$$는 bounded, injective ($$h$$가 injective이므로), holomorphic function이다. 따라서 $$H : \Omega \to H(\Omega)$$는 conformal map이고, 적당한 linear transformation을 끼얹어서 $$H$$를 수정하면 $$H(\Omega)$$가 disk의 subset이고 원점을 포함하게 할 수 있다.
2. 이제 $$\Omega$$가 원점을 포함하는 $$\mb{D}$$의 open subset이라고 가정해도 좋다. 이제, $$f(0) = 0$$을 만족하는 모든 injective holomorphic map $$f : \Omega \to \mb{D}$$의 class를 $$\mc{F}$$라고 두면 자연히 $$\mc{F}$$는 uniformly bounded이다. 더하여, $$z = 0$$ 근처에서 Cauchy integral formula를 생각하면 $$\abs{f’(0)}$$이라는 양 또한 $$f \in \mc{F}$$에 대해 uniformly bounded이다. 따라서 Montel’s theorem에 의해, 모든 $$\mc{F}$$의 수열은 수렴하는 부분수열을 갖는다.
3.   $$s = \sup_{f \in \mc{F}} \abs{f’(0)} < \infty$$를 생각하고, $$\abs{f_{n}'(0)}$$이 $$s$$로 수렴하는 수열 $$\ev{f_n}$$을 잡으면, 수렴하는 부분수열 $$\ev{f_{n(k)}}$$ 가 존재한다. 이 함수열은 모든 $$\Omega$$의 cpt subset에 대해 $$f \in \mc{H}(\Omega)$$로 수렴하는데, $$f$$는 $$\abs{f’(0)} = s > 1$$ ($$id_{\Omega} \in \mc{F}$$)이므로 nonconstant이다. 따라서 Lemma 1에 의해서 $$f$$는 injective holomorphic이고, $$f(0) = 0$$이다. 마지막으로 $$f : \Omega \in \overline{\mb{D}}$$이므로 $$\abs{f(z)} \le 1$$인데, $$f$$가 nonconstant이므로 maximum modulus principle에 의해 $$\abs{f(z)} < 1$$이다. 따라서 $$f \in \mc{F}$$임또한 알 수 있다.
4. 이제 이 $$f$$가 정말로 conformal map임을 보이자. $$f$$가 surjection임만 보이면 충분하다. 귀류법으로 $$f$$가 surjection이 아니라고 하고, $$\alpha \in \mb{D} \setminus f(\Omega)$$라고 두자. 이제 Blaschke factor $$\psi_{\alpha}$$를 합성하면, $$(\psi_{\alpha} \circ f) (U)$$는 원점을 포함하지 않는 simply connected set이다. 따라서 square root function $$g(w) = e^{\frac{1}{2}\log w}$$가 injective holomorphic function이 된다. 이제 $$F = \psi_{g(\alpha)} \circ g \circ \psi_{\alpha} \circ f$$라고 두면 $$F : \Omega \to \mb{D}$$가 되고, $$F$$ 또한 injective holomorphic이므로 $$F \in \mc{F}$$이다. 당연히 $$F(0) = 0$$이다.
5.  한편, $$f = \psi_{\alpha} \circ (z \mapsto z^{2}) \circ \psi_{\alpha} \circ F = \Phi \circ F$$를 생각하자. 이 때, $$\Phi$$의 구성요소들로부터 $$\Phi : \mb{D} \to \mb{D}$$로써 생각한다. ($$F$$의 surjectivity를 가정하지 않았음에 유의하자) $$(z \mapsto z^{2})$$가 $$\mb{D}$$에서 noninjective이므로, Schwarz lemma를 생각하면 $$\abs{\Phi’(0)} < 1$$이다. ($$\abs{\Phi’(0)} \le 1$$의 등호조건은 $$\Phi$$가 rotation인 것) 따라서 $$s = \abs{f’(0)} = \abs{\Phi’(0)} \abs{F’(0)} < \abs{F’(0)}$$이고, $$F \in \mc{F}$$임을 생각하면 모순.

따라서 $$f$$가 holomorphic bijection임을 확인할 수 있다. Schwarz Lemma의 중요성을 다시 눈여겨볼 수 있다. $$\blacksquare$$

