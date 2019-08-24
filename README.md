----------
*****Robomaster2019全国赛北理珠毅恒团队步兵视觉*****
![步兵](./images/ZZP_0896.JPG)

 1. **功能介绍**
 ----------
·本开源项目中Robomaster2019装甲板视觉识别和能量机关视觉识别。
·自定义串口通讯协议与stm32进行通讯控制云台运动。
·自动击打能量机关的控制逻辑。
·基于Qcustomplot编写的绘制波形的上位机，可实时上传数据并显示


 2. **效果展示**
 ----------
·装甲板识别
普通相机选用了4mm焦距640x360分辨率，可识别0m至2m装甲板，工业相机选用6mm焦距640x480分辨率，可识别1m至7m装甲板。装甲板识别预处理采用ICRA的颜色包围灰度灯条的思想，利用选择最小强度的方式，大大降低了低分辨率内八误识别问题。整体算法识别采用多线程，跑一帧图像1ms，加入roi可降至0.3ms满足实时性。

![视觉识别](./images/autovision.gif)

![自瞄效果](./images/autoaim_2.gif)

·能量机关识别
能量机关采用传统方法，处理单帧图像在1.5ms左右

![视觉识别](./images/buffvision.gif)

·上位机绘制波形

![绘制机器人距能量机关距离](./images/plot.gif)


 3. **依赖工具、软硬件环境**
 ----------
 软件运行环境：
 •	ubuntu 16.04
 •	OpenCV 3.4.6
 •	Qt Creator 5.12
 •	CMake 3.5.1
 •	GCC 5.4.0
 硬件
 ·免驱摄像头
 ·USB转TTL串口


 4. **编译、安装方式**
----------
使用Qmake进行编译

 5. **文件目录结构及文件用途说明**
----------

``` 
YIHENG_ZHBIT_VISION\
│  base.h							基础集成功能头文件，便于修改宏定义
│  license.txt
│  mainwindow.cpp					绘制波形窗口
│  mainwindow.h		
│  mainwindow.ui					上位机ui界面
│  qcustomplot.cpp					绘图开源库
│  qcustomplot.h
│  README.md
│  rm-vision.pro				
│  
├─armor_detection					装甲板识别
│      armor_detect.cpp
│      armor_detect.h
│      
├─buff_detection					能量机关识别
│      buff_detect.cpp
│      buff_detect.h
│      buff_offset.xml
│      
├─camera							相机类
│  │  camera_device.cpp			相机驱动
│  │  camera_device.h
│  │  save_video.cpp				保存录像
│  │  save_video.h
│  │  
│  └─camera_param				相机标定文件
│          camera4mm.xml
│          camera8mm.xml
│          galaxy_0.xml
│          
└─common							常用文件夹
    │  main.cpp					开启线程	
    │  thread_control.cpp			各线程控制
    │  thread_control.h
    │  
    ├─filter						滤波器（kalman、二项式）
    │      predict.cpp				
    │      predict.h
    │      
    ├─serial						串口通讯
    │      serial_port.cpp
    │      serial_port.h
    │      
    └─solve_angle					角度解算
            solve_angle.cpp
            solve_angle.h
            
```

 6. **软件与硬件的系统框图，数据流图**
----------

 7. **原理介绍与理论支持分析**
----------

 8. **软件架构**
----------

 9. **未来优化的方向（RoadMap）**
----------