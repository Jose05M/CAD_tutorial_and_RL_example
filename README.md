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

## Results

During testing, PPO achieved more stable learning behavior and reached positive reward values, while DQN explored the environment faster but maintained mostly negative rewards during the tested training time.

The collected evidence includes:
- Training logs
- TensorBoard reward curves
- Saved models
- Evaluation accuracy
- Simulation screenshots