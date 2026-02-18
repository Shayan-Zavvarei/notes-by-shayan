<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# You are an expert machine learning researcher, educator, and scientific software engineer with deep expertise in Simulation-Based Inference (SBI), Bayesian inference, and Python-based research tooling.

Your task is to produce a complete, rigorous, and self-contained educational resource on Simulation-Based Inference (SBI), covering both theoretical foundations and practical implementation.

IMPORTANT OUTPUT REQUIREMENTS:

- The entire output MUST be written in **Markdown format**
- The content MUST be structured as a **single downloadable Markdown file**, suitable for saving as `README.md`
- The Markdown must be clean, well-structured, and ready to be used directly in documentation or a GitHub repository

CONTENT REQUIREMENTS:

1. **Introduction and Motivation**
    - What is Simulation-Based Inference (SBI)?
    - Why SBI is necessary (intractable likelihoods, black-box simulators)
    - Comparison with classical Bayesian inference
    - Real-world applications (physics, cosmology, neuroscience, biology, etc.)
2. **Theoretical Foundations**
    - Bayesian inference refresher
    - Likelihood-free inference
    - Posterior approximation and amortized inference
    - Core SBI approaches:
        - Neural Posterior Estimation (NPE)
        - Neural Likelihood Estimation (NLE)
        - Neural Ratio Estimation (NRE)
    - Mathematical formulation of each method
    - Training objectives and loss functions
3. **Neural Network Models in SBI**
    - Role of neural networks in SBI
    - Density estimators (normalizing flows, MDNs, etc.)
    - Conditioning mechanisms
    - Amortization and generalization concepts
4. **Python Implementation Using the `sbi` Package**
    - Full introduction to the `sbi` Python library
    - Installation and environment setup
    - Core abstractions:
        - Prior
        - Simulator
        - Observation
        - Inference objects
    - Clear explanations of the API and workflow
5. **Step-by-Step Coding Examples**
    - Simple toy example (e.g., Gaussian simulator)
    - Intermediate nonlinear simulator example
    - Posterior sampling and visualization
    - Each code block must be:
        - Fully runnable
        - Clearly commented
        - Explained line by line
6. **Advanced Topics**
    - Sequential Neural Posterior Estimation (SNPE)
    - Simulation efficiency and budget control
    - Posterior diagnostics and validation
    - High-dimensional parameters and observations
7. **Best Practices and Common Pitfalls**
    - Choosing priors and simulators
    - Debugging SBI pipelines
    - Evaluating posterior quality
    - Practical advice for real scientific research
8. **Summary and Further Resources**
    - Key takeaways
    - Suggested learning roadmap
    - Recommended papers, tutorials, and documentation

FORMATTING GUIDELINES:

- Use clear Markdown headings (`#`, `##`, `###`)
- Use LaTeX-style math expressions where appropriate
- Use fenced code blocks for Python code
- Keep explanations precise, rigorous, and educational
- Avoid vague or superficial descriptions

The final output should read like a high-quality graduate-level tutorial or workshop notes, combining theory and hands-on practice seamlessly, delivered as a single, polished, downloadable Markdown document.

Now I have comprehensive information to produce the full educational Markdown document. Let me compile it.

```markdown
# Simulation-Based Inference (SBI): A Complete Graduate-Level Tutorial

> **Format:** Self-contained Markdown reference · **Level:** Graduate / Research  
> **Save as:** `README.md`  
> **Last updated:** February 2026

---

## Table of Contents

1. [Introduction and Motivation](#1-introduction-and-motivation)
2. [Theoretical Foundations](#2-theoretical-foundations)
3. [Neural Network Models in SBI](#3-neural-network-models-in-sbi)
4. [Python Implementation Using the `sbi` Package](#4-python-implementation-using-the-sbi-package)
5. [Step-by-Step Coding Examples](#5-step-by-step-coding-examples)
6. [Advanced Topics](#6-advanced-topics)
7. [Best Practices and Common Pitfalls](#7-best-practices-and-common-pitfalls)
8. [Summary and Further Resources](#8-summary-and-further-resources)

---

## 1. Introduction and Motivation

### 1.1 What Is Simulation-Based Inference?

**Simulation-Based Inference (SBI)** — also called *likelihood-free inference* or *implicit likelihood inference* — is a family of Bayesian methods for inferring the parameters \(\theta\) of a generative model (a *simulator*) given observed data \(x_o\), **without ever evaluating the likelihood** \(p(x \mid \theta)\) analytically.

The core insight: if you can *simulate* data from a model, you can *learn* the posterior \(p(\theta \mid x_o)\) using machine learning, even when the likelihood is mathematically intractable or computationally inaccessible.

```

┌──────────────────────────────────────────────────────────────┐
│  Classical Bayesian:  p(θ|x) ∝ p(x|θ) · p(θ)               │
│  Requires: explicit, evaluable p(x|θ)                        │
│                                                              │
│  SBI:  learn p(θ|x) directly from {θ, x} pairs              │
│  Requires: simulator θ → x, a prior p(θ)                     │
└──────────────────────────────────────────────────────────────┘

