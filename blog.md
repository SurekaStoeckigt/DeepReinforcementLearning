# Introduction

https://medium.com/applied-data-science/how-to-build-your-own-alphazero-ai-using-python-and-keras-7f664945c188

In March 2016, Deepmind's AlphaGo (algorithm) beat 18 times world champion Go Player, Go player Lee Sedol 4–1, in a remarkable series watched by over 200 million people. For those of you who have absolutely no idea what I am talking about - a machine had a super-human strategy for playing a game of Go, using an algorithm called AlphaGo.

This breakthrough was immense, because, up until then, this super-human strategy, was thought to be previously impossible or at least a good few years away from being accomplished.

On 18th October 2017, DeepMind released a variant of this super-human algorithm, called AphaGoZero, which could now defeat AlphaGo 100 - 0.
The amazing thing about this variant of the algortihm was that AlphaGo Zero had learnt to self play, starting at a blank state, and gradually finding strategies that would beat previous incarnations of itself.

This was the first time that the database of a human expert was not required to build a super-human AI.
On 5th December 2017, DeepMind explained how AlphaGo Zero could be updated to beat the world champion programs StockFish and Elmo at Chess, and Shogi respectively. The entire learning process took under 24 hours.

AlphaGo Zero then become modified to a general algorithm, to get learn and become good at something really quickly without any prior knowledge of human expert strategy, called AlphaZero.
This algorithm is magnificent for so many reason, but the two that would immediately jump out at you are :
1. AlphaZero requires zero human expertise as input
  The underlying methodology of AlphaGo Zero can be applied to ANY game with, as long as the game state is known to both players at all times (as no prior expertise is required beyond the rules of the game).
  All that needs to change is the input file that describes the mechanics of the game, and tweaking parameters relating to the neural network and MonteCarlo tree search.

2. The algorithm is insanely simple, in its ability to mock the usual thinking pattern of the human brain.The steps is follows are: 1. evaluate all possible future scenarios. 2. give priority to promising paths. 3. do this while considering how others are LIKELY to react to your actions. 4. continue to explore the unknown 5. reach a familair state, 6. evaluate how favorable the position is 7. cascade the score backwards through previous positions in the mental pathway that led to this input. 8. after you've thought about future possibilities, take the action that you've explored the most. 9 at the end of the game, go back and evaluate where you misjudged the value of the future positions and update your understanding accordingly.

In connect4, we would like to train our model to win by getting four of its colour tokens in a row. Although the game logic is simple, there are 4,531,985,219,092 positions of the game state(board) in total (https://medium.com/applied-data-science/how-to-build-your-own-alphazero-ai-using-python-and-keras-7f664945c188).

Initialization:

The files that are important to us to train the model are:
- a game file, containing rules and logic of the game. This file should also have a method that will return a new game state after every episode is completed. The starting player's will be placed at the bottom of the centre column.

- the file called run.ipynb. This is a file that loads the game rules and then iterates through the main loop of the learning algorithm. There are 3 fundamental stages that this file contains:

  1. Self - Playing
  2. Retraining the Neural Network
  3. Evaluating the Neural Network

- the agent in our environment is responsible for exerting an action on the environment. The environment will, in turn then return to the agent, a game-state and a "reward". Based on the value of this reward, the agent evaluates how well it has performed and seeks out what could have been done differently through back propagation.
- In our case, we have two agents, the "best player and the current player". The best player is the agent that contains the best performing neural network and is used to generate self play memories.
The current player retrains its neural network on the memories of the best player to pitch against the best player. If the current player wins, the neural network inside the best player is exchanged for that of the current player, and the learning loop starts again.

- the agent.py file will contain the Player class. Each Player is initialized with its own neural network and Monte Carlo Search Tree.
There is a method called a "simulate" which actually runs the Monte Carlo Search Tree Process (ie. the "Back Propagation Process") ie. the agent moves to a leaf node of the tree, evaluates the node with its neural network and then backfills the value of the node up through the tree.
There is also a method called "act", which repeats the simulation multiple times, in order to understand which move from the current position is most favourable, and returns the chosen action to the game, so that the game can carry out the move.
The replay method retrains the neural network, using memories from previous games.
