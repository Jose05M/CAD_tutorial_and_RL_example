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

Both algorithms were trained in the same Flatland environment using discrete navigation actions.

During training:
- PPO achieved more stable learning behavior and eventually reached positive reward values.
- DQN explored the environment faster but maintained mostly negative rewards during the tested training time.

The TensorBoard reward curves show the evolution of the learning process for both algorithms throughout training and evaluation.