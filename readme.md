# Sudoku Solver

Sudoku as a Constraint Satisfaction Problem
------------------------------------------

Sudoku can be represented as a Constraint Satisfaction Problem (CSP) when breaking down its components:

- **Variable:** Empty boxes on the Sudoku grid.
- **Domain:** Numbers 1 to 9.
- **Constraints:** Each row, column, and 3x3 square must be filled with unique numbers 1-9.

Search, Backtracking, and Variable Selection
--------------------------------------------

Depth First Search (DFS) was chosen over Breadth First Search (BFS) for its efficiency in solving Sudokus.
Backtracking was employed as it proved faster and more memory-efficient than DFS without backtracking.
Variable selection followed the Minimum Remaining Value (MRV) heuristic, selecting the variable with the fewest possibilities. This strategy reduces branching.

Search Algorithm:
1. The Sudoku board is filtered using predefined strategies.
2. The MRV variable is chosen and a new board with a value is created.
3. The validity of the new board is checked.
4. If valid, continue recursion/search. If not, backtrack and try a new value.
5. If a complete board is found, it's returned and recursion moves upwards.
6. If all values have been tried, backtracking stops, and `None` is returned, indicating an unsolvable Sudoku.

Constraint Propagation and Pruning
----------------------------------

Constraint propagation was implemented to address the CSP.
Implemented strategies for constraints and pruning:
1. **Elimination:** Utilizing set values to eliminate possibilities in unfilled variables in rows, columns, or squares.
2. **Only Choice:** Identifying values unique to a specific position within the same row, column, or square of unfilled variables.
   ([Source](https://www.sudokudragon.com/guideonlychoice.htm))
3. **Naked Twins:** Removing possibilities from other variables in the same row, column, or square when two unfilled variables with the same possibilities (length 2) appear.
   ([Source](https://www.sudokudragon.com/guidenakedtwins.htm))

Filter Algorithm: Sequence of Elimination, Only Choice, and Naked Twins.

Performance Metrics
-------------------

Average completion time for all hard Sudoku tests using different strategies:
- **Only Elimination:** 20.51 seconds
- **Elimination, Only Choice, and Naked Twins:** 1.3 seconds

The remarkable 1577.69% time reduction demonstrates the effectiveness of these strategies.

Test Environment:
- OS: Windows 10 x64
- CPU: AMD Ryzen 5 3600XT 6-Core Processor 3.80GHz
- RAM: 16GB of 3200MHz
- Storage: 1TB SSD Kingston SA2000M81000G

Future Work
-----------

The project's future directions include:

- Exploring alternative data structures instead of a 3D list to assess efficiency gains.
- Further research into local consistencies to potentially reduce search space.
- Implementation of additional techniques to enhance backtracking.
- Investigation of the impact of different solving strategy orders on Sudoku-solving speed.

Feel free to contribute and explore new avenues for improving Sudoku-solving efficiency!

**Disclaimer:** This project is designed for educational and illustrative purposes.
