# ROS 安装
## ROS 简介
ROS是一个开放的标准平台，提供了一系列的软件框架和工具以帮助如阿健开发者创建机器人应用软件，主要的目标是为机器人研究和开发提供代码复用的支持，提供了C++和Python两种主要的编程接口，提供了大量的包管理系统，开发者能够方便的开发、安装和管理应用包。
## ROS 安装过程
- 配置Ubuntu软件仓库
这个操作一般是默认的，不需要进行修改

- 添加source.list<br>
这个操作的目的是使得能够接受到来自Packages.ros.org的软件。
<pre>sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'</pre>
![1.2](https://github.com/Chenqt5/ES2016_14353028/blob/master/Lab5/ROS1.png)

- 添加keys<br>
<pre>sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.NET:80 --recv-key 0xB01FA116</pre>
![1.3](https://github.com/Chenqt5/ES2016_14353028/blob/master/Lab5/ROS2.png)

- 安装<br>
首先要确保软件包是最新的
<pre>sudo apt-get update</pre>
![1.4](https://github.com/Chenqt5/ES2016_14353028/blob/master/Lab5/ROS3.png)
然后安装完整版的程序包，这里包括了ROS核心组件、rqt、rviz、机器人通用库、2D\3D模拟器、导航以及2D\3D感知
<pre>sudo apt-get install ros-hydro-desktop-full</pre>
![1.4](https://github.com/Chenqt5/ES2016_14353028/blob/master/Lab5/ROS4.png)

- 初始化rosdep<br>
在使用之前需要进行初始化
<pre>sudo rosdep init
rosdep update</pre>
![1.5](https://github.com/Chenqt5/ES2016_14353028/blob/master/Lab5/ROS5.png)
![1.5](https://github.com/Chenqt5/ES2016_14353028/blob/master/Lab5/ROS6.png)
- 环境配置<br>
为了方便，可以设置在每次打开终端的时候就让系统自动配置好ROS环境变量
<pre>echo "source /opt/ros/hydro/setup.bash" >> ~/.bashrc
source ~/.bashrc</pre>
![1.6](https://github.com/Chenqt5/ES2016_14353028/blob/master/Lab5/ROS7.png)

- 安装rosinstall<br>
ros是一个与发行RPS版本无关的常用命令行工具，只需要一个命令就可以轻松的下载ROS程序包所需要的资源树
<pre>sudo apt-get install python-rosinstall</pre>
![1.7](https://github.com/Chenqt5/ES2016_14353028/blob/master/Lab5/ROS8.png)

## 实验结果
通过其中一条ROS指令进行测试发，发现是由相应的输出，证明ROS已经安装成功了。
![result](http://i.imgur.com/uKmayht.png)