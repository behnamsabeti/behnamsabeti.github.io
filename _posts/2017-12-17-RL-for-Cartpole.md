---
layout: post
title: Simple Reinforcement Learning to Solve Cartpole
---

the code is:

```python
action = agent.act(state)
state = next_state
```
next you can do:

```
for _ in action:
	env.act(_)
```

```python
model = Sequential()
        model.add(Dense(24, input_dim=self.state_size, activation='relu'))
        model.add(Dense(24, activation='relu'))
        model.add(Dense(self.action_size, activation='linear'))
        model.compile(loss='mse',
                      optimizer=Adam(lr=self.learning_rate))
```

<pre><code>
action = env.act(action)
</code></pre>

<script src="https://gist.github.com/behnamsabeti/f89ec3d94a12fd4a7f8ddeeeb95e75ea.js"></script>

it was a test post!
