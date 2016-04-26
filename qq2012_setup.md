# qq2012国际版安装

1. 从Ubuntu软件中心安装 "Wine Windows 程序加载器" (安装时间10min左右)
2. 从部门 移动硬盘   (/Elements/软件安装包/linux/) 拷贝wine-qqintl.zip 到/home/shaco/
3. 解压安装
  * 解压 ```unzip wine-qqintl.zip``` | ```cd wine-qqintl.zip```
  * 检查是否有安装过qq  ```dpkg -l | grep qq``` | 如果有则卸载 ```sudo dpkg -P wine-qqintl```
  * 64 位系统先在终端运行 ： ```sudo apt-get install libgtk2.0-0:i386```
  * 运行进行安装 
     ① sudo dpkg -i fonts-wqy-microhei_0.2.0-beta-2_all.deb
     ② sudo dpkg -i ttf-wqy-microhei_0.2.0-beta-2_all.deb
     ③ sudo dpkg -i wine-qqintl_0.1.3-2_i386.deb
  * 安装完成后,通过输入 wine-qqintl 启动QQ.
4. 简化调用QQ命令
  * 创建qq命令 ```cd /usr/bin``` | ```sudo vi qq```
  * 增加一下代码

  	#!/bin/bash
  	wine-qqintl &

  * 保存,并修改文件权限 ```sudo chown shaco:shaco qq``` | ```sudo chmod u+rwx qq```
  * 以后就可以通过命令行输入```qq``` 启动QQ了
