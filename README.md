# install-robot-arm
first step : https://github.com/razanasb/install_ros 
then Open Terminal
Setup your computer to accept software from packages.ros.org:
sudo sh -c 'echo "deb <a href="http://packages.ros.org/ros/ubuntu" rel="nofollow"> http://packages.ros.org/ros/ubuntu </a> $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
Set up your keys:
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
 Make sure your Debian package index is up-to-date:
sudo apt-get update
Desktop-Full Install:
sudo apt-get install ros-kinetic-desktop-full
 Environment setup:
 echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc source ~/.bashrc
To install tools and other dependencies for building ROS packages, run:
sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential
Before you can use many ROS tools, you will need to initialize rosdep:
sudo apt install python-rosdep
sudo rosdep init 
rosdep update
then Install Arduino IDE
 Download the latest Arduino software on your Ubuntu > https://www.arduino.cc/en/Main/Software
I would recommend downloading Linux 32bits because 64bits can sometimes cause trouble installing on VirtualBox Ubuntu
The file is compressed and you have to extract it in a suitable folder, remembering that it will be executed from there. (Preferable extract it in your Download folder)
 Open the arduino-1.x.x folder just created by the extraction process and spot the install.sh file > right click on it and choose Run in Terminal from the contextual menu.
The installation process will quickly end and you should find a new icon on your desktop
If you don’t find the option to run the script from the contextual menu, you have to open a Terminal window and move into the arduino-1.x.x folder

ls
cd Downloads
cd arduino-1.x.x          // x.x. is your version of Arduino
 Type the command
 ./install.sh
 Wait for the process to finish.
You should find a new icon on your desktop
Including ROS Library
1. You must first create a ROS workspace folder (Normally, this is in the Ubuntu home folder)

mkdir -p ~/catkin_ws/src
2. Now switch to /src folder

cd catkin_ws/src
3. Initialize a new ROS workspace

catkin_init_workspace
4. After initializing catkin workspace, you can build the workspace, switch from /src folder to catkin_ws folder

~/catkin_ws/src cd ..
5. Build the space

~/catkin_ws catkin_make
6. Now you can see a few folders in addition to the src files in your catkin_ws folder (src folder is where our packages are kept)

7. At a Terminal, switch to the home folder and select .bashrc file

cd ~
gedit .bashrc
8. Add the folowing line at the end of .bashrc file (after the last line "source /opt/ros/kinetic/setup.bash")

<strong>source ~/catkin_ws/devel/setup.bash</strong>
9. We source this file in Terminal (copy this same line and paste it in a Terminal)

10. Now when we use any terminal, we can access the package inside this workspace

11. After building the target executable locally, run the following command to install the executable:

catkin_make install
12. You can install rosserial for Arduino by running:

sudo apt-get install ros-kinetic-rosserial-arduino
sudo apt-get install ros-kinetic-rosserial<br>
13. In the steps below, is the directory where the Linux Arduino environment saves your sketches. Typically this is a directory called sketchbook or Arduino in your home directory. e.g cd ~/Arduino/libraries

cd /libraries
rm -rf ros_lib 
rosrun rosserial_arduino make_libraries.py .
14. After restarting your IDE, you should see ros_lib listed under examples



