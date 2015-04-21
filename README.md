# Kinect_Depth
##1.自己搭建开发环境   
这个代码用树莓派2+OpenNI+Sensor来驱动Kinect并获取它的深度信息。树莓派B+及以前的版本是不支持的。【不要问我为什么 我为这事搞了快一个学期 直到树莓派2生产出来- -|||        
- 0.在编译OpenNI和Sensor之前，需要稍微修改一下编译配置：     
   将/Platform/Linux/Build/Common/Platform.Arm某些选项注释掉(因为现在已经支持硬浮点计算了 所以我们就不用软浮点)：    
   CFLAGS += -march=armv7-a -mfpu=neno #-mfloat-abi=softfp -mcpu=cortex-a8 -mtune=cortex-A7       
- 1. 改完了就可以可以按照[OpenNI](https://github.com/OpenNI/OpenNI)和Sensor](https://github.com/ruedigerH2/SensorKinect)的官方README编译和安装了。 
- 2.对的然后你会看到里面有一个选项说doxygen是不一定要装的 但是你会发现不装的话上面的编译会error 然后你就会apt-get install doxygen 接着就发现要下载900M多的文件 啊来让我们大喊一声滚你然后默默地去手动下载编译和安装[doxygen](https://github.com/doxygen/doxygen)
- 


##1.build develop environment by yourself
This code using **Raspberry Pi 2**+OpenNI+Sensor to output Kinect's depth data in text format.(**Raspberry Pi B+** not support so far).

- 0.In OpenNI&&Sensor source, modify /Platform/Linux/Build/Common/Platform.Arm:  

        CFLAGS += -march=armv7-a -mfpu=neno #-mfloat-abi=softfp -mcpu=cortex-a8 -mtune=cortex-A7 
        
Because Pi 2 support hf.

- 1.Build and install [OpenNI](https://github.com/OpenNI/OpenNI)&&[Sensor](https://github.com/ruedigerH2/SensorKinect) according their README instroduction.   



- 2.Doxygen is necessary other ways make will fail.Using apt-get install doxygen will download 900M+ source.So we can build && install from [doxygen source](https://github.com/doxygen/doxygen).  



- 3.Editing /usr/etc/primesense/GlobalDefaultsKinect.ini to uncomment the **";UsbInterface=2"** line and change into **"UsbInterface=1"**   



- 4.Bulid main.cpp: 

        g++ -I/usr/include/ni/ -I/usr/include/GL -c main.cpp    
        g++ -o main main.o libOpenNI.so       
  


  
- 5.run the binnary then get the depth output in shell from Kinect. 

Output format:     
     time>[x,y]:data
     
     time: system uptime
     data: raw depth data,data~[0,2^11]  


ps: main.cpp is modified from OpenNI's SimpleViwer Sample.
    I still fail to generate the video output as on PC(as you see,codes of glutDisplay are commented), any advice is appreciate :-)
    
## 2.too complicated？
ok here is my uploaded img:[links](http://pan.baidu.com/s/1bI7Em)


##2.自己搭建太麻烦？
好的我把配置好的镜像上传到百度网盘了：[下载链接](http://pan.baidu.com/s/1bI7Em)   
直接用dd命令复刻到SD卡里再启动覆盘子2（无误）就可以了 超级方便有木有！
