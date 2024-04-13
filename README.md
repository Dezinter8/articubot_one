# Piper simulation

## Pre requirements

- xacro
- joint-state-publisher
- gazebo

Install those using:

```
sudo apt install ros-humble-xacro ros-humble-joint-state-publisher-gui ros-humble-gazebo-ros-pkgs
```

## Setup

### Step 1 (workspace setup)

```
cd ~

mkdir -p piper_ws/src

cd piper_ws/src

git clone https://github.com/Dezinter8/articubot_one.git
```

### Step 2 (build)

```
cd ~/piper_ws

colcon build --symlink-install

source install/setup.bash
```

### Step 3 (run)

1'st terminal (Robot. Will take a while) - Simulation

```
cd ~/piper_ws

source install/setup.bash

ros2 launch articubot_one launch_sim.launch.py world:=./src/articubot_one/worlds/obstacles.world
```

2'nd terminal (Robot) - Controlling robot movement

```
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```

### Step 4 (visualization )

3'rd terminal (best to lauch on dev machine. Can be done on Robot) - Visualization in rviz

On Dev (you need just the config/drive_bot.rviz file):

```
cd ~

mkdir -p piper_ws/src

cd piper_ws/src

git clone https://github.com/Dezinter8/articubot_one.git

rviz2 -d ~/piper_ws/src/articubot_one/config/drive_bot.rviz
```

On robot:

```
rviz2 -d ~/piper_ws/src/articubot_one/config/drive_bot.rviz
```

#### Moving the robot

To move the robot remember that the terminal window used for 2'nd comand has to be an active window.

Moving around:
u i o
j k l
m , .

### Gazebo error

If gazebo is bricked try those comands:

```
pstree
```

```
killall -9 gzserver gzclient
```
