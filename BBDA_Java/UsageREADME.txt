## 总览

程序源文件和二进制文件在文件夹中，主要有这三个程序：

- BBDA.jar 用来进行单个被试以及批处理
- BBDAManager.jar 用来管理被试信息，生成批处理命令
- Excel2CSV.py 用来进行本目录下所有xlsx文件->csv文件的转换

## BBDA

BBDA 指的是基于单个被试的计算核心方法以及其GUI界面程序
- 双击BBDA.jar 可以运行GUI程序
- CMD中输入： java -jar BBDA.jar 可以运行GUI程序
- GUI程序不接受命令行参数，但是其本质上也是调用了一个核心计算类，并且传入参数进行的计算
- 调用这个计算类进行批处理需要这样写：
java -cp BBDA.jar com.mazhangjing.lab.BBDA.DataProcess "jiangwenyue" "01" "scr" "2018-06-22 10:35:20.868380" "2018-06-22 10:35:25.018380" "2018-06-22 10:53:39.280380" "2018-06-22 10:53:41.380380" "01_jiangwanyue_scr.csv" "01_jiangwanyue_scr_201806221153.log" 
其中 java -cp BBDA.jar com.mazhangjing.lab.BBDA.DataProcess  指的是使用java程序从BBDA.jar包只能够找到DataProcess这个类，并且执行，之后的参数分别是姓名、ID、类别、实验开始和结束的4个时间，Matlab文件地址和平衡板数据地址。其中这两个地址如果不在程序同名文件夹下需要写清楚完整路径。

## BBDAManager

BBDAManager 指的是用来管理被试信息的GUI程序，这里保存了所有的被试信息，点击Batch按钮，并且点击确定可以输出一大段的命令，将这些命令复制到CMD中即可执行批处理。处理后的结果在程序同名文件夹下。BBDAManager的被试数据库采用序列化Java二进制保存，在data.dta文件中。这个程序并不进行批处理，其管理被试信息，进行批处理需要将复制得到的命令使用BBDA.jar 的DataProcess类，传递参数进行处理。BBDA默认的GUI也是这样进行处理的。

## 找不到新版本的问题

程序编写或者DEBUG后，存放在各自文件夹的out目录的artifacts子目录下，找到同名.jar文件，运行，在标题栏或者关于页面可以查看程序以及模块的版本信息。一般而言，这里的版本是最新的。

## 依赖

python 需要 python 3.5以上解释器的安装，需要安装 pandas 包，使用 pip install pandas 安装此包。

java 需要 java 1.8及以上版本的安装，不依赖第三方包。如果使用openjdk/jre而不是oracle的jdk/jre，请下载安装openjfx以运行GUI界面。