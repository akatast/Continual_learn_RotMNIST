# Continual_learn_RotMNISTWhy Continual Learning
One major obstacle towards AI is the poor ability of models to solve new problems quicker, and without forgetting previously acquired knowledge This general problem is termed catastrophic forgetting. Avoiding catastrophic forgetting and achieving nontrivial backwards transfer (BT) and forward transfer (FT) are major goals for continual learning models, and in addition, general AI.
Memory-Based CL approaches
These approaches use episodic memory that stores a subset of data from past tasks to tackle forgetting. One approach to leverage such episodic memory is to use it to constrain the optimization such that the loss on past tasks can never increase
Algorithm used : GEM ( Gradient Episodic Memory )
The 3 components involved are

Memory: For each task, let’s make sure we don’t forget them. We’ll keep a portion of them in memory.
Episodic: Let’s replay these memories to make sure we’re not damaging our accuracy on these tasks when we learn new ones. By playing them over again, we’re basically going through an episode
Gradient: When we look at the episode again, let’s make sure the gradient doesn’t go the wrong way. What this means is: let’s not unlearn what we learned on the previous task.
GEM aims to increase Backward Transfer so that knowledge gained with each new Task does not result in forgetting previously gained knowledge of Previous tasks.
Formally, Backward transfer (BWT), is the influence that learning a task t has on the performance on a previous task k ≺ t. On the one hand, there exists positive backward transfer when learning about some task t increases the performance on some preceding task k. On the other hand, there exists negative backward transfer when learning about some task t decreases the performance on some preceding task k. Large negative backward transfer is also known as (catastrophic) forgetting
In order for a gradient update to take place, compute the dot product of the current learning task with all the previous tasks in memory. The update is allowed to take place if the gradient is greater than or equal to 0 for all the episodes. This translates into constraining update for one task to not conflict with an update for the previous task.
If the gradient is going the wrong way, take this gradient update and project it to the closest possible vector that doesn’t go the wrong way. It formulates the optimization as a projection on to a cone).

Mathematically above gradient update solutions translate to below
t here is Task
when observing the triplet (x, t, y), solve the following problem:
