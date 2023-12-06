# CSDS 275 Final Project - Towers of Hanoi Robot
## By Aidan Leblanc, David Kraus, Gentiana Deda, Oneal Egwuatu, Qitai Huang

### Roles on jobs of team members
- Aidan: Group organizer and designer of robot and robot environment. Also computed the inverse kinematics of the robots
- David: Designed the manipulator and compiled code and videos into the GitHub repository
- Gentiana: Created rings for the robot to manipulate, and worked on the robot path planning
- Oneal: Was part of the team that created the code that allowed the manipulator to grab onto the rings
- Qitai:

### Introduction
The idea behind this project was to design and develop a robot that could play the puzzle game of towers of hanoi.  

Through putting together and coding this robot, we can explore a number of different topics including but not limited to:  

Inverse kinematics, Rigid body transformation matrices, Using a Jacobian to transition from joint space to task space, Implementing a method to manipulate/grab 
objects in CopelliaSim.  

We eventually want to demonstrate a robot that can pick up rings and set them down onto another tower much similar to the robot in the figure below  
 
<img src="https://github.com/Sciguy128/CSDS-275-Final-Project/assets/152509988/df43d6fb-c843-4bf8-911b-9da61c6e5b50" width="400" />

### Approach
We designed a static robot that would have the ability to pick up the rings and move them onto the right towers.  

The first thing we had to decide on was what our robot was going to look like and what the dimensions that we had to work around. Our robot is very similar to the IRB 140 robot that we worked with in class in that it consists of three major arm components and a manipulator at the end. The dimensions are shown in this table:  
| Name        | Length |
|-------------|--------|
| Column/Base | 0.5 m  |
| Upper Arm   | 0.4 m  |
| Lower Arm   | 0.35 m |
| Manipulator | 0.2 m  |

<img src="https://github.com/Sciguy128/CSDS-275-Final-Project/assets/152509988/1782fb96-0bc4-4548-a9eb-e5dd55f5fd2d" width="400" />

With the model built, we used these calculations to determine the Inverse Kinematics  

<img src="https://github.com/Sciguy128/CSDS-275-Final-Project/assets/152509988/0d44e10d-c01c-4d14-b0f6-5c57ba3a7706" width="400" />

After working out that math, we checked it by dragging around the End Effector Point, just like in the homework we've done.  

![Untitled video - Made with Clipchamp (1)](https://github.com/Sciguy128/CSDS-275-Final-Project/assets/152509988/35c681f2-7a70-4d9f-bb4d-f37bd8b5223c)

We did something similar and implemented robot control with a Jacobian transformation before moving on to the next step 

We then put in a waypoint following program and had the robot move to each ring using both types of control methods to pick them up and move them to the other towers.

Can someone make a flow chart, showing how each part of the code interacts with each other?

### Results

https://youtu.be/ubXWTYJRJ70   

<img src="https://github.com/Sciguy128/CSDS-275-Final-Project/assets/152509988/e49d92b6-3c07-492c-bf76-e3b9a879c666" width="600" />  

<img src="https://github.com/Sciguy128/CSDS-275-Final-Project/assets/152509988/398cefac-fbb3-4b76-8c48-af6e7e5713c0" width="600" />  

<img src="https://github.com/Sciguy128/CSDS-275-Final-Project/assets/152509988/1d2d1f1e-6323-45c7-85dc-bd122e2a7d60" width="600" />  


We need to talk about what the final capabilities of this robot are, what its are shortcomings and what could be improved in the future.


### Conclusion

Summarize what you did, and the result that you achieved. Discuss how the work can be further developed
or improved in the future.
