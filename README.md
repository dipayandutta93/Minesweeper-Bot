# Minesweeper-Bot
Designed a minesweeper bot that makes moves based on solving a constraint satisfaction problem for a given board state.

We represented the board in the form of a matrix, where cells with mine is given a value 1 and non-mine cells are assigned 0.

We represent each constraint with the following data structure
    
    Constraint{
    List variables;
    Int value;
    }

We represent the knowledge in the following forms:
* Safe cells list
* Mine cells list
* Probability matrix --- (this matrix is solely sufficient to store the knowledge form but safe cells list and Mine cells list increase the speed of our algorithm)
* List of constraints.

Our program checks the safe cells list, if it is not empty, then those cells are explored next. We infer safe cells by using the knowledge accumulated. If there are no elements in safe cell list, then our program chooses a cell which has minimum probability to be mine (first we consider the cells which are already in the constraints). If there is a tie between cells we choose the cell that is more connected to the knowledge base (most constrained cell).As we don’t have much knowledge about the board, we need to make a move within theknown region unless all the known region is filled with mines. However, a complete random move might not be logical. Hence, our program makes sure that the next move it makes is an optimal one by choosing the cell with minimum probability in the known region.

Space complexity : O(n^2)

Time complexity : O(n^3)
