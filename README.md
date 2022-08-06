# RL-experiments

Reinforcement learning experiments.

Based on the tutorial by Nicholas Renotte https://www.youtube.com/watch?v=dWmJ5CXSKdw

For storage reasons the checkpoints will not be uploaded.

### Requirements

- Python 3.7
- gym 0.21.0
- cuda 3.11
- pytorch 1.11
- Stable Baselines3
- numpy
- matplotlib
- opencv
- plus other stuff

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
3. Still just running through, increasing difficulty to 5 (run name: PPO11)
4. Now ignoring the monsters even more. Should start training from beginning

changing torch version to 1.11 because of [bug](https://github.com/Lightning-AI/lightning/issues/13695)

## 3. Street Fighter

Using gym retro (required python 3.5-3.7). And using optuna.

Found ROM [here](https://ia800201.us.archive.org/view_archive.php?archive=/7/items/No-Intro-Collection_2016-01-03_Fixed/Sega%20-%20Mega%20Drive%20-%20Genesis.zip)

Storing the different trial results in an sqlite database.

## 4. Chrome Dino

Build the entire game environment from scratch. Libraries used:
- MMS to get screen capture
- opencv for preprocessing
- Tesseract OCR to extract game over text
- stable baselines for the RL algorithm (DQN model)