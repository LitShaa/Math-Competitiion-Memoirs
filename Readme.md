# Counterexample Finder for Strongly Expressive Sets

## Purpose

This program systematically searches for **candidate counterexamples** to a conjecture related to *strongly expressive sets* in additive combinatorics. Given a universe `{1, 2, ..., n}` and a subset size `k`, it enumerates all `k`-element subsets and applies a multi-stage heuristic screening algorithm (`isLikelyGood`) to determine whether each subset is "likely good"—i.e., whether it can generate small signed sums (absolute value ≤ 1) through integer linear combinations with coefficients in `{-1, 0, 1}`.

Subsets that **fail all screening stages** are considered *candidate counterexamples* and are saved to an output file for further mathematical analysis.

The algorithm combines four complementary strategies:
1. **Direct verification** via zero-strong expressiveness of a transformed set.
2. **Relaxed verification** after removing critical elements (e.g., the number 1 or adjacent pairs).
3. **Structural reduction** using local difference/sum reconstruction.
4. **Greedy absorption** based on iterative element selection and difference generation.

This tool is designed to handle large values of `n` (e.g., `n ≥ 31`) efficiently by using **streaming enumeration**, which avoids storing all subsets in memory simultaneously.

---

## How to Run

### Prerequisites
- A C++ compiler supporting C++11 or later (e.g., `g++`, `clang++`)
- Standard library support for `<iostream>`, `<vector>`, `<algorithm>`, etc. (included in most modern compilers)

### Compilation
Compile the program using your preferred C++ compiler:

```bash
g++ -O2 -std=c++11 -o counterexample_finder counterexample_finder.cpp