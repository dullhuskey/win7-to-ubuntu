# sublime 安装以及中文输入修复

1. 从部门 移动硬盘   (/Elements/软件安装包/sublime/) 拷贝sublime-text_build-3103_amd64.deb 到/home/dullhuskey/
2. 基础安装 sudo dpkg -i sublime-text_build-3103_amd64.deb
3. 安装完成后, 通过命令 ```subl``` 直接调出编辑窗口

> 中文输入法修复

1. 从 https://github.com/YoungZHU/sublime-imfix 获取 sublime-imfix.c 保存到/home/dullhuskey/下
2. 编译 ```gcc -shared -o libsublime-imfix.so sublime_imfix.c  `pkg-config --libs --cflags gtk+-2.0` -fPIC```
  * 如果出现 "NO package 'gek+-2.0' found" 需要安装依赖包 | ```sudo apt-get install libgtk2.0-dev```  | 再次执行 ```gcc -shared -o libsublime-imfix.so sublime_imfix.c  `pkg-config --libs --cflags gtk+-2.0` -fPIC```
  * 上一部操作会生成一个文件 libsublime-imfix.so 
3. 将 libsublime-imfix.so 移动到 /opt/sublime_text/目录下   ```sudo mv libsublime-imfix.so /opt/sublime_text```
4. 修改/usr/bin/subl 文件内容 
	```
	#!/bin/sh
	将
	exec /opt/sublime_text/sublime_text "@"
	修改为
	LD_PRELOAD=/opt/sublime_text/libsublime-imfix.so exec /opt/sublime_text/sublime_text "$@"
	```
5. 重新打开sublime 编辑器即可输入中文