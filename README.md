
##DOL配置
###Description
>The distributed operation layer (DOL) is a software development framework to program parallel applications. The DOL allows to specify applications based on the Kahn process network model of computation and features a simulation engine based on SystemC. Moreover, the DOL provides an XML-based specification format to describe the implementation of a parallel application on a multi-processor systems, including binding and mapping.
>
###How to install
1.`安装必要环境`
>    $ sudo apt-get update  
    $ sudo apt-get install ant  
    $ sudo apt-get install openjdk-7-jdk  
    $ sudo apt-get install unzip  

2.`文件下载`
>sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz  
sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip  

3.`解压文件`
>$	mkdir dol  
$	unzip dol_ethz.zip -d dol  
$	tar -zxvf systemc-2.3.1.tgz  

4.`编译systemc`
>$	cd systemc-2.3.1  
$	mkdir objdir  
$	cd objdir  
$	../configure CXX=g++ --disable-async-updates  
$	sudo make install  
$	pwd  

5.`编译dol`  
进入刚刚dol的文件夹
`$	cd ../dol` 
 
修改build_zip.xml文件  
找到下面这段话，就是说上面编译的systemc位置在哪里，  
`<property name="systemc.inc" value="YYY/include"/>`  `<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>`
把YYY改成上页pwd的结果（注意，对于  64位 系统的机器，lib-linux要改成lib-linux64）  

然后是编译  
`$	ant -f build_zip.xml all`  
若成功会显示build successful  

接着可以试试运行第一个例子  
>$	cd build/bin/main  
$	ant -f runexample.xml -Dnumber=1

6.`Run example1`
>$ cd build/bin/main  
 $ ant -f runexample.xml -Dnumber=1
 
###Cogitate
配置环境而已~  
没什么特别难的地方，跟着步骤一步一步来就没问题了。  
挺有意思的，后面加油做~！

