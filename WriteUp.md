# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program

## The effect of PID components and hyperparameters tuning

### The effect of proportional (P)
The P value will deceide the finally value of the controller. However, if there is just the P hyperparameter in the controler, the controller output will oscillate around the finally value. Even more, the oscillation will faster with the increase of P value.

One video is shown as following, where just the P value is setted.

![P control video](videos/P_control_480.mov)

<video width="320" height="240" controls>
  <source src="videos/P_control_480.mov" type="video/mov">
</video>

### The effect of derivative (D)
The D component can reduce the oscillation by detecting the changing of CTE. When we get one suitable value for D, the oscillation will become slightly as shown in video following where just the P and D components in controller:
![PD control video](videos/PD_control_480.mov)

<video width="320" height="240" controls>
  <source src="videos/PD_control_480.mov" type="video/mov">
</video>

### The effect of integral (I)
The I component can reduce the reaction time, however more oscillation will be introduced also, which is evident in the curve part of the road. As shown in the following video, comparing with the previous video controller by PD controller, the car react more quickly in the meanwhile some over reaction is brought out leading to more oscillation. 
![PID control video](videos/PID_control_480.mov)

<video width="320" height="240" controls>
  <source src="videos/PID_control_480.mov" type="video/mov">
</video>

### Tuning step by step
Considering about their features of the three hyperparameters, I tuned them in the order or P -> D -> I.


1. In order to get one suitable *P* value as soon as possible, I limited the speed in 20 when tuning the *P* value. The fianlly *P* value lead the car finish one circle with obviously oscillation. 
1. Then the *D* value is adapted to reduce the oscillation. At the same time the speed limitation increased to 50.
1. When I get one *D* value, I found that, the car cannot react quickly without the integral component. Therefore, the *I* value is setted. And I found that if *I* value is too larger, there will be more oscillation even leading the car into dangerous situation.

Finally, I get one set of hyperparameters:
* P: 0.5
* I: 0.001
* D: 15