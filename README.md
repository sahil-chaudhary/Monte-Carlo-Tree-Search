## Contributors
1. Sahil Chaudhary

## Abstract
Monte Carlo Tree Search(MCTS) is a general approach to solving sequential decision making problems under uncertainty using stochastic(Monte Carlo) simulation. MCTS is famous for its role in Google DeepMind's Alphazero, the successor to AlphaGo.
Starting from scratch without using any domain-specific knowledge, AlphaZero was able to defeat not only its Predecssors in Go but also the best AI computer programs in chess, using 24 hours of training based on MCTS and reinforcement learning. 

MCTS is a widely used approach in solving sequential decision making problems and has recieved quite a bit attention in fields like Reinforcement Learning, AI and ML. 

## Projects 
This repo conists the projects which widely uses the idea of MCTS to solve a specific problem. This README file would give you a generic overview towards Monte Carlo Tree Search algorithm and I have tried to organize my file as systematic as possible. You can visit each of the folders and you will find a readme for the same project so that you would find it easier to understand the project.
Projects, which I have personally tried and documented are listed below:
1. Improving LLMs Reasoning abilities using Monte Carlo Tree Self-refine
2. AlphaGo

## Introduction

The algorithm deals sequential decision making under uncertainity, which can be modeled using Markov decision process. In this setting, the objective is to maximize an expected reward or minimize the error function over a finite time, given the starting state.

In a game setting like chess, tic tac toe or go, a simple version would be to maximize the probability of computer winning from the beginning of the game. Ideally, an optimal strategy should take care of every possiblity but for the games which were suggested earlier, you can think the decision tree would grow exponentially.

Thus, the idea is to try to perform an intelligent and calculated search using randomization and game simulation. Algorithms like alpha-beta favors more exploitation which misses the maximum possible reward, which is something we want to avoid. MCTS is a very clever algorithm which favors not only exploitation of the states but also lets the computer explore.  

## Principle of Operation:

The focus of MCTS is on the analysis of the most promising moves, expanding the search tree based on random sampling of the search space. 
MCTS consists of four main "operators" :
1. Selection :
    Selection correpondes to choosing a move at a node or an action in a decision tree, and the choice is based on the upper confidence bound for each possible move or action, which is a function of the current estimated value.

    Start from root R and select successive child nodes untill a leaf node L is reached. The root is the current game state and a leaf is any node that has a potential child from which no simulation has yet been started. The selection below says more about a way of biasing choice of child nodes that lets the game tree expand towards the most promising moves, which is the essence of Monte Carlo Tree search.

2. Expansion: 
    Expansion corresponds to an outcome node in a decision tree, which is an opponent's move in a game and it is modeled by a probability distribution that is a function of the state reached after the chosen move or action.

    Unless L ends the game decisively for either player, create one child nodes and choose node C from one of them. Child nodes are any valid moves from teh game position defined by L.

3. Simulation:
    Simulation corresponds to returning the estimated value at a given node, which could correspond to the actual end of the horizon or game, or simply to a point where the current estimation may be considered sufficiently accurate so as not to requre further simulation.

    Complete one random playout from node C. This step is sometimes also called playout or rollout. A playout may be as simple as choosing uniform random moves until the game is decided.

4. Backdrop
    Backdrop corresponds to the backwards dyanmic programming algorithm employed in decision trees and MDPS.

    Basically, use the result of the playout to update information in the nodes on the path from C to R.

## Exploration and Exploitation:

The main difficult in selecting child nodes is maintaining some balance between the exploitation and exploration. Formula associated with balancing the tradeoffs between exploration and exploitation is 
```math
\begin{align}
    UCB&=E[win|i]+c\sqrt{2\frac{ln(N_i)}{n_i}}\\
    &=\frac{w_i}{n_i}+c\sqrt{2\frac{ln(N_i)}{n_i}}
\end{align}
```
where,
$w_i$ is the number of wins for the node cosidered after the $i^{th}$ move,

$n_i$ is the number of simulations for the node considered after the $i^{th}$ move,

$N_i$ is the total number of simulations after the $i^{th}$ move run by the parent node of the one considered,

$c$ is the exploration parameter.

The term $E[win|i]$ corresponds to exploitation and $c\sqrt{2\frac{ln(N_i)}{n_i}}$ corresponds to exploration.

At selection, the child is selected which has maximum UCB value.

At beginning when no node is explored, it makes a random selection because there is no data available to make a more educated selection. Other operators are supposed to be used in the same manner.

## Experiments: 
To examine its performance, we experimented with tic-tac-toe of various dimensions by competing MCTS against alpha beta pruning method and minmax method.


## Conclusions: 
MCTS has its own advantages and disadvantages but one could not avoid its significance in various streams. In cases like game simulation, robotics, text generation, Monte carlo tree search has shown very promising results. To understand its signifiance at a deeper level and find its application in other fields, I have try to do experiments around this algorithm. You could visit other projects inside this repo and understands its significance in each projects.

## Papers followed:
1. https://arxiv.org/pdf/2004.11410
2. https://arxiv.org/pdf/1712.01815
3. https://arxiv.org/pdf/2103.04931
4. https://sites.ualberta.ca/~szepesva/papers/CACM-MCTS.pdf

## Blogs and other Resources:
1. https://cs.brown.edu/people/gdk/pubs/analysis_mcts.pdf
2. https://papers.nips.cc/paper/2021/file/9b0ead00a217ea2c12e06a72eec4923f-Paper.pdf
3. https://en.wikipedia.org/wiki/Monte_Carlo_tree_search
4. https://builtin.com/machine-learning/monte-carlo-tree-search
5. https://towardsdatascience.com/monte-carlo-tree-search-an-introduction-503d8c04e168
6. https://medium.com/@_michelangelo_/monte-carlo-tree-search-mcts-algorithm-for-dummies-74b2bae53bfa

## Papers with Code:
1. https://paperswithcode.com/method/monte-carlo-tree-search
