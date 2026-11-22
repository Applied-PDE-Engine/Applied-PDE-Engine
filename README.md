<div align="center">

# Applied PDE Engine

**A foundational C++11 computational engine bridging undergraduate mathematical analysis with numerical modeling of Partial Differential Equations (PDEs).**

<p>
  <img src="https://shields.io" alt="C++11" />
  <img src="https://shields.io" alt="Applied Math" />
  <img src="https://shields.io" alt="L1 Math" />
  <img src="https://shields.io" alt="License" />
</p>

</div>

<hr />

<h2>1. Academic & Mathematical Motivation</h2>

<p>
Developed as a first-year mathematics undergraduate (<strong>L1 Mathematics</strong>), this project acts as a practical laboratory to translate theoretical calculus and analysis concepts into deterministic, executable C++ algorithms:
</p>

<ul>
  <li><strong>Taylor Expansions &amp; Discretization:</strong> Approximating continuous partial derivatives on discrete grids using truncated Taylor series (Finite Differences).</li>
  <li><strong>Sequences &amp; Convergence:</strong> Studying numerical stability, boundedness, and iterative convergence of grid states across discrete time steps.</li>
  <li><strong>First-Principles Implementation:</strong> Building solvers from scratch using standard C++ without external mathematical black-box libraries.</li>
</ul>

<hr />

<h2>2. Implemented Mathematical Models</h2>

<p>The engine currently focuses on classical 1D and 2D second-order Partial Differential Equations:</p>

<table>
  <thead>
    <tr>
      <th>Equation Type</th>
      <th>Mathematical Formulation</th>
      <th>Discretization Scheme</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>1D Heat Equation</strong><br /><em>(Parabolic)</em></td>
      <td>$$\frac{\partial u}{\partial t} = \alpha \frac{\partial^2 u}{\partial x^2}$$</td>
      <td>Forward-Time Central-Space (FTCS)</td>
    </tr>
    <tr>
      <td><strong>1D Wave Equation</strong><br /><em>(Hyperbolic)</em></td>
      <td>$$\frac{\partial^2 u}{\partial t^2} = c^2 \frac{\partial^2 u}{\partial x^2}$$</td>
      <td>Central Finite Difference (Explicit)</td>
    </tr>
  </tbody>
</table>

<h3>Numerical Discretization &amp; Stability</h3>

<p>For the 1D thermal diffusion model, the continuous domain is discretized into spatial nodes <code>i</code> and time steps <code>n</code>:</p>

$$u_i^{n+1} = u_i^n + \frac{\alpha \Delta t}{\Delta x^2} \left(u_{i+1}^n - 2u_i^n + u_{i-1}^n\right)$$

<p>To prevent numerical divergence and ensure sequence convergence, the engine enforces the <strong>Courant–Friedrichs–Lewy (CFL)</strong> stability condition:</p>

$$r = \frac{\alpha \Delta t}{\Delta x^2} \le \frac{1}{2}$$

<hr />

<h2>3. Technical Architecture</h2>

<ul>
  <li><strong>Memory Efficiency:</strong> Utilizes contiguous memory allocation (<code>std::vector</code>) for cache-friendly spatial grid updates.</li>
  <li><strong>Boundary Conditions:</strong> Supports fixed Dirichlet boundary constraints ($u(0, t) = a$, $u(L, t) = b$).</li>
  <li><strong>Data Export:</strong> Outputs simulation states to <code>.csv</code> files for external visualization and analytical verification.</li>
</ul>

<details>
<summary><strong>Click to view Project Directory Structure</strong></summary>
<br />

<pre><code>Applied-PDE-Engine/
├── include/
│   ├── Grid.hpp          # Spatial domain &amp; mesh discretization
│   └── Solvers.hpp       # Finite difference time-stepping algorithms
├── src/
│   ├── Grid.cpp
│   ├── Solvers.cpp
│   └── main.cpp          # Initial conditions &amp; simulation parameters
├── output/               # Exported CSV numerical results
└── README.md
</code></pre>

</details>

<hr />

<h2>4. Build &amp; Execution</h2>

<p><strong>Prerequisites:</strong> A C++11 compatible compiler (<code>g++</code> or <code>clang++</code>) on Linux/Ubuntu.</p>

<pre><code># Clone the repository
git clone https://github.com
cd Applied-PDE-Engine

# Compile with optimization flags
g++ -std=c++11 -O2 src/*.cpp -Iinclude -o pde_engine

# Run the simulation
./pde_engine
</code></pre>

<hr />

<h2>5. Roadmap</h2>

<ul>
  <li>Implement Neumann boundary conditions (zero-flux / insulated boundaries).</li>
  <li>Add 2D Laplace &amp; Poisson steady-state solvers (Jacobi &amp; Gauss-Seidel iterations).</li>
  <li>Integrate real-time graphical rendering for grid evolution.</li>
</ul>

<hr />

<div align="center">
  <p><strong>Author:</strong> <a href="https://github.com">sjmDeveloper</a> — First-Year Mathematics Student (L1) &amp; C++ Developer</p>
</div>
