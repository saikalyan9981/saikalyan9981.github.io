---
title: "On the Role of Tracking in Stationary Environments"
date: 2020-02-05
---
 ["Link to paper"](http://www0.cs.ucl.ac.uk/staff/d.silver/web/Publications_files/tracking.pdf)

In this paper, Authors proved that tracking helps solve problems with the stationary world which have temporal coherence and are too large to be solved correctly. Authors proved using a sample case of black/white problem, and then considered a significant problem like Go, to emphasize help-fullness of tracking. Authors went on to show how a meta-learning algorithm called IDBD combined with tracking in the temporally coherent stationary environment produced excellent results.


Some understanding of basic terms:
  * Stationary world: The transitions of the model, or structure of the world remains unchanged with time.
  * Temporal coherence: Local environment/states nearby are similar
  * Tracking: It can be considered as sufficient learning during train time combined with learning during deployment time.
  * Meta-learning: Learning a feature of one task, and using that feature in the second task to get a good result in the second task.
  * Converging solution: Optimum solution learnt through training data

## Tracking in Black/White Problem
* Problem: In a strip of 20 states consisting of black/white steps, the agent moves from 1 step to adjacent randomly. The goal is to predict the probability of observing black by modelling with a single parameter.

Converging solution predicts that the probability of observing black step is 0.5, as it has seen an equal amount of black and white steps in training data,

If the environment is temporally coherent, i.e. black steps and white steps occur in clusters, Tracking with reasonable learning rate predicted better, as tracking agent gets to understand temporal space.

 Meta-learning algorithm helps in finding the value of a reasonable learning rate used in tracking.

However, if the environment is not temporally coherent, with the use of tracking coupled with meta-learning, there is a negligible improvement.



## Tracking in Go Problem
In the problem of Go, converging solution is trained with a large number of episodes of self-play and never trained again.

While tracking solution is trained with a lesser number of episodes. It is further trained during its play with the converging solution.

In this way, tracking solution can understand un-explored solutions during its play with a convergent solution when it gets punished.

However, convergent-solution always picks the optimum action learnt from its training, although it's getting punished/negatively rewarded.

Results proved that convergent-solution is out-beaten by tracking solution. Although tracking is repeatedly learning, in this case, tracking is seen to be time-constrained, Since the number of parameters to train are less



## Questions

Here are some specific questions that I have.
* Need more light on uses of meta-learning and why/how tracking helps in task-selection as said in the abstract?
* About go: In section 3, he mentions this "the game contains sufficient strategic
depth to merit a regular column in professional Go periodicals". I didn't understand what the Author meant by this?
* Based on the example of black/white, according to agent the environment is non-stationary, how can we justify that?


