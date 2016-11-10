# ROS 安装
## ROS 简介
ROS是一个开放的标准平台，提供了一系列的软件框架和工具以帮助如阿健开发者创建机器人应用软件，主要的目标是为机器人研究和开发提供代码复用的支持，提供了C++和Python两种主要的编程接口，提供了大量的包管理系统，开发者能够方便的开发、安装和管理应用包。
## ROS 安装过程
- 配置Ubuntu软件仓库
这个操作一般是默认的，不需要进行修改

- 添加source.list<br>
这个操作的目的是使得能够接受到来自Packages.ros.org的软件。
<pre>sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'</pre>
![1.2](http://oeoh8qniz.bkt.clouddn.com/Lab5/ROS1.png)

- 添加keys<br>
<pre>sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.NET:80 --recv-key 0xB01FA116</pre>
![1.3](http://oeoh8qniz.bkt.clouddn.com/Lab5/ROS2.png)

- 安装<br>
首先要确保软件包是最新的
<pre>sudo apt-get update</pre>
![1.4](http://oeoh8qniz.bkt.clouddn.com/Lab5/ROS3.png)
然后安装完整版的程序包，这里包括了ROS核心组件、rqt、rviz、机器人通用库、2D\3D模拟器、导航以及2D\3D感知
<pre>sudo apt-get install ros-hydro-desktop-full</pre>
![1.4](http://oeoh8qniz.bkt.clouddn.com/Lab5/ROS4.png)

- 初始化rosdep<br>
在使用之前需要进行初始化
<pre>sudo rosdep init
rosdep update</pre>
![1.5](http://oeoh8qniz.bkt.clouddn.com/Lab5/ROS5.png)
![1.5](http://oeoh8qniz.bkt.clouddn.com/Lab5/ROS6.png)
- 环境配置<br>
为了方便，可以设置在每次打开终端的时候就让系统自动配置好ROS环境变量
<pre>echo "source /opt/ros/hydro/setup.bash" >> ~/.bashrc
source ~/.bashrc</pre>
![1.6](http://oeoh8qniz.bkt.clouddn.com/Lab5/ROS7.png)

- 安装rosinstall<br>
ros是一个与发行RPS版本无关的常用命令行工具，只需要一个命令就可以轻松的下载ROS程序包所需要的资源树
<pre>sudo apt-get install python-rosinstall</pre>
![1.7](http://oeoh8qniz.bkt.clouddn.com/Lab5/ROS8.png)

## 实验结果
通过其中一条ROS指令进行测试发，发现是由相应的输出，证明ROS已经安装成功了。
![result](http://oeoh8qniz.bkt.clouddn.com/Lab5/result.png)


# Cartographer安装
## Cartographer简介
Cartographer是一个提供多平台和多传感器配置下完成2D和3D下的SLAM(实时地图构建和定位)系统.同时google也提供了ROS下的集成.
## Cartographer安装
### 安装所有依赖项
<pre>
sudo apt-get install -y google-mock libboost-all-dev  libeigen3-dev libgflags-dev libgoogle-glog-dev liblua5.2-dev libprotobuf-dev  libsuitesparse-dev libwebp-dev ninja-build protobuf-compiler python-sphinx  ros-kinetic-tf2-eigen libatlas-base-dev libsuitesparse-dev liblapack-dev
</pre>

### 安装Ceres solover
- 在Home下新建一个Car文件夹以备后面使用
- 获取cere-solver开源代码
<pre>1. git clone https://github.com/hitcm/ceres-solver-1.11.0.git</pre>
- 在ceres-solover-1.11.0下创建build文件夹，并进入build文件夹
<pre>
2. cd ceres-solver-1.11.0
3. mkdir build
4. cd ceres-solver-1.11.0/build</pre>
- 编译
<pre>5. cmake ..
6. make
</pre>
- 安装
<pre>7. sudo make install</pre>
### 安装cartographer
- 回退到Car文件夹中
- 获取cartographer的开源代码
<pre>
1. git clone https://github.com/hitcm/cartographer.git</pre>
- 在cartographer下创建build文件夹，并进入build文件夹
<pre>
2. cd cartographer
3. mkdir build
4. cd build
</pre>
- 编译并测试
<pre>
5. cmake .. -G Ninja
6. ninja
7. nijia test
</pre>
- 安装
<pre>
8. sudo make install
</pre>
### 安装cartographer_ros
- 回退到Car文件夹
- 安装wstool和rosdep
<pre>
1. sudo apt-get update
2. sudo apt-get install -y python-wstool python-rosdep ninja-build</pre>
- 创建catkin_ws文件夹并初始化src
<pre>
3. mkdir catkin_ws
4. cd catkin_ws
5. wstol init src
</pre>
- 进入src
<pre>
6. cd src
</pre>
- 获取cartographer_ros的源码
<pre>
7. git clone https://github.com/hitcm/cartographer_ros.git</pre>
- 回退到catkin_ws文件夹并运行catkin_make
<pre>
8. cd ..
9. catkin_make
</pre>
## Cartographer测试
- 将2d数据包放置在home文件夹下
- 配置catkin_ws
<pre>
1. source ~/catkin_ws/devel/setup.bash
2. rospack profile</pre>
- 运行数据包
<pre>
3. roslaunch cartographer_ros demo_backpack_2d.launch bag_filename:=${HOME}/Downloads/cartographer_paper_deutsches_museum.bag</pre>
- 结果

![](http://oeoh8qniz.bkt.clouddn.com/Lab5/result1.png?attname=)
![](http://oeoh8qniz.bkt.clouddn.com/Lab5/result2.png?attname=)