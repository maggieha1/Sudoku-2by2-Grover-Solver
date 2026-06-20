# **Grover's Algorithm to Solve Sudoku $2 \times $2**

This repository contains a Jupyter notebook (`.ipynb`) that demonstrates the application of Grover's algorithm to solve a $2 \times 2$ micro-Sudoku puzzle using IBM's Qiskit framework.

## **1. Introduction**

The notebook provides a complete, executable Python code to solve a simplified $2 \times 2$ Sudoku. The problem is set up as follows:

*   Cell A: 1
*   Cell B: 2
*   Cell C: 3
*   Cell D: ? (the unknown target)

Given the Sudoku constraints, Cell D must contain the number 4. The quantum circuit is designed to find this solution, which is encoded as the quantum state $|11\rangle$.

## **2. Grover's Algorithm for Sudoku**

The notebook implements the following steps of Grover's algorithm:

*   **Representing Cell D**: Two qubits are used to represent the possible values for Cell D (00, 01, 10, 11). The target state $|11\rangle$ represents the number 4.

*   **Initialization (Superposition)**: Starting from the resting state $|00\rangle$, Hadamard gates are applied to both qubits to create an equal superposition of all possible states ($|00\rangle, |01\rangle, |10\rangle, |11\rangle$).

*   **Constraint-Checking Oracle**: A Controlled-Z (CZ) gate (`qc.cz(0, 1)`) is applied. This gate selectively flips the phase of the target state $|11\rangle$, effectively 'marking' it as the desired solution. This encodes the Sudoku rule that the solution is 4.

*   **The Diffuser**: This component amplifies the amplitude of the marked state. It consists of a series of Hadamard, Pauli-X, Controlled-Z, Pauli-X, and Hadamard gates that perform an 'inversion about the average' operation, boosting the probability of measuring the correct solution to nearly 100%.

*   **Measurement**: Finally, the qubits are measured. Due to the amplification by the diffuser, the quantum state collapses to the marked state ($|11\rangle$) with high probability, yielding the classical solution for Cell D.

## **3. Execution and Results**

### **Prerequisites**

To run this notebook, you need to install Qiskit and related libraries. You can install them using pip:

```bash
!pip install qiskit
!pip install qiskit-aer
!pip install pylatexenc
!pip install matplotlib
```

### **How to Run**

1.  Open the Jupyter notebook in a compatible environment (e.g., Google Colab, Jupyter Lab).
2.  Run all cells sequentially.

### **Expected Output**

The notebook will simulate the quantum circuit using Qiskit's Aer simulator. The final output will show that the quantum computer collapsed onto the state `'11'` with 100% probability, correctly identifying that Cell D = 4.

```
Sudoku Guess Outcomes (Binary -> Times Measured):
{'11': 1024}

The quantum computer collapsed onto state '11' with 100% probability.
Mapping '11' back to classical data: Cell D = 4
```

### **Circuit Visualization**

The notebook also includes code to visualize the quantum circuit, providing both an ASCII text representation and a graphical Matplotlib rendering of the complete Grover's algorithm implementation.

## **4. Conclusion**

This demonstration highlights the power of quantum algorithms for search problems, even in a small-scale example. By leveraging quantum superposition and interference, Grover's algorithm efficiently finds the unique solution to the $2 \times 2$ micro-Sudoku puzzle.

## **5. References**

*   Czelusta, G., Verma, D. R., & Wanjalkar, G. (2024). Grover's algorithm on two-way quantum computer. arXiv. https://doi.org/10.48550/arxiv.2406.09450.
*   Jones, D., & Varcoe, B. (2022). A Method for Application of a Quantum Search Algorithm to Classical Databases. arXiv. https://doi.org/10.48550/arxiv.2206.03938.
```
