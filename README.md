# bioloidsim

I'm pretty new with Linux, so I made a step-by-step video, illustrating how to clone this repo onto a PC 
and use it to execute walking for the BIOLOID in simulation. The video is available at:
https://www.youtube.com/watch?v=kgbSgWs52Lw

Here is the summary:
1. In your existing .bashrc file, change (or add, if necessary) your ROS_IP to the IP address your internet is connected to (which can be found using 'ifconfig').
2. Clone the 'bioloidsim' repo.
3. Convert the 'typea.xacro' file to URDF, and, in that file (typea.urdf), change the robot name from 'typea' to 'bioloid'.
4. Go to the catkin_ws folder, and use the command 'catkin_make' to create the ROS packages 'typea_control', 'typea_description', and 'typea_gazebo'.
5. IMPORTANT: Use the command 'source devel/setup.bash', then close the terminal. (I actually didn't do this at first in the video.)
6. Open a new terminal, and enter 'roslaunch typea_gazebo bioloid_gazebo.launch'. This should open Gazebo automatically, and the BIOLOID robot should appear in the center of the area.
7. After seeing that the controllers are loaded, click the 'Play' button at the lower left of the Gazebo screen. If the robot falls down, the controllers have not loaded properly.
8. Open another terminal, and enter the command 'rosrun typea_gazebo walker_demo.py', which will run the simple commands in that file. 
9. To stop the simulation at any time, click the 'Pause' button at the lower left of the Gazebo screen.
10. To close Gazebo, press Ctrl-C in the first terminal, and the window should close after a few seconds.

To experiment with your own controller, go to the 'typea_gazebo/scripts' folder, and either
1. Modify the 'walker_demo.py' node (more info about the commands used there can be found by looking at the 'typea.py' file in the 'typea_gazebo/src/typea_gazebo' folder) 

2. Or, modify the main walking loop (called 'do_walk', near the end of the file) in the 'walker.py' node, and run that node (use 'rosrun' as shown earlier).

A third option is to dig deeper (i.e., examine or change what is used to execute those high-level actions). For that, take a look at the entire 'walker.py' file.
