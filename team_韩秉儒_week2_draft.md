# Week2 实验报告
姓名：韩秉儒
学号：2024010114
日期：2025.12.11
## 1. 实验任务
本周实验聚焦**Linux 基础操作**、**Python/C++ 开发环境搭建**、**ROS1 Noetic 安装与核心概念入门**、**Turtlesim 仿真控制**及**Launch 文件与多节点通信管理**五大核心模块，具体任务如下：
1. 完成 Linux 系统下文件管理、软件安装、进程监控与终止的基础命令实操
2. 搭建 Python3 与 C++ 编译调试环境，完成基础代码编写与运行调试
3. 验证 ROS1 Noetic 安装完整性，配置 ROS 环境变量并熟悉核心指令
4. 创建 CATKIN 工作空间与功能包，实现 HelloWorld 节点的编写与运行
5. 实现 Turtlesim 小乌龟的键盘控制、rostopic 指令控制及程序自动画圆
6. 编写 Launch 文件实现多乌龟多实例启动，配置独立命名空间，并用 rqt 工具分析系统通信与速度数据

## 2. 实现过程（含主要步骤与截图）
### 2.1 Linux 基础命令练习
#### 2.1.1 文件管理操作
1. 打开终端，执行`mkdir test_dir`在/home目录下创建测试目录，执行`touch test_dir/test.txt test_dir/test2.txt`创建两个测试文件
2. 执行`ls -l test_dir/`查看文件详细信息，执行`mv test_dir/test2.txt ~/`将文件移动到用户根目录
3. 执行`rm test_dir/test.txt`删除单个文件，执行`rm -rf test_dir`删除测试目录及剩余文件
https://github.com/2025BIUHcourse/week2-ros-HHH123860/blob/main/week2zhaopian1/1.jpg?raw=true
https://github.com/2025BIUHcourse/week2-ros-HHH123860/blob/main/week2zhaopian1/2.jpg?raw=true
https://github.com/2025BIUHcourse/week2-ros-HHH123860/blob/main/week2zhaopian1/3.jpg?raw=true
https://github.com/2025BIUHcourse/week2-ros-HHH123860/blob/main/week2zhaopian1/4.jpg?raw=true
https://github.com/2025BIUHcourse/week2-ros-HHH123860/blob/main/week2zhaopian1/5.jpg?raw=true
#### 2.1.2 apt 软件安装
1. 执行`sudo apt update`更新软件源列表，输入管理员密码完成授权
2. 执行`sudo apt install tree`安装树形目录查看工具，执行`sudo apt autoremove`清理无用依赖
3. 执行`tree --version`验证软件安装成功
https://github.com/2025BIUHcourse/week2-ros-HHH123860/blob/main/week2zhaopian1/6.jpg?raw=true
https://github.com/2025BIUHcourse/week2-ros-HHH123860/blob/main/week2zhaopian1/7.jpg?raw=true
https://github.com/2025BIUHcourse/week2-ros-HHH123860/blob/main/week2zhaopian1/8.jpg?raw=true
#### 2.1.3 进程管理
1. 打开火狐浏览器，在终端执行`ps -aux`查看系统所有进程，执行`ps -aux | grep firefox`过滤火狐进程
2. 记录火狐进程的PID，执行`sudo kill -9 [PID]`终止进程，再次执行`ps -aux | grep firefox`验证进程已终止
https://github.com/2025BIUHcourse/week2-ros-HHH123860/blob/main/week2zhaopian1/9.jpg?raw=true
https://github.com/2025BIUHcourse/week2-ros-HHH123860/blob/main/week2zhaopian1/10.jpg?raw=true
### 2.2 Python 与 C++ 编程练习
#### 2.2.1 Python HelloWorld
1. 打开 VSCode，新建文件夹`week2_py_cpp`，在文件夹内新建`hello.py`文件
2. 写入 HelloWorld 代码，保存文件后返回终端，执行`cd week2_py_cpp`进入目录，执行`python3 hello.py`运行程序
https://github.com/2025BIUHcourse/week2-ros-HHH123860/blob/main/week2zhaopian2/11.jpg?raw=true
https://github.com/2025BIUHcourse/week2-ros-HHH123860/blob/main/week2zhaopian2/12.jpg?raw=true
#### 2.2.2 C++ 数字求和程序
1. 在`week2_py_cpp`文件夹内新建`sum.cpp`文件，写入数字求和代码
2. 终端执行`g++ --version`验证编译环境，执行`g++ sum.cpp -o sum_app`编译代码生成可执行文件
3. 执行`./sum_app`运行程序，输入两组不同数字完成求和测试
https://github.com/2025BIUHcourse/week2-ros-HHH123860/blob/main/week2zhaopian2/13.jpg?raw=true
#### 2.2.3 VSCode 调试
1. 在 VSCode 中打开`sum.cpp`文件，安装 C/C++ 插件，点击“运行和调试”按钮
2. 选择“C++(GDB/LLDB)”调试环境，自动生成`launch.json`调试配置文件
3. 在代码的求和逻辑处设置断点，启动调试，查看变量监控面板的数值变化
https://github.com/2025BIUHcourse/week2-ros-HHH123860/blob/main/week2zhaopian2/14.jpg?raw=true
https://github.com/2025BIUHcourse/week2-ros-HHH123860/blob/main/week2zhaopian2/15.jpg?raw=true
### 2.3 ROS1 安装验证
1. 打开终端，执行`roscore`启动 ROS 核心节点，等待节点初始化完成
2. 新开一个终端，执行`rosnode list`查看当前运行的 ROS 节点，执行`rosnode info /rosout`查看核心节点信息
3. 执行`echo $ROS_DISTRO`查看 ROS 版本，执行`echo $ROS_PACKAGE_PATH`查看功能包路径
![](./16.jpg)
![](./17.jpg)
![](./18.jpg)
![](./19.jpg)
### 2.4 CATKIN 工作空间与功能包
#### 2.4.1 工作空间创建与编译
1. 执行`mkdir -p ~/catkin_ws/src`创建工作空间目录，执行`cd ~/catkin_ws`进入工作空间
2. 执行`catkin_make`初始化并编译工作空间，执行`ls`查看生成的目录文件
3. 执行`source devel/setup.bash`配置环境变量，执行`echo $ROS_PACKAGE_PATH`验证路径已更新
![](20.jpg)
#### 2.4.2 功能包创建与 HelloWorld 节点
1. 进入 src 目录，执行`catkin_create_pkg beginner_tutorials roscpp rospy std_msgs`创建功能包
2. 执行`ls beginner_tutorials/`查看功能包目录结构，确认 package.xml 和 CMakeLists.txt 文件存在
3. 在功能包中新建对应目录，编写 Python 或 C++ 版本的 HelloWorld 节点文件，赋予文件可执行权限
4. 返回工作空间执行`catkin_make`编译，执行`rosrun beginner_tutorials [节点文件名]`运行节点
![](./21.jpg)
![](./22.jpg)
### 2.5 Turtlesim 小乌龟基础
#### 2.5.1 键盘控制小乌龟
1. 执行`rosrun turtlesim turtlesim_node`启动小乌龟仿真器，等待仿真窗口弹出
2. 新开终端执行`rosrun turtlesim turtle_teleop_key`，按照终端提示按下方向键控制乌龟前进、后退、转向
3. 控制乌龟移动一段距离后，停止操作观察轨迹
![](./23.jpg)
![](./24.jpg)
#### 2.5.2 rostopic 指令控制
1. 执行`rostopic list`查看当前话题列表，执行`rostopic info /turtle1/cmd_vel`查看速度话题信息
2. 执行`rostopic pub -r 10 /turtle1/cmd_vel geometry_msgs/Twist "{linear: {x: 2.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 1.0}}"`发布持续速度指令
3. 等待乌龟运动 5 秒后，按下 Ctrl+C 终止指令发布
![](./25.jpg)
#### 2.5.3 程序控制小乌龟画圆
1. 在 beginner_tutorials 功能包的 scripts 目录下新建乌龟画圆控制文件
2. 编写控制代码，保存后执行`chmod +x [文件名]`赋予可执行权限
3. 执行`rosrun beginner_tutorials [文件名]`启动控制节点，观察小乌龟的运动轨迹
4. 执行`rostopic echo /turtle1/cmd_vel`查看节点发布的速度数据
![](./26.jpg)
![](./27.jpg)
### 2.6 多乌龟 launch + rqt 工具分析
#### 2.6.1 编写 launch 文件
1. 在 beginner_tutorials 功能包中新建`launch`目录，在目录内新建`multi_turtle.launch`文件
2. 写入多乌龟启动配置代码，配置不同命名空间，保存文件
![](./28.jpg)
#### 2.6.2 启动多乌龟并分别控制
1. 执行`roslaunch beginner_tutorials multi_turtle.launch`启动多乌龟实例，等待两个仿真窗口弹出
2. 执行`rostopic list`查看带命名空间的话题列表，确认每个乌龟的 cmd_vel 话题独立
3. 执行`rostopic pub -r 10 /turtle1/turtle1/cmd_vel [速度参数]`控制第一只乌龟，执行`rostopic pub -r 10 /turtle2/turtle1/cmd_vel [速度参数]`控制第二只乌龟
![](./29.jpg)
![](./30.jpg)
![](./31.jpg)
#### 2.6.3 rqt 工具分析
1. 执行`rqt_graph`打开节点通信图工具，调整视图大小，查看节点与话题的关联关系
2. 执行`rqt_plot /turtle1/turtle1/cmd_vel/linear/x /turtle2/turtle1/cmd_vel/linear/x`打开速度绘图工具，观察两只乌龟的线速度曲线
3. 持续监控 10 秒后，保存 rqt_graph 和 rqt_plot 的界面
![](./32.jpg)
![](./33.jpg)
![](./34.jpg)
## 3. 遇到的问题与解决方法
1. **问题**：catkin_make 编译功能包时，提示“找不到 roscpp 依赖”
    **解决方法**：打开功能包的 package.xml 文件，补充`<build_depend>roscpp</build_depend>`、`<exec_depend>roscpp</exec_depend>`依赖项；打开 CMakeLists.txt 文件，添加`find_package(catkin REQUIRED COMPONENTS roscpp rospy std_msgs)`配置，保存后重新执行 catkin_make
