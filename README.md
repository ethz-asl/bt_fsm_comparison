# Mobile Manipulation Demo

In this demo a mobile manipulator has to achieve a mobile pick&place task.

The robot is controlled both via a fault-tolerant Finite State Machine and a Behavior Tree.  
The simplest version of the mobile manipulation task is realized also with a sequential design of a FSM.

## Setup

This code was tested on Ubuntu 20.04 with ROS Noetic.

To make sure that dependencies are pulled, run the following command after cloning this repo into a ROS workspace:

```bash
git submodule update --init --recursive
```

System dependencies need to be installed by running:

```bash
./submodules/moma/install_dependencies.sh
```

Finally, the code can be built using:

```bash
catkin build mobile_manip_demo
```

## Run Experiments

The type of task the mobile manipulator can perform, can be defined by the parameter [`experiment`](https://github.com/ethz-asl/bt_fsm_comparison/blob/main/mobile_manip_demo/config/moma_demo.yaml#L38):
* 1: pick the cube2 and place it in the delivery station;
* 2: pick the cube2 and place it in the delivery station but go to recharge the batteries when they are low;
* 3: pick the cube2, place it in the delivery station, then dock the robot but go to recharge the batteries when they are low.

In a first terminal, launch the experiment environment in a gazebo simulation:

```bash
roslaunch mobile_manip_demo run_gazebo.launch
```

Then, the fault tolerant state machine can be launched through

```bash
rosrun mobile_manip_demo fault_tolerant_sm.py
```

the sequential state machine can be launched through

```bash
rosrun mobile_manip_demo sequential_sm.py
```

whereas the behavior tree can be launch through

```bash
rosrun mobile_manip_demo behavior_tree.py
```

## Workspace overview

* the control policies are defined in `src`
* the robot skills are defined in `scripts`

## Media

The video showing the mobile manipulator solving the task while controlled by the three policy representation is available at [this link](https://youtu.be/Z0GAkClVx-I).

The images of the policy representations can be found in the [imgs](https://github.com/ethz-asl/bt_fsm_comparison/tree/main/imgs) folder.

### TODOs

Add instructions to install missing dependencies:

* `catkin_simple`
* apriltag repositories https://github.com/AprilRobotics/apriltag_ros and https://github.com/AprilRobotics/apriltag
* apriltag models for gazebo https://github.com/koide3/gazebo_apriltag
* vgn package from https://github.com/ethz-asl/vgn
