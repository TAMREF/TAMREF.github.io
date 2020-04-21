---
layout: post
title: Sketching Arzela-Ascoli theorem
use_math: true
date: 2020-04-20 00:00:00
excerpt_separator: <!--more-->
categories: analysis
tags: [math, analysis]
---

Arzela-Ascoli theorem을 따로 알아야 할 상황이 생겨서, 해석개론에서 약간의 지름길을 타서 이 정리를 건드려보기로 했다.

Compactness에 대한 통찰을 요구한다.

Ref: 김성기, 김도한, 계승혁 - 해석개론

<!--more-->

$$\renewcommand\norm[1]{\left\lVert#1\right\rVert}\newcommand{\ev}[1]{\left<#1\right>}\newcommand{\mb}{\mathbb}\newcommand{\mc}{\mathcal}\renewcommand\abs[1]{\left\lvert #1 \right\rvert}$$

* $$N_{\varepsilon}(x) := \{y \mid \norm{x - y} < \varepsilon \}$$. 무엇의 부분집합인지는 context에 의존한다.

## Uniformly continuous function

함수 $$f$$가 정의역 $$X$$에서 uniformly continuous하다는 말은, given $\varepsilon > 0$에 대해
$$
\exists \delta \; \forall x, y \in X \quad \norm{x-y} < \delta \implies \norm{f(x) - f(y)} < \varepsilon \label{def:ufcon}
$$
를 만족한다는 것을 말한다.



**Heine’s theorem.**

> Compact set $$X$$에 대해 연속함수 $$f : X \to Y$$는 uniformly continuous하다.



*Proof.* Given $$\varepsilon > 0$$에 대해, $$f$$는 연속함수이므로 $$\forall y \in X \cap N_{\delta (x)}(x)$$ $$\norm{f(x) - f(y)} < \varepsilon/2$$을 만족하도록 각 $$x$$에 대해 양수 $$\delta(x) > 0$$을 잡을 수 있다. 이 때, $$\{N_{\delta(x)/2}(x)\}_{x \in X}$$는 $$X$$의 cover가 되고, $$X$$는 cpt set이므로 finite subcover가 존재한다. 이를 $$\{N_{\delta(x_i)/2}(x_i)\}_{i=1,\cdots,n}$$이라고 두자. $$\delta := \min_{i}\{\frac{\delta(x_i)}{2}\}$$가 조건을 만족함을 보이자.

$$\norm{x-y} < \delta$$라고 하자. 이 때, $$\norm{x - x_{i}} < \frac{\delta(x_{i})}{2}$$를 만족하는 $$x_{i}$$가 존재한다. 이 때 $$\norm{y - x_{i}} \le \norm{x - x_{i}} + \norm{y - x} < \delta + \frac{\delta(x_{i})}{2} < \delta(x_{i}) $$이므로 $$x,y$$는 모두 $$N_{\delta(x_{i})}(x_{i})$$의 element이다. 따라서 $$\norm{f(x) - f(y)} \le \norm{f(x) - f(x_i)} + \norm{f(y) - f(x_i)} < \varepsilon$$이 성립하고, 따라서 $$f$$는 uniformly continuous. $$\square$$



**Theorem 1.** $$f : X \to Y$$가 고른연속이고 $$\ev{x_n}$$이 $$X$$의 Cauchy 수열이면 $$\ev{f(x_n)}$$ 또한 $$Y$$의 Cauchy 수열이다.

*Proof.* $$f$$가 uniformly continuous이므로 임의의 $$\varepsilon > 0$$에 대해, $$\norm{x - y} < \delta \implies \norm{f(x) - f(y)} < \varepsilon$$를 만족하는 양수 $$\delta > 0$$이 존재한다. $$\ev{x_n}$$은 Cauchy이므로 $$m, n \ge N \implies \norm{x_m - x_n} < \delta$$를 만족하는 자연수 $$N$$이 존재한다. 역시 $$n, m \ge N \implies \norm{f(x_m) - f(x_n)} < \varepsilon$$ 이 성립하므로 $$\ev{f(x_n)}$$ 또한 Cauchy이다. $$\square$$



**Corollary 2.** $$f : X \to \mb{R}^{n}$$가 uniformly continuous라고 하면, $$f$$는 $$\overline{X}$$까지 확장될 수 있다.

*Proof.* $$z$$가 $$X$$의 limit point라고 하자. 그렇다면 $$z$$로 수렴하는 $$X$$의 수열 $$\ev{x_n}$$을 잡을 수 있다. 수렴하는 수열은 Cauchy 수열이므로 **Theorem 1**에 의해 $$\ev{f(x_n)}$$ 또한 Cauchy 수열이고, $$\mb{R}^{n}$$이 complete이므로 $$\ev{f(x_n)}$$은 수렴한다. $$\lim_{n} f(x_n) = \alpha$$라고 할 때, $$f(z) = \alpha$$가 well-defined임을 보이는 것은 어렵지 않다. $$\square$$

*Note.* $$f := x \mapsto \frac{1}{x}$$는 $$(0,1)$$에서 고른연속이 아니다; 실제로 $$f$$는 $$x = 0$$에 대해 확장될 수 없다.



## Continuous Function Space

Compact set $$X$$에 대해 $$X$$에서 $$\mb{R}^{m}$$으로 가는 연속함수의 집합 $$C(X, \mb{R}^{m})$$ (줄여서 $$C(X)$$)은 자연스러운 vector space 구조를 갖는다. 함수 $$f \in C(X)$$의 norm을 $$\norm{f}_{\sup} := \sup_{x\in X} \norm{f(x)}$$으로 두면 Max-min theorem에 의해 $$\norm{f}_{\sup} < \infty$$가 성립하고, $$(C(X), \norm{\cdot}_{\sup})$$은 normed space (metric space)가 된다.



$$C(X)$$의 ‘수열’은 연속함수열이 되고, $$C(X)$$에서 수열의 수렴성은 함수열의 uniform convergence로 대체된다.

**Remark.** $$C(X)$$의 수열 $$\ev{f_n}$$이 $$f$$로 수렴하면 $$f \in C(X)$$이다. 즉, $$C(X)$$는 closed.



**Theorem 3.** $$C(X)$$의 Cauchy sequence는 항상 수렴한다. 즉, $$C(X)$$는 complete metric space이다.

*Proof.* Given $$\varepsilon > 0$$에 대해 $$m, n \ge N \implies \norm{f_m - f_n}_{\sup} < \varepsilon$$을 만족하는 자연수 $$N$$이 존재한다고 하자. 따라서 모든 $$x \in X$$에 대해 $$m, n \ge N \implies \norm{f_m (x) - f_n (x)} < \varepsilon$$을 만족한다. 따라서 $$\ev{f_{n}(x)}$$는 $$\mb{R}^{m}$$의 Cauchy 수열이고, $$\mb{R}^{m}$$의 completeness에 의해 수렴값 $$\alpha_x$$가 존재한다. 이 때 $$f(x) := \alpha_{x} = \lim_{n} f_{n}(x)$$로 두자. 이 때 $$n \ge N$$에 대해 $$\lim_{m \to \infty} \norm{f_m - f_n}_{\sup} = \norm{f - f_{n}}_{\sup} \le \varepsilon$$이므로 $$\ev{f_n}$$은 $$f$$로 uniformly converge한다. $$\square$$



**Definition.** 함수들의 모임 $$\mc{F}$$에 대해, Given $$\varepsilon > 0$$에 대해
$$
\forall f \in \mc{F}, \forall x, y \in X \quad \norm{x-y} < \delta \implies \norm{f(x) - f(y)} < \varepsilon \label{def:eqcon}
$$
다음을 만족하는 $$\delta > 0$$이 존재하면 $$\mc{F}$$는 $$X$$에서 equicontinuous라고 한다.

**Proposition 4.** $$X$$가 cpt set이고 $$C(X)$$의 함수열 $$\ev{f_n}$$이 $$X$$에서 uniformly converge하면 $$\{f_n\}$$은 equicontinuous하다.

*Proof.* $$\ev{f_n}$$이 $$f$$로 수렴한다고 하자. $$\ev{f_n}$$은 수렴하므로 Cauchy이다. (이 사실의 증명은 짧지만 $$\mb{R}^{N}$$ case와 등가는 아니다) 따라서 Given $$\varepsilon > 0$$에 대해 $$n \ge N \implies \norm{f_n - f_N}_{\sup} < \varepsilon$$가 성립하는 자연수 $$N$$이 존재한다. **Heine’s thm**에 의해 $$f_N$$은 uniformly continuous이므로 $$\forall x , y \in X$$ $$\norm{x - y} < \delta \implies \norm{f_{N}(x) - f_{N}(y)} < \varepsilon$$을 만족하는 $$\delta > 0$$이 존재한다. 따라서 모든 $$n \ge N$$에 대해 $$\norm{x - y} < \delta \implies \norm{f_n (x) - f_n(y)} \le \norm{f_n(x) - f_N (x)} + \norm{f_N (x) - f_N (y)} + \norm{f_N (y) - f_n (y)} < 3\varepsilon$$이 성립하고, 따라서 $$\{f_{n}\}_{n \ge N}$$은 $$X$$에서 equicontinuous이다. 이 때 singleton $$\{f_i\}$$는 $$X$$에서 equicontinuous하고, 함수족 $$\mc{F}$$와 $$\mc{G}$$가 모두 $$X$$에서 equicontinuous하면 $$\mc{F} \cup \mc{G}$$ 또한 equicontinuous하므로 $$\{f_n\}_{n \ge 1}$$ 또한 equicontinuous하다. $$\square$$

**Theorem 5.** Metric space에서 cptness와 sequential cptness는 동치이다.

**Arzela - Ascoli Theorem.** cpt set $$X$$에 대해, metric space $$C(X)$$의 부분집합 $$\mc{F}$$가 (점별)유계이고 equicontinuous이면 $$\mc{F}$$ 안의 임의의 함수열 $$\ev{f_n}$$은 수렴하는 부분수열을 갖는다. 특별히 $$\mc{F}$$가 closed이면, $$\mc{F}$$는 sequentially compact하다; 따라서 $$\mc{F}$$가 closed, (pointwise-)bounded, equicontinuous하면 $$\mc{F}$$는 compact하다.

*Proof.* 자연수 $$N$$에 대해 $$\{N_{1/n}(x) \mid x \in X\}$$는 $$X$$의 open cover가 되고, $$X$$가 compact니까 finite subcover가 존재한다. 이 subcover에서 open ball들의 중심만 모아놓은 유한집합을 $$D_{n}$$이라고 하자.
$$
D := \bigcup_{i=1}^{\infty} D_{i}
$$
라 두면 $$\overline{D} \subset X$$는 $$X$$가 closed임에서, $$X \subset \overline{D}$$는 $$D$$의 정의로부터 얻을 수 있어서 $$\overline{D} = X$$가 된다. $$D$$는 countable set이 되므로 $$D := \{x_i\}_{i \ge 1}$$으로 두자.

이제 대각선 논법을 통해 $$\mc{F}$$의 함수열 $$\ev{f_n}$$의 수렴하는 부분수열을 찾는다. 실수열 $$\ev{f_n(x_1)}$$은 유계이므로 Bolzano-Weierstrass theorem에 의해 수렴하는 부분수열이 존재하고, 이를 $$\ev{f_{1n}(x_1)}$$으로 표기하자.

똑같이 $$\ev{f_{1n} (x_2)}$$를 생각하면 이 녀석도 수렴하는 부분수열을 갖는다. 이를 $$\ev{f_{2n}(x_2)}$$라고 하자. 계속해서 $$\ev{f_{in}(x_{i+1})}$$의 수렴하는 부분수열을 $$\ev{f_{i+1,n}(x_{i+1})}$$로 정의하면 함수열 $$\ev{f_{in}(x_i)}$$는 $$x_1, \cdots, x_i$$에서 수렴하는 $$\ev{f_n}$$의 부분수열이 되고, $$\ev{f_{i+1,n}}$$은 $$\ev{f_{in}}$$의 부분수열이 됨에 주목하자. $$g_{k} := f_{kk}$$로 두면 $$\ev{g_k}$$는 $$\ev{f_n}$$의 (중복 없는) 부분수열이 되고, 각 $$x_i$$에서 점별-수렴하는 함수열이다. 이제 $$\ev{g_n}$$이 (균등-)수렴하는 수열임을 보이자.

$$\mc{F}$$가 동등연속이므로, Given $$\varepsilon > 0$$에 대해 $$\forall f \in \mc{F}, \forall x, y \in X\;\; \norm{x-y} < \delta \implies \norm{f(x) - f(y)} < \varepsilon $$을 만족하는 양수 $$\delta > 0$$을 잡을 수 있다. $$\overline{D} = X$$이므로 $$\{N_{\delta}(x_{i})\}_{i \ge 1}$$은 $$X$$의 open cover가 되고, finite subcover가 존재해서 자연수 $$p$$에 대해 $$X \subset N_{\delta}(x_{i_1}) \cup \cdots \cup N_{\delta}(x_{i_p})$$가 성립한다. 즉, 임의의 $$x \in X$$에 대해 $$\norm{x - x_{i_j}} < \delta$$인 $$j \in \{1, \cdots,p\}$$가 존재한다. 편의상 $$x^{*} := x_{i_j}$$로 두자. 이 때 $$\ev{g_n}$$은 $$x^{*}$$에서 수렴하므로, 임의의 $$u, v \ge N$$에 대해 $$\norm{g_u (x^{*}) - g_v (x^{*})} < \varepsilon$$을 만족하는 자연수 $$N$$이 존재한다. 따라서 $$\norm{g_u (x) - g_v (x)} \le \norm{g_u (x) - g_u (x^{*})} + \norm{g_u(x^{*}) - g_v(x^{*})} + \norm{g_v (x^{*}) - g_v (x)} < 3\varepsilon$$이 성립하고, $$u, v \ge N$$에 대해 $$\norm{g_u - g_v}_{\sup} \le 3\varepsilon$$이 되므로 $$\ev{g_n}$$은 Cauchy이고, 따라서 수렴한다. $$\square$$

**Example 6.**

“Pulse” $$f : \mb{R} \to \mb{R}$$를 다음과 같이 정의하자.
$$
f(x) = \begin{cases} \sin(\pi x) & (x \in [0,1]) \\ 0 & (\text{otherwise}) \end{cases}
$$
$$f_{n}(x) = f(x + n)$$으로 주어진 함수열 $$\ev{f_n}$$은 (uniformly) bounded이고, equicontinuous하지만 convergent subsequence를 갖지 않는다. “진행하는 pulse”를 생각하면 꽤 직관적인 사실이다. 이는 $$\ev{f_n}$$의 domain인 $$\mb{R}$$이 compact하지 않기 때문으로, 정의역의 compactness가 Arzela-Ascoli theorem의 적용에 critical함을 보여주는 예시이다. 알려준 Starrysky에게 감사.

**Problem 7.**

이 예제도 Starrysky한테 받아왔다.

$$\mc{F} \subset C([0,1])$$이 $$(0,1)$$에서 미분가능한 함수들 중에서 아래 조건을 만족하는 함수들의 집합으로 주어졌다고 하자.
$$
\sup_{f \in \mc{F}}\sup_{t \in (0,1)} \abs{f'(t)} < M_{1} < \infty \quad \text{and} \quad \sup_{f \in \mc{F}} \abs{f(0)} < M_{2} < \infty.
$$
(단, $$M_{1}, M_{2} > 0$$) 이 때, $$\mc{F}$$ 안의 임의의 함수열은 수렴하는 부분수열을 가짐을 보여라.

*Proof.* $$\mc{F}$$가 bounded이고 equicontinuous임을 보이면 된다.

- $$\mc{F}$$ is bounded.
  $$t \in [0,1]$$에 대해 $$\sup_{f \in \mc{F}} \abs{f(t)} \le \sup_{f \in \mc{F}}(\abs{f(0)} + M_{1} \cdot t) \le M_{2} + M_{1} t < \infty$$이므로 $$\mc{F}$$는 pointwise-bounded. $$\square$$

- $$\mc{F}$$ is equicontinuous.
  Given $$\varepsilon > 0$$에 대해, 임의의 $$x, y \in [0,1]$$에 대해서 $$\abs{x - y} < \frac{\varepsilon}{M_{1}}$$이라면 임의의 $$f \in \mc{F}$$에 대해
  $$
  \abs{f(x) - f(y)} = \abs{\int_{x}^{y}f'(t)dt} \le \sup\abs{f'(t)} \cdot \abs{y-x} \le M_{1} \abs{y-x} < \varepsilon
  $$
  이므로 $$\mc{F}$$는 equicontinuous.$$\square$$

따라서 Arzela-Ascoli theorem에 의해 $$\mc{F}$의 임의의 함수열은 수렴하는 부분수열을 갖는다.