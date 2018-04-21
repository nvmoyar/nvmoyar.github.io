---
title: A game agent for Isolation Game
layout: project_page
description: In this project, we develop an adversarial search agent to play the game "Isolation".  Isolation is a deterministic, two-player game of perfect information in which the players alternate turns moving a single piece from one cell to another on a board.  Whenever either player occupies a cell, that cell becomes blocked for the remainder of the game.  The first player with no remaining legal moves loses, and the opponent is declared the winner.
project-link: https://github.com/nvmoyar/aind-isolation-game
project-image: game-agent-isolation_screenshot.png
project-category: AI Algorithms
project-tags: 
 Constraint-Satisfaction
 Search
 Heuristics
---

In this project, we develop an adversarial search agent to play the game "Isolation".  Isolation is a deterministic, two-player game of perfect information in which the players alternate turns moving a single piece from one cell to another on a board.  Whenever either player occupies a cell, that cell becomes blocked for the remainder of the game.  The first player with no remaining legal moves loses, and the opponent is declared the winner.  These rules are implemented in the `isolation.Board` class provided in the repository. 

This project uses a version of Isolation where each agent is restricted to L-shaped movements (like a knight in chess) on a rectangular grid (like a chess or checkerboard).  The agents can move to an open cell on the board that is 2-rows and 1-column or 2-columns and 1-row away from their current position on the board. Movements are blocked at the edges of the board (the board does not wrap around), however, the player can "jump" blocked or occupied spaces (just like a knight in chess).

Additionally, agents will have a fixed time limit each turn to search for the best move and respond.  If the time limit expires during a player's turn, that player forfeits the match, and the opponent wins.

#### Approach to find a good heuristics for this problem

For this heuristics evaluation three different options have been chosen following two different approaches:

* Custom: based on Manhattan distance between agent and opponent, this function leverages the number of legal moves for the agent when the moves are far from the opponent.

* Custom_2: based on the suggestions made from Thad on the lectures, this function is just a simple modification applying an arbitrary coefficient to the opponent’s movement to make the chase more ‘aggressive’ by the agent. Due to the simple nature of this functions, it was worth to give a try.

* Custom_3: based on Manhattan distance between agent and opponent, the distance value is used as a bonus to reduce the opponent’s moves (as Custom_2) but penalizing more the opponent’s moves when the agent plays long distances from the opponent. The inverse of the function has been used instead, without any significant results.

Based on improved_score() and center_score(), other modifications have been tried without significant success:

* Arbitrary pair/odd penalizing
* Change strategy depending on the remaining % blank_spaces/occupancy

#### Measurement of performance

Since most packages like logging, PDB or profile are not allowed, the performance measurement has been carried out by Terminal1.
The number of matches played: 30 in two rounds.

> python -m cProfile -s cumulative tournament.py

#### Observations

Some important observations have been noted as a result of running several times the tournament file. One important factor that has been noted as an important key to improving the performance of the agent, is how the best_move variable is initialized in get_move() functions and minimax() and alphabet() within their respective classes. Different ways to init have been used, please read the [heuristics analysis for further details](https://github.com/nvmoyar/aind1-isolation-game/blob/master/heuristic_analysis.pdf)

Easily the winning percentages, in general, may increase in 5-8% when best_move is initialized to a fixed position rather than random or not valid, there is an excellent discussion on Udacity’s AIND-Term1 that can be found on the [report](https://github.com/nvmoyar/aind1-isolation-game/blob/master/heuristic_analysis.pdf). 

Another important factor noted as important is working with heuristic functions as simple as possible. Including loops increase significantly the amount of time for the evaluation and thus, the strategy may experience variations if the function is more lightweight, thus these evaluations based on % blank spaces or pairs/odd, have been removed. In the next figure shows an example of the functions tested and finally discarded as the winning rates were below 60%.

#### Conclusions

Several tests have been run out, and an extremely high variability over the winning rates have been observed, so it is not worth getting into fine analytics. However in a rough way, we can say that the performance of the custom functions is good enough for all 3 and the winning rates are over the 60%, and the performance versus the Improved function is better as data are fairly consistent. In the same way, the rates are much better for the Minimax agent rather than the AlphaBetaPlayer using iterative deepening alpha-beta search with heuristics (see the figure below).
Due to this variability is really difficult to draw a conclusion and pick one over the rest. However, based on the winning rates and the % time CPU spent, AB_Custom_2 and AB_Custom_3, seem to be the better choices, as the winning rates are high and the cost in time is lower compared to AB_Improved or AB_Custom. 