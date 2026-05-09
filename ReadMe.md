# 🔬 Theoretically and Practically Faster Algorithms for Protein Structure Alignment

[![License: MIT](https://img.shields.io/badge/license-MIT-red.svg)](https://github.com/masat03110/ProteinStructureAlignmentPlus/blob/main/LICENSE)
![Language](https://img.shields.io/badge/Language-C++%2FPython-blue)
[![Dataset](https://img.shields.io/badge/Dataset-PDB-success)](https://www.rcsb.org/)

This repository contains an implementation of algorithms for the **Protein Structure Alignment problem**, formulated as the **sequential Largest Common Point-set (sLCP) problem** under the **bottleneck distance**.

The implementation accompanies the paper:

> **Theoretically and Practically Faster Algorithms for Protein Structure Alignment**  
> Masahito Tsukahara and Tetsuo Shibuya

---

## 📖 Overview

Protein structure alignment is a fundamental task in structural bioinformatics. Given two proteins represented as ordered sequences of Cα atoms, the goal is to find a largest order-preserving common substructure that can be aligned within a given distance threshold.

This work studies the problem through the sequential LCP formulation under the bottleneck distance. It provides both:

- a faster polynomial-time exact algorithm from a theoretical perspective, and
- a practically faster approximation algorithm with the same solution-size guarantee as the previous guaranteed framework.

The approximation algorithm is designed for realistic protein data and is evaluated on structures from the Protein Data Bank (PDB).

---

## ✨ Key Contributions

- **⚙️ Improved exact algorithm:**  
  We improve the theoretical running time of a reliable exact algorithm from  
  `O(n^14)` to `O(Δ_ε n^13 log n)`  
  by exploiting the bounded-density property of protein structures.

- **🔎 Faster guaranteed approximation:**  
  We introduce a filtering technique for the approximation framework of Li and Ng and Tsukahara--Shibuya.

- **🛡️ Preserved theoretical guarantee:**  
  The improved approximation algorithm preserves the guarantee that, for approximation factor `0 < delta <= 3`, it finds a subsequence whose size is at least the optimum under threshold `epsilon`, while allowing alignment distance `(1 + delta) epsilon`.

- **🚀 Substantial practical speedup:**  
  On PDB-derived benchmark instances, the proposed method achieves **over a 24-fold speedup at n = 130** compared with the fastest previous guaranteed baseline.

- **🧬 Larger practical input range:**  
  Previous guaranteed methods became costly around `n = 120--130`.  
  The proposed method processes:
  - `n = 120` in 5.83 minutes on average,
  - `n = 130` in 9.50 minutes on average,
  - `n = 200` in 2.33 hours on average,
  - `n = 210` in 3.33 hours on average.

- **🌍 Expanded PDB coverage:**  
  Since the median PDB entity length is around 210 residues in the analyzed dataset, the proposed method extends the practically accessible range from roughly the shortest 25% of PDB entities to nearly 50%.

---

## 📂 Repository Structure

```bash
.
├── src/         # Core algorithm implementations
├── include/     # Header files
├── samples/     # Sample PDB files
├── results/     # Alignment outputs and experimental results
├── README.md    # Project overview and usage
├── Makefile     # Build instructions
└── LICENSE      # License information
```

---

## 📦 Getting Started

### Requirements

- C++20 or later  
- Python 3.12+  
- [Eigen 3.4.0](https://eigen.tuxfamily.org/index.php?title=Main_Page) – for linear algebra operations in C++  
- [argparse](https://github.com/p-ranav/argparse) – for command-line argument parsing in C++


### Installation

```bash
# Clone the repository
git clone https://github.com/masat03110/ProteinStructureAlignmentPlus.git
cd ProteinStructureAlignmentPlus

# (Optional) Download Eigen and argparse if not already installed
# You can place them in 'include/' or adjust the include path accordingly.

# Compile the main program
make
```

### Example Usage
```bash
# Align two PDB files using AlignFastPlus
./aligner samples/1pyv_trimmed.pdb samples/7my8_trimmed.pdb --Algorithm AlignFastPlus

# Visualize output using Python
python src/plot.py
python -m http.server 8000
```

For more detailed options and usage instructions, run:
```bash
./aligner -h
python src/plot.py -h
```


---

## 📊 Experimental Summary

The algorithms were evaluated on random consecutive Cα segments sampled from PDB proteins.

Basic settings:

- distance threshold: `epsilon = 2.0 Å`
- approximation factor: `delta = 3`
- equal input lengths: `n = m`
- 1000 trials for each setting

| Metric | Previous Guaranteed Baseline | Proposed Method |
| :--- | :--- | :--- |
| Mean time at `n = 120` | 1.54 hours | 5.83 minutes |
| Mean time at `n = 130` | 3.80 hours | 9.50 minutes |
| Speedup at `n = 130` | Baseline | over 24x |
| Largest tested practical size | around 130 | around 210 |
| Mean time at `n = 200` | not evaluated | 2.33 hours |
| Mean time at `n = 210` | not evaluated | 3.33 hours |
| Theoretical guarantee | guaranteed | preserved |

---

## 🎯 Applications

- Pairwise protein structure alignment
- Common 3D substructure detection
- Comparative structural bioinformatics
- Evaluation of protein model similarity under distance constraints

---

## 📝 Citation

If you use this repository, please cite the accompanying paper:

```bibtex
@inproceedings{tsukahara_shibuya_2026_protein_alignment,
  title     = {Theoretically and Practically Faster Algorithms for Protein Structure Alignment},
  author    = {Tsukahara, Masahito and Shibuya, Tetsuo},
  year      = {2026}
}
```

---

## 🤝 Contributing
Contributions, issues, and feature requests are highly welcome!

Feel free to open a pull request or submit an issue for discussion.

---

### 📫 Contact
For questions, discussions, or collaborations:

Masahito Tsukahara

Email: tsuka03@hgc.jp

---

## ⭐ Acknowledgments
Special thanks to the open-source community and the Protein Data Bank (PDB) for providing the invaluable datasets that made this research possible.