Sudoku Solver(Using Depth First Search(backtracking) on a Constraint Satisfaction Problem)
_________________________________________________________________________________________

Sudoku as a Constraint Satisfaction Problem.
------------------------------------------
Sudoku can be seen as a Constraint Satisfaction Problem (CSP) when identifying the components of the problem.
The following are the problem's components:
Variable - empty boxes
Domain - numbers 1 to 9
Constraints - Each row, column and square (9 spaces each) needs to be filled out with the numbers 1-9, without repeating any numbers within the row, column or square.



Search, backtracking and choosing variable.
------------------------------------------
Depth First Search was used instead of Breadth First Search as it was much faster at solving sudokus.
Backtracking was used as it was faster and more memory efficient than doing DFS without backtracking.
When selecting variables/empty boxes a heuristic called Minimum Remaining Value was applied that takes the variable with the least amount of possibilities.
Minimum Remaining Value allows for less branching by taking the variable with least amount of possibilities.

Search algorithm: At the start the sudoku board is filtered using the strategies, 
it takes the minimum remaining value variable and sets up a new board with a value in place which is then checked whether it is a valid board. 
If the new board is valid it continues to recurse/search down.If the board is not valid it will try a new value through backtracking. 
If a board is found to be complete it will be returned and recursed upwards. 
If all the values have been tried but no complete answer backtracking will stop and None will be returned which means the sudoku is not solvable.



Constraint propagation and pruning.
-----------------------------------------
I decided to implement constraint propagation to solve the constraint satisfaction problem.
The implementation was able to reduce solve times significantly by reducing possible values after setting a value.
The strategies used in this implementation for constraints and pruning are:
1)Elimination - Checking set values of sudoku in each row, column or square to reduce possibilities in variables not yet filled.
2)Only choice - Checking only the unfilled variables that are within the same row, column or square of each other to identify if there is a value that can only be in one specific position. 
(https://www.sudokudragon.com/guideonlychoice.htm)
3)Naked twins - When two unfilled variables with length 2 and have the same possibilities, within the same row, column or square of each other, appear, remove the same possibilities from the other unfilled variables respective to the row, column or square.
(https://www.sudokudragon.com/guidenakedtwins.htm)

Filter algorithm: First does elimination, then only choice and into naked twins.
Total time taken on average for completion of all hard sudoku test with implementation of the strategies :
With only elimination : 20.51 seconds
With elimination, only choice and Naked Twins :1.3 seconds

It can be observed that there is a 1577.69% faster in time taken which shows the effectiveness of these strategies.
The PC that was used for this test had the specifications:
OS: Windows 10 x64
CPU: AMD Ryzen 5 3600XT 6-Core Processor 3.80Ghz
RAM: 16GB of 3200Mhz
Storage: 1TB SSD Kingston SA2000M81000G



Future of work.
-------------------------------------------
Would like to try different data structures instead of a 3D list to compare efficiency.
Exploring more about local consistencies and how it can reduce the search space.
Implementing more ways to improve backtracking.
Observe how effective it is implementing more solving strategies.
Observe how ordering of solving strategies effect the speed to solve sudokus.

