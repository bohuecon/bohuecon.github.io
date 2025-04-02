## Anonymous Shopping versus Personalization: A Model of Consumer Privacy Choice

## 1. The model 

Consider a retailer selling a large number of different goods to consumers. Each consumer can only be matched with one good, deriving positive value from their matched good and zero value from the unmatched good. Specifically, a consumer's utility from the matched good is given by $\theta v$, where $v \sim U[0,1]$ represents the horizontal match quality (how well a specific product matches the consumer's taste preferences), and $\theta$ captures the consumer's vertical quality preference (willingness-to-pay for quality) and is their private information. A high $\theta$ indicates a consumer with strong purchasing power who values quality and product fit, while a low $\theta$ suggests a price-sensitive consumer who views products as more substitutable. We assume $\theta$ follows a continuous atomless distribution with c.d.f. denoted by $G(\theta)$ on the support of $[\underline{\theta},\bar{\theta}]$.

When making a purchase, consumers face two options: they can either log in with their account or shop anonymously. For anonymous purchases, the retailer can only recommend goods with limited information and we assume an anonymous consumer can find their matched good with probability $\mu$. The retailer sets a uniform price, denoted by $p_A$, for all anonymous consumers. The retailer can not set a different price for different goods because all of them are homogeneous ex ante.

If a consumer logs in, with probability $\lambda$, the retailer can use big data analytics (including external purchasing history) to identify the consumer's taste. Once identified, the retailer can accurately recommend the matched good and charge a personalized price based on the consumer's $\theta$. With probability $1-\lambda$, the retailer cannot identify the consumer and thus treats them as an anonymous consumer.

#### Timing

The game proceeds as follows:

1. The retailer sets prices:
   - A uniform price $p_A$ for anonymous transactions
   - Personalized prices $p_I(\theta)$ for identified consumers

2. After observing these prices, consumers choose their shopping mode (login or anonymous).

3. Product matching and purchasing occurs:
   - For logged-in consumers:
     * With probability $\lambda$: Consumer is identified, receives matched good, and faces price $p_I(\theta)$
     * With probability $(1-\lambda)$: Consumer remains unidentified, receives random good, and faces price $p_A$
   - For anonymous consumers:
     * With probability $\mu$: Consumer finds matched good
     * With probability $(1-\mu)$: Consumer receives random good
     * All anonymous transactions are priced at $p_A$
   - In all cases:
     * If matched: Consumer draws match quality $v \sim U[0,1]$ and decides whether to purchase
     * If unmatched: Consumer receives zero value and does not purchase

## 2. Equilibrium 

### 2.1 Consumers

The equilibrium concept is subgame perfection. Consumers purchasing decision is trivial, they will purchase only if the value $\theta v$ is higher than the price $p$. To consider whether a consumer will log-in or shop anonymously, we can consider the expected utility in either case.

**Anonymous purchase**

Given $p_A$, a consumer of $\theta$ will have a positive expected value only if $p_A > \theta$ (otherwise, even a matched good with $v = 1$ can only deliver a value of $\theta$ which is not enough to cover $p_A$). Let the expected value denoted by $u_N(\theta)$ where $N$ represents NOT identified by the retaier. If $\theta < p_A$, then $u_N(\theta) = 0$. Otherwise, the expected value is
$$\begin{aligned}
u_N(\theta, p_A) = \mu \int_{p_A}^{\theta}(x-p_A) \frac{1}{\theta}dx 
= \mu \Big(\frac{\theta}{2} - p_A + \frac{p_A^2}{2\theta}\Big)
\end{aligned}
$$ In this derivation, we have used $x = \theta v$ to simplify the integral.
$$
u_N(\theta, p_A) = \begin{cases}
0 & \text{if } \theta < p_A \\
\mu \Big(\frac{\theta}{2} - p_A + \frac{p_A^2}{2\theta}\Big) & \text{if } \theta \geq p_A
\end{cases}
$$

**Log-in purchase** 

Suppose a consumer chooses to log in. With probability $1-\lambda$, the retailer can not identify the consumer. In this case, the consumer will receive a value of $u_N(\theta, p_A)$. With probability $\lambda$, the retailer can identify the consumer, observes the consumer's $\theta$, and recommend the matched good. Then the retailer charges a monopoly price. The retailer's problem becomes (assuming production cost is zero)
$$\max_{p} \ \Pr(p\leq \theta v) p.$$ Given that $v$ follows a uniform distribution on the support of $[0,1]$, the problem is equivalent to
$$\max_{p} \frac{\theta - p}{\theta}p.$$ Then the optimal price is $p_I(\theta) = \theta/2$ and the retailer's profit from this consumer is $\pi_I(\theta) = \theta/4$. The consumer receives a surplus of 
$$
u_I(\theta) = \int_{p_I(\theta)/\theta}^{1}(\theta v-p_L(\theta))dv = \int_{1/2}^{1}(\theta v-\theta/2)dv = \frac{\theta}{8}.
$$

**Consumer's Log-in vs. Anonymous decision**