```

### 1.2 Why SBI Is Necessary

Many scientific simulators are **black boxes**: they produce realistic outputs through stochastic forward passes (e.g., molecular dynamics, agent-based models, cosmological N-body codes), but their internal probability structure is opaque or analytically intractable. This makes standard approaches like MCMC or Variational Inference impossible to apply directly, because they require evaluating \(p(x \mid \theta)\) at every step.

Key challenges that motivate SBI:

- **Intractable likelihoods**: The simulator involves stochastic intermediate variables that are integrated out implicitly.
- **Black-box simulators**: Written in compiled code (C++, Fortran), returning only samples, not probabilities.
- **High computational cost per simulation**: Climate models, neuroscience spiking networks, or epidemiological ABMs may take minutes to hours per run.
- **Exotic data structures**: Outputs may be images, graphs, time series, or point clouds — for which no standard likelihood exists.

### 1.3 Comparison: Classical vs. Simulation-Based Inference

| Dimension | Classical Bayesian | Simulation-Based Inference |
|---|---|---|
| Likelihood required? | ✅ Yes — must be evaluable | ❌ No — only simulations needed |
| Posterior form | Analytic or MCMC-approximated | Neural network approximation |
| Scalability | Limited by MCMC mixing | Amortized — one training pass |
| Reuse for new observations | Must re-run MCMC | Instant (amortized) |
| Density of approximation | Exact (up to MCMC error) | Approximate (neural network) |
| Simulator requirement | Must write \(p(x\mid\theta)\) | Must write `simulate(θ) → x` |

### 1.4 Real-World Applications

SBI has found widespread adoption across science and engineering:

- **Cosmology**: Inferring cosmological parameters (dark matter, dark energy) from weak lensing maps and CMB power spectra, where the likelihood involves intractable galaxy formation physics.
- **Neuroscience**: Fitting biophysical neuron and network models (Hodgkin-Huxley, Poisson GLMs) to electrophysiology recordings, where stochastic spike generation makes the likelihood intractable.
- **Particle physics**: Constraining Standard Model parameters and searching for new physics at the LHC; the detector simulation chain (Geant4) is a complex black-box.
- **Population genetics**: Inferring evolutionary parameters (mutation rate, migration, selection) from allele frequency spectra.
- **Epidemiology**: Estimating transmission rates and intervention effects from incidence data using agent-based epidemic models.
- **X-ray spectral analysis**: Recovering astrophysical source parameters from spectra; SBI-NPE has been shown to produce posteriors fully consistent with standard Bayesian fitting in both Gaussian and Poisson regimes, with inference times under 1 second post-training.
- **Climate science**: Constraining earth system model parameters from observational data.
- **Robotics / engineering**: Calibrating simulation-to-real gaps in physical systems.

---

## 2. Theoretical Foundations

### 2.1 Bayesian Inference Refresher

Bayesian inference is the framework for updating beliefs about model parameters \(\theta \in \mathbb{R}^d\) in light of observed data \(x_o\). The three fundamental quantities are:

- **Prior** \(p(\theta)\): encodes beliefs about parameters before observing data.
- **Likelihood** \(p(x \mid \theta)\): probability of observed data given parameters.
- **Posterior** \(p(\theta \mid x_o)\): updated beliefs after observing \(x_o\).

These are related by **Bayes' theorem**:

\[
p(\theta \mid x_o) = \frac{p(x_o \mid \theta) \, p(\theta)}{p(x_o)}
\]

where the **marginal likelihood** (evidence) is:

\[
p(x_o) = \int p(x_o \mid \theta) \, p(\theta) \, d\theta
\]

The evidence \(p(x_o)\) is typically intractable in high dimensions, which is why MCMC methods sample from \(p(\theta \mid x_o)\) without computing it. In SBI, we bypass both \(p(x_o \mid \theta)\) and \(p(x_o)\) entirely.

### 2.2 Likelihood-Free Inference

When \(p(x \mid \theta)\) is unavailable, the classical approach — **Approximate Bayesian Computation (ABC)** — approximates the posterior by:

1. Sampling \(\theta_i \sim p(\theta)\)
2. Simulating \(x_i \sim \text{simulator}(\theta_i)\)
3. Accepting \(\theta_i\) if \(d(x_i, x_o) < \epsilon\) (for some discrepancy \(d\) and tolerance \(\epsilon\))

ABC is **asymptotically exact** as \(\epsilon \to 0\) but exponentially inefficient in high dimensions ("curse of dimensionality"). It also requires hand-crafted summary statistics and discrepancy functions.

Modern SBI replaces the rejection step with **neural density estimation**, using all simulated pairs \((\theta_i, x_i)\) to learn the full posterior, not just accepted/rejected samples.

### 2.3 Posterior Approximation and Amortized Inference

A key innovation in modern SBI is **amortization**: training a single neural network \(q_\phi(\theta \mid x)\) that can produce the posterior for *any* observation \(x\), without retraining. Once the network is trained on simulated \((\theta, x)\) pairs, inference for a new observation is a single forward pass — often under 1 second.

**Amortized inference** trades simulation budget (a one-time cost) for fast, reusable posteriors. This is especially powerful when:

- Many different observations need to be processed (e.g., thousands of galaxy spectra)
- Real-time inference is required
- The simulator is expensive but observations are plentiful

### 2.4 Core SBI Approaches

There are three main families of neural SBI, differing in *what they learn*:

#### 2.4.1 Neural Posterior Estimation (NPE)

**Goal**: Directly approximate the posterior \(p(\theta \mid x)\).

A conditional density estimator \(q_\phi(\theta \mid x)\) is trained to approximate \(p(\theta \mid x)\) over all \((\theta, x)\) pairs sampled from the joint:

\[
(\theta, x) \sim p(\theta) \cdot p(x \mid \theta) = p(\theta, x)
\]

**Training objective** (maximum likelihood over simulated pairs):

\[
\mathcal{L}_{\text{NPE}}(\phi) = -\mathbb{E}_{p(\theta, x)} \left[ \log q_\phi(\theta \mid x) \right]
\]

Minimizing this loss trains \(q_\phi\) to match \(p(\theta \mid x)\) in KL divergence. Since the network is trained on pairs from the joint, at test time, conditioning on \(x = x_o\) yields samples from an approximation of the true posterior.

**Key property**: NPE is fully amortized — a single trained network produces posteriors for any \(x_o\) instantly.

#### 2.4.2 Neural Likelihood Estimation (NLE)

**Goal**: Learn a surrogate likelihood \(\hat{p}(x \mid \theta)\), then combine with the prior for posterior inference.

A conditional density estimator \(q_\phi(x \mid \theta)\) is trained:

\[
\mathcal{L}_{\text{NLE}}(\phi) = -\mathbb{E}_{p(\theta, x)} \left[ \log q_\phi(x \mid \theta) \right]
\]

Once trained, the surrogate likelihood can be plugged into MCMC:

\[
p(\theta \mid x_o) \propto q_\phi(x_o \mid \theta) \cdot p(\theta)
\]

**Key property**: NLE separates density estimation from posterior inference. Posterior sampling requires an MCMC step, but the likelihood surrogate is highly flexible and can be reused with different priors.

#### 2.4.3 Neural Ratio Estimation (NRE)

**Goal**: Learn the **likelihood-to-prior ratio** \(r(\theta, x) = p(x \mid \theta) / p(x)\), which is proportional to the posterior-to-prior ratio.

NRE recasts ratio estimation as a **binary classification** problem. Given a classifier \(d_\phi(\theta, x)$ predicting whether a pair \((\theta, x)\) was jointly sampled (label 1) or marginally sampled (label 0):

\[
\mathcal{L}_{\text{NRE}}(\phi) = -\mathbb{E}_{p(\theta,x)}\left[\log d_\phi(\theta, x)\right] - \mathbb{E}_{p(\theta)p(x)}\left[\log(1 - d_\phi(\theta, x))\right]
\]

The optimal classifier satisfies:

\[
d_\phi^*(\theta, x) = \frac{p(\theta, x)}{p(\theta, x) + p(\theta)p(x)} \implies r(\theta, x) = \frac{d_\phi^*(\theta, x)}{1 - d_\phi^*(\theta, x)}
\]

This ratio then defines a tractable likelihood ratio for MCMC-based posterior sampling.

**Key property**: NRE avoids direct density estimation, making it robust in very high dimensions where normalizing flows can struggle.

### 2.5 Summary of SBI Methods

| Method | What Is Learned | Posterior Sampling | Amortized? | MCMC Needed? |
|---|---|---|---|---|
| NPE | \(q_\phi(\theta \mid x)\) | Direct sampling | ✅ Fully | ❌ No |
| NLE | \(q_\phi(x \mid \theta)\) | Via MCMC with surrogate | ✅ Partially | ✅ Yes |
| NRE | \(r_\phi(\theta, x)\) | Via MCMC with ratio | ✅ Partially | ✅ Yes |

---

## 3. Neural Network Models in SBI

### 3.1 Role of Neural Networks

Neural networks in SBI serve as **universal conditional density estimators**. The core task is to learn a conditional distribution — either \(p(\theta \mid x)\) (NPE), \(p(x \mid \theta)\) (NLE), or their ratio (NRE) — from finite samples. This requires architectures that:

1. Can represent complex, multimodal, non-Gaussian distributions.
2. Accept conditioning inputs efficiently (e.g., observation \(x\) as context).
3. Support both density evaluation `log_prob(θ)` and sampling `.sample()`.

### 3.2 Density Estimators

#### Mixture Density Networks (MDNs)

An MDN outputs the parameters of a Gaussian Mixture Model (GMM) as a function of the conditioning variable:

\[
q_\phi(\theta \mid x) = \sum_{k=1}^K \pi_k(x) \, \mathcal{N}(\theta; \mu_k(x), \Sigma_k(x))
\]

where the weights \(\pi_k\), means \(\mu_k\), and covariances \(\Sigma_k\) are all outputs of a neural network with input \(x\). MDNs are fast but limited in expressiveness by the number of mixture components \(K\).

#### Normalizing Flows

Normalizing flows are the dominant density estimator in modern SBI. A flow transforms a simple base distribution \(p_0(u)\) (typically \(\mathcal{N}(0, I)\)) through a series of invertible transformations \(f_1, \ldots, f_L\):

\[
\theta = f_L \circ \cdots \circ f_1(u), \quad u \sim p_0
\]

By the change-of-variables formula:

\[
\log q_\phi(\theta) = \log p_0(u) - \sum_{l=1}^L \log \left| \det J_{f_l}(u_l) \right|
\]

For a *conditional* flow \(q_\phi(\theta \mid x)\), the transformation parameters are functions of the context \(x\).

**Masked Autoregressive Flow (MAF)** is among the best-performing architectures for density estimation. It models \(\theta\) autoregressively:

\[
\theta_i = \mu_i(\theta_{1:i-1}, x) + \sigma_i(\theta_{1:i-1}, x) \cdot u_i
\]

where the autoregressive structure ensures a triangular Jacobian, making log-density evaluation \(\mathcal{O}(d)\). The MADE (Masked Autoencoder for Distribution Estimation) architecture enforces the autoregressive constraint with binary masks, enabling parallel density evaluation via a single forward pass.

**Neural Spline Flows (NSF)** use monotone rational-quadratic spline transformations to achieve higher expressiveness than affine autoregressive flows, and are the default density estimator in the `sbi` package.

#### Embedding Networks

When observations \(x\) are high-dimensional (e.g., images, time series), an **embedding network** (encoder) \(\xi_\psi: x \mapsto s\) compresses \(x\) into a low-dimensional summary statistic \(s\) before it is passed to the flow as context. This embedding is trained jointly with the flow:

\[
q_\phi(\theta \mid x) = q_\phi(\theta \mid \xi_\psi(x))
\]

Common choices: CNNs for images, LSTMs/Transformers for time series, permutation-invariant networks for set-valued data.

### 3.3 Conditioning Mechanisms

In conditional normalizing flows, the observation \(x\) (or its embedding) is fed as additional input to the networks that compute the flow's affine parameters at each layer. The two dominant patterns are:

- **Concatenation conditioning**: \(x\) is concatenated to the input of each MADE/coupling layer.
- **Hypernetwork conditioning**: A separate network maps \(x\) to the weights or biases of the flow layers.

### 3.4 Amortization and Generalization

By training on a diverse distribution of \((\theta, x)\) pairs drawn from the joint \(p(\theta, x)\), the neural network learns a *function* from observations to posteriors — not just a single posterior. This is the mechanism of amortization: generalization across the space of observations.

Amortization does introduce a trade-off: a single amortized model must generalize across all possible \(x\), whereas a *sequential* method (SNPE/SNLE/SNRE) focuses simulation budget on a specific target observation, potentially achieving higher accuracy with fewer simulations at the cost of losing amortization.

---

## 4. Python Implementation Using the `sbi` Package

### 4.1 Introduction to the `sbi` Library

`sbi` is an open-source Python toolbox for simulation-based inference, developed by the Macke Lab and collaborators. It implements all major SBI methods (NPE, NLE, NRE and their sequential variants) with a clean, unified API built on PyTorch. It is the standard library for SBI research and provides:

- Multiple inference algorithms with consistent interfaces
- Flexible neural density estimators (NSF, MAF, MDN)
- MCMC backends for NLE and NRE (NUTS, slice sampling)
- Diagnostic tools (Posterior Predictive Checks, Simulation-Based Calibration, TARP)
- Utilities for multi-round/sequential inference

**GitHub**: https://github.com/sbi-dev/sbi  
**Documentation**: https://sbi.readthedocs.io

### 4.2 Installation and Environment Setup

```bash
# Recommended: create a dedicated conda environment
conda create -n sbi_env python=3.10
conda activate sbi_env

