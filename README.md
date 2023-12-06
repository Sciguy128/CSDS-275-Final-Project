# CSDS 275 Final Project - Towers of Hanoi Robot
## By Aidan Leblanc, David Kraus, Gentiana Deda, Oneal Egwuatu, Qitai Huang

### Roles on jobs of team members
- Aidan: Group organizer and designer of robot and robot environment. Also computed the inverse kinematics of the robots.
- David: Designed the manipulator and compiled code and videos into the GitHub repository
- Gentiana: Created rings for the robot to manipulate, and worked on the robot path planning
- Oneal: 
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

Here's what that looks like in our code

```
-- ***INVERSE KINEMATICS***
function compute_geom_IK(target_pos,l1,l2,l3,l4)
    -- Extracting target position coordinates
    local x, y, z = target_pos[1], target_pos[2], target_pos[3]
    -- Calculating IK parameters
    local u = math.sqrt(x^2 + y^2) - l4
    local h = z - l1
    local v = math.sqrt(u^2 + h^2)
    local alpha = math.atan2(h, u)
    local gamma = math.acos((l2^2 + v^2 - l3^2) / (2 * l2 * v))
    -- Calculating joint angles
    local q1 = -1 * math.atan2(x, y)
    local q2 = alpha - gamma
    local q3 = math.pi - math.acos((l2^2 + l3^2 - v^2) / (2 * l2 * l3))
    local q4 = -1 * (q2 + q3)

    return {q1, q2, q3, q4}
end
```

After implementing it, we checked it by dragging around the End Effector Point, just like in the homework we've done.  

![Untitled video - Made with Clipchamp (1)](https://github.com/Sciguy128/CSDS-275-Final-Project/assets/152509988/35c681f2-7a70-4d9f-bb4d-f37bd8b5223c)

[NOT IMPLEMENTED YET]We did something similar and implemented robot control with a Jacobian transformation before moving on to the next step 

We then put in a waypoint following program and had the robot move to each ring using both types of control methods to pick them up and move them to the other towers.

Below is a flow chart demonstrating how each portion of our code interacts with each other.  

<img src="https://github.com/Sciguy128/CSDS-275-Final-Project/assets/152509988/09ce85c5-9d57-4953-b46d-b0fc394e0cd9" width="600" />  

All of the code was done in Lua, as we didn't have a need for any plugins or libraries that we could've gotten from Python.


### Results

The Robot ended up having three states that it can move in between. If you imagine that each tower is labeled 1 through 3, then the robot is able to move all three rings from one tower to another, while making sure to follow to rules of the game.  

Below is a YouTube link showing the full range of capabilities of the robot.
https://youtu.be/ubXWTYJRJ70   

<img src="https://github.com/Sciguy128/CSDS-275-Final-Project/assets/152509988/e49d92b6-3c07-492c-bf76-e3b9a879c666" width="600" />  

Here's a gif showing the robot moving the rings from tower 1 to tower 3. Notice to do this, we set TARGET_STATE = 3  

<img src="https://github.com/Sciguy128/CSDS-275-Final-Project/assets/152509988/398cefac-fbb3-4b76-8c48-af6e7e5713c0" width="600" />  

Here we can see the robot moving the rings from tower 3 to tower 2. Similarly, we've set TARGET_STATE = 2  

<img src="https://github.com/Sciguy128/CSDS-275-Final-Project/assets/152509988/1d2d1f1e-6323-45c7-85dc-bd122e2a7d60" width="600" />  

And lastly, the robot moves the rings back to tower 1 by setting the TARGET_STATE = 1  


### Conclusion

As it stands now, the robot is capable of solving any configuration of the towers of Hanoi. This means that within the controlled Coppeliasim system, the robot can stack the rings on any of the three towers.

A limitation of this robot's implementation is that it requires prior knowledge about the nature of the world. For example, the person controlling this robot needs to specify the starting state of the robot to ensure that it functions correctly. To improve the robot, computer vision could be applied to detect the configuration at any given time.

The robot could also be further developed to play the game with more than three rings. This implementation would not significantly increase the complexity of the robot’s movements, but would rather increase the complexity of the states of the game.