The expected value of log-in purchase is
$$
V_L(\theta, p_A) = \begin{cases}
\lambda \theta/8 & \text{if } \theta < p_A \\
\lambda \theta/8 +  (1-\lambda)\mu \Big(\frac{\theta}{2} - p_A + \frac{p_A^2}{2\theta}\Big)& \text{if } \theta \geq p_A
\end{cases}
$$
And the expected value of anonymous purchase is
$$
V_A(\theta, p_A) = \begin{cases}
0 & \text{if } \theta < p_A \\
\mu \Big(\frac{\theta}{2} - p_A + \frac{p_A^2}{2\theta}\Big)& \text{if } \theta \geq p_A
\end{cases}
$$

By comparing $V_L(\theta, p_A)$ and $V_A(\theta, p_A)$, we can see that if $\theta < p_A$, the consumer always log-in. If $\theta \geq p_A$, the consumer will log-in if and only if $$\frac{\theta}{8} > u_N(\theta, p_A) = \mu \Big(\frac{\theta}{2} - p_A + \frac{p_A^2}{2\theta}\Big).$$

Note that $u_N(\theta, p_A) = 0$ if $p_A = \theta$, and then as $p_A > \theta$ increases, $u_N(\theta, p_A)$ increases. Therefore, the consumer will log in shop if and only if $\theta$ is not too large.
Let $\tilde{\theta}$ denote the threshold of $\theta$ such that $\frac{\tilde{\theta}}{8} = \mu \Big(\frac{\tilde{\theta}}{2} - p_A + \frac{p_A^2}{2\tilde{\theta}}\Big)$. Then the threshold $\theta^\ast \equiv \min\{\tilde{\theta}, \bar{\theta}\}$ such that consumers log-in shop if and only if $\theta < \theta^\ast$ and shop anonymously otherwise. 

In the following figures, we plot $V_A(\theta, p_A)$ and $V_L(\theta, p_A)$ for different values of $p_A$ and obtain the corresponding $\theta^\ast$ (which is the interaction of the two lines). Notice these $p_A$ are not necessarily the optimal price. These figures are only for illustration purpose. The key take away is that $p_A$ affects the threshold $\theta^\ast$ and the consumer's log-in decision.

![Utility comparison between login and anonymous purchase](utility_comparison_multiple.png)

### 2.2 The retailer's optimal price

Let's analyze the retailer's optimal price for anonymous purchases by examining the profit obtained from different types of consumers:

1. For identified consumers (those successfully recognized after logging in), the retailer earns a profit of $\pi_I(\theta) = \theta/4$.

2. For non-identified consumers (either anonymous shoppers or unrecognized logged-in users), the profit is:
$$
\pi_N(\theta, p_A)  = \begin{cases}
0 & \text{if } \theta < p_A \\
\mu\Big(1-\frac{p_A}{\theta}\Big)p_A & \text{if } \theta \geq p_A
\end{cases}
$$

The retailer's total profit across all consumers is:
$$
\begin{aligned}
\Pi(p_A) = &\int_{\underline{\theta}}^{p_A} \lambda \frac{\theta}{4} dG(\theta) + \int_{p_A}^{\theta^\ast}\Big(\lambda \frac{\theta}{4} + (1-\lambda)\mu\Big(1-\frac{p_A}{\theta}\Big)p_A \Big)dG(\theta) \\ &+ \int_{\theta^\ast}^{\bar{\theta}} \mu\Big(1-\frac{p_A}{\theta}\Big)p_A dG(\theta)
\end{aligned}
$$

This profit function reflects three distinct consumer segments:
1. Low-value consumers ($\theta < p_A$): They always log in and only purchase when identified (with probability $\lambda$) at the personalized price.
2. Medium-value consumers ($p_A \leq \theta \leq \theta^\ast$): They log in and purchase either at the personalized price (if identified) or at the anonymous price $p_A$ (if unidentified and matched).
3. High-value consumers ($\theta > \theta^\ast$): They shop anonymously and purchase only when matched with their preferred product at price $p_A$.

To find the optimal $p_A \in [0, \bar{\theta}]$, we take the first-order derivative of $\Pi(p_A)$. Note that $\theta^\ast(p_A)$ is a function of $p_A$. Using Leibniz's rule for differentiation under the integral sign:
$$
\begin{aligned}
\frac{d\Pi}{dp_A} = &\lambda \frac{p_A}{4}g(p_A) - \Big(\lambda \frac{p_A}{4} + (1-\lambda)\mu\Big(1-\frac{p_A}{p_A}\Big)p_A \Big)g(p_A) \\
&+ \int_{p_A}^{\theta^\ast} (1-\lambda)\mu\Big(-\frac{1}{\theta} + \frac{p_A}{\theta^2}\Big)p_A + \Big(1-\frac{p_A}{\theta}\Big) dG(\theta) \\
&+ \Big(\lambda \frac{\theta^\ast}{4} + (1-\lambda)\mu\Big(1-\frac{p_A}{\theta^\ast}\Big)p_A \Big)g(\theta^\ast)\frac{d\theta^\ast}{dp_A} \\
&- \mu\Big(1-\frac{p_A}{\theta^\ast}\Big)p_A g(\theta^\ast)\frac{d\theta^\ast}{dp_A} \\
&+ \int_{\theta^\ast}^{\bar{\theta}} \mu\Big(-\frac{1}{\theta} + \frac{p_A}{\theta^2}\Big)p_A + \Big(1-\frac{p_A}{\theta}\Big) dG(\theta)
\end{aligned}
$$
Combine all terms:
$$
\begin{aligned}
\frac{d\Pi}{dp_A} &= \int_{p_A}^{\theta^\ast} (1-\lambda) \mu \left( 1 - \frac{2 p_A}{\theta} \right) dG(\theta) \\
&+ \int_{\theta^\ast}^{\bar{\theta}} \mu \left( 1 - \frac{2 p_A}{\theta} \right) dG(\theta) \\
&+ \left[ \lambda \frac{\theta^\ast}{4} - \lambda \mu \left(1 - \frac{p_A}{\theta^\ast}\right) p_A \right] g(\theta^\ast) \frac{d\theta^\ast}{dp_A}
\end{aligned}
$$