# Install sbi from PyPI
pip install sbi

# Optional: install visualization extras
pip install matplotlib seaborn

# Verify installation
python -c "from sbi.examples.minimal import simple; p = simple(); print(p)"
```

**Requirements**: Python ≥ 3.8, PyTorch ≥ 1.11.

### 4.3 Core Abstractions

Every SBI workflow involves four fundamental objects:

#### 4.3.1 Prior

The prior $p(\theta)$ defines the parameter space and your initial beliefs. In `sbi`, priors must support `.sample((n,))` and `.log_prob(theta)`. Common choices:

```python
import torch
from sbi.utils import BoxUniform

# Uniform prior over a 3D hypercube
prior = BoxUniform(
    low=torch.tensor([-2.0, -2.0, -2.0]),
    high=torch.tensor([ 2.0,  2.0,  2.0])
)

# PyTorch distributions also work directly
from torch.distributions import MultivariateNormal
prior = MultivariateNormal(torch.zeros(3), torch.eye(3))
```


#### 4.3.2 Simulator

The simulator is any callable `theta -> x`. It does not need to be written in Python — you can precompute simulations on a cluster and pass them as tensors. The only requirement is that `theta` and `x` are `torch.Tensor` of type `float32`.

```python
def simulator(theta):
    # theta: (N, d_theta) tensor
    # returns: (N, d_x) tensor
    ...
    return x
```


#### 4.3.3 Observation

The observed data `x_obs` is a 1D tensor (for a single observation) or 2D tensor for batched observations. It must lie in the same space as simulator outputs.

```python
x_obs = torch.tensor([0.8, 0.6, 0.4])  # shape: (d_x,)
```


#### 4.3.4 Inference Object

The inference object orchestrates training and posterior construction:

```python
from sbi.inference import NPE, NLE, NRE

