---
title: "ADB命令"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/ye081mwgk5dg45t9"
slug: "ye081mwgk5dg45t9"
doc_id: "179175331"
updated: "2024-07-29T08:34:29.000Z"
tags:
  - yuque
---

# ADB命令

adb version

adb devices

adb help

//杀掉ADB服务

adb kill-server

//启动adb服务

adb start-server

//查看对应设备的安卓版本

adb shell getprop ro.build.version.release

//安装apk

adb install -r -g -d

-r：表示覆盖安装，保留数据。

-g：表示授予应用程序所有运行时权限。

-d：表示允许安装降级版本（如果你在安装旧版本的APK）。

//删除app以及数据

adb uninstall  com.xx.xx

//删除app但保留数据

adb uninstall com.xx.xx -k

//查看ip

adb shell ifconfig  （wlan0  inet addr:192.xxxxxxxx）

//切换为无线，且使用5555端口

adb tcpip 5555

//连接这个ip

adb connnect 192.xxxxx

adb logcat -s Unity 专门获得Unity相关的日志

adb logcat -c 清理缓存

adb logcat -v time>E:/Log/logXXL.txt 生产日志到E盘

//获得权限

adb shell setprop nibiru.root.allowed 1

adb root

adb disable-verity

//获得权限

adb root

adb remount

//删除名字为xxx的文件夹及其里面的所有文件

rm -r xxx

//删除文件xxx

rm xxx

//删除xxx的文件夹

rmdir xxx

//创建文件夹

mkdir xxx

//修改命名

mv oldName newName

//展示所有文件并带上时间，同时倒序

 ls -lat -t

//列出所有的socket连接

adb forward --list

//查看手机端安装的所有APP包名

adb shell pm list packages

//仅显示带关键字的包名

adb shell pm list packages | findstr <关键字>

//推送电脑的文件到设备上

adb push  电脑源数据路径   设备目标路径

//拉取设备的文件到电脑上

adb pull    设备源数据路径    电脑目标路径

在进入到 shell 环境后，将源文件的路径，拷贝到目标路径，如果存在则覆盖

adb shell  cp <源文件路径> <目标文件路径>

adb push E:\SY\2024.7.1\libc++_shared.so    /data/app/~~vKIb88ldheD6Er_sCMCV7g==/com.vrcxzx.SY_CatchImage-JJbtAC8PvFbm-_8c4-Bo7w==/lib/arm64

adb push E:\SY\2024.7.1\libncvr_v0_9.so     /data/app/~~vKIb88ldheD6Er_sCMCV7g==/com.vrcxzx.SY_CatchImage-JJbtAC8PvFbm-_8c4-Bo7w==/lib/arm64

输入adb devices时，提示：Unable to start adb server: error: protocol fault (couldn't read status): Connection reset by peer

原因：5037端口被占用了（5037为adb默认端口）

//查看所有端口占用

netstat -aon

//查找某个端口的进程

netstat -aon|findstr "xxx"

//查看被占用端口对应的PID

tasklist|findstr "xxx"

//停止某个进程

taskkill /pid xxx /f

//截图

adb shell screencap /sdcard/screen.png

//录制视频

adb shell screenrecord /sdcard/demo.mp4
