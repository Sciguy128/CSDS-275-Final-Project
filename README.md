# CSDS 275 Final Project - Towers of Hanoi Robot
## By Aidan Leblanc, David Kraus, Gentiana Deda, Oneal Egwuatu, Qitai Huang

### Roles on jobs that of team memebers
- Aidan: Group organizer and designer of robot and robot enviroment. Also computed the inverse kinematics of the robots
- David: Designed the manipulator and compiled code and videos into the github repository
- Gentiana: Created rings for the robot to manipulate, and worked on the robot path planning
- Oneal: Was part of the team that created the code that allowed the manipulator to grab onto the rings
- Qitai: Was part of the team that created the code that allowed the manipulator to grab onto the rings

### Introduction
The idea behind this project was to design and develope a robot that could play the puzzle game of towers of hanoi.  

Through putting together and codeing this robot, we can explore a number of different topics including but not limited to:  

Inverse kinimatics, Rigid body transformation matrices, Using a Jacobian to trnasfrom from joint spce to task space, Implementing a method to manipulated/grab 
objects in CopelliaSim.  

We eventually want to demonstrate a robot that can pick up rings and set them down onto another tower much similar to the robot in the figure below  
 
<img src="https://github.com/Sciguy128/CSDS-275-Final-Project/assets/152509988/df43d6fb-c843-4bf8-911b-9da61c6e5b50" width="400" />

### Approach
We design a static robot that would have the ability to pick up the rings and move them onto the right towers.  

First thing we had to decide on was what our robot was going to look like and what the deminsions that we had to work around. Our robot is very similar to the IRB 140 robot that we worked with in class in that it consists of three major arm componets and a manipulator at the end. The deminsions are shown in this table:  
| Name        | Length |
|-------------|--------|
| Column/Base | 0.5 m  |
| Upper Arm   | 0.4 m  |
| Lower Arm   | 0.35 m |
| Manipulator | 0.2 m  |

With the model built we used these calculations to determine the Inverse Kinimatics  

<img src="https://github.com/Sciguy128/CSDS-275-Final-Project/assets/152509988/0d44e10d-c01c-4d14-b0f6-5c57ba3a7706" width="400" />

After working out that math, we checked it by dragging around the End Effector Point, just like in the homeworks we've done.
![Untitled video - Made with Clipchamp (1)](https://github.com/Sciguy128/CSDS-275-Final-Project/assets/152509988/35c681f2-7a70-4d9f-bb4d-f37bd8b5223c)

We did something similar and implemented robot control with a jacobian transfromation before moving on to the next step 

We then put in a way point following program and had the robot move to each ring using both types of control methods and pick them up and move them to the other towers.


### Results

### Conclusion
