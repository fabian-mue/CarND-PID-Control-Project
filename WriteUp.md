# CarND-PID-Controller-Project
## Goals
In this project the goal is to safely navigate around the lake race track from the Behavioral Cloning Project. To do this a PID controller needs to be implemented in C++ to maneuver the vehicle around the track. The used algorithm for the PID controller has been introduced in the lesson and the PID-coefficients K_p (Proportional Control), K_i (Integral Control) and K_d (Derivative Control) used for this algorithm have been fine-tuned in this project.

## The PID-Controller

The PID controller (proportional-integral-derivative controller) consists of the components of the P-element, the I-element and the D-element. The P-component ensures a fast response, the I-component can fully compensate for the control deviation (biased offsets which could cause errors) and the D-component enables fast readjustment in the event of suddenly occurring disturbances. 
The following image illustrates an overview of a PID-controller and its applied context:
![PID-feedback-loop-v1](/home/fabian/CarND-PID-Control-Project/PID-feedback-loop-v1.png)

An error, here the cross track error (CTE), is calculated between the input setpoint the current measured output from the process. This error is input in each of the PID- elements to calculate the control variable for the process. This control loop mechanism with feedback is applied to reduce the CTE to a minimum and to adjust the output to the setpoint as close as possible.
The applied formula to calculate the control variables using the PID controller is:
<img src="/home/fabian/CarND-PID-Control-Project/PID_formula.png" alt="PID_formula" style="zoom:33%;" />

In this formula 3 parameters are configurable K_p, K_d and K_i. 
These PID coefficients need to adjusted and fine-tuned to get the optimum results from the PID controller.

The effects of the individual PID elements a on the output signal are shown in the graphic below.

<img src="/home/fabian/CarND-PID-Control-Project/PID_results_Example.png" alt="PID_results_Example" style="zoom: 50%;" />

The introduced PID controller has been implemented and applied in the project. 
The video file "video_test.mp4" shows the car driving around the test track using the implemented PID controller.


## Parameter Tuning

The values of the PID coefficients K_p, K_i and K_d have been defined following this strategy: 
Initially, the parameter values from the lecture have been chosen. Afterwards, each of these parameters has been fined tuned by running the simulation and checking the driving behavior of the vehicle.
The P-coefficient is necessary to change the steering angle of the car depending on the CTE (cross-track-error). The D-coefficient has been used to prevent overshooting and the I-coefficient is applied to remove a bias error (due there is basically no bias error, this values is very small). 
The following tables shows the final coefficients:

|      | Initial values | Fine-tuned values |
| ---- | -------------- | ----------------- |
| K_p  | 0.2            | 0.19              |
| K_i  | 3.0            | 2.8               |
| K_d  | 0.004          | 0.0000001         |



###  Conclusion 

This project shows in an impressive manner how a PID Controller works and the importance of the correct handling of the PID-coefficients.
Next steps would be to additionally implement a controller for handling the speed.
Furthermore, an optimization algorithm like "Twiddle" would also be beneficial to get the optimum PID-coefficients (formula is illustrated below).

<img src="/home/fabian/CarND-PID-Control-Project/twiddle.png" alt="twiddle" style="zoom: 50%;" /> 

