# 学习笔记（一）_环境配置

## 操作环境

硬件：PC
系统：windows10professional
软件：
cmake：3.15.1 [下载地址](https://cmake.org/download/)
visual studio 2017（现在是2019） [下载地址](https://visualstudio.microsoft.com/zh-hans/?rr=https%3A%2F%2Fwww.bing.com%2F)
opencv 4.1.1 [下载地址](https://opencv.org/releases/)
opencv_contrib [下载地址](https://github.com/opencv/opencv_contrib/releases/tag/4.1.1)

---

## 软件安装


### Cmake安装
直接默认安装即可。

### Visual Studio 2017安装
目前是2019版本，大学时期就安装了2017的社区版。
我的是全部组件都安装了。这里省略。

### OpenCV4.1.1
1. 所有安装路径推荐只包含英文。
1. 下载两个资源。
1. 将opencv_contrib4.1.1解压到指定位置(路径建议全英文)。
1. 执行opencv-4.1.1-vc14_vc15.exe解压到指定位置。
1. 打开cmake，按以下步骤执行
    * 设置`Where is the source code`到路径`你的路径/opencv4.1.1/opencv/sources`。
    * 设置`where to build the binaries`为你想要的输出路径。
    * 点击`Configure`并确定。
    * 设置`Specify the generator for this project`为`Visual Studio 15 2017`s（根据自己的版本选）。
    * 等待编译。
    * 显示`Configuring done`完成。
    * **这里强调如果列表为红色，需要再次单击`Configure`直到列表不出现红色为止**。
    * 找到列表中的`OPENCV_EXTRA_MODULES_PATH`设置为`你的路径/opencv_contrib-4.1.1/modeles`，**通过cmake选择路径，不能自己复制路径**。
    * 找到列表中的`OPENCV_ENABLE_NONFREE`并勾选。
    * 单机Generate
    * 完成后左下角显示**Configuring done， Generating done**。
1. 在输出文件夹找到OpenCV.sln文件，即编译成功。

### VS2017编译
1. 用VS打开`OpenCV.sln`，等待。
1. 点击`生成->重新生成解决方案`，继续等待
1.    
    
    
# 未完待续