inference = NPE(prior=prior)
# Equivalent for other methods:
# inference = NLE(prior=prior)
# inference = NRE(prior=prior)
```


### 4.4 Core API Workflow

The full workflow in `sbi` follows four steps:

```python
# Step 1: Generate simulations
theta = prior.sample((num_simulations,))
x     = simulator(theta)

# Step 2: Append simulations to inference object
inference = inference.append_simulations(theta, x)

# Step 3: Train the density estimator
density_estimator = inference.train()

# Step 4: Build posterior and sample
posterior = inference.build_posterior()
samples   = posterior.sample((10_000,), x=x_obs)
```

The `build_posterior()` call returns a `DirectPosterior` (for NPE) or an MCMC-backed posterior (for NLE/NRE). All posterior objects expose:

- `.sample((n,), x=x_obs)` — draw $n$ samples from $p(\theta \mid x_{obs})$
- `.log_prob(theta, x=x_obs)` — evaluate log-posterior
- `.map(x=x_obs)` — Maximum A Posteriori estimate

---

## 5. Step-by-Step Coding Examples

### 5.1 Example 1: Simple Gaussian Simulator (Toy Problem)

This minimal example demonstrates the complete SBI workflow on a linear Gaussian model where the ground truth posterior is known analytically.

**Problem setup**: Parameters $\theta \in \mathbb{R}^3$, simulator adds a constant shift and Gaussian noise.

```python
# =============================================================================
# Example 1: Linear Gaussian Simulator — Complete SBI Workflow
# =============================================================================

import torch
import matplotlib.pyplot as plt
from sbi.inference import NPE
from sbi.utils import BoxUniform
from sbi.analysis import pairplot

# --- Reproducibility ---
torch.manual_seed(42)

# --- 1. Define dimensionality ---
num_dim = 3

# --- 2. Define the prior ---
# Uniform prior: each θ_i in [-2, 2]
prior = BoxUniform(
    low=-2 * torch.ones(num_dim),
    high= 2 * torch.ones(num_dim)
)

# --- 3. Define the simulator ---
def simulator(theta):
    """
    Linear Gaussian simulator.
    For each parameter vector theta, returns:
        x = theta + 1.0 + noise,  noise ~ N(0, 0.1^2 * I)
    
    Args:
        theta: torch.Tensor of shape (N, num_dim) or (num_dim,)
    Returns:
        x: torch.Tensor of same shape as theta
    """
    return theta + 1.0 + torch.randn_like(theta) * 0.1

# --- 4. Generate training simulations ---
# Sample parameters from the prior
num_simulations = 2000
theta_train = prior.sample((num_simulations,))   # shape: (2000, 3)
x_train     = simulator(theta_train)              # shape: (2000, 3)

print(f"theta_train.shape: {theta_train.shape}")  # (2000, 3)
print(f"x_train.shape:     {x_train.shape}")      # (2000, 3)

# --- 5. Instantiate and train NPE ---
# NPE = Neural Posterior Estimation (amortized)
inference = NPE(prior=prior)

# Register the simulated data with the inference object
inference.append_simulations(theta_train, x_train)

# Train the neural density estimator (a normalizing flow by default)
# This minimizes: E[-log q_φ(θ|x)] over simulated (θ, x) pairs
density_estimator = inference.train()
# Output: "Neural network successfully converged after N epochs."

# --- 6. Build the posterior object ---
# DirectPosterior: wraps the density estimator,
# adds rejection of out-of-prior samples
posterior = inference.build_posterior()

# --- 7. Define observation and sample posterior ---
# Our observed data point x_obs
# Ground truth θ* ≈ x_obs - 1.0 = [-0.2, -0.4, -0.6]
x_obs = torch.tensor([0.8, 0.6, 0.4])

# Draw 10,000 posterior samples conditioned on x_obs
# Key: no new simulations are needed — this is amortized inference
posterior_samples = posterior.sample((10_000,), x=x_obs)
print(f"posterior_samples.shape: {posterior_samples.shape}")  # (10000, 3)

# --- 8. Compute MAP estimate ---
map_estimate = posterior.map(x=x_obs, num_iter=1000)
print(f"MAP estimate: {map_estimate}")   # Should be near [-0.2, -0.4, -0.6]

# --- 9. Visualize posterior with pairplot ---
# Diagonal: 1D marginals; off-diagonal: 2D joint marginals
fig, axes = pairplot(
    posterior_samples,
    limits=[[-2, 2]] * num_dim,
    figsize=(6, 6),
    labels=[r"$\theta_1$", r"$\theta_2$", r"$\theta_3$"],
    points=map_estimate.unsqueeze(0),   # mark MAP estimate
)
plt.suptitle("NPE Posterior: Linear Gaussian Simulator", y=1.02)
plt.tight_layout()
plt.savefig("posterior_gaussian.png", dpi=150)
plt.show()

# --- 10. Posterior Predictive Check ---
# Simulate data from posterior samples and compare to observation
x_predictive = simulator(posterior_samples)
print(f"Posterior predictive mean: {x_predictive.mean(dim=0)}")
print(f"Observation:               {x_obs}")
# Should match closely, confirming the posterior is well-calibrated
```

**Expected output interpretation**: The posterior $p(\theta \mid x_{obs})$ should be centered near $\theta^* = x_{obs} - 1.0 = [-0.2, -0.4, -0.6]$, with narrow marginals reflecting the low noise level ($\sigma = 0.1$).

---

### 5.2 Example 2: Nonlinear Simulator — Two Moons Problem

The Two Moons problem is a standard SBI benchmark with a bimodal, crescent-shaped posterior — impossible to capture with a simple Gaussian approximation.

```python
# =============================================================================
# Example 2: Two Moons Benchmark — Nonlinear, Bimodal Posterior
# =============================================================================

import torch
import numpy as np
import matplotlib.pyplot as plt
from sbi.inference import NPE
from sbi.utils import BoxUniform
from sbi.analysis import pairplot

torch.manual_seed(0)

# --- 1. Prior: uniform over 2D parameter space ---
prior = BoxUniform(
    low =-torch.ones(2),
    high= torch.ones(2)
)

