# Jenkins for iOS with Fastlane and SVN
![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/1.png)
## 一、搭建环境
Jenkins的安装需要JDK环境，JDK安装方法自行参考网络。Jenkins的安装有两种方式，一种是java包安装，另一种是pkg可执行程序（两种安装后的配置一样，pkg安装会在电脑上多出一个用户）。本文采用war包 + tomcat安装方法。
### 1 安装[Java](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)环境，请自行下载安装
![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/2.png)
### 2 安装[tomcat](https://tomcat.apache.org/),打开官网地址
![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/3.png)
#### 2.1 将下载的zip包解压（可以重命名），把解压后的文件夹放到 /Library下。
![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/4.png)
#### 2.2 在终端启动Tomcat服务器，这里首先cd到Tomcat的bin目录：   
#####`sudo chmod 755 *.sh`<br>
按回车键之后会提示输入密码，请输入管理员密码。之后输入并回车:
#####`sudo sh startup.sh`<br>
执行完`startup.sh`的结果如下：     
![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/5.png)
然后在浏览器里输入：`localhost:8080`就OK了。如下图所示:
![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/6.png)

