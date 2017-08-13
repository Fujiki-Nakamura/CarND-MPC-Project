# Report for the Model Predictive Control project
[//]: # (Image References)
[image1]: ./images/update_equations.png

## The Model
The model is based on the kinematic model mentioned in the lectures. The state includes the vehicle's position coordinates (x, y), heading angle (psi), velocity (v), cross track error (cte) and heading angle error (epsi). The actuators consist of steering angle (delta) and acceleration (a). The model calcurates the current state from the previous state and actuations following the update equations below:

![alt text][image1]


## Timestep Length and Elapsed Duration (N & dt)
According to the suggestion from Udacity, I chose N = 10 and dt = 0.1. I think these values reasonable because T (= N * dt) should be a few seconds at most and N is large (or dt is small) enough to avoid the discretization error. Also I think dt = 0.1 (100ms) makes other things easier because it is the same value as the expected latency (100ms).

## Polynomial Fitting and MPC Preprocessing
I preprocessed the waypoints by transforming them into vehicle's coordinate system. 

## Model Predictive Control with Latency
To handle the 100ms latency, I calculated the current state by using the actuations two timesteps before (rather than using the actuations one timestep before). 
