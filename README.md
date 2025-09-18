# LRS-FEI
A short guide on how to work with preinstalled ubuntu LRS. 
## Setup simulation with LRS-Ubuntu image
1. In 1st terminal launch gazebo: `gazebo <path_to_world>/fei_lrs_gazebo.world`

    *NOTE: If you only see boxes in your simulation, or your simulation is missing the drone go to section [GIT-LFS](#git-lfs)*

2. In 2nd terminal launch ArduPilot SITL: 
```
cd ardupilot/ArduCopter
sim_vehicle.py -f gazebo-iris --console -l 48.15084570555732,17.072729745416016,150,0
```
3. Launch mavros `ros2 run mavros mavros_node --ros-args -p fcu_url:=udp://127.0.0.1:14551@14555`

## Simple takeoff and position control in GUIDED mode

1. Set mode.
2. Arm. 
3. Take off. 
4. Position control by waypoints.

```
ros2 service call /mavros/set_mode mavros_msgs/srv/SetMode "{base_mode: 0, custom_mode: GUIDED}"
ros2 service call /mavros/cmd/arming mavros_msgs/srv/CommandBool "{value: True}"
ros2 service call /mavros/cmd/takeoff mavros_msgs/srv/CommandTOL "{min_pitch: 0, yaw: 90, altitude: 2}"

ros2 topic pub /mavros/setpoint_raw/local mavros_msgs/msg/PositionTarget '{header: {stamp: {sec: 0, nanosec: 0}, frame_id: "",}, coordinate_frame: 1, type_mask: 0, position: {x: 0.0, y: 0.0, z: 0.0}, velocity: {x: 0.0, y: 0.0, z: 0.0}, acceleration_or_force: {x: 0.0, y: 0.0, z: 0.0}, yaw: 0.0, yaw_rate: 0.0}'
```

In the last command you need to set coordinate_frame and type_mask.
Refer to mavlink manual, that will be used in the class often.

https://mavlink.io/en/messages/common.html#POSITION_TARGET_LOCAL_NED

## Git LFS
If you are experiencing problems with loading the simulation, *(no warehouse, only boxes, no drone)*, the issue is likely that you don't have the necessary model files. This is caused by the way GitHub handles large files (over 100MB). To fix this problem:

0. Make sure you have Git LFS installed
```
sudo apt install git-lfs
```
You will probably also need a GitHub account. In some of the following steps, you may be prompted to enter your email and password. 

If this doesn't work *(password authentification was removed by github)*, you may need to create or use your [personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).
1. Enable Git LFS
```
cd <path_to_repository>/LRS-FEI #most likely ~/LRS-FEI
git lfs install
```
2. Now you generally have two options how to continue - pick whichever you prefer. 

    *IMPORTANT: both of these methods will ERASE any changes you have done inside LRS-FEI! Make sure to backup anything important (stash, hard copy, ...).* 
    <ol type="a">
    <li>Delete the repository and clone it again.
    
    ```
    cd ..
    rm -rf LRS-FEI
    git clone https://github.com/KocurMaros/LRS-FEI.git
    ```
    </li>
    <li>Reset and pull large files</li>

    ```
    git reset --hard 
    git lfs pull
    git lfs checkout
    ```
    </ol>
## Links 

https://qiao.github.io/PathFinding.js/visual/

https://github.com/shkolovy/path-finder-algorithms

https://drive.google.com/drive/folders/1QdG5tw1aGTgOuVNYAXl9BhDGObsHb8TW?usp=sharing
