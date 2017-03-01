# Jenkins for iOS with Fastlane and SVN
![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/1.png)
##    一、搭建环境
Jenkins的安装需要JDK环境，JDK安装方法自行参考网络。Jenkins的安装有两种方式，一种是java包安装，另一种是pkg可执行程序（两种安装后的配置一样，pkg安装会在电脑上多出一个用户）。本文采用war包 + tomcat安装方法。
### 1   安装[Java](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)环境，请自行下载安装
![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/2.png)
### 2   安装[tomcat](https://tomcat.apache.org/),打开官网地址
![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/3.png)
#### 2.1    将下载的zip包解压（可以重命名），把解压后的文件夹放到 /Library下。
![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/4.png)
#### 2.2    在终端启动Tomcat服务器，这里首先cd到Tomcat的bin目录：   
`sudo chmod 755 *.sh`<br>
按回车键之后会提示输入密码，请输入管理员密码。之后输入并回车:<br>
`sudo sh startup.sh`<br>
执行完`startup.sh`的结果如下:

![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/5.png)

然后在浏览器里输入：`localhost:8080`就OK了。如下图所示:

![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/6.png)

##    二、Jenkins安装，打开[官网](https://jenkins.io/index.html)
![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/7.png)

在tomcat的安装目录下，找到`webapps`，然后将下载的`war`包放到该文件夹下即可。
在浏览器里输入：`localhost:8080/Jenkins/`，几分钟后即可以看到如下界面：

![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/8.png)

根据自己安装的红色提示，前往该文件打开，找到初始密码。（pkg安装模式，会提示没有打开文件夹权限，则需要你手动获取对应的读写权限）
接下来则是傻瓜式操作。如下图所示：

![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/9.png)
![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/10.png)
![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/11.png)
![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/12.png)

设置用户名密码邮件等，最后Save and Finish，OK，到此Jenkins初始化安装完成。

##   三、安装系统插件
在“系统管理->管理插件->可选插件”中，选择下载必要的插件。
1、	Publish Over FTP Plugin
2、	Email Extension Plugin
