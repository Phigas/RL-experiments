# RL-experiments

Reinforcement learning experiments.

Based on the tutorial by Nicholas Renotte https://www.youtube.com/watch?v=dWmJ5CXSKdw

For storage reasons the checkpoints will not be uploaded.

## 1. mario

Use nespy emulator enviroment to do simple model. Reward for moving forward.

After 500k steps mario able to reasonably advance in the level but still quite some improvement.
Maybe it is difficult for the agent to learn from the videos.

## 2. doom

Use ViZDoom to build a custom enviroment class to use in gym. Comes with a variety of RL adapted levels.

### 2.1. basic

Can only move left right and has to shoot monster.

Training successful and seemed done but doomguy gets stuck on the left sometimes.

### 2.2. advanced

Doomguy is in circle and can turn and shoot. Has to defend himself from monsters that come from all directions.

Trained well and showed significant improvement. But still room for improvement.

### 2.3. corridor

Doomguy needs to walk through a corridor with enemies on the sides. Originally only reward for advancing but this is changed in the code.

Also added a learning schedule to improve learning results.
Since the simulation was more difficult here the training hyperparmeters were tuned with optuna.

1. When simulating on easiest difficulty agent was not really interested in killing the monsters (run name: PPO5)
2. Skipping to difficulty 3, increasing kill reward and decreasing being hit reward (run name: PPO9)

changing torch version to 1.11 because of [bug](https://github.com/Lightning-AI/lightning/issues/13695)
