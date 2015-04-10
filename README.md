# Kinect_Depth
1.Build and install [OpenNI](https://github.com/OpenNI/OpenNI)&&[Sensor](https://github.com/ruedigerH2/SensorKinect) according their README instroduction.   

2.Doxygen is necessary other ways make will fail.Using **apt-get install doxygen** will download 900M+ source.So we can build && install from [doxygen source](https://github.com/doxygen/doxygen).    

3.Editing /usr/etc/primesense/GlobalDefaultsKinect.ini to uncomment the **;UsbInterface=2** line and change into **UsbInterface=1**   

4.Bulid main.cpp:
  g++ -I/usr/include/ni/ -I/usr/include/GL -c main.cpp
  g++ -o main main.o libOpenNI.so   
  
5.**./mian** to run the binnary then get the depth output from Kinect. 
     
Output format:     
     time>[x,y]:data
     
     
     time: system uptime
     x: x_axis
     y: y_axis
     data: raw depth data,data~[0,2^11]  