2. **问题**：rosrun 执行 Python 节点时，终端提示“Permission denied”（权限不足）
    **解决方法**：在终端进入节点文件所在目录，执行`chmod +x [节点文件名].py`为文件添加可执行权限，同时检查文件开头是否添加`#!/usr/bin/env python3`解释器声明，确认无误后重新运行节点
3. **问题**：多乌龟 launch 启动后，执行 rostopic pub 指令无法控制乌龟，提示“话题不存在”
    **解决方法**：通过`rostopic list`确认话题的完整路径（带命名空间），修正指令中的话题名称为`/[命名空间]/turtle1/cmd_vel`，同时检查 launch 文件中命名空间配置是否正确，重新发布指令完成控制
4. **问题**：VSCode 调试 C++ 代码时，无法命中断点，提示“找不到可执行文件”
    **解决方法**：检查 launch.json 中`program`字段的路径是否指向编译后的可执行文件，重新执行 g++ 编译生成可执行文件，确保路径配置准确后重启调试
## 4. 总结与心得
通过本周实验，我全面掌握了 Linux 终端的核心操作，从文件目录管理到软件安装、进程管控，能够熟练运用各类基础指令完成系统操作；成功搭建了 Python3 与 C++ 的开发调试环境，掌握了 VSCode 断点调试的核心流程；完成了 ROS1 Noetic 的环境验证与配置，理解了 ROS 工作空间、功能包、节点的层级关系与通信逻辑；实现了 Turtlesim 小乌龟的多模式控制，从手动键盘控制到指令发布，再到程序自动控制，深入理解了 ROS 话题通信机制；同时学会了编写 Launch 文件实现多节点批量启动，利用命名空间实现节点隔离，借助 rqt 工具直观分析系统通信拓扑与数据曲线。


实验中遇到的编译依赖缺失、文件权限不足、话题路径错误、调试配置异常等问题，让我养成了先排查配置文件、再验证指令路径、最后检查权限依赖的问题解决思路，大幅提升了嵌入式开发环境下的问题定位与修复能力，为后续复杂 ROS 项目开发积累了宝贵的实操经验。














