# Note_ADB_指令



--ADB (Androi Debug Bridge)--
 
 Log 日志
 
adb logcat >C:\Users\EminemRen\Desktop\erro.txt


adb logcat *:E>>C:\Users\EminemRen\Desktop\erro.txt
 
 
adb shell
logcat|grep com.libratone


查看版本
ADB 的安装这里就不多说了，输入以下命令有如下提示就证明你环境ok，否则自行网上搜索解决下。

$ adb version

Android Debug Bridge version 1.0.36
Revision 8f855a3d9b35-android

查看连接设备
输入以下命令可以查询已连接的设备与模拟器：

$ adb devices

List of devices attached
02ae0c1021089daf       device

安装一个apk，执行以下命令：
adb install <apkfile>

// 如: adb install demo.apk
如果不是当前目录，则后面要跟路径名：

adb install /Users/storm/temp/demo.apk
保留数据和缓存文件，重新安装apk：

adb install -r demo.apk
安装apk到sd卡：

adb install -s demo.apk
卸载

直接卸载：
adb uninstall <package>

// 如：adb uninstall com.stormzhang.demo
卸载 app 但保留数据和缓存文件：

adb uninstall -k com.stormzhang.demo

启动/停止 Server
一般来说，下面两个命令基本不会用到，因为只要设备连接正确，会自动启动 adb server 的，不过大家也需要知道这俩命令：

启动 adb server ：
adb start-server

停止 adb server ：
adb kill-server

列出手机装的所有app的包名：
adb shell pm list packages

列出系统应用的所有包名：
adb shell pm list packages -s

列出除了系统应用的第三方应用包名：
adb shell pm list packages -3

使用 grep 来过滤：
adb shell pm list packages | grep qq

清除应用数据与缓存
有些时候我们测试需要清除数据与缓存，则需要用到如下命令：

adb shell pm clear <packagename>

// 如：adb shell pm clear com.stormzhang.demo

启动应用
如果我们想要通过 adb 来启动应用
adb shell am start -n com.stormzhang.demo/.ui.SplashActivity

强制停止应用
有些时候应用卡死了，需要强制停止，则执行以下命令：

adb shell am force-stop <packagename>

// 如：adb shell am force-stop cn.androidstar.demo

查看日志
adb logcat

重启
adb reboot

获取序列号
$adb get-serialno

02ae0c1021089daf

获取 MAC 地址
$adb shell  cat /sys/class/net/wlan0/address

bc:f5:ac:f9:f7:c8

查看设备型号
$adb shell getprop ro.product.model

Nexus 5

查看 Android 系统版本
$adb shell getprop ro.build.version.release

7.0.1

查看屏幕分辨率
$adb shell wm size

Physical size: 1080×1920

查看屏幕密度
$adb shell wm density

Physical density: 480

 
adb 无线调试 （usb 先连接 ，设置好之后可无线）
 
adb tcpip 5555
adb connect 192.168.125.113 (手机ip，电脑手机再同一个wifi环境下)
adb disconnect 192.168.125.133 (断开已有的无线连接)

adb shell ifconfig or adb shell ip addr (查看连接的设备ip)
