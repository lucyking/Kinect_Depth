# Kinect_Depth
##1.自己搭建开发环境
This code using **Raspberry Pi 2**+OpenNI+Sensor to output Kinect's depth data in text format.(**Raspberry Pi B+** not support so far).

- 0.In OpenNI&&Sensor source, modify /Platform/Linux/Build/Common/Platform.Arm:  

        CFLAGS += -march=armv7-a -mfpu=neno #-mfloat-abi=softfp -mcpu=cortex-a8 -mtune=cortex-A7 
        ... ...

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
##2.自己搭建太麻烦？
好的我把配置好的镜像上传到百度网盘了：[下载链接](http://pan.baidu.com/s/1bI7Em)   
直接用dd命令复刻到SD卡里再启动覆盘子2（无误）就可以了 超级方便有木有！