# --- 2. Two Moons Simulator ---
def two_moons_simulator(theta):
    """
    The Two Moons simulator produces a bimodal crescent-shaped posterior.
    
    For each parameter vector theta = (θ1, θ2):
      - Sample angle α ~ Uniform(-π/2, π/2)
      - Sample radius noise r ~ Normal(0.1, 0.01)
      - Compute p = (r*cos(α) + 0.25,  r*sin(α))
      - Output x = (p1 - |θ1 + θ2|/√2, p2 + (θ1 - θ2)/√2)
    
    This produces a two-crescent (bimodal) posterior for fixed x_obs.
    """
    if theta.ndim == 1:
        theta = theta.unsqueeze(0)
    
    n = theta.shape
    
    # Stochastic angle and radius
    alpha = torch.FloatTensor(n).uniform_(-np.pi / 2, np.pi / 2)
    r     = torch.randn(n) * 0.1 + 0.1  # radius ~ N(0.1, 0.01)
    
    # Crescent point
    p = torch.stack([
        r * torch.cos(alpha) + 0.25,
        r * torch.sin(alpha)
    ], dim=1)
    
    # Rotate/shift based on theta
    x = torch.stack([
        p[:, 0] - torch.abs(theta[:, 0] + theta[:, 1]) / (2 ** 0.5),
        p[:, 1] + (theta[:, 0] - theta[:, 1]) / (2 ** 0.5)
    ], dim=1)
    
    return x

# --- 3. Generate training data ---
num_simulations = 5000
theta_train = prior.sample((num_simulations,))
x_train     = two_moons_simulator(theta_train)

print(f"theta_train.shape: {theta_train.shape}")  # (5000, 2)
print(f"x_train.shape:     {x_train.shape}")      # (5000, 2)

# --- 4. Train NPE ---
inference = NPE(prior=prior)
inference.append_simulations(theta_train, x_train)
_ = inference.train()

# --- 5. Build posterior ---
posterior = inference.build_posterior()

# --- 6. Observe at x_obs =  and sample ---
x_obs = torch.zeros(2)   # canonical Two Moons observation

samples = posterior.sample((10_000,), x=x_obs)
log_prob = posterior.log_prob(samples, x=x_obs)
print(f"Mean log-prob of samples: {log_prob.mean():.3f}")

# --- 7. Visualize ---
fig, axes = pairplot(
    samples,
    limits=[[-1, 1], [-1, 1]],
    figsize=(5, 5),
    labels=[r"$\theta_1$", r"$\theta_2$"],
    points=torch.tensor([[0.0, 0.0]])   # true parameters (if known)
)
plt.suptitle("NPE Posterior: Two Moons (Bimodal)", y=1.02)
plt.tight_layout()
plt.savefig("posterior_two_moons.png", dpi=150)
plt.show()
```

**Expected output**: Two crescent-shaped probability mass regions in the 2D posterior, demonstrating the flow's ability to represent complex multimodal distributions.

---

### 5.3 Example 3: Using NLE and NRE

```python
# =============================================================================
# Example 3: NLE and NRE — Likelihood/Ratio Estimation Methods
# =============================================================================

import torch
from sbi.inference import NLE, NRE
from sbi.utils import BoxUniform

torch.manual_seed(1)

num_dim = 2
prior = BoxUniform(low=-2 * torch.ones(num_dim), high=2 * torch.ones(num_dim))

def simulator(theta):
    return theta + torch.randn_like(theta) * 0.5

theta = prior.sample((3000,))
x     = simulator(theta)
x_obs = torch.tensor([0.5, -0.3])

# ------- Neural Likelihood Estimation (NLE) ---------
# NLE learns q_φ(x|θ) as a surrogate likelihood.
# Posterior is then obtained via MCMC using the learned likelihood.

nle_inference = NLE(prior=prior)
nle_inference.append_simulations(theta, x)
_ = nle_inference.train()

# build_posterior uses MCMC internally (slice sampler or NUTS)
nle_posterior = nle_inference.build_posterior()

nle_samples = nle_posterior.sample((2000,), x=x_obs)
print(f"NLE posterior mean: {nle_samples.mean(dim=0)}")  # Should be near [0.5, -0.3]

# ------- Neural Ratio Estimation (NRE) ---------
# NRE learns r_φ(θ, x) = p(θ,x) / [p(θ)p(x)] via binary classification.
# The posterior is then: p(θ|x) ∝ r_φ(θ, x) * p(θ)

nre_inference = NRE(prior=prior)
nre_inference.append_simulations(theta, x)
_ = nre_inference.train()

nre_posterior = nre_inference.build_posterior()

nre_samples = nre_posterior.sample((2000,), x=x_obs)
print(f"NRE posterior mean: {nre_samples.mean(dim=0)}")  # Should be near [0.5, -0.3]

# Compare posteriors across methods
print("\nMethod comparison (posterior means at x_obs=[0.5, -0.3]):")
print(f"  NLE: {nle_samples.mean(dim=0).numpy()}")
print(f"  NRE: {nre_samples.mean(dim=0).numpy()}")
```


---

### 5.4 Example 4: Posterior Sampling and Visualization Utilities

```python
# =============================================================================
# Example 4: Advanced Visualization and Posterior Analysis
# =============================================================================

import torch
import matplotlib.pyplot as plt
from sbi.inference import NPE
from sbi.utils import BoxUniform
from sbi.analysis import pairplot, conditional_pairplot

torch.manual_seed(99)

# Setup: 4D Gaussian simulator
num_dim = 4
prior = BoxUniform(low=-3 * torch.ones(num_dim), high=3 * torch.ones(num_dim))

def simulator(theta):
    # Cross-correlated Gaussian noise to create dependencies between dims
    noise = torch.randn_like(theta) * 0.2
    noise[:, 1] += 0.3 * theta[:, 0]  # dim 1 correlated with dim 0
    return theta + 1.0 + noise

theta = prior.sample((4000,))
x     = simulator(theta)

inference = NPE(prior=prior)
inference.append_simulations(theta, x)
_ = inference.train()
posterior = inference.build_posterior()

x_obs = torch.tensor([1.0, 0.5, -0.5, 0.0])
samples = posterior.sample((20_000,), x=x_obs)

# --- Full pairplot: all marginals ---
fig, _ = pairplot(
    samples,
    limits=[[-3, 3]] * num_dim,
    figsize=(8, 8),
    labels=[rf"$\theta_{i+1}$" for i in range(num_dim)],
    upper="contour",  # use contour for off-diagonal joint marginals
)
plt.suptitle("4D Posterior Pairplot", y=1.01)
plt.tight_layout()
plt.savefig("posterior_4d_pairplot.png", dpi=150)

# --- Conditional pairplot: fix θ3=0, θ4=0, show θ1-θ2 conditional ---
fig, _ = conditional_pairplot(
    density=posterior,
    condition=x_obs,                          # x_obs used as conditioning context
    limits=[[-3, 3]] * num_dim,
    figsize=(5, 5),
    labels=[rf"$\theta_{i+1}$" for i in range(num_dim)],
)
plt.suptitle("Conditional Pairplot", y=1.01)
plt.tight_layout()
plt.savefig("conditional_pairplot.png", dpi=150)

