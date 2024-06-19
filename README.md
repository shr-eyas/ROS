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

> [!NOTE]
> Your package structure should look like this:


### Create a ROS Package
1. Navigate to the `src` directory within your workspace:
2. Create a new package:
3. Build the workspace:
4. Source the setup file again:
5. You can view first-order dependencies in `package.xml`:

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

> [!IMPORTANT]
> Key information users need to know to achieve their goal.


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
