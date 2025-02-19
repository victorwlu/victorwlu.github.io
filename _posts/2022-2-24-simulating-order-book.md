---
layout: post
title: Simulating order book data
published: true
---

In this article, let's look at a quick way to model a limit order book (LOB). I will rely heavily on C. Lehalle's paper: *Simulating and analyzing order book data: The queue-reactive model* (2014).

# Framework
Consider the LOB as a $2K$-dimensional vector, where $K$ denotes the limits on each side. The reference price $p_{ref}$ defines the center of the $2K$-dimensional vector. The simulation technique considered first will assume $p_{ref}$ constant, so that we look only at the endogenous evolution of the order-book (i.e. without news information).
It divides the LOB into two parts: the bid side $[Q_{-i} : i = 1,\dots, K]$ and the ask side $[Q_{i} : i = 1,\dots, K]$, where $Q_{\pm i}$ represents the limit at distance $i-0.5$ ticks to the right ($+i$) or to the left ($-i$) of $p_{ref}$. The number of orders at $Q_i$ is denoted by $q_i$. We consider a constant order size at each limit equal to the average event size $AES_{i}$.

The $2K$-dimensional process $X(t)=(q_{-K}(t), \dots, q_{K}(t)$ is modeled as a continuous-time Markov jump process in the countable state space $\Omega = \mathbb{N}^{2K}$, with jump size equal to 1.

# Model: collection of independent queues
Three types of orders are considered: limit orders (L), cancellations (C) and market orders (M). We suppose that the intensities $\lambda_L, \lambda_C, \lambda_M$ of these point processes are only functions of the queue size.

We define an event $\omega$ as any modification of the queue size. For queue $Q_i$, we record the waiting time $\Delta t_i (\omega)$ (in seconds) between the event $\omega$ and the preceding event at $Q_i$; the type of event $T_i(\omega)$ and the queue size $q_i(\omega)$ before the event. When the reference price changes, we restart the recording process.

We denote: $T_i \in E^{+}$ for a limit order insertion at $Q_i$, $T_i \in E^{-}$ for a limit order cancellation at $Q_i$, $T_i \in E^{t}$ for a market order at $Q_i$.

The maximum-likelihood estimation method gives the following estimates:

$$
\begin{aligned}
\hat{\Lambda}_i(n) &= (\text{mean}(\Delta t_i(\omega) | q_i(\omega) = n ))^{-1} \\
 \hat{\lambda}_{i}^{L}(n) &= \hat{\Lambda}_i(n) \frac{Card(T_i \in E^{+}, q_i(\omega)=n)}{Card(q_i(\omega)=n)} \\
  \hat{\lambda}_{i}^{C}(n) &= \hat{\Lambda}_i(n) \frac{Card(T_i \in E^{-}, q_i(\omega)=n)}{Card(q_i(\omega)=n)} \\
   \hat{\lambda}_{i}^{M}(n) &= \hat{\Lambda}_i(n) \frac{Card(T_i \in E^{t}, q_i(\omega)=n)}{Card(q_i(\omega)=n)}
\end{aligned}
$$

After getting those intensities, we can compute the invariant distribution of the LOB. The invariant distribution is given by Gross and Harris (1998):

$$
\begin{aligned}
\pi_i(n) &= \pi_i(0) \prod_{j=1}^n \rho_i (j-1) \\
\pi_i(0) &= \left( 1+ \sum_{n=1}^{\infty} \rho_i (j-1)\right)^{-1} \\
\rho_i(n) &= \frac{\lambda_{i}^{L}(n)}{\lambda_{i}^{C}(n+1)\lambda_{i}^{M}(n+1)}
\end{aligned}
$$

Then, comparing the asymptotic results of the model with the empirical distributions observed will allow us to see if the model fits correctly or not.

test