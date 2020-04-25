[//]: # (Image References)

[image1]: https://github.com/Apunti/RL-Udacity-Continuous-Control/blob/master/images/DDPG.png "DDPG"
[image2]: https://github.com/Apunti/RL-Udacity-Continuous-Control/blob/master/images/plot.png "Plot"
[image3]: https://github.com/Apunti/RL-Udacity-Continuous-Control/blob/master/images/log.png "Log"

# Report

### Learning Algorithm
The algorithm used to solve this environment is an off-policy method called DDPG (Deep Deterministic Policy Gradient) presented in
[this paper](https://arxiv.org/abs/1509.02971).

Deep Deterministic Policy Gradient (DDPG) is an algorithm which concurrently learns a Q-function and a policy. It uses off-policy data and the Bellman equation to learn the Q-function, and uses the Q-function to learn the policy.

![DDPG][image1]

For further explanation I recommend reading the [spinningup openai website](https://spinningup.openai.com/en/latest/algorithms/ddpg.html).

The architecture for the actor consists of 3 fully connected layers, combined with BatchNormalization, with Relu activation and the output with tanh activation. The architecture for the critic consists of 3 fully connected layers. I applied a BatchNormalization after the first layer, and the actions are inserted in the second. The activation function used is Relu and the output is a linear layer without activation function.

The hyperparameters used are:

- ``BUFFER_SIZE = 1e6``
- ``BATCH_SIZE = 128``
- ``GAMMA = 0.99``
- ``TAU = 0.001``
- ``LR_ACTOR = 3e-4``
- ``LR_CRITIC = 3e-4``

### Plot of rewards

![Plot][image2]
![Log][image3]

We can see that the environment is solved around the episode 300.

### Ideas for Future Works

We could try different hidden sizes to see if we can improve either the performance or the convergence time. We could also try different activation functions that could lead to faster convergence such as leaky relu or we could try to add dropout layers.

To improve the current implementation, as suggested by Udacity, we could use distributed learning. We could try different approaches trying various learning algorithms such as A2C, or D4PG.
