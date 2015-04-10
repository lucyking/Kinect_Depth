# Kinect_Depth

This code using **Raspberry Pi 2**+OpenNI+Sensor to outpu Kinect's depth data in text format.(**Raspberry Pi B+** not support so far).

0.In OpenNI&&Sensor source, modify /Platform/Linux/Build/Common/Platform.Arm:
        CFLAGS += -march=armv7-a -mfpu=neno #-mfloat-abi=softfp -mcpu=cortex-a8 -mtune=cortex-A7 
        ... ...
Because Pi 2 support hf.

1.Build and install [OpenNI](https://github.com/OpenNI/OpenNI)&&[Sensor](https://github.com/ruedigerH2/SensorKinect) according their README instroduction.   



2.Doxygen is necessary other ways make will fail.Using **apt-get install doxygen** will download 900M+ source.So we can build && install from [doxygen source](https://github.com/doxygen/doxygen).(there should be better meanings,please let me know : )    



3.Editing /usr/etc/primesense/GlobalDefaultsKinect.ini to uncomment the **";UsbInterface=2"** line and change into **"UsbInterface=1"**   



4.Bulid main.cpp:
  g++ -I/usr/include/ni/ -I/usr/include/GL -c main.cpp
  g++ -o main main.o libOpenNI.so   



  
5.**./mian** to run the binnary then get the depth output from Kinect. 

Output format:     
     time>[x,y]:data
     
     time: system uptime
     data: raw depth data,data~[0,2^11]  


ps: main.cpp is modified from OpenNI's SimpleViwer Sample.
    I still fail to generate the video output as on PC(as you see,codes of glutDisplay are commented), any advice is appreciate :-)
