# SSH model with quasiperiodic hopping terms.
codes about a ssh model with quasiperiodic hopping terms, topology and localization transition are studied.

## main function
main1: loclization-delocalization transition /mobility edges.\
main2: real space topological invariant and edge modes\

## functions
Hssh: generate the Hamiltonian (SSH model). \
Hssh_disorder: generate the Hamiltonian (SSH model with quasiperiodic hopping terms).\
r_w: calculate the topological invariant in the real space.

## Running an experiment

Use MATLAB with local functions in scripts (R2016b or later). Work from the
repository root so `Hssh_disorder.m`, `Ipr.m`, and `r_w.m` resolve locally.

```matlab
addpath(pwd)
rng(0)       % Optional reproducibility for the random phase
main1       % IPR versus hopping-modulation amplitude, colored by log10(IPR)
% Run separately:
rng(0)
main2       % Real-space invariant and minimum absolute eigenvalue
```

Both scripts use 100 unit cells and dense eigendecompositions. They draw one
random phase per invocation; edit the local experiment function to change
sizes, parameter grids, or sampling. `Hssh` uses L unit cells and returns
a 2L-by-2L matrix. In `Hssh_disorder(L,v,w,J0,delta)`, the intracell hopping
is J0 + w*cos(2*pi*omega*j + delta), and v is the intercell hopping.

`main2` now omits an unused Q1 sum. Its Q projector, sign convention,
edge cutoff, and plotted observables retain the historical implementation.
The IPR helper is deliberately local to this repository; no other repository
needs to be installed.

