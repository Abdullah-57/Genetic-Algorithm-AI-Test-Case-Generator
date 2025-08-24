# Genetic Algorithm for Automated Test Case Generation

This repository contains the implementation of a Genetic Algorithm (GA) for automated test case generation, developed as part of the **Applied Artificial Intelligence** course (Assignment 2) at FAST – National University of Computer & Emerging Sciences, Islamabad Campus. The GA optimizes test cases for date validation, ensuring coverage of valid, invalid, and boundary cases, and is compared against random testing to evaluate efficiency.

## Project Overview

**Objective**: Implement a Genetic Algorithm to generate optimized test cases for date validation, covering valid dates, invalid dates, and boundary conditions, and compare its performance with random testing.

**Course**: Applied Artificial Intelligence (Spring 2025)  
**Instructor**: Dr. Atif Jilani  
**Submitted by**: Abdullah Daoud (22I-2626)  
**Section**: SE-E  
**Institution**: FAST-NUCES, Islamabad Campus

## Features

### Genetic Algorithm Implementation
- **Chromosome Representation**: Each test case is a chromosome with three genes: 
  - Day: [1, 31] (may exceed for invalid cases)
  - Month: [1, 12] (may exceed for invalid cases)
  - Year: [0, 9999]
- **Fitness Function**: Categorizes test cases into:
  - **Valid Cases**: Leap years (e.g., 29/02/2024), 30-day months (e.g., 30/04/2024), 31-day months (e.g., 31/07/2024)
  - **Invalid Cases**: Day > 31 (e.g., 32/01/2024), Month > 12 (e.g., 10/13/2024), Non-leap February 29 (e.g., 29/02/2023)
  - **Boundary Cases**: Min/Max year (e.g., 01/01/0000, 31/12/9999), Day/Month transitions (e.g., 31/12/2024 → 01/01/2025)
  - Rewards diversity to maximize coverage across categories.
- **Mutation**: Applied with 15% probability to introduce diversity:
  - Day: ±3
  - Month: ±1
  - Year: ±100

### Parameter Tuning
- **Mutation Rate**: 15% chosen for optimal balance between diversity and convergence.
- **Population Size**: 100 individuals.
- **Generations**: 100 or until 95% coverage is achieved.
- **Impact Analysis**:
  - Higher mutation rates increase diversity but may delay convergence.
  - Lower rates speed up convergence but miss edge cases.

### Coverage Results
- **Test Cases Generated**:
  - Valid: 10
  - Invalid: 10
  - Boundary: 5
- **Coverage**: GA achieves higher coverage (~95%) compared to random testing, especially for edge cases.

### GA vs. Random Testing
- **GA Advantages**:
  - Consistently finds edge cases (e.g., leap years, invalid dates).
  - Converges to high coverage in ~30 generations.
- **Random Testing**:
  - Struggles with rare cases.
  - Generates redundant data, leading to inconsistent coverage.

## Project Structure
```plaintext
.
├── src/                    # Source code for GA implementation
│   ├── ga.js              # Genetic Algorithm logic
│   ├── fitness.js         # Fitness function for test case evaluation
│   ├── mutation.js        # Mutation logic for chromosome variation
│   └── utils.js           # Utility functions for date validation
├── data/                   # Test case outputs and coverage data
├── visualizations/         # Coverage graphs and analysis
├── README.md              # Project documentation
└── package.json           # Project dependencies and scripts
```

## Installation

### Prerequisites
- **Node.js**: v16.x or later
- **MongoDB**: Optional, for storing test case results (if implemented)
- **Dependencies**: Install via npm (listed in `package.json`)

### Setup
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/username/ga-test-case-generation.git
   cd ga-test-case-generation
   ```

2. **Install Dependencies**:
   ```bash
   npm install
   ```

3. **Run the Genetic Algorithm**:
   ```bash
   node src/ga.js
   ```

## Usage
- **Run the GA**: Execute `node src/ga.js` to generate test cases and evaluate coverage.
- **View Results**: Check the `data/` directory for generated test cases (valid, invalid, boundary).
- **Analyze Coverage**: Refer to `visualizations/` for graphs showing coverage improvement over generations.
- **Compare with Random Testing**: Modify `src/ga.js` to toggle between GA and random testing modes for comparison.

## Key Findings
- **GA Performance**: Outperforms random testing by efficiently covering edge cases and achieving ~95% coverage in fewer generations.
- **Fitness Function**: Successfully ensures diversity in test cases, enhancing fault detection.
- **Local Search**: Refines test cases for optimal coverage.

## Contributing
Contributions to enhance the GA or add new features are welcome:
1. Fork the repository.
2. Create a feature branch (`git checkout -b feature-branch`).
3. Commit changes (`git commit -m "Add feature"`).
4. Push to the branch (`git push origin feature-branch`).
5. Open a pull request.

## License
MIT License - see `LICENSE` for details.

## Contact
- **Author**: Abdullah Daoud (22I-2626)
- **Instructor**: Dr. Atif Jilani
- **Institution**: FAST-NUCES, Islamabad Campus