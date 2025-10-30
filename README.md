# OrbSlam2
操作指南见https://www.cnblogs.com/flypopo/p/18304242

出现问题：在执行安装 ORB_SLAM2的代码./build.sh时出现了虚拟机卡死的情况

问题原因：./build.sh中使用make -j对虚拟机性能要求较高

解决方法：在终端执行gedit build.sh，然后将make -j改为make -j2

执行命令：在终端命令执行cd ~/repos/ORB_SLAM2/，然后执行./Examples/Monocular/mono_euroc \
    Vocabulary/ORBvoc.txt \
    Examples/Monocular/EuRoC.yaml \
    data/MH_01_easy/mav0/cam0/data \
    Examples/Monocular/EuRoC_TimeStamps/MH01.txt

执行结果：

ORB-SLAM2 Copyright (C) 2014-2016 Raul Mur-Artal, University of Zaragoza.
This program comes with ABSOLUTELY NO WARRANTY;
This is free software, and you are welcome to redistribute it
under certain conditions. See LICENSE.txt.

Input sensor was set to: Monocular

Loading ORB Vocabulary. This could take a while...
Vocabulary loaded!


Camera Parameters: 
- fx: 458.654
- fy: 457.296
- cx: 367.215
- cy: 248.375
- k1: -0.283408
- k2: 0.0739591
- p1: 0.00019359
- p2: 1.76187e-05
- fps: 20
- color order: RGB (ignored if grayscale)

ORB Extractor Parameters: 
- Number of Features: 1000
- Scale Levels: 8
- Scale Factor: 1.2
- Initial Fast Threshold: 20
- Minimum Fast Threshold: 7

-------
Start processing sequence ...
Images in the sequence: 3682

New Map created with 87 points
Wrong initialization, reseting...
System Reseting
Gtk-Message: 12:06:55.491: Failed to load module "canberra-gtk-module"
Reseting Local Mapper... done
Reseting Loop Closing... done
Reseting Database... done
New Map created with 81 points
Wrong initialization, reseting...
System Reseting
Reseting Local Mapper... done
Reseting Loop Closing... done
Reseting Database... done
New Map created with 83 points
Wrong initialization, reseting...
System Reseting
Reseting Local Mapper... done
Reseting Loop Closing... done
Reseting Database... done
New Map created with 102 points
-------

median tracking time: 0.0460165
mean tracking time: 0.0512518

Saving keyframe trajectory to KeyFrameTrajectory.txt ...

trajectory saved!


