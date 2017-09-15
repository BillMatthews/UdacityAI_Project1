# Artificial Intelligence Nanodegree
## Introductory Project: Diagonal Sudoku Solver

# Question 1 (Naked Twins)
Q: How do we use constraint propagation to solve the naked twins problem?  
A: Within classical sudoku, there is a general constraint that any number (1 to 9) can only appear once in each of the rows, columns and 3x3 boxes within a Sudoku grid. The Naked Twins Strategy is an elimination strategy that is based exploiting this constraint when two boxes that have common peers both have only the same two possible solutions which means that these two solution values must be in these boxes (but we don't know which box has which option) and so these two values can be eliminated from any common peers.

When we eliminate values from the common peers using the Naked Twins strategy we alter the constraints for those affected boxes and in turn this change may propogate to other boxes that are not common peers of the identified twins. While the Naked Twins strategy does not solve either of the twin boxes it can have the effect of reducing the seach space for solutions amonst its peers by removing solution options from those boxes and in turn introduces constraints in other parts of the grid. 

In this implementation we use the Naked Twin strategy on each pass through the grid while attempting to reduce the puzzle.

When thinking about the sequencing of the strategies in the solution, it made sense to use the Naked Twin strategy after the general elimination of solved boxed from their peers but before the Only One strategy. The rationale was the Naked Twin strategy may reduce the available options and so may result in more boxes where the "Only One" strategy would be successful. The latter strategy (Only One) is based on a constraint that works best when we have reduced the grid as far as we can within a given iteration, whereas the former (Naked Twins) is a reduction strategy.

If these strategies were swapped, then it is possible that an additional pass through the grid would be requied to solve some boxes.

# Question 2 (Diagonal Sudoku)
Q: How do we use constraint propagation to solve the diagonal sudoku problem?  
A: Whereas classical Sudoku requires that the numbers 1 to 9 can only apepar once in each  row, column or 3x3 grid can only contain, the Diagonal Sudoku adds to these constraints such that the  numbers 1 to 9 can only appear once on each of the main diagonals (trailing and leading).

If we treat the leading and trailing diagonals as additional unit where the general constraint must be satisfied then the existing strategies being used (Single possibility, Only One and Naked Twins) can be extended to include these additional units.

As each of these strategies alter the values associated with a box, the change is propogated through the box's units (to preserve the general constraint).  

### Install

This project requires **Python 3**.

We recommend students install [Anaconda](https://www.continuum.io/downloads), a pre-packaged Python distribution that contains all of the necessary libraries and software for this project. 
Please try using the environment we provided in the Anaconda lesson of the Nanodegree.

##### Optional: Pygame

Optionally, you can also install pygame if you want to see your visualization. If you've followed our instructions for setting up our conda environment, you should be all set.

If not, please see how to download pygame [here](http://www.pygame.org/download.shtml).

### Code

* `solution.py` - You'll fill this in as part of your solution.
* `solution_test.py` - Do not modify this. You can test your solution by running `python solution_test.py`.
* `PySudoku.py` - Do not modify this. This is code for visualizing your solution.
* `visualize.py` - Do not modify this. This is code for visualizing your solution.

### Visualizing

To visualize your solution, please only assign values to the values_dict using the `assign_value` function provided in solution.py

### Submission
Before submitting your solution to a reviewer, you are required to submit your project to Udacity's Project Assistant, which will provide some initial feedback.  

The setup is simple.  If you have not installed the client tool already, then you may do so with the command `pip install udacity-pa`.  

To submit your code to the project assistant, run `udacity submit` from within the top-level directory of this project.  You will be prompted for a username and password.  If you login using google or facebook, visit [this link](https://project-assistant.udacity.com/auth_tokens/jwt_login) for alternate login instructions.

This process will create a zipfile in your top-level directory named sudoku-<id>.zip.  This is the file that you should submit to the Udacity reviews system.

