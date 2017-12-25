## README STILL UNDER CONSTRUCTION


# RL A3C Pytorch Continuous

![A3C LSTM playing BipedalWalkerHardcore-v2](https://github.com/dgriff777/a3c_continuous/blob/master/demo/BPHC1.gif) ![A3C LSTM playing BipedalWalkerHardcore-v2](https://github.com/dgriff777/a3c_continuous/blob/master/demo/BPHC2.gif)

This repository includes my implementation with reinforcement learning using Asynchronous Advantage Actor-Critic (A3C) in Pytorch an algorithm from Google Deep Mind's paper "Asynchronous Methods for Deep Reinforcement Learning."

### A3C LSTM

This is continuous domain version of my other a3c repo. Here I show A3C can solve BipedalWalker-v2 but also the much harder BipedalWalkerHardcore-v2 version as well. "Solved" meaning to train a model capable of averaging reward over 300 for 100 consecutive episodes

Added trained model for BipedWalkerHardcore-v2

## Requirements

- Python 2.7+
- Openai Gym
- Pytorch

## Training
*When training model it is important to limit number of worker threads to number of cpu cores available as too many threads (e.g. more than one thread per cpu core available) will actually be detrimental in training speed and effectiveness*

To train agent in BipedalWalker-v2 environment with 6 different worker threads:
*On a MacPro 2014 laptop traing typically takes 15-20mins to get to a winning solution*

```
python main.py --workers 6 --env BipedalWalker-v2 --save-score-level 300 --model MLP --stack-frames 1
```

To train agent in BipedalWalkerHardcore-v2 environment with 64 different worker threads:
*BipedalWalkerHardcore-v2 is much harder environment compared to normal BipedalWalker*
*On a 72 cpu AWS EC2 c5.18xlarge instance training took a full 24hrs to get to model that could solve the environment*

```
python main.py --workers 64 --env BipedalWalkerHardcore-v2 --save-score-level 300 --model CONV --stack-frames 4
```

Hit Ctrl C to end training session properly

![A3C LSTM playing BipedalWalkerHardcore-v2](https://github.com/dgriff777/a3c_continuous/blob/master/demo/BPHC3.gif)

## Evaluation
To run a 100 episode gym evaluation with trained model
```
python gym_eval.py --env BipedalWalkerHardcore-v2 --num-episodes 100 --stack-frames 4 --model CONV --new-gym-eval True
```

## README STILL UNDER CONSTRUCTION
