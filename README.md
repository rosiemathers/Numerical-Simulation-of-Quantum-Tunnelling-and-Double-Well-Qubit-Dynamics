# Quantum Tunnelling and Double-Well Qubit Dynamics

## Project Brief

A quantum particle approaching a potential barrier with less energy than
the barrier height can tunnel through it, whereas a classical particle
would be reflected. This project simulates quantum tunnelling by
propagating a Gaussian wave packet through a one-dimensional potential
barrier, extracting transmission and reflection probabilities, and
comparing them with exact analytical results.

The project will then extend this approach to a double-well potential,
$V(x)=ax^4-bx^2$, to investigate how quantum tunnelling can transfer a
particle between two spatially separated states. The left and right
wells can be associated with the computational basis states $|0\rangle$
and $|1\rangle$, respectively, providing a model for exploring
quantum-bit dynamics. By calculating the energy eigenstates and
propagating an initially localised wave packet, the relationship between
energy splitting, tunnelling timescales and superposition states can be
investigated.

As a possible further extension, a time-dependent external field can be
introduced to drive transitions between the wells. By tuning the driving
frequency and duration, the simulation can explore controlled state
transfer and the principles underlying quantum gates.

The project combines numerical solutions of the time-dependent
Schrödinger equation with applications to quantum computing, where
controlled quantum-state evolution is fundamental.

## Governing Equations

In one dimension, the wavefunction $\psi(x,t)$ obeys the time-dependent
Schrödinger equation:

$$
i\hbar\frac{\partial\psi}{\partial t}
=
\left[
-\frac{\hbar^2}{2m}\frac{\partial^2}{\partial x^2}
+V(x,t)
\right]\psi.
$$

The domain is $x\in[-L,L]$, with boundary conditions
$\psi(-L,t)=\psi(L,t)=0$. The probability density is $|\psi(x,t)|^2$,
and the normalisation condition is

$$
\int_{-L}^{L}|\psi(x,t)|^2\,dx=1.
$$

The initial condition for the barrier problem is a Gaussian wave packet:

$$
\psi(x,0)
=
C\exp\left[-\frac{(x-x_0)^2}{4\sigma^2}\right]
e^{ik_0x},
$$

where $C$ is a normalisation constant, $x_0$ is the initial position,
$\sigma$ is the spatial width and $k_0$ is the central wave number. Its
approximate mean kinetic energy is

$$
E\approx\frac{\hbar^2 k_0^2}{2m}.
$$

For a free packet, the spatial width evolves according to

$$
\sigma(t)
=
\sigma\sqrt{1+\left(\frac{\hbar t}{2m\sigma^2}\right)^2}.
$$

### Rectangular Potential Barrier

For a rectangular barrier of height $V_0$ and width $d$, with $E<V_0$,
the analytical transmission coefficient is

$$
T=
\left[
1+\frac{V_0^2\sinh^2(\kappa d)}
{4E(V_0-E)}
\right]^{-1},
$$

where

$$
\kappa=\frac{\sqrt{2m(V_0-E)}}{\hbar}.
$$

The reflection coefficient is $R=1-T$ for a stationary scattering state.
For a numerically propagated wave packet, transmission and reflection
probabilities can be calculated by integrating the probability density
on either side of the barrier after the collision.

### Double-Well Potential

The double-well extension uses the static potential

$$
V(x)=ax^4-bx^2,\qquad a,b>0.
$$

The two minima are located at

$$
x_{\mathrm{min}}=\pm\sqrt{\frac{b}{2a}},
$$

and the central barrier has height

$$
V(0)-V(x_{\mathrm{min}})=\frac{b^2}{4a}.
$$

The energy eigenstates satisfy

$$
\hat{H}\phi_n(x)=E_n\phi_n(x),
$$

where the Hamiltonian is

$$
\hat{H}
=
-\frac{\hbar^2}{2m}\frac{d^2}{dx^2}+V(x).
$$

For a symmetric double well, the two lowest eigenstates are
approximately symmetric and antisymmetric combinations of states
localised in the left and right wells:

$$
|E_0\rangle\approx\frac{|0\rangle+|1\rangle}{\sqrt{2}},
$$

$$
|E_1\rangle\approx\frac{|0\rangle-|1\rangle}{\sqrt{2}}.
$$

Here, $|0\rangle$ represents a state localised in the left well, while
$|1\rangle$ represents a state localised in the right well. These are
approximate localised states rather than exact energy eigenstates.

The energy difference between the two lowest eigenstates is

$$
\Delta E=E_1-E_0,
$$

which determines the characteristic angular frequency of tunnelling:

$$
\omega_{01}=\frac{\Delta E}{\hbar}.
$$

An initially localised wave packet can therefore evolve between the two
wells due to quantum tunnelling. At suitable times, the state may become
localised predominantly in the opposite well or form a superposition of
the two localised states.

### Time-Dependent Driving and Quantum Gates

To investigate controlled quantum dynamics, an oscillating external
field can be introduced through the time-dependent potential

$$
V(x,t)=ax^4-bx^2+Ax\cos(\omega t),
$$

where $A$ is the driving amplitude and $\omega$ is the angular driving
frequency.

Driving near the transition frequency between the lowest energy
eigenstates can induce transitions between them. By adjusting the
driving frequency, amplitude and duration, the simulation can
investigate controlled state transfer and the creation of superposition
states.

The ideal Pauli-X gate exchanges the two computational basis states:

$$
X|0\rangle=|1\rangle,\qquad X|1\rangle=|0\rangle.
$$

An ideal Hadamard gate transforms the basis states according to

