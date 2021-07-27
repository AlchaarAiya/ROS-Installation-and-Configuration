# ROS-Installation-and-Configuration

The following repository aims to provide the steps for installing and configuring Robot Operating System (ROS) on Ubuntu. The steps provided are for downloading ROS Melodic which is compatible with Ubuntu 18.04. The document follows by providing the commands needed to install and configure the robot arm package designed by the Smart Methods which is simulated on Gazebo. 

ROS installation commands:
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" >/etc/apt/sources.list.d/ros-latest.list'
sudo apt install curl 
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add –
sudo apt update
sudo apt install ros-melodic-desktop-full
echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
source ~/.bashrc
sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential
sudo apt install python-rosdep
sudo rosdep init
rosdep update


Commands needed to install and configure the robot arm package:
sudo apt-get install ros-melodic-catkin
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/
catkin_make
cd ~/catkin_ws/src
git clone https://github.com/smart-methods/arduino_robot_arm.git 
cd ~/catkin_ws
rosdep install --from-paths src --ignore-src -r -y
sudo apt-get install ros-melodic-moveit
sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui
sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher
sudo apt-get install ros-melodic-ros-controllers ros-kinetic-ros-control
Open a new terminal and complete with the following steps:
sudo nano ~/.bashrc
at the end of the file add the follwing line, noting that the name of your device is correctly written.
(source /home/DIRECTORY-NAME/catkin_ws/devel/setup.bash)
ctrl + o
source ~/.bashrc
roslaunch robot_arm_pkg check_motors.launch

Screenshots of results:
![Screenshot from 2021-06-20 16-41-27](https://user-images.githubusercontent.com/67293724/127146083-222c791b-b5f8-4c99-9722-bd514c36a8df.png)
![Screenshot from 2021-06-20 16-51-29](https://user-images.githubusercontent.com/67293724/127146119-52bb235c-e11f-49fd-92ad-b9f5cf4d363a.png)
