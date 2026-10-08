## Reminder: how randomized Kaczmarz works

Randomized Kaczmarz (RK) solves a consistent linear system $Ax=b$, where $A\in\mathbb{R}^{m\times n}$ has rows $a_1^\top,\dots,a_m^\top$ and $x^\star$ denotes a solution. Starting from an initial guess $x_0$ (for instance $x_0=0$), at each iteration $k$ the algorithm:

1. **Samples a row.** Draw a row index $I_k\in\{1,\dots,m\}$ at random from a fixed PMF $p=(p_1,\dots,p_m)$, independently of all previous draws (sampling **with replacement**).
2. **Projects onto that equation.** Move the current iterate to the closest point on the hyperplane $\{x : a_{I_k}^\top x=b_{I_k}\}$:
$$
x_{k+1}=x_k+\frac{b_{I_k}-a_{I_k}^\top x_k}{\|a_{I_k}\|^2}\,a_{I_k}.
$$

After this step the iterate satisfies equation $I_k$ exactly, so sampling the same row twice in a row (a **collision**) makes no progress.

Two standard choices of PMF are the **row-norm** PMF $p_i=\|a_i\|^2/\|A\|_F^2$ and the **uniform** PMF $p_i=1/m$.
