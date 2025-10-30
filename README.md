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