$$
H|0\rangle=\frac{|0\rangle+|1\rangle}{\sqrt{2}},
$$

$$
H|1\rangle=\frac{|0\rangle-|1\rangle}{\sqrt{2}}.
$$

Equal probabilities in the two wells do not, by themselves, establish
that a Hadamard gate has been implemented. The relative phase and the
action on both basis states must also be considered.

## Geometry and Parameters

Use natural units $\hbar=m=1$.

### Initial Tunnelling Simulation

-   **Domain:** $x\in[-100,100]$, with $N\approx4000$ spatial grid
    points.
-   **Wave packet:** $x_0=-30$, $\sigma=3$, $k_0=1$, giving
    $E\approx0.5$.
-   **Rectangular barrier:** centred at $x=0$, height $V_0=1$, width
    $d=2$.
-   **Time step:** $\Delta t\approx0.05$.
-   **Final time:** $t\approx80$.

### Double-Well Extension

Use the potential $V(x)=ax^4-bx^2$, choosing positive values of $a$ and
$b$ to produce two distinct wells separated by a central barrier. The
well locations are determined by

$$
x_{\mathrm{min}}=\pm\sqrt{\frac{b}{2a}}.
$$

The domain and spatial resolution should be selected to resolve both
wells and the lowest energy eigenstates. Choose a time step that
adequately resolves the tunnelling dynamics, and ensure that the
wavefunction remains negligible at the boundaries.

For the driven system, investigate suitable driving amplitudes and
frequencies, including frequencies near $\omega_{01}$. Vary the driving
duration to study its effect on the probability of finding the particle
in each well.

## Recommended Numerical Approach

Discretise the second spatial derivative using second-order central
differences:

$$
\frac{\partial^2\psi}{\partial x^2}
\approx
\frac{\psi_{j+1}-2\psi_j+\psi_{j-1}}{\Delta x^2}.
$$

Advance the wavefunction in time using the Crank--Nicolson method:

$$
\left(I+\frac{i\Delta t}{2\hbar}H\right)\psi^{n+1}
=
\left(I-\frac{i\Delta t}{2\hbar}H\right)\psi^n,
$$

where $H$ is the discretised Hamiltonian. The resulting tridiagonal
system can be solved using `scipy.linalg.solve_banded`, or factorised
once using sparse LU when the Hamiltonian is time-independent.

For a Hermitian, time-independent Hamiltonian, Crank--Nicolson is
unconditionally stable and preserves the discrete norm, up to
floating-point and linear-solver errors. For a time-dependent potential,
the Hamiltonian can be evaluated at the midpoint of each time step, with
accuracy checked through convergence tests.

For the double-well problem, calculate the lowest energy eigenstates
using `scipy.sparse.linalg.eigsh`. Construct an initial wave packet
localised in one well and propagate it using the same numerical solver.
Calculate the probability in each well as a function of time to observe
tunnelling and investigate its relationship with the energy splitting.

For the driven system, incorporate the oscillating perturbation into the
Hamiltonian and investigate how the driving frequency, amplitude and
duration affect the probability of occupying each well.

## Ideas for Exploration

1.  **Free wave packet:** Propagate the packet with $V=0$. Plot
    $|\psi(x,t)|^2$ at several times and compare its spreading with the
    analytical result. Investigate convergence in $\Delta x$ and
    $\Delta t$.
2.  **Conservation laws:** Verify norm conservation to numerical
    precision. Calculate $\langle x\rangle(t)$ and
    $\langle E\rangle(t)$, confirming energy conservation for a static
    potential.
3.  **Rectangular barrier:** Plot the wave packet before, during and
    after the collision. Measure transmission and reflection
    probabilities and check that $T+R\approx1$.
4.  **Transmission spectrum:** Vary $k_0$ or the mean energy and compare
    numerical transmission with the analytical formula. Investigate the
    effects of barrier width and the finite energy spread of the packet.
5.  **Double-well eigenstates:** Calculate the lowest energy eigenstates
    and plot their probability densities. Investigate how the well depth
    and barrier height affect the energy splitting.
6.  **Quantum tunnelling dynamics:** Initialise a wave packet in the
    left well and propagate it in the symmetric double-well potential.
    Plot the probability of finding the particle in each well and
    estimate the tunnelling timescale.
7.  **Driven double well:** Add the oscillating external field and
    investigate how the driving frequency and amplitude affect
    transitions between the wells. Compare resonant and off-resonant
    driving.
8.  **Quantum gate operations:** Investigate whether appropriately timed
    tunnelling or external driving can implement population transfer
    analogous to a Pauli-X gate, or create an equal superposition of the
    two well-localised states. Analyse the relative phase as well as the
    probabilities to assess the resulting quantum operation.

## Ideas for Further Extensions

-   **Resonant tunnelling:** Introduce a double-barrier potential and
    investigate transmission peaks associated with quasi-bound states.
-   **Alternative integrator:** Implement the split-step Fourier method
    and compare its computational cost and accuracy with
    Crank--Nicolson.
-   **Imaginary-time propagation:** Use imaginary-time evolution to
    approximate the ground state of a potential and compare it with the
    eigenvalue solver.
-   **Quantum control:** Investigate pulse duration and amplitude to
    determine the conditions required for reliable state transfer and
    superposition creation.
-   **Gate fidelity:** Compare the simulated evolution with ideal
    single-qubit operations, accounting for phase differences and
    population in higher energy states.

The initial tunnelling simulation provides the core project, while the
double-well and driven-qubit investigations offer progressively more
ambitious extensions towards quantum computing.
