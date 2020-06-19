# Development and Testing of a Deep Learning based Bin Picking System using ROS
Aubo i5 Dual Arm Collaborative Robot - RealSense D435 - 3D Object Pose Estimation - ROS

A package for detecting and estimating the 6-DoF pose of known objects using a novel architecture and data generation pipeline using the state of the art algorithm DOPE in Aubo i5 collaborative robot with Intel Realsense D435i camera. The neural network consists several steps to reﬁne and estimates of the 2D coordinates of projected vertices of each object’s 3D bounding cuboid. These vertices are then used to output the ﬁnal pose using PnP, with known camera intrinsic and object dimensions. The neural network trained only on photorealistic data can attain state of the art results compared with a neural network trained on real world data and  resulting poses are with much needed accuracy for robotic pick and place.


<img src="https://github.com/avinashsen707/AUBOi5-D435-ROS-DOPE/blob/master/results/IMG_20200309_191924_212.jpg" width="80%" height="80%">

__[[Demonstrarion of the Developed Bin Picking system : Link]](https://youtu.be/IGGV9dj_fZs)__

<img src="https://github.com/avinashsen707/AUBOi5-D435-ROS-DOPE/blob/master/results/GIF-200619_132514.gif" width="70%" height="70%">

### Development Environment
- __Ubuntu 16.04.2__
- __ROS Kinetic__

- __Ubuntu 18.04.1__
- __ROS Melodic__
***

__[[Running_Demo_Video]](https://youtu.be/kFdxqJA0BTg)__

<img src="https://github.com/avinashsen707/AUBOi5-D435-ROS-DOPE/blob/master/results/Front%20Screenshot%20from%202020-03-10%2000-47-35.png" width="80%" height="80%">


<img src="https://github.com/avinashsen707/AUBOi5-D435-ROS-DOPE/blob/master/results/Back%20Screenshot%20from%202020-03-10%2000-48-08.png" width="80%" height="80%">

__[[Pose_Demo_Video]](https://youtu.be/cB5miHZ5tPc)__

***

### How can you get the datasets object in the real world
 
In __[Datasets_obj](https://github.com/avinashsen707/AUBOi5-D435-ROS-DOPE/tree/master/ycb%20objects)__  folder you can printing the object texture onto a box of the exact size.

For more, Download the __[Dataset](https://research.nvidia.com/publication/2018-06_Falling-Things)__ and __[train](https://github.com/avinashsen707/AUBOi5-D435-ROS-DOPE/blob/master/dope/scripts/train.py)__ the objects to get respective weights.
***

## Creation of Custom-Dataset-UE4-DOPE

__Please check the [NVIDIA Deep learning Dataset Synthesizer (Synthetic-Data-UE4)](https://github.com/NVIDIA/Dataset_Synthesizer)__

<img src="https://github.com/avinashsen707/AUBOi5-D435-ROS-DOPE/blob/master/results/GIF-200619_202902.gif" width="70%" height="70%">


## STEP 1 - Download the NDDS Documentation

__[NVIDIA Deep learning Dataset Synthesizer (NDDS) Documentation](https://github.com/NVIDIA/Dataset_Synthesizer/blob/master/Documentation/NDDS.pdf)__


## STEP 2 - Installing NDDS
__Windows Specific:__

First, install Visual Studio.
a. If you are installing Visual Studio or Visual Studio Community, use the 2017 version located [here](https://visualstudio.microsoft.com/zh-hans/vs/community/). (Other versions may not be compatible.)

i. We successfully tested NDDS using Visual Studio 2017 version 15.9.

b. When installing Visual Studio, you will need to perform a CUSTOM INSTALL. Make sure the following are selected

* Desktop development with C++
* Latest Windows 10 SDK
* Windows 8.1 SDK (if you are still on Windows 8.1)

Download the following:

a. [Epic's Launcher](https://www.epicgames.com/unrealtournament/download) so that you can install Unreal Engine.

i. Due to Unreal's requirements, please always ensure that you create your directory starting with a letter and not a number.

b. Installation instructions are found here.

1. Let's start with Unreal. Once you have downloaded Epic Launcher, install it and create an Epic account.

2. Once installed start the Launcher, login with your account and go to the Unreal Engine tab on the upper left corner of the Launcher. From here, make sur eyou have Library highlighted and then click the " + " icon.

a. A pull down menu will appear with various engine versions. Please select Version 4.21.0

3. With the engine is installed, start the Editor by pressing the Launch button. You will need to start the Editor at least once so that it sets file associations.
Creating a blank default project is good enough.

4. Close the Editor and Launcher for now.

___

__Linux Specific:__

a. for Unreal Engine, refer to the UE4 website instructions: [https://wiki.unrealengine.com/Building_On_Linux](https://wiki.unrealengine.com/Building_On_Linux)
Note NDDS uses UE version 4.21.0, with respect to the unreal first time setup documentation, use git clone -b 4.21

See also [https://docs.unrealengine.com/en-US/Platforms/Linux/GettingStarted](https://docs.unrealengine.com/en-US/Platforms/Linux/GettingStarted/index.html)

b. Note that `NDDS` currently supports only `Ubuntu 16.04.4 LTS`

c. We successfully tested NDDS using NVIDIA driver versions 387.34 and 390.67

d. If you get this warning, select "More options", then "Skip conversion"

__Installation__
1. Download NDDS:

a. Ensure LFS is installed: [https://help.github.com/articles/installing-git-large-file-storage/](https://help.github.com/en/articles/installing-git-large-file-storage).

Install the NDDS files for the dataset synthesizer.
```
git clone https://github.com/NVIDIA/Dataset_Synthesizer.git
```

2. Navigate to the directory containing the files and find NDDS.uproject. This should be under the \Source sub-directory.

3. Run NDDS.uproject and select "Yes" when it prompts you to rebuild binaries. The compilation will occur behind the scene and open the project wh en
completed.

Note: Nvidia Deep Learning Dataset Synthesizer plugins may only be used within a project (game) -- hosting as engine plugins not yet supported.

***

## STEP 3 - Installing Blender

__Download [[Blender]](https://www.blender.org/)__

<img src="https://github.com/avinashsen707/AUBOi5-D435-ROS-DOPE/blob/master/results/GIF-200619_205101.gif" width="70%" height="70%">

__[How to use the Blender : Link](https://youtu.be/bK2NJmRyP6g)__

Make a 3D model in solidworks or CAD etc.,then import a 3D model in Blender (.stl .dae ...) and export it as a __fbx__ file
then import that __fbx__ file into UE4,  __fbx__ file is work in UE4.

***

## STEP 4 - Run the NDDS

Open the Unreal Editor with the `Dataset_Synthesizer/Source/`__NDDS.uproject__, a default level called TestCapturer will load as indicated at the top left hand corner of the 3D view port. This level has a sample scene with a basic simulation capture set up.

__[How to use the UE4 : Link](https://youtu.be/qrhS-UxqNlQ)__


## STEP 5 - Train the DOPE model
Training code is also provided but not supported - [train.py](https://github.com/avinashsen707/AUBOi5-D435-ROS-DOPE/blob/master/dope/scripts/train.py)

```
python train.py --data ./cube/ --outf cube_1214  --gpuids 0 1 --epochs 120 --loginterval 1 --batchsize 32

```

## DOPE Installing

__Step 1: Download the DOPE code__

    cd ~/catkin_ws/src
    git clone https://github.com/yehengchen/DOPE-ROS-Realsense.git

__Step 2: Install python dependencies__

    cd ~/catkin_ws/src/dope
    pip install -r requirements.txt

__Step 3: Install ROS dependencies__

    cd ~/catkin_ws
    rosdep install --from-paths src -i --rosdistro kinetic
    sudo apt-get install ros-kinetic-rosbash ros-kinetic-ros-comm
    Build

    cd ~/catkin_ws
    catkin_make

__Step 4: Download [the weights](https://drive.google.com/open?id=1DfoA3m_Bm0fW8tOWXGVxi4ETlLEAgmcg) and save them to the `weights` folder, *i.e.*, `~/catkin_ws/src/dope/weights/`.__

***

## ROS Wrapper for Intel® RealSense D435 - Ubuntu 16.04_ROS Kinetic

__Step 1: Install the latest Intel® RealSense™ SDK 2.0__

Install from [Debian Package](https://github.com/IntelRealSense/librealsense/blob/master/doc/distribution_linux.md#installing-the-packages) - In that case treat yourself as a developer. Make sure you follow the instructions to also install librealsense2-dev and librealsense-dkms packages.
OR
Build from sources by downloading the latest Intel® RealSense™ SDK 2.0 and follow the instructions under [Linux Installation](https://github.com/IntelRealSense/librealsense/blob/master/doc/installation.md)

__Step 2: Install the ROS distribution__
Install ROS Kinetic, on Ubuntu 16.04

__Step 3: Install Intel® RealSense™ ROS from Sources__
  
    cd ~/catkin_ws/src/

Clone the latest Intel® RealSense™ ROS from [here](https://github.com/IntelRealSense/realsense-ros/releases) into 'catkin_ws/src/'

    git clone https://github.com/IntelRealSense/realsense-ros.git
    cd realsense-ros/
    git checkout `git tag | sort -V | grep -P "^\d+\.\d+\.\d+" | tail -1`
    cd ..

Make sure all dependent packages are installed. You can check .travis.yml file for reference.
Specifically, make sure that the ros package ddynamic_reconfigure is installed. If ddynamic_reconfigure cannot be installed using APT, you may clone it into your workspace 'catkin_ws/src/' from [here](https://github.com/pal-robotics/ddynamic_reconfigure/tree/kinetic-devel) (Version 0.2.0)

    catkin_init_workspace
    cd ..
    catkin_make clean
    catkin_make -DCATKIN_ENABLE_TESTING=False -DCMAKE_BUILD_TYPE=Release
    catkin_make install
    echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
    source ~/.bashrc

## ROS Wrapper for Intel® RealSense D435 - Ubuntu 18.04_ROS Melodic

* ### The steps are described in bellow documentation
  __[[IntelRealSense -Linux Distribution]](https://github.com/IntelRealSense/librealsense/blob/master/doc/distribution_linux.md)__
  
  ```
  
  sudo apt-key adv --keyserver keys.gnupg.net --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE || sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-key F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE  

  sudo add-apt-repository "deb http://realsense-hw-public.s3.amazonaws.com/Debian/apt-repo bionic main" -u
  
  sudo apt-get install librealsense2-dkms
  
  sudo apt-get install librealsense2-utils
  
  sudo apt-get install librealsense2-dev
  
  sudo apt-get install librealsense2-dbg #(리얼센스 패키지 설치 확인하기)
  
  realsense-viewer
  
  ```
  
* ### Installing Realsense-ros 
  1) __catkin workspace__
  
  ```
  mkdir -p ~/catkin_ws/src
  cd ~/catkin_ws/src/
  ```
  
  2) __Download realsense-ros pkg__
  	
  ```
  git clone https://github.com/IntelRealSense/realsense-ros.git
  cd realsense-ros/
  git checkout `git tag | sort -V | grep -P "^\d+\.\d+\.\d+" | tail -1`
  cd ..
  ```
  
  3) __Download ddynamic_reconfigure__
  
  ```
  cd src
  git clone https://github.com/pal-robotics/ddynamic_reconfigure/tree/kinetic-devel
  cd ..
  ```
  
  4) __Pkg installation__
  
  ```
  catkin_init_workspace
  cd ..
  catkin_make clean
  catkin_make -DCATKIN_ENABLE_TESTING=False -DCMAKE_BUILD_TYPE=Release
  catkin_make install
  echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
  source ~/.bashrc
  ```
  

  5) __Run D435 node__
  ```
  roslaunch realsense2_camera rs_camera.launch
  ```
  
  6) __Run rviz testing__

  ```
  rosrun rviz rvzi
  Add > Image to view the raw RGB image
  ```



***
## Running

__1. Start ROS master__

```
cd ~/catkin_ws
source devel/setup.bash
roscore
```

__2. Start camera node (or start your own camera node)__
    
Realsense D435 & usb_cam node (./dope/config/config_pose.yaml):    

``` 
topic_camera: "/camera/color/image_raw"            #"/usb_cam/image_raw"
topic_camera_info: "/camera/color/camera_info"     #"/usb_cam/camera_info"
``` 

Start camera node:
   
``` 
roslaunch realsense2_camera rs_rgbd.launch  # Publishes RGB images to `/camera/color/image_raw`
```

__3. Start DOPE node__
    
```
roslaunch dope dope.launch [config:=/path/to/my_config.yaml]  # Config file is optional; default is `config_pose.yaml`
```

__4. Start rviz node__
```
rosrun rviz rviz
```

## Debugging

* The following ROS topics are published (assuming `topic_publishing == 'dope'`):
```
    /dope/webcam_rgb_raw       # RGB images from camera
    /dope/dimension_[obj_name] # dimensions of object
    /dope/pose_[obj_name]      # timestamped pose of object
    /dope/rgb_points           # RGB images with detected cuboids overlaid
    /dope/detected_objects     # vision_msgs/Detection3DArray of all detected objects
    /dope/markers              # RViz visualization markers for all objects
```
    *Note:* `[obj_name]` is in {cracker, gelatin, meat, mustard, soup, sugar}

* To debug in RViz, run `rviz`, then add one or more of the following displays:
    
    * `Add > Image` to view the raw RGB image or the image with cuboids overlaid
    * `Add > Pose` to view the object coordinate frame in 3D.
    * `Add > MarkerArray` to view the cuboids, meshes etc. in 3D.
    * `Add > Camera` to view the RGB Image with the poses and markers from above.
    

## Citing

If you use this tool in a research project, please cite as follows:
```
@inproceedings{tremblay2018corl:dope,
 author = {Jonathan Tremblay and Thang To and Balakumar Sundaralingam and Yu Xiang and Dieter Fox and Stan Birchfield},
 title = {Deep Object Pose Estimation for Semantic Robotic Grasping of Household Objects},
 booktitle = {Conference on Robot Learning (CoRL)},
 url = "https://arxiv.org/abs/1809.10790",
 year = 2018
}
```
## License

Copyright (C) 2018 NVIDIA Corporation. All rights reserved. Licensed under the [CC BY-NC-SA 4.0 license](https://creativecommons.org/licenses/by-nc-sa/4.0/legalcode).

## Reference

__[DOPE](https://github.com/NVlabs/Deep_Object_Pose) - Deep Object Pose Estimation (DOPE) – ROS inference (CoRL 2018)__
    