plt.show()
```


---

## 6. Advanced Topics

### 6.1 Sequential Neural Posterior Estimation (SNPE)

Standard (amortized) NPE trains on simulations drawn from the prior $p(\theta)$. This can be wasteful: many simulations explore prior regions of low posterior mass. **Sequential NPE (SNPE)** addresses this by running inference in multiple *rounds*, each focusing simulations on increasingly relevant parameter regions.

**SNPE Algorithm (SNPE-C / APT)**:

```
Round 1:
  1. Sample θ ~ p(θ)           [prior proposal]
  2. Simulate x ~ simulator(θ)
  3. Train q_φ(θ|x) with standard MLE loss
  4. Set proposal p̃(θ) ← q_φ(θ|x_obs)

Round r > 1:
  1. Sample θ ~ p̃(θ)           [posterior proposal]
  2. Simulate x ~ simulator(θ)
  3. Train q_φ(θ|x) with CORRECTED loss:
     L(φ) = -E[ log q_φ(θ|x) - log p̃(θ) + log p(θ) ]
  4. Update proposal p̃(θ) ← q_φ(θ|x_obs)
```

The correction in Step 3 of each subsequent round (the APT / SNPE-C loss) is critical: without it, training on non-prior proposals produces a biased posterior estimate.

```python
# =============================================================================
# Sequential NPE (SNPE): Multi-Round Inference
# =============================================================================

import torch
from sbi.inference import NPE
from sbi.utils import BoxUniform

torch.manual_seed(7)

num_dim = 2
prior = BoxUniform(low=-2 * torch.ones(num_dim), high=2 * torch.ones(num_dim))

def simulator(theta):
    return theta + torch.randn_like(theta) * 0.5

x_obs = torch.tensor([1.2, -0.8])

# Instantiate inference object
inference = NPE(prior=prior)

# ---- Round 1: simulate from prior ----
num_sims_round1 = 1000
theta_r1 = prior.sample((num_sims_round1,))
x_r1     = simulator(theta_r1)

inference = inference.append_simulations(theta_r1, x_r1, proposal=prior)
_ = inference.train()
posterior_r1 = inference.build_posterior()

# ---- Round 2: simulate from round-1 posterior ----
# Use the round-1 posterior as the new proposal (focused on x_obs)
proposal_r2 = posterior_r1.set_default_x(x_obs)

num_sims_round2 = 1000
theta_r2 = proposal_r2.sample((num_sims_round2,))
x_r2     = simulator(theta_r2)

# append_simulations with the proposal — sbi handles the APT correction
inference = inference.append_simulations(theta_r2, x_r2, proposal=proposal_r2)
_ = inference.train()
posterior_r2 = inference.build_posterior()

# ---- Compare round-1 vs round-2 posteriors ----
samples_r1 = posterior_r1.sample((5000,), x=x_obs)
samples_r2 = posterior_r2.sample((5000,), x=x_obs)

print(f"Round 1 posterior mean: {samples_r1.mean(dim=0)}")
print(f"Round 2 posterior mean: {samples_r2.mean(dim=0)}")
# Round 2 should be more concentrated around the true θ* = [1.2, -0.8]

# Variance comparison: round 2 should have smaller variance
print(f"Round 1 posterior std:  {samples_r1.std(dim=0)}")
print(f"Round 2 posterior std:  {samples_r2.std(dim=0)}")
```

**When to use SNPE**: When simulations are expensive and you have a specific target observation. The simulation budget is concentrated around the relevant posterior region, often achieving equivalent accuracy to amortized NPE with 5-10× fewer simulations.

### 6.2 Simulation Budget Control

Controlling the simulation budget is a key practical concern. Guidelines:


| Problem complexity | Recommended simulations (amortized) | SNPE rounds |
| :-- | :-- | :-- |
| Low-dim ($d \leq 5$), simple posterior | 1,000 – 5,000 | 2–3 rounds × 500 |
| Medium-dim ($5 < d \leq 20$), complex posterior | 10,000 – 50,000 | 3–5 rounds × 2,000 |
| High-dim ($d > 20$), multimodal | 50,000+ | 5–10 rounds × 5,000 |

The `simulate_for_sbi` utility in `sbi` enables parallelized simulation generation:

```python
from sbi.utils import simulate_for_sbi

# Parallel simulation using joblib
theta, x = simulate_for_sbi(
    simulator=simulator,
    proposal=prior,
    num_simulations=10_000,
    num_workers=8,       # parallel workers
    simulation_batch_size=100,
)
```


### 6.3 Posterior Diagnostics and Validation

A trained posterior must be validated before trusting inference results. The `sbi` package implements three complementary diagnostics:

#### Posterior Predictive Checks (PPC)

Draw samples from the posterior, simulate new data, and compare to the observation:

```python
# PPC: posterior samples should reproduce x_obs
theta_post = posterior.sample((1000,), x=x_obs)
x_pred     = simulator(theta_post)

# Check: mean of predictive should match x_obs
print("Predictive mean:", x_pred.mean(dim=0))
print("Observation:    ", x_obs)

# Visualize distribution of predictives vs observation
import matplotlib.pyplot as plt
plt.hist(x_pred[:, 0].numpy(), bins=50, alpha=0.7, label="Predictive")
plt.axvline(x_obs.item(), color='red', label="Observed")
plt.legend(); plt.title("Posterior Predictive Check — Dim 1")
plt.savefig("ppc.png", dpi=150); plt.show()
```


#### Simulation-Based Calibration (SBC)

SBC checks whether the posterior has well-calibrated uncertainty. For each "fake" observation $x_i$ generated from a known $\theta_i^* \sim p(\theta)$, the rank of $\theta_i^*$ within posterior samples should be **uniformly distributed** if calibration is correct.

```python
from sbi.diagnostics import run_sbc, check_sbc

# Generate ground-truth (theta*, x*) pairs from joint
num_sbc_runs = 500
thetas_sbc = prior.sample((num_sbc_runs,))
xs_sbc     = simulator(thetas_sbc)

# Run SBC
ranks, dap_samples = run_sbc(
    thetas_sbc,
    xs_sbc,
    posterior,
    num_posterior_samples=500,
    num_workers=4,
)

# Check: should show uniform rank histograms
check_results = check_sbc(
    ranks,
    thetas_sbc,
    dap_samples,
    num_posterior_samples=500,
)
print(check_results)  # Reports uniformity statistics per dimension
```

**Interpretation**: A U-shaped rank histogram indicates **overconfident** posteriors (too narrow). An inverted-U shape indicates **underconfident** posteriors (too wide). A flat histogram = well-calibrated.

#### TARP (Test of Accuracy with Random Points)

TARP provides both necessary *and* sufficient conditions for posterior accuracy by testing expected coverage probabilities. It is available in `sbi` via `run_tarp`:

```python
from sbi.diagnostics import run_tarp