This is the first-order condition to set to zero for the optimal \(p_A\), once \(\theta^\ast(p_A)\) and \(G(\theta)\) are specified.

Let's analyze the forces that prevent $p_A$ from reaching the upper bound $\bar{\theta}$. Looking at $\frac{d\Pi}{dp_A}$:

1. The third term is positive because the retailer's profit from charging $p_A$ cannot exceed the monopoly profit $\theta^\ast/4$.

2. In the first two integral terms, the expression $1 - \frac{2p_A}{\theta}$ changes sign:
   - For $\theta < 2p_A$: The expression is negative because $p_A$ exceeds the monopoly price $\theta/2$. Increasing $p_A$ reduces profit from these consumers.
   - For $\theta > 2p_A$: The expression is positive because $p_A$ is below the monopoly price. Increasing $p_A$ raises profit from these consumers.

3. When the distribution $G(\theta)$ has more mass on lower values of $\theta$, the negative effect from small-$\theta$ consumers dominates, pushing the optimal $p_A$ down from the upper bound $\bar{\theta}$. This explains why $p_A$ can stay below $\bar{\theta}$.

For a reasonable parameter setting (see the script login.jl), we plot the retailer's profit as a function of $p_A$. 

![Retailer's profits as a function of $p_A$](profit_function.png)

We then plot the utilities for consumers with different $\theta$ values under two scenarios: when they are identified ($u_I(\theta) = \theta/8$) and when they are not identified ($u_N(\theta, p_A)$), where $p_A$ is set at the retailer's optimal price. The figure reveals three distinct consumer segments:

1. Low-$\theta$ consumers: These consumers always log in but only make purchases when identified. This allows them to benefit from personalized pricing ($\theta/2$), which is lower than the anonymous price $p_A$.

2. Medium-$\theta$ consumers: These consumers log in and make purchases regardless of whether they are identified. When identified, they receive personalized prices; when not identified, they still find the anonymous price $p_A$ acceptable.

3. High-$\theta$ consumers: These consumers choose to shop anonymously. Despite potentially benefiting from personalized recommendations when logging in, they prefer anonymous shopping to avoid price discrimination that would extract too much of their surplus.

![Retailer's profits as a function of $p_A$](utility_comparison.png)

### Comparative Statics
Our numerical analysis of the comparative statics reveals how the threshold $\theta^\ast$ responds to changes in identification probability $\lambda$ and matching probability $\mu$:

1. Effect of identification probability ($\lambda$): As $\lambda$ increases, $\theta^\ast$ increases. This occurs because higher $\lambda$ means fewer login consumers are treated as anonymous shoppers. Consequently, the retailer can raise $p_A$ with less concern about losing profits from unidentified login consumers.

2. Effect of matching probability ($\mu$): As $\mu$ increases, $\theta^\ast$ decreases. When anonymous matching becomes more effective, anonymous purchase gains a higher weight in the revenue of the retailer. Thus, the retailer has a lower incentive to raise $p_A$.

![Comparative Statics with respect to $\lambda$ and $\mu$.](optimal_price_sensitivity.png)


### Policy Implications

Our model provides a framework to evaluate several privacy-protection policies. First, we can analyze the impact of data collection restrictions by examining how changes in λ (the probability of successful identification) affect market outcomes. Such restrictions might include limiting the duration of data storage or requiring periodic data deletion, effectively reducing the retailer's ability to identify consumers. Second, we can evaluate a "right to be forgotten" policy by extending our model to include an additional stage where identified consumers can choose to delete their data and revert to anonymous shopping after observing their personalized price p_I(θ). This policy is particularly relevant as it has been implemented in various jurisdictions, including the EU's GDPR. Finally, we can assess the welfare implications of requiring retailers to maintain an anonymous shopping option by comparing our baseline model with a counterfactual where retailers can mandate login. This comparison is especially pertinent for essential goods and services where consumers might have limited alternatives. For each policy, we can quantify the effects on consumer surplus across different θ segments, overall social welfare, and market efficiency in terms of matching quality.

