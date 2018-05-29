# OpenAI Retro Contest

## 项目介绍

[比赛链接](https://contest.openai.com/)

We're holding a transfer-learning contest using the Sonic The Hedgehog™ series of games for SEGA Genesis. In this contest, participants try to create the best agent for playing custom levels of the Sonic games — without having access to those levels during development. See our [blog post](https://blog.openai.com/retro-contest/) for more details.

Here's how the contest works:

1. Train or script your agent to play Sonic The Hedgehog™
2. Submit your agent to us as a Docker container
3. We evaluate your agent on a set of secret test levels
4. Your agent's score appears on the leaderboard

This process is illustrated in the schematic below.

![img](https://contest.openai.com/static/images/contest-schematic.svg)

We believe that the next step for reinforcement learning is to leverage past experience to quickly learn new environments. Current algorithms are very prone to memorization and can't adapt well to new situations. While this contest focuses on video game levels, we hope the winning techniques will be applicable to a wide variety of domains.

The contest will run from April 5 to June 5 (2 months) and winners will receive some pretty cool trophies.

To see rules for the contest or to get started with it, look at the [details page](https://contest.openai.com/details). To see the current best submissions check out the [leaderboard](https://contest.openai.com/leaderboard). The [blog post](https://blog.openai.com/retro-contest/) has an overview of the motivations for the contest and the [tech report](https://s3-us-west-2.amazonaws.com/openai-assets/research-covers/retro-contest/gotta_learn_fast_report.pdf) describes the benchmark used by the contest in detail.

- [RESEARCH](https://openai.com/research)
- [SYSTEMS](https://openai.com/systems)
- [ABOUT](https://openai.com/about/)
- [BLOG](https://blog.openai.com/)
- [PRESS](https://openai.com/press/)
- [JOBS](https://openai.com/jobs/)

- [Twitter](https://twitter.com/openai)
- [Facebook](https://www.facebook.com/openai.research/)

## 主要方法

DQN + TensorFlow + gym

## 项目文件

### 1. 名称

[sonic_RL](sonic_RL)：主文件

#### 1.1 函数

- `class DQN:`：主要使用的DQN类，所有方法放在类中。成员变量包括网络参数，优化函数等。

- `save_model(self):`：保存模型参数。

- `onehot_action(action):`：将动作空间从12维转化为8维

  >  原12维向量：B, A, MODE, START, UP, DOWN, LEFT, RIGHT, C, Y, X, Z动作空间：{{LEFT}, {RIGHT}, {LEFT, DOWN}, {RIGHT, DOWN}， {DOWN}, {DOWN, B}, {B}}

- `dehot_action(action):`：将动作空间从8维转化为12维

- `conv2d(x, w):`：步长为1x1的卷积核

- `max_pool_2x2(x):`：2x2池化层

- `create_q_network(self):`：定义网络每一层参数，返回网络输出值

- `weight_variable(shape):`：权重初始化

- `bias_variable(shape):` ：置偏初始化

- `create_training_method(self):`：定义损失函数和优化方法

- `perceive(self, state, action, reward, next_state, done):`：DQN中的存储器保存数据

- `train_q_network(self):`：从仓库中取数据进行训练网络

- `egreedy_action(self, state):`：使用e-greedy来获取行为

- `action(self, state):`：根据greedy来获取行为

 