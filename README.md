# DeepONet and φ-DeepONet for Diffusion Equations

This repository explores DeepONet and φ-DeepONet for solving diffusion equations through a sequence of problems with increasing complexity.

The simulations progress through the following stages:

1. **Constant source term:** Establishing a baseline for learning the solution operator.
2. **Variable source term:** Learning solutions for spatially varying source functions.
3. **Constant diffusion coefficient:** Studying the diffusion equation with fixed material properties.
4. **Variable diffusion coefficient:** Predicting solutions for spatially varying coefficients α(x).
5. **Interface problems:** Extending the framework to diffusion across materials with discontinuous coefficients, requiring continuity of the solution and diffusive flux at the interface.

### Why is learning variable α(x) challenging?

The governing equation is

$$
-\frac{d}{dx}\left(\alpha(x)\frac{dp}{dx}\right)=f(x).
$$

The solution depends on the spatial distribution of α(x) across the entire domain, not just its value at individual points. For a given source term, regions with lower diffusion coefficients generally require steeper solution gradients to maintain the same flux. This makes the relationship between α(x) and the solution nonlocal and nonlinear in the coefficient.

Interfaces introduce an additional challenge: the solution remains continuous, but its gradient can change abruptly to maintain flux continuity. This makes standard DeepONet learning more difficult and motivates the use of φ-DeepONet to better represent interface behaviour.

The repository compares both architectures across these increasingly challenging problems to evaluate their accuracy and ability to learn the underlying solution operators.
