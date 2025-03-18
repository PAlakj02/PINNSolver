# 🧠 Physics-Informed Neural Networks (PINNs) for Solving Differential Equations

## 📌 Project Overview
This project leverages **Physics-Informed Neural Networks (PINNs)** to solve the **time-dependent Schrödinger equation**, a fundamental equation in quantum mechanics. Unlike traditional numerical methods (finite difference, finite element), PINNs offer a **mesh-free**, **differentiable**, and **computationally efficient** approach by embedding the physics of the problem into the neural network loss function.  

We compare the performance of a **standard Neural Network (NN)** with a **PINN-based model** and evaluate different training approaches to highlight the advantages of PINNs in solving differential equations.

---

## 📚 Table of Contents
- [📌 Project Overview](#-project-overview)
- [📊 Mathematical Formulation](#-mathematical-formulation)
- [🛠 Model Architecture](#-model-architecture)
- [🚀 Implementation](#-implementation)
- [📈 Results & Approaches](#-results--approaches)
- [🔍 Dependencies & Setup](#-dependencies--setup)
- [🔬 Future Improvements](#-future-improvements)
- [📝 References](#-references)

---

## 📊 Mathematical Formulation
### **Schrödinger Equation**
The one-dimensional **time-dependent Schrödinger equation** governs the wave function evolution of a quantum system:  

\[
i \hbar \frac{\partial \psi(x,t)}{\partial t} = -\frac{\hbar^2}{2m} \frac{\partial^2 \psi(x,t)}{\partial x^2} + V(x) \psi(x,t)
\]

where:
- \( \psi(x,t) \) is the complex wave function
- \( V(x) \) is the potential energy function
- \( \hbar \) is the reduced Planck’s constant

### **Initial and Boundary Conditions**
- **Initial Wave Function**: Modeled as a **Gaussian wave packet**  
- **Boundary Conditions**: Zero-boundary conditions within a **bounded spatial domain**  

---

## 🛠 Model Architecture

### **🔹 Neural Network Model (NN)**
- **Hidden Layers**: 2 layers, 64 neurons each
- **Activation**: ReLU
- **Output**: Real & imaginary parts of \( \psi(x,t) \)
- **Optimizer**: Adam (\( lr = 1 \times 10^{-3} \))
- **Loss Function**: Mean Squared Error (MSE)

### **🔹 Physics-Informed Neural Network (PINN)**
- **Same architecture as NN** but with an additional **physics loss** term  
- **Total Loss Function**:
  \[
  \mathcal{L}_{\text{total}} = \mathcal{L}_{\text{data}} + \lambda \mathcal{L}_{\text{physics}}
  \]
  where:
  - \( \mathcal{L}_{\text{data}} \) minimizes the difference between predicted and actual wave functions  
  - \( \mathcal{L}_{\text{physics}} \) enforces the Schrödinger equation constraints  

---

## 🚀 Implementation

### **🔹 Tools & Libraries**
- 🟢 **TensorFlow / PyTorch** - Neural Network Training  
- 📈 **Matplotlib** - Graphing and Visualization  
- 🔢 **NumPy** - Numerical Computations  
- 📚 **Jupyter Notebook** - Code Development  

### **🔹 Workflow**
1️⃣ **Data Preparation**  
   - Normalize spatial and temporal domains  
   - Load wave function dataset  
   - Generate training & test sets  

2️⃣ **Two Training Approaches Tested**  
   - **First Approach (Rejected)**: Trained NN first, then used PINN, but results were unstable  
   - **Second Approach (Final Choice)**: Generated dataset → Trained NN → Trained PINN → Evaluated results  

3️⃣ **Evaluate & Compare**  
   - Loss curves, visualizations, and MSE comparison  

---

## 📈 Results & Approaches

### **🔹 Comparison of Training Approaches**
| Approach  | Description | Performance |
|-----------|------------|-------------|
| **First Approach** | Train NN first, then PINN | High errors, unstable predictions |
| **Second Approach** | Generate dataset → Train NN → Train PINN | Lower MSE, better convergence |

### **🔹 Model Performance**
- **Training Loss**: PINN showed superior convergence  
- **Predicted vs. True Wave Function**: PINN maintained **physical consistency**, unlike NN  

🔍 **MSE Loss Comparison**  
| Model  | MSE Loss |
|--------|---------|
| **NN**  | 0.01026 |
| **PINN** | 0.00984 |

🔍 **Visualizations**
- 📉 Loss Curves Over Training Epochs  
- 🌊 Probability Density Evolution (NN vs. PINN vs. Ground Truth)  

---

## 🔍 Dependencies & Setup
📌 Install required libraries using:  
```bash
pip install numpy matplotlib torch tensorflow
```
📌 Run the Jupyter notebook:
```bash
jupyter notebook
```

---

## 🔬 Future Improvements
✅ **Improve Loss Function**: Fine-tune balance between physics & data loss  
✅ **Expand to Multi-Dimensional Systems**: Solve higher-order PDEs  
✅ **Regularization Techniques**: Prevent overfitting & training instability  

---

## 📝 References
- **Original Research Paper on PINNs**: [Raissi et al., 2019](https://arxiv.org/abs/1711.10561)  
- **Physics-Informed Machine Learning**: [DeepXDE Documentation](https://deepxde.readthedocs.io/en/latest/)  

---

🚀 **Developed by [Your Name]**  
🔗 **GitHub Repository**: [GitHub Link]

