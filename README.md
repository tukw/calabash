# Calabash Brothers

<img src="img/calabash.jpg" width=300>

There are N calabash brothers numbered with 1, 2, ..., N. Each of them has a skill, which they may choose to use or not. So each of them has two states: positive if he uses the skill and negative if not. For example, if K uses his skill, his state is +K, otherwise -K. When the N brothers come together, they can create a new calabash brother, called Diamond brother, numbered with 0. Diamond is a fusion of N brothers and he is incredibly powerful, though he has no skill and only one state 0. Your work is to determine the states of N brothers. Once N states decided, the brothers including Diamond form various tree structures and Diamond is always the root. So they are connected by hidden directed edges, which has different weights. The edge weights depend on the two associated brothers and their states. Whenever they form a new tree, the power of Diamond has an addition, which is the product of edge weights in the tree. The total power of Diamond is the summation of all the additions of all the different trees. We wonder how to choose the states of N brothers such that the total power of Diamond is as large as possible.

## Input

The first line is an integer N. In the following 4N<sup>2</sup>-2N lines, each line has 3 numbers U, V, W, which means the weight of the edge from U to V is W.

## Output

The output has only one line, which contains N integers of the states of our choices, separated by a space.

## Sample

The sample with the following input has 2 calabash brothers and a Diamond. There are 4 possible choices: -1, -2; -1, +2; +1, -2; +1, +2. The corresponding total powers are as follows.

| Choices |            All Trees             |            Total Power             |
| :-----: | :------------------------------: | :--------------------------------: |
| -1, -2  | <img src="img/00.png" width=300> | 0.1x0.1 + 0.3x0.3 + 0.1x0.3 = 0.13 |
| -1, +2  | <img src="img/01.png" width=300> | 0.1x0.3 + 0.4x0.2 + 0.1x0.4 = 0.15 |
| +1, -2  | <img src="img/10.png" width=300> | 0.2x0.4 + 0.3x0.1 + 0.2x0.3 = 0.17 |
| +1, +2  | <img src="img/11.png" width=300> | 0.2x0.2 + 0.4x0.4 + 0.2x0.4 = 0.28 |

When we choose +1, +2, we get the maximum total power 0.28. So we should output +1 +2.

### Sample Input

```
2
-1 -2 0.1
-1 +2 0.3
+1 -2 0.4
+1 +2 0.2
-2 -1 0.3
-2 +1 0.1
+2 -1 0.2
+2 +1 0.4
0 -1 0.1
0 +1 0.2
0 -2 0.3
0 +2 0.4
```

### Sample Output

```
+1 +2
```

## Getting Started



The starter code [calabash.py](calabash.py) contains a simple solution implemented with Python 2.7 and NumPy, which can be easily installed with [Anaconda](https://www.anaconda.com/download/). After Anaconda installed, we can run `python calabash.py` and paste the sample input into the terminal, then we will get the sample output +1 +2.

## Evaluation

Your score of the project positively correlates with the total power of your output. We will give 10 inputs to you to test your solution. For each input, you should write your output to the file under folder [output](output) with the same name as the input. You will get a rank ratio R for each input, and your project score for this input is -2log(R). For example, R = 0.11, which means you are the top 11% among all students in our class, and you will get score -2log(0.11) = 4.415. Your final project score is the summation of all scores of 10 inputs.

### Submitting

Your solutions should be submitted to [Gradebot](https://gradebot.org/). See [Gradebot User's Manual](http://gradebot.org/gradebot/static/user.html) for help.

**IMPORTANT**

- When you submit solutions, you should also submit all the source code you write, otherwise, you will be treated as cheating.
- It's your responsibility to reproduce your results with your submitted source code. Any irreproducible result will be treated as cheating.

## Hints

After the states determined, all the chosen states and Diamond form a graph, and the total power can be found in O(N<sup>3</sup>) time by [matrix-tree theorem](http://people.reed.edu/~davidp/412/handouts/matrix-tree.pdf), which has been implemented in [calabash.py](calabash.py).

The tractable exact solver may not exist. We can employ various approximation methods. The following are some ideas.

### Randomized Algorithms

Randomly generate some choices and find the maximum total power of them. This method has been implemented in [calabash.py](calabash.py).

### Greedy Algorithms

Similar to [Prim's algorithm](https://en.wikipedia.org/wiki/Prim's_algorithm), start from 0 and greedily choose the maximum available edges.

### Local Search

Randomly initialize a choice, and then repeatedly try to change some states in the choice to make the total power larger.

### Dynamic Programming

Choose a tree structure of brothers first, and then find the best states in the tree using dynamic programming.
