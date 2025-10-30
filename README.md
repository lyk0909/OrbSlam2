# ORB-SLAM2 踩坑 & 运行记录

---

## 1. 依赖安装
| 问题 | 原因 | 解决 |
|---|---|---|
| `sudo apt install libjpeg-dev libpng12-dev …` 报 `libpng12-dev` 不存在 | Ubuntu 20.04 仓库已移除 `libpng12` | 改为 `libpng-dev`：&lt;br&gt;`sudo apt install libjpeg-dev libpng-dev libtiff5-dev libopenexr-dev` |

---

## 2. 编译卡死
| 问题 | 原因 | 解决 |
|---|---|---|
| 执行 `./build.sh` 时虚拟机直接卡死 | 默认 `make -j` 占用全部逻辑核，虚拟机资源不足 | 编辑 `build.sh` 把 `make -j` 改成 `make -j2`（或更小） |

---

## 3. 运行示例
### 3.1 启动命令
```bash
cd ~/repos/ORB_SLAM2/
./Examples/Monocular/mono_euroc \
    Vocabulary/ORBvoc.txt \
    Examples/Monocular/EuRoC.yaml \
    data/MH_01_easy/mav0/cam0/data \
    Examples/Monocular/EuRoC_TimeStamps/MH01.txt
```
### 3.2 运行日志
```bash
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
Gtk-Message: 12:06:55
```
## 4. 小结
| 类别     | 现象                                  | 处理                                                      |
| ------ | ----------------------------------- | ------------------------------------------------------- |
| **依赖** | `libpng12-dev` 缺失                   | 用 `libpng-dev` 替代                                       |
| **编译** | 虚拟机卡死                               | 把 `make -j` 改成 `make -j2`                               |
| **运行** | `Wrong initialization, reseting...` | 正常迭代，可忽略                                                |
| **警告** | `canberra-gtk-module`               | 不影响算法，可选 `sudo apt install libcanberra-gtk-module` 消除提示 |
