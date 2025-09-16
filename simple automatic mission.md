### **Project specification**

1. __Map handling.__
    - implementation or tool - 3D map loading - **required**
    - implementation of obstacle inflation - **required**
    - implementation of map transformations, rotations etc. - **if needed**
2. __Map search algorithm. (Path finding)__
    - implementation or tool - advanced planning algorithm - **required**
        - RRT, A*...
3. __Trajectory planning.__
    - Use pointcloud to plan the trajectory, the trajectory planning needs to be done in 3D.
    - implementation or tool - optimization of path - **if needed**
        - minimal requirement - elimination of not necessary points (elimination of sequences of horizontal, vertical, diagonal paths...)          
4. __ROS Drone control node__
    - implementation - trajectory loading - **required**
    - implementation - mission tasks/commands - **required**
    - implementation - position controller - **required** 
5. __Point specification/task/command__
    - implementation - land and takeoff - **required**
    - implementation - point radius (precision of position controller for given point - Hard/Soft) - **required**
    - implementation - yaw control in a specific angle - **required**
6. __Documentation__ 
    - analysis of each used approach - **required**
        - pros and cons
        - explanation of the algorithms or implementations
    - overal solution diagram - **required**
        - data processing paths
        - ROS Drone control diagram

_Note: Map search algorithm and some parts of Trajectory planning can be implemented in one method, if you choose so._
_Note: If a software tool is used, it must be well documented and explained in documentation._

#### Advanced planning algorithm
Implement or integrate the algorithm into the planning trajectory algorithm from your 1st assignemnt. 

RRT explained in 2D: https://theclassytim.medium.com/robotic-path-planning-rrt-and-rrt-212319121378
RRT and RRT* implemented in 3D: https://github.com/motion-planning/rrt-algorithms

#### Pointcloud and planning in 3D
You have to work with this map: https://github.com/MartinSedlacek/LRS-FEI/blob/2nd_project/maps/FEI_LRS_PCD/map.pcd
To load this map you can use PCL library. 

To install the library you can use: `sudo apt install libpcl-dev`, to use the library to load the pointcloud you can refer to the tutorial for example: https://pcl.readthedocs.io/projects/tutorials/en/latest/reading_pcd.html. 

To further process the pointcloud to voxel grid, you can refer to: https://pcl.readthedocs.io/projects/tutorials/en/latest/voxel_grid.html

### **Example mission** 


![image](resources/test_map.png)


|| X | Y | Z | Precision| Task |
|---| ---      | ---      | ---      |---  |--- |
|1| x0  | y0   | 2   | - |takeoff |
|2| x1 | y1 | 2 | soft | yaw 90 |
|3| x2   |   y2    |2   | hard   |landtakeoff |
|4| x3 | y3 | 1| soft| - | 

### **Example mission 2** 
[Link to file](resources/points_example.csv)


|| X | Y | Z | Precision| Task |
|---| ---      | ---      | ---      |---  |--- |
|1|13.60|1.50|1.00|soft|takeoff|
|2|8.65|2.02|1.00|soft|-|
|3|4.84|5.37|2.00|hard|yaw180|
|4|2.08|9.74|1.75|hard|-|
|5|8.84|6.90|2.00|hard|landtakeoff|
|6|2.81|8.15|1.50|soft|yaw90|
|7|13.60|1.50|2.00|hard|land|
