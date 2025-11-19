# LogicGraphNet - Counterfactual-Guided Policy Improvement for Neural Theorem Proving

[![Kaggle](https://img.shields.io/badge/Kaggle-Notebooks-20BEFF?logo=kaggle&logoColor=white)](https://www.kaggle.com/code)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

## 📋 Overview
LogicGraphNet introduces **Counterfactual-Guided Policy Improvement (CGPI)**, a training methodology that teaches neural theorem provers to anticipate and avoid failures by learning from imagined "what-if" scenarios. Combined with a specialized graph-based architecture, it achieves competitive performance with large language models while being **63× smaller** and **1.7× faster**.

### 🎯 Key Innovations
- **🧠 CGPI Training**: Generates counterfactual "good" states from failed proofs, enabling proactive failure avoidance
- **📊 Graph Architecture**: Specialized encoder for proof structure representation  
- **🚀 Superior Generalization**: 71.21% success on novel mathematical concepts vs LLM's 68.18%

### ✅ Key Achievements
- Equal performance to 125M-parameter LLM with only **1.98M parameters** (63× smaller)
- **+10.2% improvement** from CGPI training (ablation-validated)
- **Better generalization**: Performs better on unseen concepts (negative generalization gap)
- **Practical efficiency**: 7.55 MB memory footprint, 0.075s inference time

## 🏆 Main Results

<div align="center">

### Model Comparison (LeanDojo Benchmark 4 - Novel Premises Split)
| Model | Success Rate | Params | Memory | Inference Time | Novel Premises | Speedup |
|:-----:|:------------:|:------:|:------:|:--------------:|:--------------:|:-------:|
| **LogicGraphNet** | **65.0%** | **1.98M** | **7.55 MB** | **0.075s** | **71.21%** | **1.7×** |
| LLM Baseline (Galactica-125M) | 65.0% | 125.03M | 476.95 MB | 0.129s | 68.18% | 1.0× |
| NeuralSearchBaseline | 34.0% | 0.97M | 3.68 MB | 0.037s | 40.91% | 3.5× |
| Random | 15.5% | - | - | - | 18.18% | - |

**Key Finding**: LogicGraphNet matches the 125M-parameter LLM performance while being **63.2× smaller** in parameters and **63.2× more memory efficient**, with superior generalization to novel mathematical concepts (**+3.03%** on novel premises).

### Ablation Study: CGPI Training Contribution
| Training Method | Success Rate | Novel Premises | Verifier Calls | Improvement |
|:---------------:|:------------:|:--------------:|:--------------:|:-----------:|
| **Full CGPI** | **65.0%** | **71.21%** | **5.66** | - |
| Standard RL (No CGPI) | 59.0% | 62.12% | 7.95 | - |
| **CGPI Contribution** | **+6.0%** | **+9.09%** | **-28.9%** | **+10.2% relative** |

**Conclusion**: CGPI training provides statistically significant performance gains (**+10.2%** relative improvement), validating the counterfactual learning hypothesis.

### Generalization Analysis: Negative Generalization Gap
| Model | Overall Success | Novel Premises | Generalization Gap |
|:-----:|:--------------:|:--------------:|:------------------:|
| **LogicGraphNet** | **65.0%** | **71.21%** | **-6.21% ✅** |
| LLM Baseline | 65.0% | 68.18% | -3.18% |
| NeuralSearchBaseline | 34.0% | 40.91% | -6.91% |

**Interpretation**: Negative gap indicates the model performs better on unseen mathematical concepts, demonstrating robust reasoning strategies rather than memorization.

</div>

## 💻 Code & Notebook
**Complete Experiment**: **[LogicGraphNet_Experiment1.ipynb](https://github.com/Ahmed-Sleem/LogicGraphNet/blob/main/LogicGraphNet_Experiment1.ipynb)**
- Full training, evaluation, and ablation studies
- Main model training (LogicGraphNet, LLM, NeuralSearch baselines)
- CGPI vs Standard RL ablation
- Corrective Lookahead vs Greedy search analysis
- Hyperparameter sensitivity (lookahead depth)
- Memory and timing analysis
- All visualizations and metrics

**Platform**: Kaggle GPU/CPU (fully reproducible)  
**Runtime**: ~15 minutes (training + all ablations)  
**Dataset**: LeanDojo Benchmark 4 (Novel Premises split, 8K train / 200 test theorems)

## 📊 Dataset
**LeanDojo Benchmark 4 (Novel Premises Split)**: **[Kaggle Dataset](https://www.kaggle.com/datasets/a7medsleem/leandojo-benchmark-4-creators)**
- **Source**: Kaggle Dataset
- **Task**: Formal mathematics theorem proving in Lean
- **Challenge**: Generalize to theorems requiring novel mathematical premises (zero-shot reasoning)
- **Split**: 145,520 train / 2,000 val / 2,000 test theorems
- **Used**: 8,000 train / 200 val / 200 test (resource-constrained setting)
- **Preprocessing**: Graph construction from proof traces, sinusoidal encoding for node features, counterfactual augmentation for failed proofs

## 📁 Repository Structure


```text
LogicGraphNet/
│
├── LogicGraphNet_Experiment1.ipynb    # Complete experimental suite
├── LICENSE                            # Apache-2.0 License
└── README.md                          # This file
```


## 🔬 Key Contributions
1. **CGPI Methodology**: First counterfactual-guided training for theorem provers (10.2% ablation-validated improvement)
2. **Negative Generalization Gap**: Superior performance on novel concepts (71.21% vs 68.18%)
3. **Practical Efficiency**: 63× smaller, 1.7× faster than competitive LLM baseline
4. **Graph-Based Architecture**: Specialized design for proof structure (1.98M parameters)

## 📝 Citation

If you use this work in your research, please cite:

```bibtex
@article{sleem2024logicgraphnet,
  title={Failing Forward: How Analyzing Mistakes Creates More Efficient and Robust AI Theorem Provers},
  author={Sleem, Ahmed and Adly, Nihal Ahmed and Zaky, Ahmed B.},
  year={2024},
  institution={Egypt-Japan University of Science and Technology (E-JUST)},
  url={https://github.com/Ahmed-Sleem/LogicGraphNet},
  doi={10.5281/zenodo.XXXXXXX}
}
```

## 📧 Contact

**Ahmed Sleem**  
📧 ahmad.muhamad@ejust.edu.eg  🏛️ Egypt-Japan University of Science and Technology (E-JUST), Alexandria, Egypt

📧 ahmedsleemsocial@gmail.com

**Co-authors**:
- Nihal Ahmed Adly (nihal.abdelmonem@ejust.edu.eg)
- Gamila S. Elfayoumi (gamila.elfayoumi@ejust.edu.eg)
- Ahmed B. Zaky (ahmed.zaky@ejust.edu.eg, ahmed.zaky@feng.bu.edu.eg)

---

## 📜 License

This project is licensed under the Apache License 2.0 - see the LICENSE file for details.

```text
Copyright 2024 Ahmed Sleem, Egypt-Japan University of Science and Technology

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

<div align="center">
Egypt-Japan University of Science and Technology (E-JUST)

⭐ If you find this work useful, please cite our paper and star this repository!
</div>

