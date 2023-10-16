# ROS2 inside dev Container

This package will get you set up using ROS2 with VSCode as your IDE.

## Steps

- [ROS2 inside dev Container](#ros2-inside-dev-container)
  - [Steps](#steps)
  - [Prerequisites](#prerequisites)
  - [1. Setup VSCode ROS2 Workspace Template](#1-setup-vscode-ros2-workspace-template)
  - [1.1 Setup template for ROS2](#11-setup-template-for-ros2)
    - [1.1.1 Clone the repository](#111-clone-the-repository)
    - [1.1.2 Modify the Dockerfile](#112-modify-the-dockerfile)
  - [2. Open the workspace in VSCode using Dev Containers](#2-open-the-workspace-in-vscode-using-dev-containers)
  - [2.1. Verify ROS2 installation](#21-verify-ros2-installation)
  - [4 References](#4-references)

## Prerequisites

- Ubuntu 22.04 (installed previously)
- Docker (installed previously)
- Visual Studio Code (installed previously)
- Remote - Containers extension (installed previously)

## 1. Setup VSCode ROS2 Workspace Template

## 1.1 Setup template for ROS2 

### 1.1.1 Clone the repository

Clone the following repository to your local machine:

```bash

cd ~ # Navigate to your home directory (or any other directory of your choice)
## Clone the repository to your local machine (humble branch)
git clone https://github.com/SESASR-Course/vscode_ros2_workspace.git -b humble
```

### 1.1.2 Modify the Dockerfile

Open the ```vscode_ros2_workspace/.devcontainer/Dockerfile``` in the repository and modify the first line:

```bash
FROM althack/ros2:humble-devel  
```

into :

```bash
FROM andreaostuni/ros2:humble-gazebo-arm
```

This will install ROS2 with Gazebo and other dependencies.

After this step and go to [2. Open the workspace in VSCode using Dev Containers](#2-open-the-workspace-in-vscode-using-dev-containers)

## 2. Open the workspace in VSCode using Dev Containers

Open the ```vscode_ros2_workspace``` folder in VSCode (File -> Open Folder).

The first time you open the folder in VSCode, you will be prompted to reopen the folder in a container.

![reopen_in_container](/dual_boot/images/open_in_dev_cont.png)

Click on **Reopen in Container** to open the folder in a container.

If you don't see the pop-up, click on the little green square in the bottom left corner, which should bring up the container dialog

![template_vscode_bottom](/dual_boot/images/template_vscode_bottom.png)

In the dialog, select ***"Remote Containers: Reopen in container"*** or press ```Ctrl + Shift + P``` and type ***"Remote Containers: Reopen in container"***

VSCode will build the dockerfile inside of .devcontainer for you. If you open a terminal inside VSCode (Terminal->New Terminal), you should see that your username has been changed to ros, and the bottom left green corner should say "Dev Container" it may take a few minutes to build the first time.

![template_container](/dual_boot/images/template_container.png)

Congratulations! You are now running ROS2 inside a container!

## 2.1. Verify ROS2 installation

To verify the installation, open a terminal inside VSCode (Terminal->New Terminal) and run the following command:

```bash
ros2 topic list
```

You should see the following output:

```bash
/parameter_events
/rosout
```

## 4 References

- [VSCode ROS2 Workspace Template](https://github.com/athackst/vscode_ros2_workspace)
- [ROS2 docker images](https://hub.docker.com/r/althack/ros2)
