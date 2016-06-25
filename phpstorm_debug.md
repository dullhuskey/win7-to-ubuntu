#PHPStorm debug单步跟踪设置

1. **安装XDebug**
	* https://xdebug.org/download.php 页面,寻找适合的版本下载 Source 包。xdebug-2.3.3.tgz
	* `#tar zxvf xdebug-2.3.3.tgz`	 
	* `#cd xdebug-2.3.3`
	* `#phpize` 或者 `#/usr/local/php/bin/phpize`
	* `#./configure --enable-xdebug`
	* `#make`
	* `#cp modules/xdebug.so /usr/local/php/lib/php/extensions/no-debug-non-zts-20131226/` PHP extensions 路径根据自己实际情况替换
	* `#vi /usr/local/php.ini`
	* 在底部添加xdebug配置
		```
		[xDebug]
		zend_extension=/usr/local/php/lib/php/extensions/no-debug-non-zts-20131226/xdebug.so
		xdebug.remote_enable=1
		xdebug.remote_host=mws.local.com
		xdebug.max_nesting_level = 500

		```
	* 重新加载php配置 `#/etc/init.d/php-fpm reload`
	
2. **Chrome 插件Xdebug helper 安装以及设置**
	* 在chrome 扩展插件中搜索`xdebug`, 并安装
	* 设置xdebug配置, 在 **IDE KEY**中选择 phpstorm
3. **设置php.ini**
	* 设置HOST以及PATH
		```
		[HOST=ets.local.com]
		open_basedir=/home/wwwroot/ets.local.com/:/tmp/
		[PATH=/home/wwwroot/ets.local.com]
		open_basedir=/home/wwwroot/ets.local.com/:/tmp/

		```
4. ** PHPStorm 开启调试**
	* 菜单> run > web server debug validation .
	* 设置 Url to validation script 为 `http://ets.local.com` 点击 `validate`
	* 根据提示解决还存在的问题.
	* 点击 菜单 > Run > Start listen ..
	* 浏览器输入带跟踪链接, 并将xdebug helper 插件设置成 debug 模式.即可进行跟踪.
	* 菜单> Run > Break at  first line in php Script 选中则程序从进入时就开始跟踪而不是在遇到断点才跟踪. 根据自己需求灵活设置.

