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

###   1   安装系统插件
在“系统管理->管理插件->可选插件”中，选择下载必要的插件。<br>
1、	Publish Over FTP Plugin<br>
2、	Email Extension Plugin<br>
###   2   系统配置
####   2.1   在“系统管理->系统设置”中找到“Jenkins Location”配置，配置如下图：
![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/13.png)
####   2.2   在“系统管理->系统设置”中找到“Publish over FTP”配置，配置如下图：
![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/14.png)
####   2.3   在“系统管理->系统设置”中找到“Extended E-mail Notification”配置，配置如下图：
![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/15.png)
![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/16.png)
![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/17.png)


####   Default Content样例：
```
(本邮件是程序自动下发的，请勿回复！)<br/><hr/>
项目名称：$PROJECT_NAME<br/><hr/>
版本号：${FILE,path="version.txt"}<br/><hr/>
svn版本号：${SVN_REVISION}<br/><hr/>
构建状态：$BUILD_STATUS<br/><hr/>
触发原因：${CAUSE}<br/><hr/>
构建日志地址：<a href="${BUILD_URL}console">${BUILD_URL}console</a><br/><hr/>
变更集:${JELLY_SCRIPT,template="html"}<br/><hr/>
```
##    三、Fastlane安装
###   1   安装ruby版本>=2.2
####    1.1   安装rvm版本管理器
  `$ curl -L https://get.rvm.io | bash -s stable`
####    1.2   等待一段时间后， 使用一下命令进行验证
  ```
	$ source ~/.bashrc
  $ source ~/.bash_profile
  ```
####    1.3   测试是否安装正常
  `$ rvm -v`
如果出现rvm（版本号）.....基本就算是安装RVM成功了。<br>
补充一些常用命令：<br>
```
    rvm list 查看已安装ruby
    rvm list known 列出ruby可安装版本信息
    rvm remove 2.2.2 卸载一个已安装的ruby版本
    gem source 查看已有源
    gem sources -a http://ruby.taobao.org把源切换至淘宝镜像服务器
```
####    1.4   安装ruby
    `$ rvm install 2.4`

###   2   安装fastlane，详细资料请看[Github地址](https://github.com/fastlane/fastlane)
####    2.1   命令安装
    `$ sudo gem install fastlane`
####    2.2   查看版本
    `$ fastlane –v`<br>
    ![image](https://github.com/lxbboy326/jenkins-for-iOS-with-fastlane-and-svn/blob/master/resources/18.png)





