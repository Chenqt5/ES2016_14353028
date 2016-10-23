# DOL
## 实验过程
### Mission One
这里任务是将三个square模块修改成两个，那么只要修改example2.xml代码中，将迭代的次数修改成两次就可以了，这样就只定义了两个模块，然后只有三个通道
### Mission Two
这里任务要修改example，使得处理模块输出的是三次方而不是二次方，那么只要在square.c修改处理模块的功能函数，将i = i * i改成i = i * i * i就可以输出三次方
## 实验结果

### Mission One
![mission1](http://i.imgur.com/YZ8Ig2z.png)

### Mission Two
![mission2](http://i.imgur.com/FsSw4L4.png)

## 实验感想
- 通过本次实验，复习了一下之前在操作系统上学习到的生产者和消费者模型，并了解了在这两个中间加入处理模块的模型
- 通过看一些源代码，知道了怎么构建一个模型，很多都是分成多个模块，再根据xml设置，定义好输入输出将各个模块链接起来，形成一个整体