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

<pre><code>
action = env.act(action)
</code></pre>

it was a test post!
