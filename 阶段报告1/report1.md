### 一、 阶段任务
  hubot、slack、ansible、prometheus、grafana等基础环境的搭建。    
### 二、 完成情况  
   hubot + slack 智能机器人实现；ansible连接远程主机实现；prometheus 实现；prometheus + grafana未实现。    
### 三、 遇到的问题及解决方法  
（1）执行“npm install”时出现如下错误：    
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190406152808251.png)  
       想卸载npm重新安装，会出现错误：    
       ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190406152830637.png)  
      解决办法：强制卸载 ，执行：`sudo apt-get purge nodejs-legacy nodejs`，然后再重新下载npm，nodejs等等。  
（2）安装部署ansible，执行`ssh-keygen -t rsa` ，在输入密码时填写了自己设置的密码，导致在远连接时需要远程主机用户的密码，而且在ssh远程主机时出现了要求输入本机密码的错误。
       解决办法：在执行`ssh-keygen -t rsa` 时，一直按回车，不输入密码生成公钥和密钥文件。  
 (3）ssh远程主机，出现“pression denied”。  
       解决办法：进入 `/etc/ssh/sshd_config`，修改为`PermitRootLogin yes`，然后重启ssh,即可。(注意：本机和远程主机要在同一网段！）  
       （4）在启动 grafana后，访问页面`http://loaclhost:3000`，登录执行设置数据源，配置  prometheus 时，出现错误：“HTTP ERROR:Bad Getway”。
       解决办法：还没找到。  
       ### 1. 安装Hubot：权限问题
在执行命令“yo hubot”的时候，出现下图错误提示：
![image](https://github.com/Breeze16/HubotStudy/blob/master/pictures/yo_error.png)                         
根据错误提示，是打开某文件夹权限出问题了。我去找了具体的文件夹，发现权限是root下，于是我使用chmod改变了权限组，解决了这个问题。
安装好Hubot后，出现了如下界面：
![image](https://github.com/Breeze16/HubotStudy/blob/master/pictures/robot.png)
  （4）安装Slack：翻墙问题
下载好Slack后，发现无法正常打开。想到老师有说需要翻墙，于是我下载了蓝灯。翻墙后成功打开了Slack桌面版。
  （5）连接时出现的错误
将Hubot连接 到Slack上，需要在Slack上下载一个插件。下载好后，将其解压后放在了Hubot文件里。不过我现在没怎么搞懂这个插件应该如何用。
然后就是连接问题了。根据教程配置环境变量时，输入以下命令：，出现错误提示：body-parser deprecated undefined extended: provide extended option node_modules。查找了很多资料也没找到具体的解决办法。我刚开始输入的配置命令是：env HUBOT_SLACK_TOKEN=xoxb-582490373506-582410260944-3dgJTSFfpoDihwFEfjbpvVnU ./bin/hubot --adapter slack。后面根据老师的提示，将命令改成了：env HUBOT_SLACK_TOKEN=xoxb-582490373506-582410260944-3dgJTSFfpoDihwFEfjbpvVnU ./bin/hubot -a slack。试着运行了一下发现Slack上的Hubot可以正常使用了。如下图：                   
![](https://github.com/Breeze16/HubotStudy/blob/master/pictures/ping_pong.png)               
  （6）连接localhost成功，但是连接另一个组员时出现图二错误。这个错误老师也说没有遇到过，可能跟我的ubuntu版本或者ansible版本有关。暂时没有相关的解决办法。不过我组员的电脑可以成功连接到我这边，故而在后续开发中不会影响，因此这个问题被搁浅了。                    
![](https://github.com/Breeze16/HubotStudy/blob/master/pictures/success.png)           
![](https://github.com/Breeze16/HubotStudy/blob/master/pictures/Unreacheable.png)      
图一：连接本地成功;图二：连接外网失败。                 
 （7）配置ssh时，无法连接到另一个组员的IP。后来发现是我们没在一个网段上。           
### 四、 后续工作  
 实现prometheus + grafana搭建监控系统，对数据进行采集，存储，并且能够对采集到的数据进行分析。  
