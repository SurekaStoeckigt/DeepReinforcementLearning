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

How AlphaGo Zero Works:
