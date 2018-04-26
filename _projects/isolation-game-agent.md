---
title: A game agent for Isolation Game
layout: project_page
description: In this project, we develop an adversarial search agent to play the game "Isolation".  Isolation is a deterministic, two-player game of perfect information in which the players alternate turns moving a single piece from one cell to another on a board.  Whenever either player occupies a cell, that cell becomes blocked for the remainder of the game.  The first player with no remaining legal moves loses, and the opponent is declared the winner.
project-link: https://github.com/nvmoyar/aind1-isolation-game
project-image: game-agent-isolation_screenshot.png
project-category: AI-Algorithms
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

