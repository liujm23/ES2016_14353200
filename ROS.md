## Linus下的ROS安装及配置  
From：14M2 刘锦明 14353200

#一：ROS简介
> ROS的全名是Robot Operating System，即机器人操作系统。  
> 
> 机器人操作系统是一个机器人软件平台，它能为异质计算机集群提供类似操作系统的功能。ROS的前身是斯坦福人工智能实验室为了支持斯坦福智能机器人STAIR而建立的交换庭(switchyard)项目。到2008年，主要由威楼加拉吉继续该项目的研发。  
> 
ROS提供一些标准操作系统服务，例如硬件抽象，底层设备控制，常用功能实现，进程间消息以及数据包管理。ROS是基于一种图状架构，从而不同节点的进程能接受，发布，聚合各种信息（例如传感，控制，状态，规划等等）。目前ROS主要支持Ubuntu操作系统。  

#二：ROS配置
> 主要参考网站：[http://wiki.ros.org/jade/Installation/Ubuntu](http://http://wiki.ros.org/jade/Installation/Ubuntu)  
##1-配置Ubuntu的软件源
配置Ubuntu要求允许接受restricted、universe和multiverse的软件源  
  
可以根据下面的链接配置: [https://help.ubuntu.com/community/Repositories/Ubuntu](http://https://help.ubuntu.com/community/Repositories/Ubuntu)  

配置成如下图所示即可，一般情况下，这些配置都是默认的。  
![](https://github.com/liujm23/ES2016_14353200/raw/pngs/ros1.png)  

##2-添加软件源到sources.list

### · 设置软件源
代码如下：  

`$ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu trusty main" > /etc/apt/sources.list.d/ros-latest.list'`  

一旦添加了正确的软件源，操作系统就知道去哪里下载程序，并根据命令自动安装软件。  

###· 设置密钥  
添加key到source中 
`$ sudo apt-key adv --keyserver hkp://pool.sks-keyservers.net --recv-key 0xB01FA116`  

###· 安装
首先保证我们的软件包是最新的,用以下代码检查并更新我们的软件包：   
`$ sudo apt-get update`  

在ROS中有许多不同的函数库和工具，建议是完全安装，也可以根据自己的要求分别安装。完全安装时的工具包括ROS、rqt、可视化环境rviz、通用机器人库robot-generic libraries、2D（如stage）和3D（如Gazebo）仿真环境2D/3D simulators、导航功能包集navigation and 2D/3D（移动、定位、地图绘制、机械臂控制）、感知库perception（如视觉、激光雷达、RGB-D摄像头等）。  
`$ sudo apt-get install ros-indigo-desktop-full`  

###· 初始化rosdep  
rosdep不仅能够使你更方便的安装一些系统依赖程序包，而且ROS的一些主要部件的运行也需要rosdep。  
`$ sudo rosdep init`  
`$ rosdep update`  

###· 安装rosinstall  
rosinstall命令是一个使用的非常频繁的命令，使用这个命令可以轻松的下载许多ROS软件包。  
`$ sudo apt-get install python-rosinstall`

###· 设置环境  
添加ROS的环境变量，这样，当你打开你新的shell时，你的bash会话中会自动添加环境变量。  
`$ echo "source /opt/ros/indigo/setup.bash" >> ~/.bashrc        # 使环境变量设置立即生效`  
`$ source ~/.bashrc`

###· 配置你的ROS环境
注意：当你用像apt这样的软件包安装管理器安装ROS，那么这些软件包用户是没有权利的去编辑的，当创建一个ROS package和处理一个ROS package时，你应该始终选择一个你有权限工作的目录作为工作目录。  

##三：实验心得  
这次实验是让我们学习如何在Linus系统上安装ROS，但是由于我并不知道安装这么一个系统到底有什么用，所以对于这次实验存在很大的疑问。于是我在做实验前对ROS系统先进行了一次详细的深入的了解，明白到ROS系统的强大作用后再来做这个实验就感到充满了动力了！  
在这里我想记录一下ROS的运行机制，希望后面可以帮助自己复习：  

**ROS内核**(roscore)是ROS运行的基础，它里面有参数服务器(parameter server)。一个运行中的ROS有且仅有一个ROS内核，ROS上的一切都依赖于这个内核。ROS底层的通信是通过HTTP完成的，因此ROS内核本质上是一个HTTP服务器，它的地址一般是http://localhost:11311/ ，即本机的11311端口。当需要连接到另一台计算机上运行的ROS时，只要连上该机的11311端口即可。  

**节点** (node)是ROS运行的基本单位，每个节点通常执行整个系统的一小部分功能，比如发送机器人位姿信息、发送控制信息、执行一定的计算任务等。一个机器人的运行，依赖于节点彼此之间的协作。因此，有人说ROS是分布式的。节点之间的通信，依靠消息(message)和服务(service)。  

**消息**是节点对某个主题发布信息的重要途径，订阅了该主题的节点会自动接收到信息。  

**服务**是节点之间除消息以外的另一种通信方式。每个节点都可以创建服务。其它节点可以向该服务发出一个请求(request)，负责这个服务的节点就要相应地返回一个应答(response)。  

After all，我明白到，想要学好ROS，一定一定要参照官方的英文文档！说到底还是要提高自己的英语水平啊，而且最好还是参加一个机器人项目吧！只有这样才能真正理解这个系统~






