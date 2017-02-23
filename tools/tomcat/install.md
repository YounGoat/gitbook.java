#	在不同的操作系统中安装 Tomcat

##	在 Mac OS X 中安装 Tomcat

```bash
# 从官方网站下载二进制包。
wget http://apache.fayea.com/tomcat/tomcat-9/v9.0.0.M17/bin/apache-tomcat-9.0.0.M17.tar.gz

# 解压缩并重命名文件夹。
tar -xvf apache-tomcat-9.0.0.M17.tar.gz
mv apache-tomcat-9.0.0.M17 Tomcat9

# 移动文件夹至系统库目录。`	`
sudo mv Tomcat9 /Library/
cd /Library/
# 这一步骤不是必须的。

# 启动守护进程。
cd Tomcat9/bin/
./startup.sh
# 守护进程将维持一个默认端口为 8080 的 HTTP 服务。

# 在浏览器中打开首页。
open http://localhost:8080
```

如果希望使用首页上提供的管理功能，需要先启用管理员账号。启用的方法很简单，需要修改 ./conf/tomcat-users.xml 文件并重启服务。

##	默认应用

缺省安装的 Tomcat 拥有以下默认应用：

*	http://localhost:8080/
*	http://localhost:8080/docs/
*	http://localhost:8080/examples/
*	http://localhost:8080/host-manager/
*	http://localhost:8080/manager/

##	管理脚本

在 Tomcat 安装目录的 /bin/ 子目录下，有若干预设的脚本（或批处理文件），常用的有：

*	*startup.sh*, run catalina.sh
	>	Start Script for the CATALINA Server

*	*catalina.sh*, run setenv.sh, setclasspath.sh  
 	>	Control Script for the CATALINA Server

*	*daemon.sh*
	>	Commons Daemon wrapper script

*	*shutdown.sh*
	>	Stop script for the CATALINA Server

*	*setenv.sh*  
	该脚本默认是不存在的，但如果需要设置或修改 Tomcat 相关的环境变量，建议创建这一脚本并在其中完成。其他管理脚本会在合适的时机尝试调用 setenv.sh（如果存在的话）。

*	*setclasspath.sh*


##	REF

*	*A Complete Guide To Tomcat Start-Up*  
	https://www.mulesoft.com/tcat/tomcat-start

*	*Installing Tomcat 6.0 On Linux, Mac OS X, And Windows*  
	https://www.mulesoft.com/tcat/tomcat-60
