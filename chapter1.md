# lnmp环境配置

1. 安装 lnmp       (部门 移动硬盘   /Elements/软件安装包/linux/lnmp/lnmp.full.1.1.tar.gz)
   * 解压   ```tar -zxvf lnmp.full.1.1.tar.gz```
   * 安装   ```cd lnmp.full.1.1 & sudo ./ubuntu.sh```
   * 按步骤设置 | mysql root 必须设置密码 | PHP 5.3.28 | mysql 5.5.37
   
2. 网站代码获取
   * ```cd /home/wwwroot/```
   * 通过git拉取网站代码  ```git clone git@192.168.1.4:/opt/git/ets.git ```
   * 修改网站目录  ```mv ets ets.local.com```
   * 复制配置文件  ```scp root@192.168.1.4:/home/wwwroot/ets.local.com/app/etc/local.xml app/etc/  ```
   * 修改配置文件  ```vi app/etc/local.xml```  | 修改 host 为 192.168.1.4 | 数据库链接帐号密码修改
   * 切换到在开发 主分支  ```git branch develop origin/develop```  

3. 复制NGINX服务器配置
  * 复制服务器配置文件 ```scp -r root@192.168.1.4:/usr/local/nginx/conf/* /usr/local/nginx/conf/```
  * 清理掉不需要的VHOST配置  |  /usr/loca/nginx/conf/vhost/ 里除了 ets.local.com.conf 都可以清掉
 
4. 配置hosts文件  | ```sudo vi /etc/hosts ``` | 添加 127.0.0.1 ets.local.com 

5. 增加 git 对 ets.local.com 的操作权限  
  * ```sudo usermod -a -G www shaco```   www 为WEB 用户组, shaco 为ubuntu 用户名
  * 更改网站所有权 | ```cd /home/wwwroot/```  | ```chown www:www -R ets.local.com```
      
7. 浏览器访问 ets.local.com 即可生效 
   

     


