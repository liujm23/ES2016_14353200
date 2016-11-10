## Linus下的DOL实例分析&编程  
From：14M2 刘锦明 14353200

##一：Example1
**代码分析：**  
>下图是已经修改过后的square.c中的代码  
>原来代码中square_fire()函数对i执行的操作是：i = i * i  
>也就是对输入的数都进行一次平方操作  
 
**修改代码：**  
>我们只需要将该操作改为 i = i * i * i，也即下图所示：  
  
![](https://github.com/liujm23/ES2016_14353200/raw/pngs/dol1.png)   

**显示结果：**  
![](https://github.com/liujm23/ES2016_14353200/raw/pngs/dol2.png)   

##二：Example2
**代码分析：**  
>我们需要观察example2.xml中的代码  
>我们可以发现，这里的 < variable value="3" name="N" />  
>后面有 < iterator variable="i" range="N" />  
>也即这里的层次是通过N这个变量来区分的，原来是3个嵌套，我们只需要改为2个嵌套，即可得到我们想要的结果  

**修改代码：**  
> 将 < variable value="3" name="N" /> 修改为  
>  < variable value="2" name="N" />   

![](https://github.com/liujm23/ES2016_14353200/raw/pngs/dol3.png)    

**显示结果：**  
![](https://github.com/liujm23/ES2016_14353200/raw/pngs/dol4.png)    

##三：实验心得  
这次实验是让我们学习Linus下的DOL实例分析，上课的时候TA已经花了很多时间给我们解释代码了，我们需要做的就是理解TA所说的代码，理解DOL的架构，并根据要求，一步一步地分析代码，最后修改相应的代码即可。  
说实话，这次实验不难，但我们不能仅仅完成了实验就妄自菲薄，而应该深入的去了解DOL实例，最好是能够自己写出一个例子来尝试一下运行，看能不能得到自己想要的结果。