ecp, alpha = run_tarp(
    thetas_sbc,
    xs_sbc,
    posterior,
    num_posterior_samples=1000,
)
# Plot: ecp (Expected Coverage Probability) vs alpha (credibility level)
# Perfect calibration: ecp == alpha (diagonal line)
import matplotlib.pyplot as plt
plt.plot(alpha, ecp, label="TARP"); plt.plot(,,'k--', label="Ideal")[^1]
plt.xlabel("α"); plt.ylabel("ECP"); plt.legend()
plt.title("TARP Coverage Diagnostic")
plt.savefig("tarp.png", dpi=150); plt.show()
```


### 6.4 High-Dimensional Parameters and Observations

SBI in high dimensions requires special attention:

**High-dimensional observations** (e.g., images, spectra): Use an embedding network to reduce $x$ to a compact summary statistic $s = \xi_\psi(x)$.

```python
import torch.nn as nn
from sbi.inference import NPE
from sbi.utils.user_input_checks import process_prior

# Example: CNN embedding for 1D spectral data (1000 channels)
class SpectralEmbedding(nn.Module):
    def __init__(self, input_size=1000, output_size=32):
        super().__init__()
        self.net = nn.Sequential(
            nn.Conv1d(1, 16, kernel_size=5, stride=2, padding=2),
            nn.ReLU(),
            nn.Conv1d(16, 32, kernel_size=5, stride=2, padding=2),
            nn.ReLU(),
            nn.AdaptiveAvgPool1d(1),
            nn.Flatten(),
            nn.Linear(32, output_size),
        )
    
    def forward(self, x):
        # x: (batch, 1000) -> reshape to (batch, 1, 1000)
        return self.net(x.unsqueeze(1))

embedding_net = SpectralEmbedding(input_size=1000, output_size=32)

# Pass embedding network to NPE
inference = NPE(
    prior=prior,
    embedding_net=embedding_net,
)
```

**High-dimensional parameters**: Use Neural Spline Flows with sufficient coupling layers. Autoregressive flows scale well to $d \sim 100$ but can become slow at sampling. For $d > 50$, consider NRE which avoids flow normalization in parameter space.

---

## 7. Best Practices and Common Pitfalls

### 7.1 Choosing Priors and Simulators

**Prior design**:

- Make the prior as informative as physically reasonable — wide priors waste simulation budget on implausible regions.
- Avoid hard bounds on parameters that are naturally continuous; use transformed parameterizations where possible (e.g., log-uniform for scale parameters).
- For SNPE, the prior only needs to cover the posterior support — using a narrowed prior from domain knowledge dramatically reduces required simulations.

**Simulator design**:

- **Ensure differentiable-free execution**: `sbi` does not require gradients through the simulator.
- **Batch your simulator**: Always accept a 2D tensor `(N, d_theta)` as input and return `(N, d_x)`. This is orders of magnitude faster than a Python loop.
- **Test the simulator on edge cases**: Simulators often crash or return NaN for extreme parameter values. Pre-screen with `prior.sample((100,))` before training.
- **Handle failed simulations**: Use `sbi`'s built-in NaN-filtering: `inference.append_simulations(theta, x, exclude_invalid_x=True)`.


### 7.2 Debugging SBI Pipelines

Common failure modes and diagnostics:


| Symptom | Likely Cause | Fix |
| :-- | :-- | :-- |
| Training loss doesn't decrease | Learning rate too high; data not normalized | Reduce LR; normalize `x` to zero mean, unit std |
| Posterior is the prior | Too few simulations; simulator output wrong shape | Increase `num_simulations`; check shapes |
| Posterior collapse (all mass on single point) | LR too low; overtraining | Early stopping; regularization |
| NaN loss | Numerical instability in simulator or flow | Check simulator outputs; clip gradients |
| SBC rank histograms non-uniform | Insufficient simulations or bad embedding | Increase budget; improve embedding |
| Posterior samples outside prior | Prior bounds not enforced | Use `DirectPosterior` which rejects OOB samples |

**Debugging checklist**:

```python
# 1. Check shapes
assert theta.shape == (N, d_theta), f"Expected ({N}, {d_theta}), got {theta.shape}"
assert x.shape == (N, d_x),       f"Expected ({N}, {d_x}), got {x.shape}"

# 2. Check for NaN/Inf
assert not torch.isnan(theta).any(), "NaN in theta!"
assert not torch.isnan(x).any(),     "NaN in x!"

# 3. Normalize x (strongly recommended)
x_mean, x_std = x.mean(dim=0), x.std(dim=0)
x_normalized  = (x - x_mean) / (x_std + 1e-6)
x_obs_normalized = (x_obs - x_mean) / (x_std + 1e-6)
# Use x_normalized for training and x_obs_normalized for sampling

# 4. Quick sanity check: prior predictive
# Posterior predictive should be near x_obs if inference is working
theta_prior = prior.sample((100,))
x_prior_predictive = simulator(theta_prior)
print("Prior predictive range:", x_prior_predictive.min(dim=0).values,
                                  x_prior_predictive.max(dim=0).values)
