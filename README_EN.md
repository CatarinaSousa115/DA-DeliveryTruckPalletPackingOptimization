# Delivery Truck Pallet Packing Optimization

[Versão Portuguesa](README.md)

> A C++ tool that optimizes pallet loading for a delivery truck, a real-world variation of the 0/1 Knapsack Problem.

## Authors

| Nome                           | E-Mail            |
| ------------------------------ | ----------------- |
| Ana Catarina Monteiro de Sousa | up202306419@up.pt |

## Academic Context

- **Course:** Design of Algorithms (L.EIC016)
- **Institution:** FEUP — Faculty of Engineering of the University of Porto
- **Year/Semester:** 2024/2025 — 2nd semester
- **Final Grade:** 18.5/20

## Description

The goal is to solve the **Delivery Truck Pallet Packing Optimization Problem**, a real-world variation of the **0/1 Knapsack Problem**. The objective is to maximize the total profit of pallets loaded into a delivery truck without exceeding its maximum weight capacity.

### Implemented Algorithms

The tool provides four different algorithmic approaches to solve the problem:

1. **Brute-Force (Exhaustive Search)**
   - Explores all possible subsets of pallets to find the absolute optimal solution.
   - **Time Complexity:** O(2ⁿ), where n is the number of pallets.
   - **Space Complexity:** O(n) (recursion depth).

2. **Dynamic Programming**
   - Uses a 2D table to store the maximum profit for subproblems.
   - **Tie-breaking rules:** if two combinations have the same profit, it prefers the one with fewer pallets; if they still tie, it prefers the one with the smallest sum of original indices.
   - **Time Complexity:** O(n · W), where W is the truck's capacity.
   - **Space Complexity:** O(n · W) for the DP table.

3. **Greedy Algorithm**
   - An approximation algorithm that selects pallets based on their **profit-to-weight ratio**.
   - **Time Complexity:** O(n log n) due to sorting.
   - **Space Complexity:** O(n).

4. **Hybrid Algorithm**
   - Combines the Greedy approach and Dynamic Programming.
   - It first computes a baseline using the Greedy heuristic and then performs DP to find the optimal solution, allowing for performance comparisons.

## Technologies Used

- C++ (C++14)
- CMake (≥ 3.29)
- Doxygen (documentation)
- CSV files for input/output

## Project Structure

```text
.
├── code/                       # Source code files
│   ├── algorithms/             # Implementation of optimization algorithms
│   ├── input_output/           # CSV reading and result printing utilities
│   ├── menu/                   # CLI menu implementation
│   ├── structs/                # Data structures (pallet, truck)
│   ├── functions.h             # Main header with function prototypes
│   └── main.cpp                # Program entry point
├── datasets/                   # CSV input files (Truck capacity and Pallet data)
├── documentation/              # Doxygen generated documentation (HTML/LaTeX)
├── Project_2_Description.pdf   # Official project requirements
├── presentation.pdf            # Project presentation and results demo
├── CMakeLists.txt              # Build configuration
└── Doxyfile                    # Doxygen configuration file
```

## Requirements

- **CMake** (version 3.29 or higher)
- **C++ Compiler** (supporting C++14)

## How to Build / Run

### Compilation

To compile the project, run the following commands in the root directory:

```bash
mkdir build
cd build
cmake ..
make
```

### Execution

After compilation, run the executable:

```bash
./DA_project2
```

## Usage

The application features a command-line interface:

1. **Select Dataset:** Enter the number of the dataset you wish to test (e.g., `1` for `datasets/Pallets_01.csv`).
2. **Choose Algorithm:** Select one of the four available algorithms to process the data.
3. **View Results:** The program will output the maximum profit, the number of pallets selected, execution time, and details for each selected pallet.

### Datasets

The input data is provided in two CSV files per dataset:

- `TruckAndPallets_<X>.csv`: Contains the `Capacity` and total number of `Pallets`.
- `Pallets_<X>.csv`: Contains the `Pallet` ID, `Weight`, and `Profit` for each item.

## Additional Notes

The code is fully documented using **Doxygen**. You can find the generated documentation in the `documentation/html/` folder. To view it, open `documentation/html/index.html` in your web browser.
