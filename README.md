# ChessBot
A chess game with an AI bot which can play as the opponent.

## Installation
In order to run the game, you need have `python 3` installed, along with `pygame` and `cppyy` modules
Python 3 can be downloaded and installed from the official python website. Pygame and cppyy can be installed using the `pip` command. 
The links to documentation for installation of above requirements are provided below:

[Python](https://wiki.python.org/moin/BeginnersGuide)

[Pygame](https://www.pygame.org/wiki/GettingStarted)

[Cppyy](https://cppyy.readthedocs.io/en/latest/installation.html)

If you are running the game on windows, you will also need Microsoft Visual Studio Build Tools. You can find it on the [Microsoft Visual Studio website](https://visualstudio.microsoft.com/downloads/) by opening the drop down menu labelled ***Tools for Visual Studio 2022***

## Running the game
Open the file labelled `ChessUI.py` in any IDE which supports Python3 and press _run_. If you only have the Python interpreter installed, you can simply double-click the file to run it. 
**Note:** Python interpreter needs to be restarted after quitting the game each time, else the game will not load and will show errors.<br>
## Working

The algorithm used in the bot is a **Minimax algorithm** with **Alpha-Beta Pruning**.<br>
Minimax algorithm involves using **Depth First Search** upto a certain depth and calculating the advantage for BLACK or WHITE at the position based on certain heuristic values.<br>
<br>
![plot](Assets/minimax.png)
<br>
<br>
In this graph, the values at the leaf nodes is calculated using certain heuristic functions.
These functions are prepared by consultation from **experts** in the field i.e. Strong chess players.
<br>
For example, a piece such as a kinght is good in the middle of the board, so a heuristic function will prefer a knight to be in the middle of the board rather than at the edges.
<br>
<br>
Finally these values are passed upwards in an **alternating minimum-maximum** fashion.
<br>
As we can see the node at depth 3 are maximizers so we select the move has the maximum value from the nodes below it.
<br>
<br>
![plot](Assets/minimax1.png)
<br>
<br>
For example at the node D, we select the value at I which is 4 since that is the maximum value at the nodes below it.
<br>
Similarly at depth 2 we select the the move that has the maximum value below it. 
<br>
<br>
![plot](Assets/minimax1.png)
<br>
<br>
At node B, we select the value at node D which is 4 as that is the minimum value below it.
<br>
Along with this we have used **Zobrist Hashing** to reduce the number of computations we need to do for calculating the value of a position.
<br>
In this method we generate unique random numbers for a certain position and store that value in a hash table along with the evaluation of that position.
For this application, we have used a 32-bit hash table with 64 bit zobrist key. To deal with collisions we have implemented separate chaining and stored the evaluations one after another.
<br>
<br>
![plot](Assets/Zobrist.png)
