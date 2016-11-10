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