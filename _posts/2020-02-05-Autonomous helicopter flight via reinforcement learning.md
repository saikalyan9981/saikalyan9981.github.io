---
title: "Autonomous helicopter flight via reinforcement learning"
date: 2020-01-20
---
["Link to paper"](https://people.eecs.berkeley.edu/~jordan/papers/ng-etal03.pdf)

In this paper, Authors tried to tackle Autonomous helicopter flight in a noisy environment.
They were successful in Hovering the helicopter and fly maneuvers taken from an RC helicopter
competition.

Helicopter flight is modeled by 4 actions (a_1,a_2,a_3,a_4). The state is considered with respect to the position of the helicopter. 
Firstly a model is fit to obtain helicopter dynamics.
When state and action at time t are given as input, the one-step differences in the state were predicted using linear regression, allowing  to predict s_{t+1} as a function of s_t and a_t plus noise. By exploiting symmetries and other knowledge, number of parameters were reduced to estimate were reduced,


After fitting helicopter dynamics, Now Reinforcement learning is used to hover the helicopter. A  manually designed neural network which takes inputs and results in the action values (a_1,a_2,a_3,a_4) is trained by using RL. For encouraging small actions and a small change in state values during hovering, a quadratic cost function is chosen to penalise actions and abrupt movements. Here Pegasus Algorithm is used for Reinforcement learning and using hill-climbing/gradient ascent, the parameters for an optimal policy are found, Normal Monte-Carlo method failed to perform, as much variance is observed in total reward estimates of trajectory.



For flying trajectories, the neural network is modified, and reward function is modified in such a way that So that it is rewarded when it follows the desired trajectory.


I found some relations  were fine-tuned manually based on observations, which could be possibly true only for particular tasks in maneuvers, like they artificially slowed down the z-response, by adding parameter t in policy class, which slows down response in downward(Z) direction by t seconds. I felt this is one of the demerits.

This paper is one of the giant-steps to prove that RL works for solving a complex problem like Autonomous Helicopter flight not only on simulations but also on physical fields. 


Here are some specific questions that I have.
*  I could not understand some of the variables/parameters used in regression and how
noise is handled.
*  Need clarity on Pegasus Algorithm