print("Observation:           ", x_obs)
# If x_obs is outside this range, your prior is misspecified!
```


### 7.3 Evaluating Posterior Quality

Use the three-layer validation strategy:

1. **Posterior Predictive Checks (PPC)** — always run first. A passing PPC is evidence that the posterior is consistent with the data.
2. **Simulation-Based Calibration (SBC)** — run with ~200-500 ground-truth pairs. A failing SBC definitively indicates miscalibration.
3. **TARP** — for a sufficient (not just necessary) calibration condition.

Additionally:

- Compare NPE vs NLE posteriors for the same problem — agreement is evidence of correctness.
- Cross-validate by running inference on held-out simulated observations with known ground truth.
- Compute the **Expected Log Predictive Density (ELPD)** to compare models.


### 7.4 Practical Advice for Real Scientific Research

- **Start simple**: Begin with a toy version of your problem (fewer parameters, simpler simulator). Validate thoroughly before scaling up.
- **Precompute simulations**: Run your (expensive) simulator on a cluster, save $(\theta, x)$ pairs to disk, then train on the cluster or locally.
- **Use `simulate_for_sbi`** with `num_workers > 1` for CPU-parallelized simulation.
- **Monitor training curves**: Access training/validation loss with `inference._summary["training_log_probs"]`. Use this to detect overfitting.
- **Consider sequential methods when**: simulations cost > 10 seconds each, and you have a specific target observation.
- **Consider amortized methods when**: you need inference for many observations, or want to share a trained model.
- **Normalize your data**: Always standardize `x` to have zero mean and unit variance before passing to the flow. This is one of the highest-leverage interventions for training stability.
- **Publish your simulation budget**: Reproducible SBI requires documenting how many simulations were used, which method, and what validation diagnostics were run.

---

## 8. Summary and Further Resources

### 8.1 Key Takeaways

- **SBI enables Bayesian inference when the likelihood is intractable**, using only the ability to simulate data from the model.
- The three core methods — **NPE** (direct posterior estimation), **NLE** (surrogate likelihood), and **NRE** (likelihood ratio estimation) — trade off amortization, MCMC requirements, and expressiveness.
- **Amortized NPE** is the most convenient for problems requiring posteriors at many observations; **sequential SNPE** is more simulation-efficient for a single target observation.
- **Normalizing flows** (especially Neural Spline Flows and MAF) are the workhorse density estimators in modern SBI.
- **Validation is non-negotiable**: always run PPCs and SBC/TARP before trusting SBI posteriors in scientific applications.
- The `sbi` Python package provides a production-quality, batteries-included implementation of all major SBI methods.


### 8.2 Suggested Learning Roadmap

1. **Foundations**: Read Cranmer, Brehmer \& Louppe (2020) — "The frontier of simulation-based inference"
2. **NPE**: Papamakarios \& Murray (NeurIPS 2016) and Greenberg, Nonnenmacher \& Macke (ICML 2019 — APT/SNPE-C)
3. **NLE**: Papamakarios, Sterratt \& Murray (AISTATS 2019)
4. **NRE**: Hermans, Begy \& Louppe (ICML 2020)
5. **Normalizing flows**: Rezende \& Mohamed (2015); Papamakarios et al. (2021) "Normalizing Flows for Probabilistic Modeling"
6. **Diagnostics**: Talts et al. (2018) — Simulation-Based Calibration; Lemos et al. (2023) — TARP
7. **Hands-on**: Work through all tutorials at https://sbi.readthedocs.io

### 8.3 Recommended Papers

| Paper | Method | Venue |
| :-- | :-- | :-- |
| Cranmer, Brehmer \& Louppe (2020) | Review | PNAS |
| Papamakarios \& Murray (2016) | NPE (MDN) | NeurIPS |
| Lueckmann et al. (2017) | SNPE-B | NeurIPS |
| Greenberg, Nonnenmacher \& Macke (2019) | SNPE-C / APT | ICML |
| Papamakarios, Sterratt \& Murray (2019) | SNLE | AISTATS |
| Hermans, Begy \& Louppe (2020) | NRE | ICML |
| Durkan, Murray \& Papamakarios (2020) | NRE-C | ICML |
| Delaunoy et al. (2022) | BNRE | NeurIPS |
| Deistler, Goncalves \& Macke (2022) | TSNPE | NeurIPS |
| Talts et al. (2018) | SBC | arXiv |
| Lemos et al. (2023) | TARP | ICML |
| Papamakarios et al. (2017) | MAF | NeurIPS |

### 8.4 Recommended Resources

- **`sbi` documentation**: https://sbi.readthedocs.io
- **`sbi` GitHub**: https://github.com/sbi-dev/sbi
- **SBI benchmark suite (sbibm)**: https://github.com/sbi-benchmark/sbibm
- **Neural Likelihood-Free Inference paper list**: https://neurallikelihoodfreeinference.github.io
- **Normalizing Flows review (Papamakarios et al., 2021)**: https://arxiv.org/abs/1912.02762
- **LAMPE library** (lightweight SBI in PyTorch): https://github.com/probabilists/lampe
- **FlowJAX** (JAX-based flows with SNPE): https://github.com/danielward27/flowjax
- **BayesFlow** (Keras-based amortized inference): https://github.com/bayesflow-org/bayesflow

---

*This document was prepared as a self-contained graduate-level tutorial on Simulation-Based Inference. All code examples target `sbi >= 0.22` and Python 3.10. For bug reports or contributions, please refer to the official `sbi` repository.*

```

***

The above is the complete Markdown document. Here is a summary of what it covers, with source attribution:

The document is structured as a single, downloadable `README.md` covering all eight requested sections. Key factual foundations were drawn from the official `sbi` documentation and GitHub repository, the official getting-started tutorial, and peer-reviewed papers on the underlying methods. Specifically:[^2][^3][^4]

- **SBI motivation and applications** (including the X-ray spectral fitting example achieving sub-second posteriors post-training)[^5][^1]
- **NPE/NLE/NRE method descriptions** sourced from the `sbi` overview and comparative literature[^6][^2]
- **Sequential SNPE algorithm and APT correction** based on the Greenberg et al. (2019) framework documented in the `sbi` library[^7][^8]
- **Masked Autoregressive Flow** as the density estimation backbone[^9][^10]
- **SBC and TARP diagnostics** from the `sbi` diagnostics documentation[^11][^12]
- **Full API examples** following the official `sbi` tutorial patterns[^3][^4]
<span style="display:none">[^13][^14][^15][^16][^17][^18][^19][^20][^21][^22][^23][^24][^25][^26][^27][^28][^29][^30]</span>

<div align="center">⁂</div>

[^1]: https://arxiv.org/abs/2401.06061
[^2]: https://sbi-dev.github.io/sbi/0.22/
[^3]: https://github.com/sbi-dev/sbi
[^4]: https://sbi-dev.github.io/sbi/v0.25.0/tutorials/00_getting_started/
[^5]: https://ui.adsabs.harvard.edu/abs/2024A&A...686A.133B/abstract
[^6]: https://arxiv.org/pdf/2507.08734v1.pdf
[^7]: https://danielward27.github.io/flowjax/examples/snpe.html
[^8]: https://www.emergentmind.com/topics/sequential-neural-posterior-estimation-snpe
[^9]: https://arxiv.org/pdf/1705.07057.pdf
[^10]: https://arxiv.org/abs/1705.07057
[^11]: https://sbi-dev.github.io/sbi/v0.23.1/tutorials/11_diagnostics_simulation_based_calibration/
[^12]: https://sbi-dev.github.io/sbi/0.22/tutorial/13_diagnostics_simulation_based_calibration/
[^13]: https://arxiv.org/html/2401.06061v1
[^14]: https://wwwmpa.mpa-garching.mpg.de/~komatsu/lecturenotes/Noemi_Anau_Montel_on_SBI.pdf
[^15]: https://pypi.org/project/sbi/0.10.0/
[^16]: https://pypi.org/project/sbi/0.19.1/
[^17]: https://arxiv.org/abs/2404.13557
[^18]: https://sbi.readthedocs.io/en/latest/
[^19]: https://neurallikelihoodfreeinference.github.io
[^20]: https://www.biorxiv.org/content/10.1101/2025.11.25.690436v1
[^21]: https://www.youtube.com/watch?v=9Mc-xg1DJ7k
[^22]: https://homepages.inf.ed.ac.uk/imurray2/pub/17maf/maf.pdf
[^23]: https://www.research.ed.ac.uk/en/publications/masked-autoregressive-flow-for-density-estimation
[^24]: https://www.youtube.com/watch?v=oKeDfD4IYLY
[^25]: https://arxiv.org/html/2502.03279v2
[^26]: https://www.emergentmind.com/topics/masked-autoregressive-flow
[^27]: https://peluigi.hatenablog.com/entry/2018/07/18/174133
[^28]: https://arxiv.org/html/2311.12530v4
[^29]: https://www.youtube.com/watch?v=7q4ueFiJjAY
[^30]: https://mc-stan.org/docs/stan-users-guide/simulation-based-calibration.html```

