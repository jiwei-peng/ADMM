# Alternating Direction Method of Multipliers (ADMM)

The Alternating Direction Method of Multipliers (ADMM) is an algorithm designed to solve convex optimization problems of the form

$$
\min_{x,z}  f(x) + g(z)\quad \text{subject to} \quad Ax + Bz = c,
$$

where $f$ and $g$ are convex functions.


## Augmented Lagrangian

The augmented Lagrangian function associated with this problem is

$$
L_\rho(x,z,\lambda)=f(x)+g(z)+\lambda^T(Ax+Bz-c)+\frac{\rho}{2}\Vert Ax+Bz-c \Vert_2^2
$$

where $\rho > 0$ is the penalty parameter, and $\lambda$ is the dual variable.



## Unscaled ADMM

The ADMM iterations are given by


$$ 
x^{k+1} = \arg \min_x L_\rho(x,z^k,\lambda^k),
$$

$$ 
z^{k+1} = \arg \min_z L_\rho(x^{k+1}, z, \lambda^k), 
$$

$$ 
\lambda^{k+1} = \lambda^k + \rho ( Ax ^{k+1} + Bz^{k+1} - c). 
$$


## Scaled Form ADMM

Define the scaled dual variable $u = \frac{1}{\rho} \lambda$, then the augmented Lagrangian function can be expressed as 

$$
L_\rho(x, z, u) = f(x) + g(z) + \frac{\rho}{2} \Vert Ax + Bz - c + u \Vert^2_2 - \frac{\rho}{2} \Vert u \Vert^2_2.
$$

Thus, the ADMM updates become 

$$ 
x^{k+1} = \arg \min_x f(x) +\frac{\rho}{2}\Vert Ax+Bz^k-c+u^k\Vert_2^2 ,
$$

$$ 
z^{k+1} = \arg \min_z g(z)+\frac{\rho}{2}\Vert Ax^{k+1}+Bz-c+u^k \Vert_2^2 ,
$$


$$ 
u^{k+1} = u^k + Ax^{k+1}+Bz^{k+1}-c.
$$

This formulation is commonly referred to as the **scaled form** of ADMM.

## References

- [S. Boyd, N. Parikh, E. Chu, B. Peleato, and J. Eckstein — *Distributed Optimization and Statistical Learning via the Alternating Direction Method of Multipliers*](https://web.stanford.edu/~boyd/papers/pdf/admm_distr_stats.pdf)



