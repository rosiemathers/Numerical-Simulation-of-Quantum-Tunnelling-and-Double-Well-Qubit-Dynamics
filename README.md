# Quantum Tunnelling and Double-Well Qubit Dynamics
The attached FinalProposedProjectBrief.ipynb includes details of equations, parameters and information needed.

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

