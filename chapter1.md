# 学习笔记（一）_OpenCV安装及环境配置

## 操作环境

硬件：PC
系统：windows10professional
软件：

* cmake：3.15.1 [下载地址](https://cmake.org/download/)
* visual studio ~~2017~~（现在是2019） [下载地址]* (https://visualstudio.microsoft.com/zh-hans/?rr=https%3A%2F%2Fwww.bing.com%2F)
* opencv 4.1.1 [下载地址](https://opencv.org/releases/)
* opencv_contrib [下载地址](https://github.com/opencv/opencv_contrib/releases/tag/4.1.1)

---

## 软件安装


### Cmake安装
直接默认安装即可。

### ~~Visual Studio 2017安装~~
~~目前是2019版本，大学时期就安装了2017的社区版。
我的是全部组件都安装了。这里省略。~~

###Visual Studio 2019安装
根据步骤来即可，我这里选择全部安装，也可以根据需要选择不安装的内容。

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

### ~~VS2017~~VS2019编译
~~使用vs2017进行配置时遇到了一个大坑，费了很多时间，现在已经转到VS2019。~~
转到vs2019，vs2019的配置非常方便。

1. 创建一个空项目。
1. 创建一个空源文件。
1. 将上方的`x86`改为`x64`。
1. 点击`视图->其他窗口->属性管理器`。
1. 右键`Debug|x64`单击`属性`。
1. 进入`VC++目录`
1. 添加`你的路径\opencv\build\include`和`你的路径\opencv\build\include\opencv2`到`包含目录`
1. 添加`你的路径\opencv\build\x64\vc14\lib`到`库目录`。
1. 进入`链接器->输入`,添加`opencv_world411d.lib`进入`附加依赖项`（这里411是当前版本4.1.1，下一个版本4.1.2这里就是opencv_world412d.lib，以此类推）
1. 确定

在源文件中测试以下代码:
```c++
#include <opencv2/opencv.hpp>
using namespace cv;

int main() 
{
    Mat img = imread("C:\\IMG_0213.jpg");    //引号内选一张    自己计算机内的图片的路径
    imshow("card", img);    //打开一个窗口，显示图片
    waitKey(0);    //在键盘敲入字符前程序处于等待状态
    destroyAllWindows();    //关闭所有窗口
    return 0;
}
```

跑通即可

**PS. 因为opencv的配置还是比较麻烦的，这里如果想要保存配置，在`属性管理器->Debug|x64->Microsoft.Cpp.x64.user`右键添加新项目属性表，以后的项目在这里添加现有属性表即可**
    
    