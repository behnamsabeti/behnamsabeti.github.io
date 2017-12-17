---
layout: post
title: Simple Reinforcement Learning to Solve Cartpole
---

the code is:

```python
action = agent.act(state)
next_state, reward, done, _ = env.step(action)
reward = reward if not done else -10
next_state = np.reshape(next_state, [1, state_size])
agent.remember(state, action, reward, next_state, done)
state = next_state
```
