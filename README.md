# Bayesian-Analysis-of-Cosmic-Ray-Proton-Spectrum

# Bayesian Analysis of the Cosmic Ray Proton Spectrum

## Overview

This repository contains a statistical and Bayesian analysis of cosmic ray proton flux measurements obtained from multiple experiments in the Cosmic Ray Database (CRDB). The objective of the project is to estimate the parameters of the cosmic ray energy spectrum and evaluate whether the observed data can be described by a single power-law model.

Cosmic rays are highly energetic charged particles originating from astrophysical sources such as supernova remnants and other energetic galactic processes. The energy spectrum of cosmic rays is known to approximately follow a power-law distribution across a wide range of energies.

This project applies both deterministic fitting and Bayesian inference using Markov Chain Monte Carlo (MCMC) to estimate the parameters of the cosmic ray proton spectrum.

---

## Physical Model

The cosmic ray flux is modeled using a power-law relationship between particle energy and flux:

$$
F(E) = F_0 E^{-p}
$$

where

- $F(E)$ represents the differential cosmic ray flux
- $E$ is the particle kinetic energy per nucleon
- $F_0$ is the normalization constant
- $p$ is the spectral index

---

## Dataset

The dataset consists of multiple experimental measurements of proton flux. Each experiment provides measurements of

- mean energy $\langle E \rangle$
- measured flux
- statistical uncertainty
- systematic uncertainty
- total measurement error

To reduce the influence of solar modulation at low energies, only data above the threshold

$$
E > 24 \, \mathrm{GeV/n}
$$

are used in the fitting procedure.

---

## Deterministic Fit

A deterministic least-squares fit is performed by minimizing the chi-square statistic

$$
\chi^2 = \sum_{i} \left(\frac{y_i - F(E_i)}{\sigma_i}\right)^2
$$

where

- $y_i$ is the observed flux
- $\sigma_i$ is the measurement uncertainty
- $F(E_i)$ is the model prediction

The goodness of fit is evaluated using

$$
\chi^2_{\mathrm{red}} = \frac{\chi^2}{\nu}
$$

where $\nu$ is the number of degrees of freedom.

---

## Bayesian Inference

To obtain probabilistic estimates of the parameters, Bayesian inference is performed using MCMC sampling.

The posterior distribution is given by

$$
P(\theta|D) \propto P(D|\theta)P(\theta)
$$

where

- $\theta = (F_0, p, f)$ are the model parameters
- $P(D|\theta)$ is the likelihood
- $P(\theta)$ is the prior distribution

---

## Likelihood Function

The likelihood assumes Gaussian measurement uncertainties. The log-likelihood is written as

$$
\ln L = -\frac{1}{2} \sum_i
\left[
\frac{(y_i - F(E_i))^2}{\sigma_i^2}
+
\ln(\sigma_i^2)
\right]
$$

To account for possible additional scatter between experiments, an extra fractional variance parameter $f$ is introduced:

$$
\sigma_{\mathrm{tot}}^2 = \sigma_i^2 + (f y_i)^2
$$

---

## Parameters Estimated

The Bayesian analysis estimates three parameters:

- $F_0$ : normalization constant
- $p$ : spectral index
- $f$ : additional fractional scatter

---

## MCMC Sampling

The posterior distribution is sampled using an ensemble MCMC sampler. Multiple walkers explore the parameter space and generate a chain of samples from the posterior distribution.

Posterior samples are used to compute

- median parameter values
- credible intervals
- parameter correlations

These results are visualized using corner plots and posterior predictive models.

---

## Posterior Predictive Model

Posterior samples are used to generate predicted spectra

$$
F(E;F_0,p)
$$

which produce credible intervals representing the uncertainty in the model prediction.

---

## Residual Analysis

Model performance is evaluated using normalized residuals

$$
r_i = \frac{y_i - F(E_i)}{\sigma_i}
$$

Residual distributions help identify systematic deviations between the model and the observed data.

---

## Scientific Interpretation

The inferred spectral index is consistent with the expected cosmic ray spectrum observed in high-energy astrophysics.

The additional variance parameter indicates that small systematic differences exist between experimental datasets.

---

## Key Concepts

This project demonstrates the application of

- statistical model fitting
- chi-square goodness-of-fit testing
- Bayesian inference
- Markov Chain Monte Carlo sampling
- posterior predictive modeling

to real astrophysical observational data.

---

## Tools Used

- Python
- NumPy
- Pandas
- SciPy
- Matplotlib
- emcee
- corner

---

## Repository Structure

