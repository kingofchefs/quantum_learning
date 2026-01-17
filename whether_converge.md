It can be proved that if the function ($ \mathcal{E}: \mathbb{R}^d\to\mathbb{R}$)has the following features, we can find its global minimum with PSO-w.

1. $\text{there exists } x^{*} \in \mathbb{R}^d \text{ such that } \mathcal{E}(x^*)=inf_{x \in \mathbb{R}^d} \mathcal{E}(x)=: \underline{\mathcal{E}}$

2. $\text{there exists some constant } L_{\mathcal{E}}>0 \text{ such that }$
$$
|\mathcal{E}(x)-\mathcal{E}(x')| \leq L_{\mathcal{E}}(|x|+|x'|)|x-x'| \text{, for all } x, x' \in \mathbb{R}^d
$$ 

3. $\text{either } \overline{\mathcal{E}}:=sup_{x \in \mathbb{R}^d} \mathcal{E}(x)<\infty \text{ or there exists constant }c_{\mathcal{E}}, R>0 \text{ such that }$
$$
\mathcal{E}(x)-\overline{\mathcal{E}} \geq c_{\mathcal{E}}|x|^2, \text{, for all } x \in \mathbb{R}^d \text{ with } |x|\geq R
$$

4. $\mathcal{E} \in C^2(\mathbb{R}^d) \text{ with } ||\nabla^2\mathcal{E}||_{\infty} \leq C_{\mathcal{E}} \text{, for some constant } C_{\mathcal{E}}>0$

5. $\text{there exist } \eta>0 \text{ and } \nu \in (0,\infty) \text{ such that for any } x \in \mathbb{R}^d \text{ there exists a global minimizer } x^* \text{ of } \mathcal{E} \text{(which may depend on x) such that}$
$$
|x-x^*| \leq (\mathcal{E}(x)-\underline{\mathcal{E}})^{\nu}/\eta
$$

Assumption 1 just states that the objective function $\mathcal{E}$ attains its infimum at some $x^* \in \mathbb{R}^d$, which may not necessarily be unique.

Assumption 2 describes the local Lipschitz-continuity of $\mathcal{E}$, entailing in particular that the objective has at most quadratic growth at infinity.

Assumption 3 requires $\mathcal{E}$ to be either bounded or of at least quadratic growth in the farfield

Assumption 4 is required only for the theoretical analysis.

Assumption 5 is the most important one. It states that if the function value at the point is very closed to the global minimum, the point is very closed to one of the global best point.



