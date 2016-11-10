## ROS下的Cartographer安装及配置  
From：14M2 刘锦明 14353200

#一：Cartographer安装

> 主要参考网站：[http://www.cnblogs.com/hitcm/p/5939507.html](http://www.cnblogs.com/hitcm/p/5939507.html)

##0. 安装所有依赖项  
使用以下代码安装Cartographer所需要的所有依赖项：  

>$ sudo apt-get install -y google-mock libboost-all-dev  libeigen3-dev libgflags-dev libgoogle-glog-dev liblua5.2-dev libprotobuf-dev  libsuitesparse-dev libwebp-dev ninja-build protobuf-compiler python-sphinx  ros-indigo-tf2-eigen libatlas-base-dev libsuitesparse-dev liblapack-dev  

##1. 安装ceres solver

1.  `$ git clone https://github.com/hitcm/ceres-solver-1.11.0.git`
2.  `$ cd ceres-solver-1.11.0`
3.  `$ mkdir build`
4.  `$ cd build`
5.  `$ cmake ..`
6.  `$ make –j3`
7.  `$ make test`
8.  `$ sudo make install`

成功测试截图：  
![](https://github.com/liujm23/ES2016_14353200/raw/pngs/car1.png)  

##2. 安装Cartographer
1. `$ git clone https://github.com/hitcm/cartographer.git`
2. `$ cd cartographer`
3. `$ mkdir build`
4. `$ cd build`
3. `$ cmake .. -G Ninja`
4. `$ ninja`
5. `$ ninja test`
6. `$ sudo ninja install`

成功测试截图：  
![](https://github.com/liujm23/ES2016_14353200/raw/pngs/car2.png)  

##3. 安装cartographer_ros
1. `$ cd catkin_ws/src`
2. `$ git clone https://github.com/hitcm/cartographer_ros.git`
3. `$ cd ..`
4. `$ catkin_make`

#二：Cartographer运行及结果
1.在下面的地址中下载数据包
>2d数据，500M左右，下载好放到ubuntu下：  
>https://storage.googleapis.com/cartographer-public-data/bags/backpack_2d/cartographer_paper_deutsches_museum.bag  
>
>3d数据，8G左右，下载好放到ubuntu下：  
>https://storage.googleapis.com/cartographer-public-data/bags/backpack_3d/cartographer_3d_deutsches_museum.bag
>  

2.使用以下命令运行数据包  

`$ roslaunch cartographer_ros demo_backpack_2d.launch bag_filename:=${HOME}/Downloads/cartographer_paper_deutsches_museum.bag`  

`$ roslaunch cartographer_ros demo_backpack_3d.launch bag_filename:=${HOME}/Downloads/cartographer_3d_deutsches_museum.bag`  

测试结果（这里暂时只测试了2d结果）：  
![](https://github.com/liujm23/ES2016_14353200/raw/pngs/car3.png)  

#三：实验心得体会
Cartographer是一个非常非常牛逼的实时同步定位与制图库，开发人员可以用这个库实现二维与三维定位及制图功能。  
根据上网插到的资料，我们可以发现，Cartographer制图与定位的过程跟我们在自己房间里绘制平面图和定位的过程很像：  
1. 站在房间中央，在地图上画一个X来表示当前所在的位置。   
2. 用激光测距仪测量当前位置到一面墙的距离，在地图上画一条线来表示那面墙。  
3. 对当前位置所能见到的所有墙重复步骤2，直到把所有墙都画出来。  
4. 移动的新的位置之后，再次测量到墙面的距离就可以确定你的新位置。  
5. 不断重复前面的过程，就可以制作出一个地图。  

说实话，我根本不敢想象自己能够帮助这个项目并不断完善这个项目，我只希望自己能够读懂这一个项目的代码，并且能够利用这个库来帮助自己实现一些功能，虽然当前来看，也是可望不可即的一个目标呀！但是，加油，找些时间来认真分析分析吧。