# Reinforcement Learning Navigation with ROS 2 and Flatland

This project implements a reinforcement learning navigation task using ROS 2, Flatland, Gymnasium, and Stable-Baselines3.

The robot learns to navigate through a hallway environment using LiDAR data and three discrete actions:
- Move forward
- Rotate left
- Rotate right

Two reinforcement learning algorithms were tested:
- PPO (Proximal Policy Optimization)
- DQN (Deep Q-Network)

## Running the Simulation

```bash
ros2 launch serp_rl serp_rl.launch.py
```

## TensorBoard Monitoring

```bash
cd results
tensorboard --logdir tensorboard_logs
```

Open in browser:

```text
http://localhost:6006
```

## Saving Training Logs

PPO:
```bash
ros2 launch serp_rl serp_rl.launch.py | tee ppo_log.txt
```

DQN:
```bash
ros2 launch serp_rl serp_rl.launch.py | tee dqn_log.txt
```

## Saving Models

```python
agent.save("models/ppo")
agent.save("models/dqn")
```

# Results

All training results and evidence were stored inside the `results/` folder.

## Included Evidence

- `ppo_log.txt` and `dqn_log.txt`
  - Terminal training logs for both algorithms.
  - Include rewards, timesteps, episode information, and evaluation accuracy.

- `graphs/`
  - TensorBoard screenshots showing reward evolution and training metrics for PPO and DQN.

- `tensorboard_logs/`
  - Raw TensorBoard event files generated during training.

- `models/`
  - Saved trained models:
    - `ppo.zip`
    - `dqn.zip`

## Observed Behavior

Two reinforcement learning algorithms were tested:
- PPO (Proximal Policy Optimization)
- DQN (Deep Q-Network)

The PPO and DQN algorithms showed different learning behaviors during training.

### PPO Results

![PPO Reward Curve](results/graphs/ppo/ep_rew_mean.png)
The PPO reward curves showed more stable learning behavior throughout training. Some PPO runs gradually increased from negative rewards to strongly positive reward values, reaching values above 250. This indicates that the agent successfully learned how to navigate the environment, avoid collisions, and reach the target more consistently.

Although some PPO runs remained negative, the best-performing runs demonstrated clear learning improvement and better final performance overall.

### DQN Results

![DQN Reward Curve](results/graphs/dqn/ep_rew_mean.png)
The DQN reward curves showed faster initial changes in reward values, but all runs remained in the negative reward region during the tested training time. The rewards improved gradually from approximately -140 to around -100, showing that the agent was learning some navigation behavior, but it still struggled with collisions and unsuccessful episodes.

DQN also showed more uniform behavior between runs, but it did not achieve the positive reward values reached by PPO.

### Comparison

Overall, PPO achieved better final performance and more successful learning behavior in this navigation task. PPO was able to reach positive rewards, indicating successful task completion more frequently, while DQN mainly reduced negative rewards without fully converging to successful navigation behavior during the tested training duration.

# CAD Tutorial

## LEGO Piece CAD Model

As part of the activity, a simple LEGO piece was modeled in CAD by following the tutorial showed in class. The activity focused on practicing basic CAD operations such as sketching, dimensions, extrusion, and feature creation.

The process started by defining the parameters and dimensions used for each sketch. First, the base rectangle of the LEGO piece was created, and then the stud feature was added. After that, a stud pattern was generated according to the dimensions of the rectangle to complete the LEGO design.

The `CAD_tutorial/` folder includes:
- The CAD model exported as an `.stl` file
- A screenshot/render of the final LEGO piece design

## CAD Visualization

![CAD Model](CAD_tutorial/design.jpeg)