# StudyRecord


查看Android应用包名、Activity的几个方法
一、只有Apk的情况

（1）aapt

使用命令行aapt dump xmltree ColaBox.apk AndroidManifest.xml

（2）使用apktool

使用反编译工具apktool，反编译后打开AndroidManifest.xml文件，查找方式同“有源码情况”

（3）aapt

aapt dump badging xxx.apk (|findstr "package")


二、没有apk，应用已经安装到手机或虚拟机中

1.logcat

.清除logcat内容，使用命令adb logcat -c

.启动logcat，使用命令adb logcat ActivityManager:I *:s

.启动要查看的程序，

2.dumpsys

（1）启动要查看的程序；

（2）命令行输入：adb shell dumpsys window w |findstr \/ |findstr name=



三、获取Activity方式

方法1:dumpsys window


先打开要获取的App，再输入以下命令

adb shell "dumpsys window | grep mCurrent"

adb shell dumpsys window | findstr mCurrent

方法2:dumpsys activity


先打开要获取的App，再输入以下命令

adb shell "dumpsys activity | grep mFocusedActivity"

adb shell dumpsys activity | findstr mFocusedActivity





注：
1. findstr 和 grep 查找字符串说明
findstr：windows平台查找字符串命令， 一般格式如下：
adb shell  xxx  | findstr xxx
grep：linux平台查找字符串命令，一般先adb shell 进入shell命令行再使用，也可直接使用，把shell 后面带grep的命令加双引号即可：
