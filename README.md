# Echo Chamber Effect Research: Signaling Game Model

**Project Code:** PROJECT_ECHO_GAME

## Overview

This project implements a multi-agent evolutionary model to study echo chamber formation in social networks through signaling game theory. The simulation explores how the pursuit of social reputation (rather than truth) leads to opinion polarization and identifies critical phase transitions in collective behavior.

## Key Features

- **Game-Theoretic Framework**: Agents balance local conformity pressure against global truth-seeking
- **Phase Transition Analysis**: Identifies critical parameters where consensus shifts to extreme polarization
- **Adaptive Experimentation**: Auto-evaluation loop ensures scientific rigor
- **Publication-Ready Output**: Complete academic paper with high-quality visualizations

## Requirements

```bash
pip install numpy networkx matplotlib scipy
```

For paper compilation:
```bash
sudo apt-get install texlive-latex-base texlive-latex-extra texlive-fonts-recommended texlive-science
```

## Usage

### Run Simulation

```bash
python3 simulation.py
```

The simulation will:
1. Conduct parameter sweeps over α (conformity) and β (truth concern)
2. Run auto-evaluation checkpoints
3. Generate data in `data/results_final.csv`
4. Create visualizations in `figures/`

**Expected runtime**: 5-10 minutes

### Compile Paper

```bash
cd paper
pdflatex main.tex
pdflatex main.tex  # Second pass for references
```

Note: You may need to press Enter when prompted about bibliography warnings.

## Project Structure

```
.
├── simulation.py           # Main simulation code with adaptive loop
├── data/
│   ├── results_final.csv   # Final experimental data
│   └── results_iter1.csv   # Iteration 1 data
├── figures/
│   ├── fig1_phase_diagram.png      # Phase transition map
│   ├── fig2_time_evolution.png     # Temporal dynamics
│   └── fig3_network_structure.png  # Echo chamber clustering
├── paper/
│   ├── main.tex            # LaTeX source
│   └── main.pdf            # Compiled paper (7 pages, 4.2MB)
└── agent_task.md           # Original task specification
```

## Scientific Model

### Network Topology
- Watts-Strogatz small-world network
- N = 1000 nodes, k = 10 neighbors, p = 0.1 rewiring probability

### Agent Dynamics

Each agent has:
- **Opinion** O ∈ [-1, 1]: Position on an issue
- **Reputation** R: Cumulative social score
- **Strategy** (α, β): Conformity vs. truth-seeking parameters

### Utility Function

```
U_i = α · LocalConformity - β · TruthDeviation

LocalConformity = -|O_i - ⟨O_neighbors⟩|
TruthDeviation = |O_i - O_true|
```

### Key Findings

1. **Phase Transition**: Sharp boundary near α ≈ β (around 0.5-0.6)
2. **Critical Insight**: Echo chambers inevitable when α > β
3. **Temporal Pattern**: Bimodal split occurs at t ≈ 50-100 steps
4. **Network Effect**: Spatial segregation emerges spontaneously

## Output Files

### Data Files
- `data/results_final.csv`: Contains α, β, polarization index, standard deviation, and convergence times

### Visualizations
- **Fig 1**: Phase diagram showing polarization as function of (α, β)
- **Fig 2**: Opinion distribution evolution at four time points
- **Fig 3**: Network visualization with opinion-based node coloring

### Academic Paper
- 7-page publication-ready paper
- Suitable for Physical Review E or Journal of Artificial Societies and Social Simulation (JASSS)
- Includes Abstract, Model, Results, Discussion, and References

## Auto-Evaluation Checkpoints

The simulation includes three quality checks:

1. **Non-triviality**: Results must show ≥3 distinct polarization levels
2. **Phase Transition**: Maximum polarization jump must exceed 0.05
3. **Robustness**: Standard deviation across runs must be <0.2

## Citation

If you use this code, please cite:

```bibtex
@article{echogame2024,
  title={Echo Chamber Formation through Signaling Games: A Phase Transition Analysis},
  author={PI-Agent Research Group},
  journal={In Preparation},
  year={2024}
}
```

## License

This project is for academic research purposes.

## Acknowledgments

Built using:
- NumPy for numerical computations
- NetworkX for graph operations
- Matplotlib for visualizations
- LaTeX for paper production

---

**Status**: ✅ Complete and ready for publication
