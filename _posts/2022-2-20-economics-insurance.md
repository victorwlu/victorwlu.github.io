---
layout: post
title: Economics of insurance
published: true
---
Let's look in this article at how insurance can be a win-win deal. Consider a property owner who has a utility of wealth function $u(w)$. The owner faces a possible loss due to random events that may damage the property. The distribution of the loss $X$ is assumed to be known. According to utility theory, the owner will be indifferent between paying an amount $G$ to the insurer, who will assume the random financial loss, and assuming the risk himself if:

$$ u(w-G) = E[u(w-X)]$$

# Case 1, linear utility function
If the owner has an increasing linear utility function, $u(w)=bw+d$ with $b>0$. In this case the owner prefers, or is indifferent to the insurance when:

$$
\begin{aligned}
u(w-G) = b(w-G)+d &\geq E[u(w-X)] = E[b(w-X)+d] \\
b(w-G)+d &\geq b(w-\mu) +d \\
G &\leq \mu
\end{aligned}
$$

The owner thus prefers the insurance when the premium paid is less than or equal to the expected loss. However, an insurer to be profitable over the long term must charge more than its expected loss. In the case of this linear utility function, there seems to be little opportunity for a win-win contract. Yes, actually most people don't have a linear utility function but a concave one.

# Case 2, decreasing marginal utility
It seems natural to assume that $u(w)$ is an increasing function, more money is better. Moreover, it has been observed that for many decision makers, each additional increment of wealth results in smaller increment of associated utility. This is the idea of decreasing marginal utility.

Mathematically, it can be stated as:

$$
\left\{
    \begin{array}{ll}
        u'(w)>0\\
        u''(w)<0
    \end{array}
\right.
$$

Jensen's inequality state that for a random variable $X$ and function $u(w)$,

$$ \text{if } u''(w)<0, \text{then } E[u(X)] \leq u(E[X])$$

Let's apply this inequality to the previous problem, we have:

$$ u(w-G) = E[u(w-X)] \leq u(w-\mu) $$

Because $u(w)$ in an increasing function. Therefore, we have $G\geq \mu$. It means that the decision maker is willing to pay an amount greater than the expected loss for insurance. If $G$ is a least equal to the premium set by the insurer, there is an opportunity for a *win-win* insurance contract.
