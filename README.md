# Nonequilibrium training dynamics and scaling laws of language models

Xu Z., 2026, *Nonequilibrium training dynamics and scaling laws of language models*, Zenodo [doi:10.5281/zenodo.24096774](https://doi.org/10.5281/zenodo.24096774). The preprint is posted on Research Square, [doi:10.21203/rs.3.rs-10529159/v1](https://doi.org/10.21203/rs.3.rs-10529159/v1). This record is a new version of the earlier record [zenodo.org/records/21685713](https://zenodo.org/records/21685713).

Why does the loss of a large language model (LLM) fall as a power law of training data and model size? This work explains the neural scaling laws of LLMs with a stochastic multiscale theory borrowed from turbulence and cosmic structure formation, and tests it on the scale-dependent cross-entropy loss of the Pythia model suite, GPT-2 and SmolLM2.

## Major findings

- The scale-dependent loss L<sub>r</sub>(r, s), the held-out loss when the usable context is restricted to the last r tokens at training step s, defines a loss spectrum E<sub>X</sub> = −∂L<sub>r</sub>/∂r, the analogue of the energy spectrum of turbulence.
- Treating learning as a biased random walk in r with waiting time τ<sub>r</sub> ∝ r<sup>−γ</sup>, the exact Fokker–Planck solution gives E<sub>X</sub> ∝ r<sup>−(1+γ)</sup> with an exponential cutoff at a scale ξ; Heaps’ law (α<sub>H</sub> ≈ 1/2) fixes γ = α<sub>H</sub>/3 = 1/6, so E<sub>X</sub> ∝ r<sup>−7/6</sup>. The measured spectra of converged Pythia and GPT-2 models fall as r<sup>−1.10</sup> to r<sup>−1.21</sup> over r = 2–32.
- Training has two phases separated by a critical step s* (about 2000 for Pythia-160M). After s* the context gain ΔL<sub>r</sub> and the full-context loss L<sub>∞</sub> are predicted to change as s<sup>+1/10</sup> and s<sup>−1/10</sup>; Pythia-160M gives s<sup>+0.075</sup> and s<sup>−0.101</sup> over s = 2000–10<sup>4</sup>.
- The same theory gives the loss-versus-data exponent α<sub>D</sub> = γ/(2 − 2γ) = 1/10, close to the empirical 0.095; treating model size N as the effective Langevin time gives α<sub>N</sub> = λγ/(2 − 2γ), with λ = 3/4 giving 3/40 ≈ 0.075, and the joint form L(N, D) = [(N<sub>c</sub>/N)<sup>λ</sup> + D<sub>c</sub>/D]<sup>α<sub>D</sub></sup>.
- Against model size, L<sub>∞</sub> of Pythia 14M–1.4B at the final checkpoint falls as N<sub>nb</sub><sup>−0.10</sup> (non-embedding parameters) and N<sub>tot</sub><sup>−0.155</sup> (total parameters).

## Contents

- `P25_revised.pdf`: the manuscript.
- `csv/`: the plotted data of Figs 1–9 and the model properties of Table 1 (10 files).
- `CITATION.cff`: citation metadata.
- `LICENSE`: licence for the contents.

The losses are cross-entropy losses of public checkpoints of the Pythia suite ([EleutherAI/pythia](https://github.com/EleutherAI/pythia)), GPT-2 and SmolLM2, evaluated by the author.

The same files are archived on Zenodo: [doi:10.5281/zenodo.24096774](https://doi.org/10.5281/zenodo.24096774) (all versions: [doi:10.5281/zenodo.21685712](https://doi.org/10.5281/zenodo.21685712)).
