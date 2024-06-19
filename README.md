_A personal guide to refer while working on ROS `Noetic` and ROS2 `Humble`_

## ROS Noetic

### Manage your Environment 

First, source the ROS Noetic environment setup file. It's recommended to add this to your `.bashrc` file for automatic sourcing:
```bash
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

> [!TIP]
> Alternatively, you can choose to run this command on every new shell you open to have access to the ROS commands. This process allows you to install several ROS distributions (e.g. indigo and kinetic) on the same computer and switch between them.
> ```bash
> source /opt/ros/kinetic/setup.bash
> ```

### Create a ROS Workspace

1. Create a new workspace:
    ```bash
    mkdir -p workspace_name/src
    cd workspace_name
    catkin_make
    ```
    
2. Source the workspace setup file:
    ```bash
    source devel/setup.bash
    ```

### Create a ROS Package

1. Navigate to the `src` directory within your workspace:
    ```bash
    cd src
    ```
    
2. Create a new package:
    ```bash
    catkin_create_pkg package_name std_msgs rospy roscpp
    ```
    
3. Build the workspace:
    ```bash
    cd ..
    catkin_make
    ```
    
4. Source the setup file again:
    ```bash
    source devel/setup.bash
    ```

5. You can view first-order dependencies in `package.xml`:
    ```xml
    <build_depend>roscpp</build_depend>
    <build_depend>rospy</build_depend>
    <build_depend>std_msgs</build_depend>
    ```
    
> [!NOTE]
> Your workspace structure should look like this:
> ```
>  workspace_folder/        
>    src/                  
>      CMakeLists.txt      
>      package_1/
>        include
>        src
>        CMakeLists.txt    
>        package.xml        
>      ...
>      package_n/
>        include
>        src
>        CMakeLists.txt     
>        package.xml       


### Create a ROS Node

1. Inside your package, create a `scripts` directory:
    ```bash
    cd src/package_name
    mkdir scripts
    cd scripts
    ```
    
2. Create a new Python node:
    ```bash
    touch node_name.py
    chmod +x node_name.py
    ```

3. Add additional dependencies to `package.xml`:
    ```xml
    <build_depend>opencv</build_depend>
    <build_depend>python3-numpy</build_depend>
    <build_export_depend>opencv</build_export_depend>
    <build_export_depend>python3-numpy</build_export_depend>
    <exec_depend>opencv</exec_depend>
    <exec_depend>python3-numpy</exec_depend>
    ```

4. Modify CMakeLists.txt to install the Python node:
    ```cmake
    catkin_package(
      CATKIN_DEPENDS roscpp rospy std_msgs
    )
    
    catkin_install_python(PROGRAMS
      scripts/node_name.py
      DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
    )
    ```
    
5. Go to the workspace and build it:
    ```bash
    cd ../../..
    catkin_make
    ```

### Run ROS Node

1. Make sure that a `roscore` is up and running:
   ```bash
   roscore
   ```

2. Source the workspace's `setup.sh` file
   ```bash
   cd workspace_name
   source devel/setup.bash
   ```

3. Run the node!
   ```bash
   rosrun workspace_name node_name.py 
   ```
   
> [!IMPORTANT]
> `roscore` is the first thing you should run when using ROS.
> ```bash
> roscore
> ```


<!---

> [!NOTE]
> Useful information that users should know, even when skimming content.

> [!IMPORTANT]
> Key information users need to know to achieve their goal.

> [!WARNING]
> Urgent info that needs immediate user attention to avoid problems.

> [!CAUTION]
> Advises about risks or negative outcomes of certain actions.

-->
