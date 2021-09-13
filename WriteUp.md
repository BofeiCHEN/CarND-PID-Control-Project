# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program

## The effect of PID components and hyperparameters tuning

### The effect of proportional (P)
The P value will deceide the finally value of the controller. However, if there is just the P hyperparameter in the controler, the controller output will oscillate around the finally value. Even more, the oscillation will faster with the increase of P value.

One video is saved in the folder **videos** as *P_control_480.mov* and the **.gif** image as following, where just the P value is setted.

![P control video](images/P_control_480.gif)



### The effect of derivative (D)
The D component can reduce the oscillation by detecting the changing of CTE. When we get one suitable value for D, the oscillation will become slightly as shown in  the following **.gif** where just the P and D components in controller. The original video *PD_control_480.mov* can be found in folder *videos*.
![PD control video](images/PD_control_480.gif)


### The effect of integral (I)
The I component can reduce the reaction time, however more oscillation will be introduced also, which is evident in the curve part of the road. As shown in the following video, comparing with the previous video controller by PD controller, the car react more quickly in the meanwhile some over reaction is brought out leading to more oscillation. One original video *PID_control_480.mov* can be found in folder *videos*. The **.gif** image as following:
![PID control video](images/PID_control_480.gif)


### Tuning step by step
Considering about their features of the three hyperparameters, I tuned them in the order or P -> D -> I.


1. In order to get one suitable *P* value as soon as possible, I limited the speed in 20 when tuning the *P* value. The fianlly *P* value lead the car finish one circle with obviously oscillation. 
1. Then the *D* value is adapted to reduce the oscillation. At the same time the speed limitation increased to 50.
1. When I get one *D* value, I found that, the car cannot react quickly without the integral component. Therefore, the *I* value is setted. And I found that if *I* value is too larger, there will be more oscillation even leading the car into dangerous situation.

Finally, I get one set of hyperparameters:
* P: 0.5
* I: 0.001
* D: 15