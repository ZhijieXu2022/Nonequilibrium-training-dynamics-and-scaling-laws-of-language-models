# Nonequilibrium training dynamics and scaling laws of language models

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24096774.svg)](https://doi.org/10.5281/zenodo.24096774)
[![Preprint](https://img.shields.io/badge/Research%20Square-10.21203%2Frs.3.rs--10529159%2Fv1-blue)](https://doi.org/10.21203/rs.3.rs-10529159/v1)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

Xu Z., 2026, *Nonequilibrium training dynamics and scaling laws of language models*, Zenodo [doi:10.5281/zenodo.24096774](https://doi.org/10.5281/zenodo.24096774). The preprint is posted on Research Square, [doi:10.21203/rs.3.rs-10529159/v1](https://doi.org/10.21203/rs.3.rs-10529159/v1). This record is a new version of the earlier record [zenodo.org/records/21685713](https://zenodo.org/records/21685713).

Why does the loss of a large language model (LLM) fall as a power law of training data and model size? This work explains the neural scaling laws of LLMs with a stochastic multiscale theory borrowed from turbulence and cosmic structure formation, and tests it on the scale-dependent cross-entropy loss of the Pythia model suite, GPT-2 and SmolLM2.

**Keywords:** large language models (LLM), neural scaling laws, training dynamics, loss spectrum, context length, cross-entropy loss, Heaps' law, Kaplan scaling law, Fokker–Planck equation, random walk, nonequilibrium statistical physics, turbulence, energy cascade, Kolmogorov spectrum, Pythia, GPT-2, SmolLM2, transformer.

## Major findings

- The scale-dependent loss L<sub>r</sub>(r, s), the held-out loss when the usable context is restricted to the last r tokens at training step s, defines a loss spectrum E<sub>X</sub> = −∂L<sub>r</sub>/∂r, the analogue of the energy spectrum of turbulence.
- Treating learning as a biased random walk in r with waiting time τ<sub>r</sub> ∝ r<sup>−γ</sup>, the exact Fokker–Planck solution gives E<sub>X</sub> ∝ r<sup>−(1+γ)</sup> with an exponential cutoff at a scale ξ; Heaps’ law (α<sub>H</sub> ≈ 1/2) fixes γ = α<sub>H</sub>/3 = 1/6, so E<sub>X</sub> ∝ r<sup>−7/6</sup>. The measured spectra of converged Pythia and GPT-2 models fall as r<sup>−1.10</sup> to r<sup>−1.21</sup> over r = 2–32.
- Training has two phases separated by a critical step s* (about 2000 for Pythia-160M). After s* the context gain ΔL<sub>r</sub> and the full-context loss L<sub>∞</sub> are predicted to change as s<sup>+1/10</sup> and s<sup>−1/10</sup>; Pythia-160M gives s<sup>+0.075</sup> and s<sup>−0.101</sup> over s = 2000–10<sup>4</sup>.
- The same theory gives the loss-versus-data exponent α<sub>D</sub> = γ/(2 − 2γ) = 1/10, close to the empirical 0.095; treating model size N as the effective Langevin time gives α<sub>N</sub> = λγ/(2 − 2γ), with λ = 3/4 giving 3/40 ≈ 0.075, and the joint form L(N, D) = [(N<sub>c</sub>/N)<sup>λ</sup> + D<sub>c</sub>/D]<sup>α<sub>D</sub></sup>.
- Against model size, L<sub>∞</sub> of Pythia 14M–1.4B at the final checkpoint falls as N<sub>nb</sub><sup>−0.10</sup> (non-embedding parameters) and N<sub>tot</sub><sup>−0.155</sup> (total parameters).

## Contents

- `P25_revised.pdf`: the manuscript.
- `csv/`: the plotted data of Figs 1–9 and the model properties of Table 1 (10 files, described below).
- `CITATION.cff`: citation metadata (used by GitHub's "Cite this repository" button).
- `LICENSE`: licence for the contents.

### Data files

| File | Content |
|---|---|
| `csv/Fig01_L_vs_r_2.csv` | Fig. 1: scale-dependent loss L<sub>r</sub>(r) of converged GPT-2, Pythia-70M/160M/410M and SmolLM2-135M |
| `csv/Fig02_L_vs_r_all_steps_2.csv` | Fig. 2: L<sub>r</sub>(r, s) of Pythia-160M at training steps s = 1 … 143 000 (and TinyLlama) |
| `csv/Fig03_L_vs_steps_fix_r_4.csv` | Fig. 3: L<sub>1</sub>(s), L<sub>∞</sub>(s) and ΔL<sub>r</sub>(s) of Pythia-160M with guide lines |
| `csv/Fig04_Normalized_spectrum_L_vs_steps_3.csv` | Fig. 4: normalized loss spectrum P<sub>X</sub>(r, s) of Pythia-160M and converged models |
| `csv/Fig05_cumulateive_loss_vs_r_5.csv` | Fig. 5: cumulative loss Λ<sub>X</sub>(r, s) = L<sub>r</sub> − L<sub>∞</sub> of Pythia-160M |
| `csv/Fig06_Loss_vs_xi_2.csv` | Fig. 6: theory curves ΔL<sub>r</sub> = Bξ<sup>β</sup> and L<sub>∞</sub> = ln(N<sub>voc</sub>) ξ<sup>−γ</sup> |
| `csv/Fig07_varepsilon_vs_logL_logxi_2.csv` | Fig. 7: normalized flux ε̄<sub>X</sub>(μ) for r/ξ = 1, 0.5, 0.1, 0.01 |
| `csv/Fig08_Kesi_and_delta_L_r_vs_steps.csv` | Fig. 8: fitted ξ<sub>A</sub>(s), C<sub>X</sub>(s) and A(s) of Pythia-160M with guide lines |
| `csv/Fig09_L_vs_N_parameter.csv` | Fig. 9: L<sub>1</sub>, L<sub>∞</sub> and ΔL<sub>r</sub> of Pythia 14M–1.4B at s = 143 000 against total and non-embedding parameters |
| `csv/Table01_model_properties.csv` | Table 1: architectures of the models (dimensions, heads, layers, context length, vocabulary, parameter counts) |

Each CSV starts with `#` header lines (publisher, date, name, reference, notes) followed by the column names and the data. Losses are cross-entropy in nats; r is the context length in tokens; s is the optimizer step.

The losses are cross-entropy losses of public checkpoints of the Pythia suite ([EleutherAI/pythia](https://github.com/EleutherAI/pythia)), GPT-2 and SmolLM2, evaluated by the author.

## How to cite

```bibtex
@misc{Xu2026_nonequilibrium_scaling_zenodo,
  author    = {Xu, Zhijie},
  title     = {Nonequilibrium training dynamics and scaling laws of language models},
  year      = {2026},
  publisher = {Zenodo},
  version   = {v2},
  doi       = {10.5281/zenodo.24096774},
  url       = {https://doi.org/10.5281/zenodo.24096774}
}

@misc{Xu2026_nonequilibrium_scaling_preprint,
  author = {Xu, Zhijie},
  title  = {Nonequilibrium training dynamics and scaling laws of language models},
  year   = {2026},
  note   = {Preprint, Research Square},
  doi    = {10.21203/rs.3.rs-10529159/v1}
}
```

## Related work

The random-walk theory behind this work, for the Kolmogorov spectrum, halo mass functions and halo density profiles: Z. Xu, *Scientific Reports* (2026), [doi:10.1038/s41598-026-69825-4](https://doi.org/10.1038/s41598-026-69825-4).

The same files are archived on Zenodo: [doi:10.5281/zenodo.24096774](https://doi.org/10.5281/zenodo.24096774) (all versions: [doi:10.5281/zenodo.21685712](https://doi.org/10.5281/zenodo.21685712)).
