<<<<<<< HEAD
[//]: # (Image References)

[image2]: https://github.com/TmoreiraBR/UnityMLAgents1stProject/blob/main/TrainedResults.jpg  "Test Agent"

# Report for Project 1: Navigation

### Introduction

For solving this project a Deep Q-Learning Algorithim, with two neural networks (local and target) and  was utilized.

The Algorithim, based on [[1]](#1), utilizes the "local" neural network as a function approximation for the action-value function:

<img src="https://render.githubusercontent.com/render/math?math=\hat{q}_{\pi}(s,a,\theta)">,

where the function approximation is parametrized by the neural network weights <img src="https://render.githubusercontent.com/render/math?math=\theta">.

Assuming an already trained neural network, the optimal policy can be obtained by sampling actions that maximize the action value function:

<img src="https://render.githubusercontent.com/render/math?math=arg max_a \hat{q}_{\pi^*}(s,a,\theta)">.

Since the parametrized action-value function is continuous, on-policy learning approch, such as updating a Q-table, could lead to reinforcing correlated state-actions values (i.e. actions that lead to known states), which is bad for generalization.

To avoid this, the Algorithim utilizes Experience Replay, where batches of <img src="https://render.githubusercontent.com/render/math?math=<s_{t}, a_{t}, r_{t+1}, s_{t+1}, a_{t+1}>"> are sampled randomly, breaking the correlation.

Also, to avoid unstable learning a second network, called "target" network is utilized during the update step. This target network has its weights frozen during the update, and after some number of steps (hyperparameter) its weights are updated to be the same as the "local" network:

<img src="https://render.githubusercontent.com/render/math?math=\Delta w = \alpha (r_{t+1} \quad + \gamma max_a \hat{q}(s,a,\theta_{frozen}) - \hat{q}(s,a,\theta)) \nabla w \hat{q}(s,a,\theta)">.

## Algorithim



## Results

![Test Agent][image2]


## References
<a id="1">[1]</a> 
Mnih, V., Kavukcuoglu, K., Silver, D., Rusu, A.A., Veness, J., Bellemare, M.G., Graves, A., Riedmiller, M., Fidjeland, A.K., Ostrovski, G. and Petersen, S., 2015. Human-level control through deep reinforcement learning. nature, 518(7540), pp.529-533.
