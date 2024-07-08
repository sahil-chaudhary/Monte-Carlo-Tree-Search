## Monte Carlo Tree Search for LLMs

## Credits and Copyrights
The work is inspired from the work done by Di Zhang et. al in https://github.com/trotsky1997/MathBlackBox . The repo had python files which demostrated their work. The programs were not well managed and results were hardly reproducible for us(we suffered from multi processing issues because of poor threading and device compatiblity). Fortunately, @puffy310 was working on conversion of this repo into a single jupyter notebook to make sense of the paper. Although, the jupyter notebook was also flawed and had some issues which we corrected in this repo and tried to put instructions and comments so that people can reproduce the results in the paper and make commercial use of it by creating a pipeline in their AI systems.

The work has been done under the instruction of Nehal Gajraj(https://github.com/nehalgajraj), RedTree. For any code usage other than which was already used in the original code, please contact him.

The work is still in progress and we would share our results soon.

Contributors:
1. Sahil Chaudhary
2. Balaji R (https://github.com/blackscreen-whitetext)

## Abstract
https://arxiv.org/abs/2406.07394 introduces the idea of Monte Carlo self-Refine algorithm. The idea is pretty simple, integrate the Monte Carlo Tree Search and Self Refine to Large Language MOdels. The main motivation for the writers are to enhance the performance in complex mathematical reasoning tasks.

The algorithm constructs a Monte Carlo search TRee through iterative process of selection, self-refine, self-evaluation and backpropagation utilizing an improved upper confidence bound(UCB).

## Modifications
The modification done in the paper in comprasion to original monte carlo tree search involves modification of UCB and addition of self-refine to generate responses.
Nodes on, this tree represent different versions of answers to same question while edges denote the attempt at improvement(While improvemnent is a over statement but self refining happens to work if context length is maintained). The algorithm's operations flow inspires or copies the MCTS algorithm general pattern.
One has to note self-ecaluation is driven by model's self reward capability.

### Notations used
```P```: The problem instance being addressed

```A```: The set of nodes, each representing potential anwer to P

```M```: The set of actions available at each node representing the possible self refine modifications to an answer

```R```: A function that samples self rewards for nodes based on the quality and effectiveness of the modifications

```R_a```: A set that stores all self-rewards sampling results of node a with self-rewards function R

```T```: A function determining the termination of the search process based on the criteria specified


Functions:
Q(a): A value function estimating the worth of an answer node a(using self-reward model)

U(a): The upper confidence bound for the Q value of node a to balance between exploitation and exploration

N(a): The total number of visits to node a, used to calculate its UCB value and asses exploration and exploitation.


## Papers to follow
1. https://arxiv.org/pdf/2303.17651(self refine)
2. https://arxiv.org/abs/2406.07394(MCTS-r)
