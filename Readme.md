# DOL开发环境配置
## 一、DOL框架描述
The distributed operation layer (DOL) is a framework that enables the (semi-) automatic mapping of applications onto the multiprocessor SHAPES architecture platform. The DOL consists of basically three parts:

- DOL Application Programming Interface: The DOL defines a set of computation and communication routines that enable the programming of distributed, parallel applications for the SHAPES platform. Using these routines, application programmers can write programs without having detailed knowledge about the underlying architecture. In fact, these routines are subject to further refinement in the hardware dependent software (HdS) layer.
- DOL Functional Simulation: To provide programmers a possibility to test their applications, a functional simulation framework has been developed. Besides functional verification of applications, this framework is used to obtain performance parameters at the application level.
- DOL Mapping Optimization: The goal of the DOL mapping optimization is to compute a set of optimal mappings of an application onto the SHAPES architecture platform. In a first step, XML based specification formats have been defined that allow to describe the application and the architecture at an abstract level. Still, all the information necessary to obtain accurate performance estimates is contained.
## 二、DOL安装笔记
### 1. Ubuntu 安装必要的环境
- `$ sudo apt-get update` <br>
- `$ sudo apt-get install ant`
- `$ sudo apt-get install openjdk-7-jdk(or openjdk-8-jdk)`
- `$ sudo apt-get install upzip`
### 2. 下载必要的文件
- 下载systemc-2.3.1.tgz文件
`$ sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz`
- 下载dol_ethz.zip文件
`sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip`
### 3. 解压文件
- 新建dol的文件夹<br>
`$ mkdir dol`
- 将dolethz.zip解压到dol文件夹中
`$ unzip dol_ethz.zip -d dol`
- 解压systemc文件<br>
`$ tar -zxvf systemc-2.3.1.tgz`
### 4. 编译systemc
- 进入systemc-2.3.1<br>
`$ cd systemc-2.3.1`
- 新建临时文件夹<br>
`$ mkdir objdir`
- 进入临时文件夹<br>
`$ cd objdir`
- 运行configure<br>
`$ ../configure CXX=g++ --disable-async-updates`
![result](http://oeoh8qniz.bkt.clouddn.com/result1.png)
- 编译<br>
`$ sudo make install`
 ![result](http://oeoh8qniz.bkt.clouddn.com/result2.png)
- 记录当前的工作路径<br>
`$ pwd`
 ![result](http://oeoh8qniz.bkt.clouddn.com/result3.png)
### 5. 编译dol
- 进入dol文件夹<br>
`$ cd../dol`
- 修改build_zip.xml文件[pwd是前面储存的工作路径]<br>
`<property name="systemc.inc" value="pwd/include"/>` 
`<property name="systemc.lib" value="pwd/lib-linux64/libsystemc.a"/>`
 ![result](http://oeoh8qniz.bkt.clouddn.com/result4.png)
- 编译<br>
`$ sudo ant -f build_zip.xml all`
 ![result](http://oeoh8qniz.bkt.clouddn.com/result5.png)
- 进入build/bin/main<br>
`$ cd build/bin/main`
- 运行第一个例子<br>
`$ sudo ant -f runexample.xml -Dnumber=1`
 ![result](http://oeoh8qniz.bkt.clouddn.com/result6.png)

## 三、实验感想
通过本次实验完成了在Ubuntu下配置DOL框架，然后使用Markdown语言写本次配置的文档。使用的软件是MarkdownPad2,然后使用的图床是使用国内的七牛云在线储存。然后学习了将文档储存到github上进行版本管理。