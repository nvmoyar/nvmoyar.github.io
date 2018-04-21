---
title: Sudoku
layout: project_page
description: In this project, we write code to implement two extensions of our Sudoku solver. The first one will be to implement the technique called "naked twins". The second one will be to modify our existing code to solve a diagonal sudoku. The goals are to implement the naked twins function and write an AI agent that will solve the Diagonal Sudoku game and experience constraint propagation in both implementations. Some additional features have been added in this implementation. Although that was not requested for this project, some suggestions were made by the Udacity reviewer and they have been added as improvements. 
project-link: https://github.com/nvmoyar/sudoku
project-image: sudoku_screenshot.gif
project-category: AI Algorithms
project-tags:
 Constraint-Satisfaction
 Search
---

In this project, we write code to implement two extensions of our Sudoku solver. The first one will be to implement the technique called "naked twins". The second one will be to modify our existing code to solve a diagonal sudoku. The goals are to implement the naked twins function and write an AI agent that will solve the Diagonal Sudoku game and experience constraint propagation in both implementations. 

Some additional features have been added in this implementation. Although that was not requested for this project, some suggestions were made by the Udacity reviewer and they have been added as improvements: 

* Added quick testers [Effective assertions](https://wiki.python.org/moin/UsingAssertionsEffectively)
* Added logging calls [Basic logging tutorial](https://docs.python.org/3/howto/logging.html)
* Modularize the code. The original naked_twins() function was written in a single function, and after the review has been split in find_twins() and eliminate_twins()
* Implement hidden_twins() as a new solver strategy 
    * [Reference1](https://www.sudokuoftheday.com/techniques/hidden-pairs-triples/)
    * [Reference2](http://www.sudokudragon.com/tutorialhiddentwins.htm)