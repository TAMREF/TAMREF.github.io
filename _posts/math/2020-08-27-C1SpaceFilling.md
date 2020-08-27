---
layout: post
title: Non-Existence of $C^{1}$ space-filling curves
date: 2020-08-27 00:00
tags: [analysis, math]
categories: analysis
excerpt_separator: <!--more-->
---



Space-filling curve는 일반적으로 $I := [0,1]$에서 $I \times I$로 가는 continuous onto function을 말한다. Hilbert’s curve, Sierpinski’s curve 등 여러 가지가 알려져 있다. 이런 curve들의 특징은 uniformly converge하는 연속함수열의 극한으로 정의된다는 점인데, 그렇지 않고는 Space Filling Curve를 만들기 굉장히 어렵기 때문이다. 이 포스팅에서는 $C^{1}$ class의 space-filling curve가 존재하지 않음을 보인다.

<!--more-->

$\gamma : I \to I^{2}$이 $C^{1}$ space-filling curve라고 가정해보자. 즉 $\gamma$는 onto이고, $\gamma’$이 연속이다.

그렇다면 $\mathrm{length}(\gamma) = \int_{0}^{1} \lVert \gamma’(t) \rVert dt$는 finite한 값을 가져야 한다.

하지만 $(i/n, j/n)$ 꼴로 주어진 $(n+1)^{2}$개의 점을 생각해 보자. $\gamma$는 이 점들도 모두 지나야 한다. 서로 다른 두 점들 사이의 거리는 $\frac{1}{n}$이상이므로, $\gamma$의 길이는 최소한 $\frac{1}{n} \cdot ((n+1)^{2} - 1) = n+2$ 이상이어야 한다. 당연히 $n$을 무한대로 보내면 이 길이는 무한히 커지고, $\gamma$의 길이가 무한히라는 가정에 모순이 된다. $\blacksquare$